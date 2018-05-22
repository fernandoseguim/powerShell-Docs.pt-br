---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Usando recursos com várias versões
ms.openlocfilehash: 6400d6506106657ba28fa1f9c83d9f8ee1c93ba3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="using-resources-with-multiple-versions"></a><span data-ttu-id="39437-103">Usando recursos com várias versões</span><span class="sxs-lookup"><span data-stu-id="39437-103">Using resources with multiple versions</span></span>

> <span data-ttu-id="39437-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="39437-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="39437-105">No PowerShell 5.0, recursos de DSC podem ter várias versões e as versões podem ser instaladas em um computador lado a lado.</span><span class="sxs-lookup"><span data-stu-id="39437-105">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="39437-106">Isso é implementado por ter várias versões de um módulo de recursos que estão contidas na mesma pasta de módulo.</span><span class="sxs-lookup"><span data-stu-id="39437-106">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>

## <a name="installing-multiple-resource-versions-side-by-side"></a><span data-ttu-id="39437-107">Instalando várias versões de recurso lado a lado</span><span class="sxs-lookup"><span data-stu-id="39437-107">Installing multiple resource versions side-by-side</span></span>

<span data-ttu-id="39437-108">Você pode usar os parâmetros **MinimumVersion**, **MaximumVersion** e **RequiredVersion** do cmdlet [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) para especificar qual versão de um módulo instalar.</span><span class="sxs-lookup"><span data-stu-id="39437-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="39437-109">Se você chamar **Install-Module** sem especificar uma versão, a versão mais recente será instalada.</span><span class="sxs-lookup"><span data-stu-id="39437-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="39437-110">Por exemplo, há várias versões do módulo **xFailOverCluster**, cada um com um recurso **xCluster**.</span><span class="sxs-lookup"><span data-stu-id="39437-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resouce.</span></span> <span data-ttu-id="39437-111">O resultado da chamada **Install-Module** sem especificar o número da versão é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="39437-111">The result of calling **Install-Module** without specifying the version number is as follows:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="39437-112">Agora, se você chamar **Install-Module** novamente, mas especificar uma **RequiredVersion** de 1.1.0.0, resultará no seguinte:</span><span class="sxs-lookup"><span data-stu-id="39437-112">Now, if you call **Install-Module** again, but specify a **RequiredVersion** of 1.1.0.0, it results in the following:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="39437-113">Especificando uma versão do recurso em uma configuração</span><span class="sxs-lookup"><span data-stu-id="39437-113">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="39437-114">Se você tiver vários recursos instalados em um computador, deve especificar a versão do recurso ao usá-lo em uma configuração.</span><span class="sxs-lookup"><span data-stu-id="39437-114">If you have multiple resources installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="39437-115">Faça isso especificando o parâmetro **ModuleVersion** da palavra-chave **Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="39437-115">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="39437-116">Se você não especificar a versão de um módulo de um recurso do qual tem mais de uma versão instalada, a configuração vai gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="39437-116">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="39437-117">A configuração a seguir mostra como especificar a versão do recurso a ser chamado:</span><span class="sxs-lookup"><span data-stu-id="39437-117">The following configuration shows how to specify the version of the resource to call:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

><span data-ttu-id="39437-118">Observação: o parâmetro ModuleVersion de Import-DscResource não está disponível no PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="39437-118">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="39437-119">No PowerShell 4.0, é possível especificar uma versão de módulo passando um objeto de especificação de módulo para o parâmetro ModuleName de Import-DscResource.</span><span class="sxs-lookup"><span data-stu-id="39437-119">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="39437-120">Um objeto de especificação de módulo é uma tabela de hash que contém as chaves ModuleName e RequiredVersion.</span><span class="sxs-lookup"><span data-stu-id="39437-120">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="39437-121">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="39437-121">For example:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

<span data-ttu-id="39437-122">Isso também funcionará no PowerShell 5.0, mas é recomendável que você use o parâmetro **ModuleVersion**.</span><span class="sxs-lookup"><span data-stu-id="39437-122">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="39437-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39437-123">See also</span></span>
* [<span data-ttu-id="39437-124">Configurações DSC</span><span class="sxs-lookup"><span data-stu-id="39437-124">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="39437-125">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="39437-125">DSC Resources</span></span>](resources.md)