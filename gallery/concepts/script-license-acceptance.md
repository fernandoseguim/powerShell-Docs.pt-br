---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Exigindo a aceitação da licença para scripts
ms.openlocfilehash: 6374c8c8536dd0c8f27580a5b8895b8db18424f9
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="7ba45-103">Exigindo a aceitação da licença para scripts</span><span class="sxs-lookup"><span data-stu-id="7ba45-103">Requiring license acceptance for scripts</span></span>

<span data-ttu-id="7ba45-104">Não há suporte para a Aceitação de Licença para scripts.</span><span class="sxs-lookup"><span data-stu-id="7ba45-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="7ba45-105">No entanto, há suporte para o cenário em que um script depende de um módulo que exige a aceitação da licença.</span><span class="sxs-lookup"><span data-stu-id="7ba45-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="7ba45-106">Os comandos de script (Install-Script/Save-Script/Update-Script) oferecem suporte a um novo parâmetro -AcceptLicense que se comporta como se o usuário tivesse visto a licença.</span><span class="sxs-lookup"><span data-stu-id="7ba45-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="7ba45-107">Se -AcceptLicense não for especificado; o usuário verá o license.txt para o módulo dependente e receberá a solicitação para aceitar a licença.</span><span class="sxs-lookup"><span data-stu-id="7ba45-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="7ba45-108">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="7ba45-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="7ba45-109">Exemplo 1: Instalar Script com dependências exigindo a aceitação da licença</span><span class="sxs-lookup"><span data-stu-id="7ba45-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>

<span data-ttu-id="7ba45-110">O script 'ScriptRequireLicenseAcceptance' depende do módulo 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="7ba45-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="7ba45-111">O usuário recebe a solicitação para aceitar licença.</span><span class="sxs-lookup"><span data-stu-id="7ba45-111">User is prompted to Accept License.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="7ba45-112">Exemplo 2: Instalar o Script com dependências exigindo a aceitação da licença e -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="7ba45-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="7ba45-113">O script 'ScriptRequireLicenseAcceptance' depende do módulo 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="7ba45-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="7ba45-114">O usuário não recebe a solicitação para aceitar a licença, pois - AcceptLicense é especificado.</span><span class="sxs-lookup"><span data-stu-id="7ba45-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="7ba45-115">Mais detalhes</span><span class="sxs-lookup"><span data-stu-id="7ba45-115">More details</span></span>

- [<span data-ttu-id="7ba45-116">Suporte à exigência de aceitação da licença para Módulos</span><span class="sxs-lookup"><span data-stu-id="7ba45-116">Require License Acceptance support for Modules</span></span>](module-license-acceptance.md)
- [<span data-ttu-id="7ba45-117">Suporte à exigência de aceitação da licença no PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="7ba45-117">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-items/items-that-require-license-acceptance.md)
- [<span data-ttu-id="7ba45-118">Exigir a aceitação da licença ao implantar na Automação do Azure</span><span class="sxs-lookup"><span data-stu-id="7ba45-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-items/deploy-to-azure-automation.md)