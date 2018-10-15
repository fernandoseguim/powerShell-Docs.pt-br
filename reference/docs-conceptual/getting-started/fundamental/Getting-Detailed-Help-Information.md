---
ms.date: 08/27/2018
keywords: powershell, cmdlet
title: Obtendo informações de ajuda detalhadas
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: d2578604ec7c01c0b2734bd180e1babaca58b153
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851265"
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="6c2cb-103">Obtendo informações de ajuda detalhadas</span><span class="sxs-lookup"><span data-stu-id="6c2cb-103">Getting detailed help information</span></span>

<span data-ttu-id="6c2cb-104">O PowerShell inclui artigos detalhados de Ajuda que explicam os conceitos do PowerShell e a linguagem do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-104">PowerShell includes detailed Help articles that explain PowerShell concepts and the PowerShell language.</span></span> <span data-ttu-id="6c2cb-105">Também há artigos de Ajuda para cada cmdlet e tópicos de provedor e para muitas funções e scripts.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-105">There are also Help articles for each cmdlet and provider and for many functions and scripts.</span></span>

<span data-ttu-id="6c2cb-106">Você pode exibir esses artigos de Ajuda no prompt de comando ou exibir as versões mais atualizadas dos seguintes artigos na documentação online do [PowerShell](/powershell/scripting/powershell-scripting).</span><span class="sxs-lookup"><span data-stu-id="6c2cb-106">You can display these Help articles at the command prompt or view the most recently updated versions of these articles in the [PowerShell](/powershell/scripting/powershell-scripting) documentation online.</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="6c2cb-107">Obter ajuda para cmdlets</span><span class="sxs-lookup"><span data-stu-id="6c2cb-107">Getting help for cmdlets</span></span>

