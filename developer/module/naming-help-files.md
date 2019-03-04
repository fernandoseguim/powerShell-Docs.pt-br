---
title: Arquivos de ajuda de nomenclatura | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: 06281a1260dbdc120867fce89e6d5c8dd0754b87
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856662"
---
# <a name="naming-help-files"></a><span data-ttu-id="1a5e8-102">Nomear arquivos de ajuda</span><span class="sxs-lookup"><span data-stu-id="1a5e8-102">Naming Help Files</span></span>

<span data-ttu-id="1a5e8-103">Este tópico explica como nomear um arquivo de ajuda baseados em XML, de modo que o [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet pode encontrá-lo.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="1a5e8-104">Os requisitos de nome são diferentes para cada tipo de comando.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-104">The name requirements differ for each command type.</span></span>
<span data-ttu-id="1a5e8-105">Este tópico explica como nomear um arquivo de ajuda baseados em XML, de modo que o [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet pode encontrá-lo.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-105">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="1a5e8-106">Os requisitos de nome são diferentes para cada tipo de comando.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-106">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="1a5e8-107">Arquivos de Ajuda do cmdlet</span><span class="sxs-lookup"><span data-stu-id="1a5e8-107">Cmdlet Help Files</span></span>

<span data-ttu-id="1a5e8-108">O arquivo de ajuda para um C# cmdlet deve ser nomeado para o assembly no qual o cmdlet é definido.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-108">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="1a5e8-109">Use o seguinte formato de nome de arquivo:</span><span class="sxs-lookup"><span data-stu-id="1a5e8-109">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="1a5e8-110">O formato de nome do assembly é necessário, mesmo quando o assembly é um módulo aninhado.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-110">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="1a5e8-111">Por exemplo, o [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet é definida no assembly Microsoft.PowerShell.Diagnostics.dll.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-111">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="1a5e8-112">O `Get-Help` cmdlet procura por um tópico da Ajuda para o `Get-WinEvent` cmdlet apenas no arquivo Microsoft.PowerShell.Diagnostics.dll help.xml no diretório do módulo.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-112">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>
<span data-ttu-id="1a5e8-113">Por exemplo, o [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet é definida no assembly Microsoft.PowerShell.Diagnostics.dll.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-113">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="1a5e8-114">O `Get-Help` cmdlet procura por um tópico da Ajuda para o `Get-WinEvent` cmdlet apenas no arquivo Microsoft.PowerShell.Diagnostics.dll help.xml no diretório do módulo.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-114">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="1a5e8-115">Arquivos de Ajuda do provedor</span><span class="sxs-lookup"><span data-stu-id="1a5e8-115">Provider Help files</span></span>

<span data-ttu-id="1a5e8-116">O arquivo de ajuda para um provedor do Windows PowerShell deve ser nomeado para o assembly no qual o provedor é definido.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-116">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="1a5e8-117">Use o seguinte formato de nome de arquivo:</span><span class="sxs-lookup"><span data-stu-id="1a5e8-117">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="1a5e8-118">O formato de nome do assembly é necessário, mesmo quando o assembly é um módulo aninhado.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-118">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="1a5e8-119">Por exemplo, o provedor de certificado é definido no assembly Microsoft.PowerShell.Security.dll.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-119">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="1a5e8-120">O `Get-Help` cmdlet procura um tópico da Ajuda para o provedor de certificado apenas no arquivo Microsoft.PowerShell.Security.dll help.xml no diretório do módulo.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-120">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="1a5e8-121">Arquivos de ajuda de função</span><span class="sxs-lookup"><span data-stu-id="1a5e8-121">Function Help Files</span></span>

<span data-ttu-id="1a5e8-122">Funções podem ser documentadas usando [a Ajuda baseada em comentário](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) ou documentados em um arquivo de Ajuda do XML.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-122">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="1a5e8-123">Quando a função está documentada em um arquivo XML, a função deve ter um `.ExternalHelp` comentar a palavra-chave que associa a função com o arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-123">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="1a5e8-124">Caso contrário, o `Get-Help` cmdlet não é possível localizar o arquivo de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-124">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>
<span data-ttu-id="1a5e8-125">Funções podem ser documentadas usando [a Ajuda baseada em comentário](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) ou documentados em um arquivo de Ajuda do XML.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-125">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="1a5e8-126">Quando a função está documentada em um arquivo XML, a função deve ter um `.ExternalHelp` comentar a palavra-chave que associa a função com o arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-126">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="1a5e8-127">Caso contrário, o `Get-Help` cmdlet não é possível localizar o arquivo de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-127">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="1a5e8-128">Não há nenhum requisitos técnicos para o nome de um arquivo de ajuda de função.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-128">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="1a5e8-129">No entanto, é uma prática recomendada nomear o arquivo de ajuda para o módulo de script no qual a função é definida.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-129">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="1a5e8-130">Por exemplo, a função a seguir é definida no arquivo MyModule.psm1.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-130">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="1a5e8-131">Arquivos de ajuda de comando do CIM</span><span class="sxs-lookup"><span data-stu-id="1a5e8-131">CIM Command Help Files</span></span>

<span data-ttu-id="1a5e8-132">O arquivo de ajuda para um comando CIM deve ser nomeado para o arquivo CDXML no qual o comando CIM é definido.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-132">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="1a5e8-133">Use o seguinte formato de nome de arquivo:</span><span class="sxs-lookup"><span data-stu-id="1a5e8-133">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="1a5e8-134">Comandos CIM são definidos em arquivos CDXML que podem ser incluídos nos módulos, como módulos aninhados.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-134">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="1a5e8-135">Quando o comando CIM é importado para a sessão como uma função, o Windows PowerShell adiciona um `.ExternalHelp` comentário palavra-chave para a definição da função que associa a função com uma ajuda XML do arquivo que é nomeado para o arquivo CDXML no qual o comando CIM é definido.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-135">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="1a5e8-136">Arquivos de Ajuda do fluxo de trabalho de script</span><span class="sxs-lookup"><span data-stu-id="1a5e8-136">Script Workflow Help Files</span></span>

<span data-ttu-id="1a5e8-137">Fluxos de trabalho de script que estão incluídos nos módulos podem ser documentados nos arquivos de ajuda baseados em XML.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-137">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="1a5e8-138">Não há nenhum requisitos técnicos para o nome do arquivo de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-138">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="1a5e8-139">No entanto, é uma prática recomendada nomear o arquivo de ajuda para o módulo de script no qual o fluxo de trabalho de script é definido.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-139">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="1a5e8-140">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1a5e8-140">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="1a5e8-141">Ao contrário de outros comandos em script, fluxos de trabalho de script não exigem um `.ExternalHelp` comentar a palavra-chave para associá-los a um arquivo de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-141">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="1a5e8-142">Em vez disso, o Windows PowerShell pesquisa os subdiretórios específicos da cultura de interface do usuário do diretório do módulo para arquivos de ajuda baseados em XML e procura ajuda para o fluxo de trabalho de script em todos os arquivos.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-142">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="1a5e8-143">`.ExternalHelp` Comente a palavra-chave são ignorados.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-143">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="1a5e8-144">Porque o `.ExternalHelp` palavra-chave do comentário é ignorado, a `Get-Help` cmdlet pode encontrar ajuda para fluxos de trabalho de script apenas quando eles são incluídos nos módulos.</span><span class="sxs-lookup"><span data-stu-id="1a5e8-144">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>