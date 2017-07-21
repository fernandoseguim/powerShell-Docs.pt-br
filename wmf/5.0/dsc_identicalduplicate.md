---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: d3a625d05eaf4e7448b4abf90499f6a94e2f7718
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="50170-102">Permitindo recursos duplicados idênticos em uma configuração</span><span class="sxs-lookup"><span data-stu-id="50170-102">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="50170-103">O DSC não permite nem manipula definições de recursos conflitantes dentro de uma configuração.</span><span class="sxs-lookup"><span data-stu-id="50170-103">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="50170-104">Em vez de tentar resolver o conflito, ele simplesmente falha.</span><span class="sxs-lookup"><span data-stu-id="50170-104">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="50170-105">Como a reutilização de configuração é cada mais utilizada por meio de recursos de composição, etc., os conflitos ocorrerão com mais frequência.</span><span class="sxs-lookup"><span data-stu-id="50170-105">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="50170-106">Quando definições de recursos conflitantes forem idênticas, o DSC deverá ter inteligência para permiti-las.</span><span class="sxs-lookup"><span data-stu-id="50170-106">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="50170-107">Com esta versão, damos suporte a várias instâncias de recursos com definições idênticas:</span><span class="sxs-lookup"><span data-stu-id="50170-107">With this release, we support having multiple resource instances that have identical definitions:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="50170-108">Em versões anteriores, o resultado seria uma compilação com falha devido a um conflito entre as instâncias de WindowsFeature FE_IIS e WindowsFeature Worker_IIS tentando garantir que a função “Web-Server” está instalada.</span><span class="sxs-lookup"><span data-stu-id="50170-108">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="50170-109">Observe que *todas* as propriedades que estão sendo configuradas são idênticas nessas duas configurações.</span><span class="sxs-lookup"><span data-stu-id="50170-109">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="50170-110">Uma vez que *todas* as propriedades nesses dois recursos são idênticas, agora isso resultará em uma compilação bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="50170-110">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span> 

<span data-ttu-id="50170-111">Se alguma das propriedades for diferente entre os dois recursos, elas não serão consideradas idênticas e a compilação falhará:</span><span class="sxs-lookup"><span data-stu-id="50170-111">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS
    {
        Ensure = 'Present'     # Ensure is Present here
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS
    {
        Ensure = 'Absent'      # Ensure property is Absent instead of Present
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="50170-112">Essa configuração bem semelhante falhará porque os recursos WindowsFeature FE_IIS e WindowsFeature Worker_IIS não serão mais idênticos e, portanto, entrarão em conflito.</span><span class="sxs-lookup"><span data-stu-id="50170-112">This very similar configuration will fail because the WindowsFeature FE_IIS and the WindowsFeature Worker_IIS resources are no longer identical and therefore conflict.</span></span>

