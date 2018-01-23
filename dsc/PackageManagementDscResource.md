---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Recurso PackageManagement de DSC
ms.openlocfilehash: 4cd7625af7ed0bb3fe971c826ac2075841cdfdc5
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="029a8-103">Recurso PackageManagement de DSC</span><span class="sxs-lookup"><span data-stu-id="029a8-103">DSC PackageManagement Resource</span></span>

> <span data-ttu-id="029a8-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="029a8-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="029a8-105">O recurso **PackageManagement** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para instalar ou desinstalar pacotes de Gerenciamento de Pacotes em um nó de destino.</span><span class="sxs-lookup"><span data-stu-id="029a8-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="029a8-106">Este recurso requer o módulo **PackageManagement**, disponível em http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="029a8-106">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="029a8-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="029a8-107">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="029a8-108">Propriedades</span><span class="sxs-lookup"><span data-stu-id="029a8-108">Properties</span></span>
|  <span data-ttu-id="029a8-109">Propriedade</span><span class="sxs-lookup"><span data-stu-id="029a8-109">Property</span></span>  |  <span data-ttu-id="029a8-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="029a8-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="029a8-111">Nome</span><span class="sxs-lookup"><span data-stu-id="029a8-111">Name</span></span>| <span data-ttu-id="029a8-112">Especifica o nome do Pacote a ser instalado ou desinstalado.</span><span class="sxs-lookup"><span data-stu-id="029a8-112">Specifies the name of the Package to be installed or uninstalled.</span></span>| 
| <span data-ttu-id="029a8-113">Origem</span><span class="sxs-lookup"><span data-stu-id="029a8-113">Source</span></span>| <span data-ttu-id="029a8-114">Especifica o nome da origem do pacote onde é possível encontrar o pacote.</span><span class="sxs-lookup"><span data-stu-id="029a8-114">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="029a8-115">Isso pode ser um URI ou uma fonte registrada com o recurso de DSC Register-PackageSource ou PackageManagementSource.</span><span class="sxs-lookup"><span data-stu-id="029a8-115">This can either be a URI or a source registered with Register-PackageSource or PackageManagementSource DSC resource.</span></span> <span data-ttu-id="029a8-116">O recurso de DSC MSFT_PackageManagementSource também pode registrar uma origem de pacote.</span><span class="sxs-lookup"><span data-stu-id="029a8-116">The DSC resource MSFT_PackageManagementSource can also register a package source.</span></span>| 
| <span data-ttu-id="029a8-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="029a8-117">Ensure</span></span>| <span data-ttu-id="029a8-118">Determina se o pacote deve ser instalado ou desinstalado.</span><span class="sxs-lookup"><span data-stu-id="029a8-118">Determines whether the package is to be installed or uninstalled.</span></span>| 
| <span data-ttu-id="029a8-119">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="029a8-119">RequiredVersion</span></span>| <span data-ttu-id="029a8-120">Especifica a versão exata do pacote que você deseja instalar.</span><span class="sxs-lookup"><span data-stu-id="029a8-120">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="029a8-121">Se você não especificar esse parâmetro, esse recurso DSC instalará a versão disponível mais recente do pacote que também atende a qualquer versão máxima especificada pelo parâmetro MaximumVersion.</span><span class="sxs-lookup"><span data-stu-id="029a8-121">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the MaximumVersion parameter.</span></span>| 
| <span data-ttu-id="029a8-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="029a8-122">MinimumVersion</span></span>| <span data-ttu-id="029a8-123">Especifica a versão mínima permitida do pacote que você deseja instalar.</span><span class="sxs-lookup"><span data-stu-id="029a8-123">Specifies the minimum allowed version of the package that you want to install.</span></span> <span data-ttu-id="029a8-124">Se você não adicionar esse parâmetro, esse recurso de DSC instalará a versão disponível mais recente do pacote que também atende a qualquer versão máxima especificada pelo parâmetro MaximumVersion.</span><span class="sxs-lookup"><span data-stu-id="029a8-124">If you do not add this parameter, this DSC resource intalls the highest available version of the package that also satisfies any maximum specified version specified by the MaximumVersion parameter.</span></span>| 
| <span data-ttu-id="029a8-125">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="029a8-125">MaximumVersion</span></span>| <span data-ttu-id="029a8-126">Especifica a versão máxima permitida do pacote que você deseja instalar.</span><span class="sxs-lookup"><span data-stu-id="029a8-126">Specifies the maximum allowed version of the package that you want to install.</span></span> <span data-ttu-id="029a8-127">Se você não especificar esse parâmetro, esse recurso de DSC instalará a versão com maior numeração disponível do pacote.</span><span class="sxs-lookup"><span data-stu-id="029a8-127">If you do not specify this parameter, this DSC resource installs the highest-numbered available version of the package.</span></span>| 
| <span data-ttu-id="029a8-128">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="029a8-128">SourceCredential</span></span> | <span data-ttu-id="029a8-129">Especifica uma conta de usuário que tenha direitos para instalar um pacote para um provedor de pacote ou origem específicos.</span><span class="sxs-lookup"><span data-stu-id="029a8-129">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>| 
| <span data-ttu-id="029a8-130">ProviderName</span><span class="sxs-lookup"><span data-stu-id="029a8-130">ProviderName</span></span>| <span data-ttu-id="029a8-131">Especifica um nome de provedor de pacote para o qual definir o escopo de sua pesquisa de pacote.</span><span class="sxs-lookup"><span data-stu-id="029a8-131">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="029a8-132">Você pode obter os nomes de provedores de pacote executando o cmdlet Get-PackageProvider.</span><span class="sxs-lookup"><span data-stu-id="029a8-132">You can get package provider names by running the Get-PackageProvider cmdlet.</span></span>| 
| <span data-ttu-id="029a8-133">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="029a8-133">AdditionalParameters</span></span>| <span data-ttu-id="029a8-134">Parâmetros específicos do provedor que são transmitidos como uma tabela de hash.</span><span class="sxs-lookup"><span data-stu-id="029a8-134">Provider specific parameters that are passed as an Hashtable.</span></span> <span data-ttu-id="029a8-135">Por exemplo, para o provedor do NuGet, você pode transmitir parâmetros adicionais, como DestinationPath.</span><span class="sxs-lookup"><span data-stu-id="029a8-135">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>| 

