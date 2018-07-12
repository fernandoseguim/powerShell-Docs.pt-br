---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Módulos que exigem a aceitação da licença
ms.openlocfilehash: 93f92f6e83bcf18a40c3d89eb39a154e16ca5063
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893103"
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="c9014-103">Módulos que exigem a aceitação da licença</span><span class="sxs-lookup"><span data-stu-id="c9014-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="c9014-104">SINOPSE</span><span class="sxs-lookup"><span data-stu-id="c9014-104">SYNOPSIS</span></span>

<span data-ttu-id="c9014-105">Os departamentos jurídicos de alguns publicadores de módulo exigem que os clientes aceitem explicitamente a licença antes de instalar o módulo da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c9014-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="c9014-106">Se um usuário instala, atualiza ou salva um módulo usando o PowerShellGet, seja diretamente ou como uma dependência de outro item, e esse módulo exige que o usuário concorde com uma licença, o usuário deverá indicar que aceita a licença ou a operação falhará.</span><span class="sxs-lookup"><span data-stu-id="c9014-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another item, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="c9014-107">Requisitos de publicação para os módulos</span><span class="sxs-lookup"><span data-stu-id="c9014-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="c9014-108">Os módulos que gostariam de exigir dos usuários a aceitação da licença devem atender aos seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="c9014-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>

- <span data-ttu-id="c9014-109">A seção PSData do manifesto do módulo deve incluir RequireLicenseAcceptance = $True.</span><span class="sxs-lookup"><span data-stu-id="c9014-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="c9014-110">O módulo deve conter o arquivo license.txt no diretório raiz.</span><span class="sxs-lookup"><span data-stu-id="c9014-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="c9014-111">O manifesto do módulo deve conter o Uri da Licença.</span><span class="sxs-lookup"><span data-stu-id="c9014-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="c9014-112">O módulo deve ser publicado com o PowerShellGet Format Versão 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="c9014-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="c9014-113">Impacto em Install/Save/Update-Module</span><span class="sxs-lookup"><span data-stu-id="c9014-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="c9014-114">Os cmdlets Install/Save/Update darão suporte a um novo parâmetro –AcceptLicense que se comportará como se o usuário tivesse visto a licença.</span><span class="sxs-lookup"><span data-stu-id="c9014-114">Install/Save/Update cmdlets will support a new parameter –AcceptLicense that will behave as though the user saw the license.</span></span>
- <span data-ttu-id="c9014-115">Se RequiredLicenseAcceptance for True e –AcceptLicense não for especificado, o usuário verá o license.txt e receberá a pergunta: &quot;Você aceita os termos desta licença (Yes/No/YesToAll/NoToAll)&quot;.</span><span class="sxs-lookup"><span data-stu-id="c9014-115">If RequiredLicenseAcceptance is True and –AcceptLicense is not specified, the user will be shown the license.txt, and prompted with: &quot;Do you accept these license terms (Yes/No/YesToAll/NoToAll)&quot;.</span></span>
  - <span data-ttu-id="c9014-116">Se a licença for aceita</span><span class="sxs-lookup"><span data-stu-id="c9014-116">If the license is accepted</span></span>
    - <span data-ttu-id="c9014-117">**Save-Module:** o módulo será copiado no sistema do usuário</span><span class="sxs-lookup"><span data-stu-id="c9014-117">**Save-Module:** the module will be copied to the user&#39;s system</span></span>
    - <span data-ttu-id="c9014-118">**Install-Module:** o módulo será copiado no sistema do usuário, na pasta apropriada (com base no escopo)</span><span class="sxs-lookup"><span data-stu-id="c9014-118">**Install-Module:** the module will be copied to the user&#39;s system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="c9014-119">**Update-Module:** o módulo será atualizado.</span><span class="sxs-lookup"><span data-stu-id="c9014-119">**Update-Module:** the module will be updated.</span></span>
  - <span data-ttu-id="c9014-120">Se a licença for recusada.</span><span class="sxs-lookup"><span data-stu-id="c9014-120">If the license is declined.</span></span>
    - <span data-ttu-id="c9014-121">A operação será cancelada.</span><span class="sxs-lookup"><span data-stu-id="c9014-121">Operation will be cancelled.</span></span>
    - <span data-ttu-id="c9014-122">Todos os cmdlets verificarão a existência dos metadados (requireLicenseAcceptance e Versão do Formato) que informam a exigência da aceitação da licença</span><span class="sxs-lookup"><span data-stu-id="c9014-122">All cmdlets will check for the metadata(requireLicenseAcceptance and Format Version) that says a license acceptance is required</span></span>
    - <span data-ttu-id="c9014-123">Se a versão do formato do cliente for anterior à 2.0, a operação falhará e pedirá ao usuário para atualizar o cliente.</span><span class="sxs-lookup"><span data-stu-id="c9014-123">If format version of client is older than 2.0, operation will fail and ask the user to update the client.</span></span>
    - <span data-ttu-id="c9014-124">Se o módulo tiver sido publicado com a versão de formato mais antiga do que 2.0, o sinalizador requireLicenseAcceptance será ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9014-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag will be ignored.</span></span>

