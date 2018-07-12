---
ms.date: 06/20/2018
keywords: DSC,powershell,configuração,instalação
title: Recurso PackageManagement de DSC
ms.openlocfilehash: 281aee13eb005f00b23c97870eaefaa332d9c232
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892494"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="56376-103">Recurso PackageManagement de DSC</span><span class="sxs-lookup"><span data-stu-id="56376-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="56376-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="56376-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="56376-105">O recurso **PackageManagement** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para instalar ou desinstalar pacotes de Gerenciamento de Pacotes em um nó de destino.</span><span class="sxs-lookup"><span data-stu-id="56376-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="56376-106">Este recurso requer o módulo **PackageManagement**, disponível em [http://PowerShellGallery.com](http://PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="56376-106">This resource requires the **PackageManagement** module, available from [http://PowerShellGallery.com](http://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="56376-107">O módulo **PackageManagement** deve ser pelo menos a versão 1.1.7.0 para as informações de propriedade a seguir estarem corretas.</span><span class="sxs-lookup"><span data-stu-id="56376-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="56376-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="56376-108">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="56376-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="56376-109">Properties</span></span>

|  <span data-ttu-id="56376-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="56376-110">Property</span></span>  |  <span data-ttu-id="56376-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="56376-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="56376-112">Nome</span><span class="sxs-lookup"><span data-stu-id="56376-112">Name</span></span>| <span data-ttu-id="56376-113">Especifica o nome do Pacote a ser instalado ou desinstalado.</span><span class="sxs-lookup"><span data-stu-id="56376-113">Specifies the name of the Package to be installed or uninstalled.</span></span>|
| <span data-ttu-id="56376-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="56376-114">AdditionalParameters</span></span>| <span data-ttu-id="56376-115">Tabela de hash específica do provedor dos parâmetros que seria passado para o `Get-Package -AdditionalArguments`.</span><span class="sxs-lookup"><span data-stu-id="56376-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="56376-116">Por exemplo, para o provedor do NuGet, você pode transmitir parâmetros adicionais, como DestinationPath.</span><span class="sxs-lookup"><span data-stu-id="56376-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>|
| <span data-ttu-id="56376-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="56376-117">Ensure</span></span>| <span data-ttu-id="56376-118">Determina se o pacote deve ser instalado ou desinstalado.</span><span class="sxs-lookup"><span data-stu-id="56376-118">Determines whether the package is to be installed or uninstalled.</span></span>|
| <span data-ttu-id="56376-119">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="56376-119">MaximumVersion</span></span>|<span data-ttu-id="56376-120">Especifica a versão máxima permitida do pacote que você deseja encontrar.</span><span class="sxs-lookup"><span data-stu-id="56376-120">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="56376-121">Se você não adicionar esse parâmetro, o recurso localizará a versão mais recente disponível do pacote.</span><span class="sxs-lookup"><span data-stu-id="56376-121">If you do not add this parameter, the resource finds the highest available version of the package.</span></span>|
| <span data-ttu-id="56376-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="56376-122">MinimumVersion</span></span>|<span data-ttu-id="56376-123">Especifica a versão mínima permitida do pacote que você deseja encontrar.</span><span class="sxs-lookup"><span data-stu-id="56376-123">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="56376-124">Se você não adicionar esse parâmetro, esse recurso encontrará a versão disponível mais recente do pacote que também atende a qualquer versão máxima especificada pelo parâmetro _MaximumVersion_.</span><span class="sxs-lookup"><span data-stu-id="56376-124">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="56376-125">ProviderName</span><span class="sxs-lookup"><span data-stu-id="56376-125">ProviderName</span></span>| <span data-ttu-id="56376-126">Especifica um nome de provedor de pacote para o qual definir o escopo de sua pesquisa de pacote.</span><span class="sxs-lookup"><span data-stu-id="56376-126">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="56376-127">Você pode obter os nomes de provedor de pacotes executando o cmdlet `Get-PackageProvider`.</span><span class="sxs-lookup"><span data-stu-id="56376-127">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>|
| <span data-ttu-id="56376-128">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="56376-128">RequiredVersion</span></span>| <span data-ttu-id="56376-129">Especifica a versão exata do pacote que você deseja instalar.</span><span class="sxs-lookup"><span data-stu-id="56376-129">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="56376-130">Se você não especificar esse parâmetro, esse recurso DSC instalará a versão disponível mais recente do pacote que também atende a qualquer versão máxima especificada pelo parâmetro _MaximumVersion_.</span><span class="sxs-lookup"><span data-stu-id="56376-130">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="56376-131">Origem</span><span class="sxs-lookup"><span data-stu-id="56376-131">Source</span></span>| <span data-ttu-id="56376-132">Especifica o nome da origem do pacote onde é possível encontrar o pacote.</span><span class="sxs-lookup"><span data-stu-id="56376-132">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="56376-133">Isso pode ser um URI ou uma fonte registrada com o recurso de DSC `Register-PackageSource` ou PackageManagementSource.</span><span class="sxs-lookup"><span data-stu-id="56376-133">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span>|
| <span data-ttu-id="56376-134">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="56376-134">SourceCredential</span></span> | <span data-ttu-id="56376-135">Especifica uma conta de usuário que tenha direitos para instalar um pacote para um provedor de pacote ou origem específicos.</span><span class="sxs-lookup"><span data-stu-id="56376-135">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>|

## <a name="additional-parameters"></a><span data-ttu-id="56376-136">Parâmetros Adicionais</span><span class="sxs-lookup"><span data-stu-id="56376-136">Additional Parameters</span></span>

<span data-ttu-id="56376-137">A tabela a seguir lista as opções para a propriedade AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="56376-137">The following table lists options for the AdditionalParameters property.</span></span>
|  <span data-ttu-id="56376-138">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="56376-138">Parameter</span></span>  | <span data-ttu-id="56376-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="56376-139">Description</span></span>   |
|---|---|
| <span data-ttu-id="56376-140">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="56376-140">DestinationPath</span></span>| <span data-ttu-id="56376-141">Usada por provedores como o Nuget interno.</span><span class="sxs-lookup"><span data-stu-id="56376-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="56376-142">Especifica o local de um arquivo onde você deseja que o pacote seja instalado.</span><span class="sxs-lookup"><span data-stu-id="56376-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="56376-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="56376-143">InstallationPolicy</span></span>| <span data-ttu-id="56376-144">Usada por provedores como o Nuget interno.</span><span class="sxs-lookup"><span data-stu-id="56376-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="56376-145">Determina se você confia na origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="56376-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="56376-146">Um destes: "Não confiável", "Confiável".</span><span class="sxs-lookup"><span data-stu-id="56376-146">One of: "Untrusted", "Trusted".</span></span>|

## <a name="example"></a><span data-ttu-id="56376-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="56376-147">Example</span></span>

<span data-ttu-id="56376-148">Este exemplo instala o pacote do NuGet **JQuery** e o módulo do PowerShell **GistProvider** usando o recurso de DSC **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="56376-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="56376-149">Este exemplo primeiro garante que as origens dos pacotes necessários estejam disponíveis e, em seguida, define o estado esperado dos pacotes **JQuery** e **GistProvider** (NuGet e PowerShell, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="56376-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
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