<span data-ttu-id="6c2cb-108">Para obter Ajuda sobre cmdlets do PowerShell, use o cmdlet [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help).</span><span class="sxs-lookup"><span data-stu-id="6c2cb-108">To get Help about PowerShell cmdlets, use the [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span></span> <span data-ttu-id="6c2cb-109">Por exemplo, para obter Ajuda para o cmdlet `Get-ChildItem`, digite:</span><span class="sxs-lookup"><span data-stu-id="6c2cb-109">For example, to get Help for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="6c2cb-110">ou</span><span class="sxs-lookup"><span data-stu-id="6c2cb-110">or</span></span>

```powershell
Get-ChildItem -?
```

<span data-ttu-id="6c2cb-111">Você pode até mesmo obter ajuda para o cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-111">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="6c2cb-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6c2cb-112">For example:</span></span>

```powershell
Get-Help Get-Help
```

<span data-ttu-id="6c2cb-113">Para obter uma lista de todos os artigos de Ajuda de cmdlet em sua sessão, digite:</span><span class="sxs-lookup"><span data-stu-id="6c2cb-113">To get a list of all the cmdlet Help articles in your session, type:</span></span>

```powershell
Get-Help -Category Cmdlet
```

<span data-ttu-id="6c2cb-114">Para exibir uma página por vez de cada artigo de Ajuda, use a função `help` ou seu alias `man`.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-114">To display one page of each Help article at a time, use the `help` function or its alias `man`.</span></span>
<span data-ttu-id="6c2cb-115">Por exemplo, para exibir a Ajuda sobre o cmdlet `Get-ChildItem`, digite</span><span class="sxs-lookup"><span data-stu-id="6c2cb-115">For example, to display Help for the `Get-ChildItem` cmdlet, type</span></span>

```powershell
man Get-ChildItem
```

<span data-ttu-id="6c2cb-116">ou</span><span class="sxs-lookup"><span data-stu-id="6c2cb-116">or</span></span>

```powershell
help Get-ChildItem
```

<span data-ttu-id="6c2cb-117">Para exibir informações detalhadas, use o parâmetro **Detailed** do cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-117">To display detailed information, use the **Detailed** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="6c2cb-118">Por exemplo, para obter informações detalhadas sobre o cmdlet `Get-ChildItem`, digite:</span><span class="sxs-lookup"><span data-stu-id="6c2cb-118">For example, to get detailed information about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Detailed
```

<span data-ttu-id="6c2cb-119">Para exibir todo o conteúdo do artigo de Ajuda, use o parâmetro **Full** do cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-119">To display all content in the Help article, use the **Full** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="6c2cb-120">Por exemplo, para exibir todo o conteúdo do artigo de Ajuda do cmdlet `Get-ChildItem`, digite:</span><span class="sxs-lookup"><span data-stu-id="6c2cb-120">For example, to display all content in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Full
```

<span data-ttu-id="6c2cb-121">Para obter Ajuda detalhada para os parâmetros de um cmdlet, use o parâmetro **Parameter** do cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-121">To get detailed Help about the parameters of a cmdlet, use the **Parameter** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="6c2cb-122">Por exemplo, para obter Ajuda detalhada para todos os parâmetros do cmdlet `Get-ChildItem`, digite:</span><span class="sxs-lookup"><span data-stu-id="6c2cb-122">For example, to get detailed Help for all of the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Parameter *
```

<span data-ttu-id="6c2cb-123">Para exibir apenas os exemplos em um artigo de Ajuda, use o parâmetro **Examples** de `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-123">To display only the examples in a Help article, use the **Examples** parameter of the `Get-Help`.</span></span>
<span data-ttu-id="6c2cb-124">Por exemplo, para exibir apenas os exemplos no artigo de Ajuda para o cmdlet `Get-ChildItem `, digite:</span><span class="sxs-lookup"><span data-stu-id="6c2cb-124">For example, to display only the examples in the Help article for the `Get-ChildItem `cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Examples
```

<span data-ttu-id="6c2cb-125">Para obter informações de como escrever artigos de Ajuda para os cmdlets que você escreve, confira [Como escrever a Ajuda do cmdlet](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="6c2cb-125">For information about how to write Help articles for the cmdlets that you write, see [How to Write Cmdlet Help](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="6c2cb-126">Obter ajuda conceitual</span><span class="sxs-lookup"><span data-stu-id="6c2cb-126">Getting conceptual help</span></span>

<span data-ttu-id="6c2cb-127">O cmdlet `Get-Help` também exibe informações sobre artigos conceituais no PowerShell, incluindo artigos sobre a linguagem do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-127">The `Get-Help` cmdlet also displays information about conceptual articles in PowerShell, including articles about the PowerShell language.</span></span> <span data-ttu-id="6c2cb-128">Artigos de Ajuda conceituais começam com o prefixo "about_", como about_line_editing.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-128">Conceptual Help articles begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="6c2cb-129">(O nome do artigo conceitual deve ser inserido em inglês, mesmo em versões do PowerShell em idiomas diferentes do inglês).</span><span class="sxs-lookup"><span data-stu-id="6c2cb-129">(The name of the conceptual article must be entered in English even on non-English versions of PowerShell.)</span></span>

<span data-ttu-id="6c2cb-130">Para exibir uma lista de artigos conceituais, digite:</span><span class="sxs-lookup"><span data-stu-id="6c2cb-130">To display a list of conceptual articles, type:</span></span>

```powershell
Get-Help about_*
```

<span data-ttu-id="6c2cb-131">Para exibir um artigo de Ajuda específico, digite o nome do tópico, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6c2cb-131">To display a particular Help article, type the article name, for example:</span></span>

```powershell
Get-Help about_command_syntax
```

<span data-ttu-id="6c2cb-132">Os parâmetros de `Get-Help`, como **Detailed**, **Parameter** e **Examples** não têm efeito sobre a exibição dos artigos conceituais da Ajuda.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-132">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of conceptual Help articles.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="6c2cb-133">Obter ajuda sobre provedores</span><span class="sxs-lookup"><span data-stu-id="6c2cb-133">Getting help about providers</span></span>

<span data-ttu-id="6c2cb-134">O cmdlet `Get-Help` exibe informações sobre provedores do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-134">The `Get-Help` cmdlet displays information about PowerShell providers.</span></span> <span data-ttu-id="6c2cb-135">Para obter Ajuda para um provedor, digite `Get-Help` seguido pelo nome do provedor.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-135">To get Help for a provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="6c2cb-136">Por exemplo, para obter Ajuda para o provedor de Registro, digite:</span><span class="sxs-lookup"><span data-stu-id="6c2cb-136">For example, to get Help for the Registry provider, type:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="6c2cb-137">Para obter uma lista de todos os artigos de Ajuda de provedor em sua sessão, digite</span><span class="sxs-lookup"><span data-stu-id="6c2cb-137">To get a list of all the provider Help articles in your session, type</span></span>

```powershell
Get-Help -Category provider
```

<span data-ttu-id="6c2cb-138">Os parâmetros de `Get-Help`, como **Detailed**, **Parameter** e **Examples** não têm efeito sobre a exibição dos artigos de Ajuda referentes ao provedor.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-138">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of provider Help articles.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="6c2cb-139">Obter ajuda sobre scripts e funções</span><span class="sxs-lookup"><span data-stu-id="6c2cb-139">Getting help about scripts and functions</span></span>

<span data-ttu-id="6c2cb-140">Muitos scripts e funções no PowerShell têm artigos de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-140">Many scripts and functions in PowerShell have Help articles.</span></span> <span data-ttu-id="6c2cb-141">Use o cmdlet `Get-Help` para exibir os artigos de Ajuda para scripts e funções.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-141">Use the `Get-Help` cmdlet to display the Help articles for scripts and functions.</span></span>

<span data-ttu-id="6c2cb-142">Para exibir a Ajuda para uma função, digite `Get-Help` seguido pelo nome da função.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-142">To display the Help for a function, type `Get-Help` followed by the function name.</span></span> <span data-ttu-id="6c2cb-143">Por exemplo, para obter Ajuda para a função `Disable-PSRemoting`, digite:</span><span class="sxs-lookup"><span data-stu-id="6c2cb-143">For example, to get Help for the `Disable-PSRemoting` function, type:</span></span>

```powershell
Get-Help Disable-PSRemoting
```

<span data-ttu-id="6c2cb-144">Para exibir a Ajuda para um script, digite o caminho até o arquivo de script.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-144">To display the Help for a script, type the path to the script file.</span></span> <span data-ttu-id="6c2cb-145">Se o script não estiver em um caminho listado na variável de ambiente Path, será necessário usar o caminho totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-145">If the script is not in a path listed in the Path environment variable, you must use the fully qualified path.</span></span>

<span data-ttu-id="6c2cb-146">Por exemplo, se você tiver um script chamado "TestScript.ps1" no diretório C:\\PS-Test, para exibir o artigo de Ajuda do script, digite:</span><span class="sxs-lookup"><span data-stu-id="6c2cb-146">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help article for the script, type:</span></span>

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="6c2cb-147">Os parâmetros projetados para exibir a Ajuda do cmdlet também funcionam para a Ajuda de script e de função.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-147">The parameters that are designed for displaying cmdlet Help work for script and function Help, too.</span></span> <span data-ttu-id="6c2cb-148">No entanto, a ajuda para funções e scripts não é exibida quando você executa `Get-Help *`.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-148">However, help for functions and scripts is not shown when you run `Get-Help *`.</span></span>

<span data-ttu-id="6c2cb-149">Para saber mais sobre como escrever artigos de Ajuda para suas funções e scripts, consulte os artigos a seguir:</span><span class="sxs-lookup"><span data-stu-id="6c2cb-149">For information about writing Help articles for your functions and scripts, see the following articles:</span></span>

- [<span data-ttu-id="6c2cb-150">about_Functions</span><span class="sxs-lookup"><span data-stu-id="6c2cb-150">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="6c2cb-151">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="6c2cb-151">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="6c2cb-152">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="6c2cb-152">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a><span data-ttu-id="6c2cb-153">Obter ajuda online</span><span class="sxs-lookup"><span data-stu-id="6c2cb-153">Getting help online</span></span>

<span data-ttu-id="6c2cb-154">Exibir artigos de Ajuda online é uma das melhores maneiras de obter ajuda.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-154">Viewing the Help articles online is one of the best ways to get help.</span></span> <span data-ttu-id="6c2cb-155">Os artigos online são mais fáceis de atualizar e fornecem o conteúdo mais atual.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-155">Online articles are easier to update and provide the most current content.</span></span>

<span data-ttu-id="6c2cb-156">Para obter Ajuda online, use o parâmetro **Online** do cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-156">To get Help online, use the **Online** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="6c2cb-157">Todos os artigos de Ajuda que acompanham o PowerShell, incluindo a Ajuda do provedor e artigos conceituais de Ajuda (Sobre), estão disponíveis online na documentação do [PowerShell](/powershell/scripting/powershell-scripting).</span><span class="sxs-lookup"><span data-stu-id="6c2cb-157">All the Help articles that come with PowerShell, including provider Help and conceptual (About) Help articles, are available online in the [PowerShell](/powershell/scripting/powershell-scripting) documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="6c2cb-158">Não é possível usar o parâmetro **Online** com artigos de Ajuda do provedor ou conceituais (about_\*).</span><span class="sxs-lookup"><span data-stu-id="6c2cb-158">You can't use the **Online** parameter with conceptual (about_\*) or provider Help articles.</span></span>
> <span data-ttu-id="6c2cb-159">A ajuda online é opcional, portanto não funciona para todos os cmdlets, funções ou scripts.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-159">Online help is optional, so it does not work for every cmdlet, function, or script.</span></span>

<span data-ttu-id="6c2cb-160">Por exemplo, para obter a versão online do artigo de Ajuda sobre o cmdlet `Get-ChildItem`, digite:</span><span class="sxs-lookup"><span data-stu-id="6c2cb-160">For example, to get the online version of the Help article about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Online
```

<span data-ttu-id="6c2cb-161">O PowerShell abre o artigo em seu navegador padrão.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-161">PowerShell opens the article in your default browser.</span></span> <span data-ttu-id="6c2cb-162">Se a Ajuda online tiver suporte para um artigo de Ajuda, você também poderá exibir a URL do artigo de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-162">If online Help is supported for a Help article, you can also view the URL of the Help article.</span></span> <span data-ttu-id="6c2cb-163">A URL aparece na seção Links Relacionados de um artigo de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-163">The URL appears in the Related Links section of a Help article.</span></span>

<span data-ttu-id="6c2cb-164">Por exemplo, para ver a URL da versão online do cmdlet Add-Computer, digite:</span><span class="sxs-lookup"><span data-stu-id="6c2cb-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```powershell
Get-Help Add-Computer
```

<span data-ttu-id="6c2cb-165">A primeira linha na seção Links Relacionados do artigo é mostrada abaixo.</span><span class="sxs-lookup"><span data-stu-id="6c2cb-165">The first line in the Related Links section of the article is shown below.</span></span>

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

<span data-ttu-id="6c2cb-166">Para saber mais sobre como fornecer suporte online dos artigos de Ajuda, confira [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span><span class="sxs-lookup"><span data-stu-id="6c2cb-166">For information about how to provide online support for your Help articles, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

## <a name="see-also"></a><span data-ttu-id="6c2cb-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c2cb-167">See also</span></span>

- [<span data-ttu-id="6c2cb-168">about_Functions</span><span class="sxs-lookup"><span data-stu-id="6c2cb-168">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="6c2cb-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="6c2cb-169">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="6c2cb-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="6c2cb-170">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [<span data-ttu-id="6c2cb-171">Get-Help</span><span class="sxs-lookup"><span data-stu-id="6c2cb-171">Get-Help</span></span>](/powershell/module/microsoft.powershell.core/get-help)