## <a name="module-dependencies"></a><span data-ttu-id="c9014-125">Dependências de módulo</span><span class="sxs-lookup"><span data-stu-id="c9014-125">Module Dependencies</span></span>

- <span data-ttu-id="c9014-126">Durante uma operação Install/Save/Update, se um módulo dependente (outra coisa depender do módulo) exigir a aceitação da licença, o comportamento de aceitação da licença (acima) será necessário.</span><span class="sxs-lookup"><span data-stu-id="c9014-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) will be required.</span></span>
- <span data-ttu-id="c9014-127">Se a versão do módulo já estiver listada no catálogo local como instalada no sistema, ignoraremos a verificação da licença.</span><span class="sxs-lookup"><span data-stu-id="c9014-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="c9014-128">Durante a operação de Install/Save/Update, se um módulo dependente exigir uma licença, e a aceitação da licença não ocorrer, a operação falhará e seguirá os processos normais para o item que não conseguiu instalar/salvar/atualizar.</span><span class="sxs-lookup"><span data-stu-id="c9014-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation will fail and follow normal processes for the item failed to install/save/update.</span></span>

## <a name="impact-on--force"></a><span data-ttu-id="c9014-129">Impacto sobre -Force</span><span class="sxs-lookup"><span data-stu-id="c9014-129">Impact on -Force</span></span>

<span data-ttu-id="c9014-130">Especificar `–Force` NÃO é suficiente para aceitar uma licença.</span><span class="sxs-lookup"><span data-stu-id="c9014-130">Specifying `–Force` is NOT sufficient to accept a license.</span></span> <span data-ttu-id="c9014-131">`–AcceptLicense` é necessário para obter a permissão de instalação.</span><span class="sxs-lookup"><span data-stu-id="c9014-131">`–AcceptLicense` is required for permission to install.</span></span> <span data-ttu-id="c9014-132">Se `–Force` for especificado, RequiredLicenseAcceptance for True e `–AcceptLicense` NÃO for especificado, a operação falhará.</span><span class="sxs-lookup"><span data-stu-id="c9014-132">If `–Force` is specified, RequiredLicenseAcceptance is True, and `–AcceptLicense` is NOT specified, the operation will fail.</span></span>

## <a name="examples"></a><span data-ttu-id="c9014-133">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="c9014-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="c9014-134">Exemplo 1: Atualizar Manifesto do Módulo para exigir a aceitação da licença</span><span class="sxs-lookup"><span data-stu-id="c9014-134">Example 1: Update Module Manifest to require license acceptance</span></span>

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

<span data-ttu-id="c9014-135">Esse comando atualiza o arquivo de manifesto e define o sinalizador RequireLicenseAcceptance como true.</span><span class="sxs-lookup"><span data-stu-id="c9014-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>

### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="c9014-136">Exemplo 2: Instalar o Módulo exigindo a aceitação da licença</span><span class="sxs-lookup"><span data-stu-id="c9014-136">Example 2: Install Module requiring license acceptance</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="c9014-137">Este comando mostra a licença do arquivo license.txt e solicita ao usuário a aceitação da licença.</span><span class="sxs-lookup"><span data-stu-id="c9014-137">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="c9014-138">Exemplo 3: Instalar o Módulo exigindo a aceitação da licença com -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="c9014-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="c9014-139">O módulo é instalado sem qualquer solicitação de aceitação da licença.</span><span class="sxs-lookup"><span data-stu-id="c9014-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="c9014-140">Exemplo 4: Instalar o Módulo exigindo a aceitação da licença com -Force</span><span class="sxs-lookup"><span data-stu-id="c9014-140">Example 4: Install Module requiring license acceptance with -Force</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -Force
```

```output
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="c9014-141">Exemplo 5: Instalar o Módulo com dependências exigindo a aceitação da licença</span><span class="sxs-lookup"><span data-stu-id="c9014-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>

<span data-ttu-id="c9014-142">O módulo 'ModuleWithDependency' depende do módulo 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="c9014-142">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="c9014-143">O usuário recebe a solicitação para aceitar licença.</span><span class="sxs-lookup"><span data-stu-id="c9014-143">User is prompted to Accept License.</span></span>

```powershell
Install-Module -Name ModuleWithDependency
```

```output
License Acceptance
MIT License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="c9014-144">Exemplo 6: Instalar o Módulo com dependências exigindo a aceitação da licença e -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="c9014-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="c9014-145">O módulo 'ModuleWithDependency' depende do módulo 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="c9014-145">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="c9014-146">O usuário não recebe a solicitação para aceitar a licença, pois - AcceptLicense é especificado.</span><span class="sxs-lookup"><span data-stu-id="c9014-146">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="c9014-147">Exemplo 7: Instalar o módulo exigindo a aceitação da licença em um cliente mais antigo do que PSGetFormatVersion 2.0</span><span class="sxs-lookup"><span data-stu-id="c9014-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="c9014-148">Exemplo 8: Salvar o Módulo exigindo a aceitação da licença</span><span class="sxs-lookup"><span data-stu-id="c9014-148">Example 8: Save Module requiring license acceptance</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved
```

```output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="c9014-149">Este comando mostra a licença do arquivo license.txt e solicita ao usuário a aceitação da licença.</span><span class="sxs-lookup"><span data-stu-id="c9014-149">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="c9014-150">Exemplo 9: Salvar o Módulo exigindo a aceitação da licença com -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="c9014-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

<span data-ttu-id="c9014-151">O módulo é salvo sem qualquer solicitação de aceitação da licença.</span><span class="sxs-lookup"><span data-stu-id="c9014-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="c9014-152">Exemplo 10: Atualizar o Módulo exigindo a aceitação da licença</span><span class="sxs-lookup"><span data-stu-id="c9014-152">Example 10: Update Module requiring license acceptance</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance
```

```output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="c9014-153">Este comando mostra a licença do arquivo license.txt e solicita ao usuário a aceitação da licença.</span><span class="sxs-lookup"><span data-stu-id="c9014-153">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="c9014-154">Exemplo 11: Atualizar o Módulo exigindo a aceitação da licença com -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="c9014-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="c9014-155">O módulo é atualizado sem qualquer solicitação de aceitação da licença.</span><span class="sxs-lookup"><span data-stu-id="c9014-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="c9014-156">Mais detalhes</span><span class="sxs-lookup"><span data-stu-id="c9014-156">More details</span></span>

[<span data-ttu-id="c9014-157">Exigir a aceitação da licença para Scripts</span><span class="sxs-lookup"><span data-stu-id="c9014-157">Require License Acceptance for Scripts</span></span>](./script-license-acceptance.md)

[<span data-ttu-id="c9014-158">Suporte à exigência de aceitação da licença no PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="c9014-158">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-items/items-that-require-license-acceptance.md)

[<span data-ttu-id="c9014-159">Exigir a aceitação da licença ao implantar na Automação do Azure</span><span class="sxs-lookup"><span data-stu-id="c9014-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-items/deploy-to-azure-automation.md)