---
ms.date: 06/20/2018
keywords: DSC,powershell,configuração,instalação
title: Recurso PackageManagementSource da DSC
ms.openlocfilehash: e51b5318288bef458567dd4b58d17caaea3ed69b
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046993"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="263ea-103">Recurso PackageManagementSource da DSC</span><span class="sxs-lookup"><span data-stu-id="263ea-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="263ea-104">Aplica-se a: Windows PowerShell 4.0, o Windows PowerShell 5.0, o Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="263ea-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="263ea-105">O recurso **PackageManagementSource** na Configuração do Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para registrar ou cancelar o registro de fontes de Gerenciamento de Pacote em um nó de destino.</span><span class="sxs-lookup"><span data-stu-id="263ea-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="263ea-106">**Fontes de Gerenciamento de Pacote registradas dessa forma são registradas no contexto do Sistema, podem ser usadas pela conta do Sistema ou pelo mecanismo de DSC.**</span><span class="sxs-lookup"><span data-stu-id="263ea-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="263ea-107">Este recurso requer o módulo **PackageManagement**, disponível em http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="263ea-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="263ea-108">O módulo **PackageManagement** deve ser pelo menos a versão 1.1.7.0 para as informações de propriedade a seguir estarem corretas.</span><span class="sxs-lookup"><span data-stu-id="263ea-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="263ea-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="263ea-109">Syntax</span></span>

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="263ea-110">Propriedades</span><span class="sxs-lookup"><span data-stu-id="263ea-110">Properties</span></span>

|  <span data-ttu-id="263ea-111">Propriedade</span><span class="sxs-lookup"><span data-stu-id="263ea-111">Property</span></span>  |  <span data-ttu-id="263ea-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="263ea-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="263ea-113">Nome</span><span class="sxs-lookup"><span data-stu-id="263ea-113">Name</span></span>| <span data-ttu-id="263ea-114">Especifica o nome da origem do pacote a ser registrado ou cancelado no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="263ea-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="263ea-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="263ea-115">ProviderName</span></span>| <span data-ttu-id="263ea-116">Especifica o nome do provedor OneGet por meio do qual você pode fornecer interoperabilidade com a origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="263ea-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="263ea-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="263ea-117">SourceLocation</span></span>| <span data-ttu-id="263ea-118">Especifica o URI de origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="263ea-118">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="263ea-119">Ensure</span><span class="sxs-lookup"><span data-stu-id="263ea-119">Ensure</span></span>| <span data-ttu-id="263ea-120">Determina se a origem do pacote deve ser registrada ou cancelada.</span><span class="sxs-lookup"><span data-stu-id="263ea-120">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="263ea-121">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="263ea-121">InstallationPolicy</span></span>| <span data-ttu-id="263ea-122">Usada por provedores como o Nuget interno.</span><span class="sxs-lookup"><span data-stu-id="263ea-122">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="263ea-123">Determina se você confia na origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="263ea-123">Determines whether you trust the package's source.</span></span> <span data-ttu-id="263ea-124">Um de: , . "Não confiável", "confiável".</span><span class="sxs-lookup"><span data-stu-id="263ea-124">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="263ea-125">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="263ea-125">SourceCredential</span></span>| <span data-ttu-id="263ea-126">Fornece acesso ao pacote em uma fonte remota.</span><span class="sxs-lookup"><span data-stu-id="263ea-126">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="263ea-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="263ea-127">Example</span></span>

<span data-ttu-id="263ea-128">Este exemplo registra a origem do pacote de http://nuget.org usando o recurso DSC **PackageManagementSource**.</span><span class="sxs-lookup"><span data-stu-id="263ea-128">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```