## <a name="additional-parameters"></a><span data-ttu-id="029a8-136">Parâmetros Adicionais</span><span class="sxs-lookup"><span data-stu-id="029a8-136">Additional Parameters</span></span>
<span data-ttu-id="029a8-137">A tabela a seguir lista as opções para a propriedade AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="029a8-137">The following table lists options for the AdditionalParameters property.</span></span>
|  <span data-ttu-id="029a8-138">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="029a8-138">Parameter</span></span>  | <span data-ttu-id="029a8-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="029a8-139">Description</span></span>   | 
|---|---|
| <span data-ttu-id="029a8-140">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="029a8-140">DestinationPath</span></span>| <span data-ttu-id="029a8-141">Usada por provedores como o Nuget interno.</span><span class="sxs-lookup"><span data-stu-id="029a8-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="029a8-142">Especifica o local de um arquivo onde você deseja que o pacote seja instalado.</span><span class="sxs-lookup"><span data-stu-id="029a8-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="029a8-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="029a8-143">InstallationPolicy</span></span>| <span data-ttu-id="029a8-144">Usada por provedores como o Nuget interno.</span><span class="sxs-lookup"><span data-stu-id="029a8-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="029a8-145">Determina se você confia na origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="029a8-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="029a8-146">Um destes: "Não confiável", "Confiável".</span><span class="sxs-lookup"><span data-stu-id="029a8-146">One of: "Untrusted", "Trusted".</span></span>|

## <a name="example"></a><span data-ttu-id="029a8-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="029a8-147">Example</span></span>

<span data-ttu-id="029a8-148">Este exemplo instala o pacote do NuGet **JQuery** e o módulo do PowerShell **GistProvider** usando o recurso de DSC **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="029a8-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="029a8-149">Este exemplo primeiro garante que as origens dos pacotes necessários estejam disponíveis e, em seguida, define o estado esperado dos pacotes **JQuery** e **GistProvider** (NuGet e PowerShell, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="029a8-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{    
    PackageManagementSource SourceRepository 
    { 
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }    
    
    PackageManagementSource PSGallery 
    { 
        Ensure      = "Present" 
        Name        = "psgallery" 
        ProviderName= "PowerShellGet" 
        SourceUri   = "https://www.powershellgallery.com/api/v2/"   
        InstallationPolicy ="Trusted" 
    } 
          
    PackageManagement NugetPackage 
    { 
        Ensure               = "Present"  
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1" 
        DependsOn            = "[PackageManagementSource]SourceRepository" 
    }
    
    PackageManagement PSModule 
    { 
        Ensure               = "Present"  
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery" 
    }
}
```

