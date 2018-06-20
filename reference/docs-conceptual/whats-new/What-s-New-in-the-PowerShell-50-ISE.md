---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: O que há de novo no ISE do PowerShell 50
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
ms.openlocfilehash: 35b825cfa6ea720d0af3537c5d1b16c5ececb701
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953575"
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a><span data-ttu-id="dd5eb-103">Novidades no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd5eb-103">What&#39;s New in the Windows PowerShell ISE</span></span>
<span data-ttu-id="dd5eb-104">Este tópico explica os recursos novos e atualizados que foram introduzidos em versões do ISE (Ambiente de Script Integrado) do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell  Integrated Scripting Environment (ISE).</span></span>

## <a name="feature-description"></a><span data-ttu-id="dd5eb-105">Descrição do recurso</span><span class="sxs-lookup"><span data-stu-id="dd5eb-105">Feature description</span></span>
<span data-ttu-id="dd5eb-106">O ISE do Windows PowerShell é um aplicativo host que permite gravar, executar e testar scripts e módulos em um ambiente gráfico e intuitivo.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="dd5eb-107">Recursos importantes como coloração de sintaxe, preenchimento de guias, depuração visual, conformidade com Unicode e Ajuda contextual permitem uma experiência avançada de script.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="dd5eb-108">Para ter uma visão geral do ISE do Windows PowerShell, consulte [Visão geral do Ambiente de Script Integrado do Windows PowerShell](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).</span><span class="sxs-lookup"><span data-stu-id="dd5eb-108">For an overview of Windows PowerShell ISE, see [Windows PowerShell Integrated Scripting Environment overview](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).</span></span>

## <a name="new-and-changed-functionality-in-windows-powershell-ise"></a><span data-ttu-id="dd5eb-109">Funcionalidades novas e alteradas no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd5eb-109">New and changed functionality in Windows PowerShell ISE</span></span>
<span data-ttu-id="dd5eb-110">A tabela a seguir lista os recursos novos e alterados para esta versão do ISE do Windows PowerShell no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-110">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

|<span data-ttu-id="dd5eb-111">Recurso/funcionalidade</span><span class="sxs-lookup"><span data-stu-id="dd5eb-111">Feature/functionality</span></span>|<span data-ttu-id="dd5eb-112">ISE do Windows PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="dd5eb-112">Windows PowerShell ISE 4.0</span></span>|<span data-ttu-id="dd5eb-113">ISE do Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="dd5eb-113">Windows PowerShell ISE 3.0</span></span>|<span data-ttu-id="dd5eb-114">ISE do Windows PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="dd5eb-114">Windows PowerShell ISE 2.0</span></span>|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|<span data-ttu-id="dd5eb-115">**[IntelliSense](#intellisense)**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-115">**[IntelliSense](#intellisense)**</span></span>|<span data-ttu-id="dd5eb-116">X</span><span class="sxs-lookup"><span data-stu-id="dd5eb-116">X</span></span>|<span data-ttu-id="dd5eb-117">X</span><span class="sxs-lookup"><span data-stu-id="dd5eb-117">X</span></span>||
|<span data-ttu-id="dd5eb-118">**[Trechos de código](#snippets)**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-118">**[Snippets](#snippets)**</span></span>|<span data-ttu-id="dd5eb-119">X</span><span class="sxs-lookup"><span data-stu-id="dd5eb-119">X</span></span>|<span data-ttu-id="dd5eb-120">X</span><span class="sxs-lookup"><span data-stu-id="dd5eb-120">X</span></span>||
|<span data-ttu-id="dd5eb-121">**[Ferramentas complementares](#add-on-tools)**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-121">**[Add-on Tools](#add-on-tools)**</span></span>|<span data-ttu-id="dd5eb-122">X</span><span class="sxs-lookup"><span data-stu-id="dd5eb-122">X</span></span>|<span data-ttu-id="dd5eb-123">X</span><span class="sxs-lookup"><span data-stu-id="dd5eb-123">X</span></span>||
|<span data-ttu-id="dd5eb-124">**[Gerenciador de Reinicialização e Salvamento Automático](#restart-manager-and-auto-save)**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-124">**[Restart Manager and Auto-save](#restart-manager-and-auto-save)**</span></span>|<span data-ttu-id="dd5eb-125">X</span><span class="sxs-lookup"><span data-stu-id="dd5eb-125">X</span></span>|<span data-ttu-id="dd5eb-126">X</span><span class="sxs-lookup"><span data-stu-id="dd5eb-126">X</span></span>||
|<span data-ttu-id="dd5eb-127">**[Lista de recém-usados](#most-recently-used-list)**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-127">**[Most-recently used list](#most-recently-used-list)**</span></span>|<span data-ttu-id="dd5eb-128">X</span><span class="sxs-lookup"><span data-stu-id="dd5eb-128">X</span></span>|<span data-ttu-id="dd5eb-129">X</span><span class="sxs-lookup"><span data-stu-id="dd5eb-129">X</span></span>||
|<span data-ttu-id="dd5eb-130">**[Painel de Console](#console-pane)**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-130">**[Console Pane](#console-pane)**</span></span>|<span data-ttu-id="dd5eb-131">X</span><span class="sxs-lookup"><span data-stu-id="dd5eb-131">X</span></span>|<span data-ttu-id="dd5eb-132">X</span><span class="sxs-lookup"><span data-stu-id="dd5eb-132">X</span></span>||
|<span data-ttu-id="dd5eb-133">**[Opções de linha de comando](#command-line-switches)**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-133">**[Command-line switches](#command-line-switches)**</span></span>|<span data-ttu-id="dd5eb-134">X</span><span class="sxs-lookup"><span data-stu-id="dd5eb-134">X</span></span>|<span data-ttu-id="dd5eb-135">X</span><span class="sxs-lookup"><span data-stu-id="dd5eb-135">X</span></span>||
|<span data-ttu-id="dd5eb-136">**[Novos recursos do editor](#new-editor-features)**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-136">**[New editor features](#new-editor-features)**</span></span>|<span data-ttu-id="dd5eb-137">X</span><span class="sxs-lookup"><span data-stu-id="dd5eb-137">X</span></span>|<span data-ttu-id="dd5eb-138">X</span><span class="sxs-lookup"><span data-stu-id="dd5eb-138">X</span></span>||
|<span data-ttu-id="dd5eb-139">**[Janela do novo visualizador da ajuda](#new-help-viewer-window)**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-139">**[New Help viewer window](#new-help-viewer-window)**</span></span>|<span data-ttu-id="dd5eb-140">X</span><span class="sxs-lookup"><span data-stu-id="dd5eb-140">X</span></span>|<span data-ttu-id="dd5eb-141">X</span><span class="sxs-lookup"><span data-stu-id="dd5eb-141">X</span></span>||
|<span data-ttu-id="dd5eb-142">**[Cmdlet Show-Command](#show-command-cmdlet)**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-142">**[Show-Command cmdlet](#show-command-cmdlet)**</span></span>|<span data-ttu-id="dd5eb-143">X</span><span class="sxs-lookup"><span data-stu-id="dd5eb-143">X</span></span>|<span data-ttu-id="dd5eb-144">X</span><span class="sxs-lookup"><span data-stu-id="dd5eb-144">X</span></span>||

### <a name="intellisense"></a><span data-ttu-id="dd5eb-145">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="dd5eb-145">IntelliSense</span></span>
<span data-ttu-id="dd5eb-146">**Adicionado no ISE 3.0**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-146">**Added in ISE 3.0**</span></span>

<span data-ttu-id="dd5eb-147">O IntelliSense é um recurso de assistência de preenchimento automático que faz parte do ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-147">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span> <span data-ttu-id="dd5eb-148">O IntelliSense exibe menus clicáveis dos cmdlets, parâmetros, valores de parâmetro, arquivos ou pastas potencialmente correspondentes conforme você digita.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-148">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="dd5eb-149">**Qual é o valor adicionado por esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-149">**What value does this change add?**</span></span>

<span data-ttu-id="dd5eb-150">Com a adição do IntelliSense, ficou mais fácil de descobrir cmdlets e sintaxe ao usar o ISE do Windows PowerShell para criar scripts.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-150">With the addition of IntelliSense, it is easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="dd5eb-151">Você também pode usar o ISE do Windows PowerShell para conhecer o Windows PowerShell enquanto cria novos scripts.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-151">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="dd5eb-152">**O que passou a funcionar de maneira diferente?**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-152">**What works differently?**</span></span>

<span data-ttu-id="dd5eb-153">Quando você digita cmdlets no ISE do Windows PowerShell 3.0 ou posterior, um menu rolável e clicável é exibido, permitindo que você navegue e selecione os comandos apropriados.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-153">When you type cmdlets in the Windows PowerShell ISE 3.0 or later, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

### <a name="snippets"></a><span data-ttu-id="dd5eb-154">Trechos de código</span><span class="sxs-lookup"><span data-stu-id="dd5eb-154">Snippets</span></span>
<span data-ttu-id="dd5eb-155">**Adicionado no ISE 3.0**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-155">**Added in ISE 3.0**</span></span>

<span data-ttu-id="dd5eb-156">*Trechos de código* são sessões de código Windows PowerShell curtas que você pode inserir nos scritps que cria no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-156">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="dd5eb-157">O ISE do Windows PowerShell vem com um conjunto padrão de trechos de código.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-157">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="dd5eb-158">Você pode adicionar trechos de código usando o cmdlet **New-Snippet** enquanto trabalha no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-158">You can add snippets by using the **New-Snippet** cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="dd5eb-159">**Qual é o valor adicionado por esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-159">**What value does this change add?**</span></span>

<span data-ttu-id="dd5eb-160">Usando trechos de código, você pode montar e criar scripts para automatizar seu ambiente rapidamente.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-160">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="dd5eb-161">**O que passou a funcionar de maneira diferente?**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-161">**What works differently?**</span></span>

<span data-ttu-id="dd5eb-162">Para usar trechos de código no Windows PowerShell 3.0 ou posterior, no menu **Editar**, clique em **Iniciar Trechos de Código** ou pressione **Ctrl-J**.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-162">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press **Ctrl-J**.</span></span>

### <a name="add-on-tools"></a><span data-ttu-id="dd5eb-163">Ferramentas complementares</span><span class="sxs-lookup"><span data-stu-id="dd5eb-163">Add-on tools</span></span>
<span data-ttu-id="dd5eb-164">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-164">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="dd5eb-165">O ISE do Windows PowerShell agora dá suporte para ferramentas complementares, que são controles do WPF (Windows Presentation Foundation) que são adicionados usando o modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-165">Windows PowerShell ISE now supports add-on tools, which are Windows Presentation Foundation (WPF) controls that are added by using the object model.</span></span> <span data-ttu-id="dd5eb-166">As ferramentas complementares podem ser exibidas como um painel vertical ou horizontal no console.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-166">Add-on tools can be displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="dd5eb-167">Várias ferramentas complementares em um painel são exibidas como um controle com guias.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-167">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="dd5eb-168">Você também pode adicionar ou remover ferramentas complementares produzidas por terceiros.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-168">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="dd5eb-169">Para obter mais informações sobre como importar ou remover ferramentas complementares, confira [Windows PowerShell ISE Operations](http://technet.microsoft.com/library/cc732148.aspx) (Operações do ISE do Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="dd5eb-169">For more information about how to import or remove add-on tools, see [Windows PowerShell ISE Operations](http://technet.microsoft.com/library/cc732148.aspx).</span></span>

<span data-ttu-id="dd5eb-170">**Qual é o valor adicionado por esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-170">**What value does this change add?**</span></span>

<span data-ttu-id="dd5eb-171">Os complementos permitem estender e personalizar o ISE do Windows PowerShell com ferramentas que podem melhorar sua experiência com scripts ou adicionar funcionalidades ao ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-171">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that can enhance your scripting experience or add functionality to Windows PowerShell ISE.</span></span>

<span data-ttu-id="dd5eb-172">**O que passou a funcionar de maneira diferente?**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-172">**What works differently?**</span></span>

<span data-ttu-id="dd5eb-173">O ISE do Windows PowerShell 3.0 e posterior vêm com o complemento **Comandos**.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-173">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="dd5eb-174">O complemento **Comandos** permite que você procure cmdlets e acesse a Ajuda para os cmdlets lado a lado com os Painéis de **Script** e **Console**.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-174">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="dd5eb-175">Complementos adicionais podem ser encontrados usando o comando **Abrir o Site de Ferramentas Complementares** no menu **Complementos**.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-175">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

### <a name="restart-manager-and-auto-save"></a><span data-ttu-id="dd5eb-176">Gerenciador de Reinicialização e Salvamento Automático</span><span class="sxs-lookup"><span data-stu-id="dd5eb-176">Restart manager and auto-save</span></span>
<span data-ttu-id="dd5eb-177">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-177">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="dd5eb-178">O ISE do Windows PowerShell agora salva automaticamente os scripts abertos a cada dois minutos em uma localização separada.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-178">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span>  <span data-ttu-id="dd5eb-179">Se o ISE do Windows PowerShell parar de funcionar ou o sistema operacional for reiniciado, depois do ISE do Windows PowerShell reiniciar, ele recuperará os scripts que estavam abertos na última sessão, mesmo que eles não tenham sido salvos.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-179">If Windows PowerShell ISE stops working, or if the operating system is restarted, after Windows PowerShell ISE restarts, it recovers scripts that were open in the last session, even if the scripts were not saved.</span></span>

<span data-ttu-id="dd5eb-180">Para alterar o intervalo de salvamento automático, execute o seguinte comando no painel de console: **$psise.Options.AutoSaveMinuteInterval**.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-180">To change the automatic saving interval, run the following command in the Console pane: **$psise.Options.AutoSaveMinuteInterval**.</span></span>

<span data-ttu-id="dd5eb-181">**Qual é o valor adicionado por esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-181">**What value does this change add?**</span></span>

<span data-ttu-id="dd5eb-182">Agora você pode trabalhar no ISE do Windows PowerShell sabendo que os scripts abertos são salvos automaticamente em caso de uma reinicialização inesperada.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-182">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved in the event of an unexpected restart.</span></span>

<span data-ttu-id="dd5eb-183">**O que passou a funcionar de maneira diferente?**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-183">**What works differently?**</span></span>

<span data-ttu-id="dd5eb-184">O ISE do Windows PowerShell 2.0 não salva os scripts automaticamente em caso de reinicialização.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-184">Windows PowerShell ISE 2.0 does not save the scripts automatically in the event of a restart.</span></span>

### <a name="most-recently-used-list"></a><span data-ttu-id="dd5eb-185">Lista de recém-usados</span><span class="sxs-lookup"><span data-stu-id="dd5eb-185">Most-recently used list</span></span>
<span data-ttu-id="dd5eb-186">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-186">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="dd5eb-187">O ISE do Windows PowerShell agora tem uma lista de arquivos recém-usados.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-187">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="dd5eb-188">Quando você abre um arquivo no ISE do Windows PowerShell, ele é adicionado à lista de recém-usados no menu **Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-188">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="dd5eb-189">Para alterar o número padrão de arquivos na lista de recém-usados, execute o seguinte comando no Painel de Console: **$psise.Options.MruCount**.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-189">To change the default number of files in the most-recently used list, run the following command in the Console Pane: **$psise.Options.MruCount**.</span></span>

<span data-ttu-id="dd5eb-190">**Qual é o valor adicionado por esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-190">**What value does this change add?**</span></span>

<span data-ttu-id="dd5eb-191">Agora você pode usar a lista de recém-usados para acessar facilmente os arquivos usados frequentemente.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-191">You can now use the most-recently used list to easily access your frequently-used files.</span></span>

<span data-ttu-id="dd5eb-192">**O que passou a funcionar de maneira diferente?**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-192">**What works differently?**</span></span>

<span data-ttu-id="dd5eb-193">O ISE do Windows PowerShell 2.0 não tem uma lista de recém-usados.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-193">Windows PowerShell ISE 2.0 does not have a most-recently used list.</span></span>

### <a name="console-pane"></a><span data-ttu-id="dd5eb-194">Painel de Console</span><span class="sxs-lookup"><span data-stu-id="dd5eb-194">Console Pane</span></span>
<span data-ttu-id="dd5eb-195">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-195">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="dd5eb-196">Os Painéis de Comando e Saída separados que estavam disponíveis na primeira versão do ISE do Windows PowerShell foram combinados em um Painel de Console único.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-196">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="dd5eb-197">O Painel de Console é semelhante, em termos de função e aparência, a um console típico do Windows PowerShell, mas ele inclui as melhorias a seguir (a maioria delas é descrita neste tópico).</span><span class="sxs-lookup"><span data-stu-id="dd5eb-197">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements (most are described in this topic).</span></span>

- <span data-ttu-id="dd5eb-198">Cores de sintaxe para texto de entrada (não para texto de saída), incluindo sintaxe XML</span><span class="sxs-lookup"><span data-stu-id="dd5eb-198">Syntax coloring for input text (not output text), including XML syntax</span></span>

- <span data-ttu-id="dd5eb-199">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="dd5eb-199">IntelliSense</span></span>

- <span data-ttu-id="dd5eb-200">Correspondência de chaves</span><span class="sxs-lookup"><span data-stu-id="dd5eb-200">Brace matching</span></span>

- <span data-ttu-id="dd5eb-201">Indicação de erros</span><span class="sxs-lookup"><span data-stu-id="dd5eb-201">Error indication</span></span>

- <span data-ttu-id="dd5eb-202">Suporte total a Unicode</span><span class="sxs-lookup"><span data-stu-id="dd5eb-202">Full Unicode support</span></span>

- <span data-ttu-id="dd5eb-203">Ajuda contextual com **F1**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-203">**F1** context-sensitive help</span></span>

- <span data-ttu-id="dd5eb-204">Show-Command contextual com **Ctrl+F1**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-204">**Ctrl+F1** context-sensitive Show-Command</span></span>

- <span data-ttu-id="dd5eb-205">Suporte a scripts complexos e leitura da direita para a esquerda</span><span class="sxs-lookup"><span data-stu-id="dd5eb-205">Complex script and right-to-left support</span></span>

- <span data-ttu-id="dd5eb-206">Suporte a fontes</span><span class="sxs-lookup"><span data-stu-id="dd5eb-206">Font support</span></span>

- <span data-ttu-id="dd5eb-207">Zoom</span><span class="sxs-lookup"><span data-stu-id="dd5eb-207">Zoom</span></span>

- <span data-ttu-id="dd5eb-208">Modos de seleção de linha e seleção de blocos</span><span class="sxs-lookup"><span data-stu-id="dd5eb-208">Line-select and block-select modes</span></span>

- <span data-ttu-id="dd5eb-209">Preservação do conteúdo digitado na linha de comando quando você pressiona a seta **para cima** para exibir o histórico no console</span><span class="sxs-lookup"><span data-stu-id="dd5eb-209">Preservation of typed content at the command line when you press the **Up** arrow to view history in the console</span></span>

<span data-ttu-id="dd5eb-210">**Qual é o valor adicionado por esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-210">**What value does this change add?**</span></span>

<span data-ttu-id="dd5eb-211">A adição dessas alterações do Painel de Console fornece uma experiência de script que é mais consistente com a interface do console.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-211">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="dd5eb-212">**O que passou a funcionar de maneira diferente?**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-212">**What works differently?**</span></span>

<span data-ttu-id="dd5eb-213">O ISE do Windows PowerShell 2.0 tem Painéis de Comando e de Saída separados.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-213">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

### <a name="command-line-switches"></a><span data-ttu-id="dd5eb-214">Opções de linha de comando</span><span class="sxs-lookup"><span data-stu-id="dd5eb-214">Command-line switches</span></span>
<span data-ttu-id="dd5eb-215">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-215">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="dd5eb-216">Se você iniciar o ISE do Windows PowerShell com a linha de comando (digitando **powershell_ise.exe**), será possível adicionar as novas opções de linha de comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-216">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="dd5eb-217">*-NoProfile*: inicia o ISE do Windows PowerShell sem executar **$profile**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-217">*-NoProfile*: Starts Windows PowerShell ISE without running **$profile**</span></span>

- <span data-ttu-id="dd5eb-218">*-Help*: exibe uma janela de Ajuda</span><span class="sxs-lookup"><span data-stu-id="dd5eb-218">*-Help*: Displays a Help window</span></span>

- <span data-ttu-id="dd5eb-219">*-mta*: inicia o ISE do Windows PowerShell no modo Multi-Threaded Apartment.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-219">*-mta*: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="dd5eb-220">O modo de operação padrão para o ISE do Windows PowerShell é o modo Single-Threaded Apartment ou *-STA*.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-220">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or *-sta*.</span></span>

<span data-ttu-id="dd5eb-221">**Qual é o valor adicionado por esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-221">**What value does this change add?**</span></span>

<span data-ttu-id="dd5eb-222">A adição dessas opções de linha de comando permite controlar o ambiente no qual o ISE do Windows PowerShell é executado.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-222">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="dd5eb-223">**O que passou a funcionar de maneira diferente?**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-223">**What works differently?**</span></span>

<span data-ttu-id="dd5eb-224">O ISE do Windows PowerShell 2.0 não reconhece essas opções de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-224">Windows PowerShell ISE 2.0 does not recognize these command-line switches.</span></span>

### <a name="new-editor-features"></a><span data-ttu-id="dd5eb-225">Novos recursos do editor</span><span class="sxs-lookup"><span data-stu-id="dd5eb-225">New editor features</span></span>
<span data-ttu-id="dd5eb-226">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-226">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="dd5eb-227">Outros recursos de edição do ISE do Windows PowerShell incluem:</span><span class="sxs-lookup"><span data-stu-id="dd5eb-227">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="dd5eb-228">**Cores de sintaxe de XML**Agora o ISE do Windows PowerShell tem sintaxe XML colorida da mesma maneira que a sintaxe colorida do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-228">**XML syntax coloring**Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>

- <span data-ttu-id="dd5eb-229">**Correspondência de chaves** O ISE do Windows PowerShell inclui o realce e a correspondência de chaves e pode ser usado das seguintes maneiras: (por exemplo, o uso do comando **Ir para Correspondência** ou **Ctrl + ]** localizará a chave de fechamento, se você tiver selecionado uma chave de abertura).</span><span class="sxs-lookup"><span data-stu-id="dd5eb-229">**Brace matching** Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or **Ctrl + ]** locates the closing brace, if you have an opening brace selected).</span></span>

- <span data-ttu-id="dd5eb-230">**Exibição de estrutura de tópicos** O Painel de Script dá suporte à exibição das estruturas de tópicos, que permitem recolher ou expandir seções de códigos com cliques nos sinais de adição ou subtração na margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-230">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="dd5eb-231">Você pode usar chaves ou as marcas **#region** e **#endregion** para marcar o início ou o final de uma seção recolhível.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-231">You can use braces or the **#region** and **#endregion** tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="dd5eb-232">Para expandir ou recolher todas as regiões, pressione **Ctrl + M**.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-232">To expand or collapse all regions, press **Ctrl + M**.</span></span>

- <span data-ttu-id="dd5eb-233">**Edição de texto com arrastar e soltar**O ISE do Windows PowerShell agora dá suporte à edição de texto com arrasta e soltar.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-233">**Drag and drop text editing**Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="dd5eb-234">Você pode selecionar qualquer bloco de texto e arrastar o texto para outro local no editor ou no console para mover o texto.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-234">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="dd5eb-235">Se você mantiver pressionada a tecla Ctrl enquanto arrasta o texto selecionado, quando soltar o botão do mouse, o texto será copiado para o novo local.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-235">If you hold down the Ctrl key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="dd5eb-236">Nesta versão do ISE do Windows PowerShell, bem como sua versão anterior, quando você arrasta e solta arquivos no ISE do Windows PowerShell, ele abre o arquivo.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-236">In this version of Windows PowerShell ISE, as well as the previous version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>

- <span data-ttu-id="dd5eb-237">**Analisar a exibição de erro** Erros de análise são indicados com um sublinhado vermelho.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-237">**Parse error display** Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="dd5eb-238">Quando você passa o cursor sobre um erro indicado, o texto da dica de ferramenta exibe o problema encontrado no código.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-238">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>

- <span data-ttu-id="dd5eb-239">**Zoom** É possível definir o percentual de zoom do conteúdo do console usando o controle deslizante de zoom (no canto inferior direito da janela do ISE do Windows PowerShell) ou digitando o comando **$psise.options.Zoom** no Painel de Console.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-239">**Zoom** The zoom percentage of the console'™s content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command **$psise.options.Zoom** in the Console Pane.</span></span>

- <span data-ttu-id="dd5eb-240">**Copiar e colar rich text** A cópia para a área de transferência no ISE do Windows PowerShell preserva as informações de fonte, tamanho e cor da seleção original.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-240">**Rich text copy and paste** Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>

- <span data-ttu-id="dd5eb-241">**Seleção de bloco** Você pode selecionar um bloco de texto mantendo a tecla ALT pressionada enquanto seleciona o texto no Painel de Script com o mouse ou pressionando **Alt+Shift+Seta**.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-241">**Block selection** You can select a block of text by holding down the ALT key while selecting text in the Script Pane with your mouse, or by pressing **Alt+Shift+Arrow**.</span></span>

<span data-ttu-id="dd5eb-242">**Qual é o valor adicionado por esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-242">**What value does this change add?**</span></span>

<span data-ttu-id="dd5eb-243">Os recursos de edição adicionais fornecem um ambiente de edição mais consistente e eficiente.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-243">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="dd5eb-244">**O que passou a funcionar de maneira diferente?**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-244">**What works differently?**</span></span>

<span data-ttu-id="dd5eb-245">Esses aprimoramentos na edição não estavam presentes no ISE do Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-245">These editing enhancements were not present in Windows PowerShell ISE 2.0.</span></span>

### <a name="new-help-viewer-window"></a><span data-ttu-id="dd5eb-246">Janela do novo visualizador da ajuda</span><span class="sxs-lookup"><span data-stu-id="dd5eb-246">New Help viewer window</span></span>
<span data-ttu-id="dd5eb-247">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-247">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="dd5eb-248">Se você pressionar **F1** quando o cursor estiver em um cmdlet ou se parte de um cmdlet estiver realçada, o novo visualizador da Ajuda abrirá uma ajuda contextual sobre o cmdlet realçado.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-248">If you press **F1** when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="dd5eb-249">Para exibir a ajuda conceitual do Windows PowerShell, digite **operators** no painel de console e pressione **F1**.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-249">To display Windows PowerShell About help, type  **operators** in the console pane, and then press **F1**.</span></span>

<span data-ttu-id="dd5eb-250">Antes de usar este recurso, baixe a versão mais atual dos tópicos de ajuda do Windows PowerShell do site da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-250">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="dd5eb-251">O método mais simples para baixar os tópicos da Ajuda é executar o cmdlet **Update-Help** no Painel de Console durante a execução do ISE do Windows PowerShell como administrador.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-251">The simplest method for downloading the Help topics is to run the **Update-Help** cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="dd5eb-252">Você pode alterar onde a tecla **F1** busca Ajuda.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-252">You can alter where the **F1** key looks for Help.</span></span> <span data-ttu-id="dd5eb-253">No menu **Ferramentas**/**Opções**, na guia **Configurações Gerais** em **Outras Configurações**, você pode marcar ou desmarcar a caixa de seleção **Usar conteúdo da ajuda local em vez de conteúdo online**.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-253">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="dd5eb-254">Se estiver selecionado, o cliente procurará o cmdlet Help na Ajuda baixada encontrada na pasta de módulos.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-254">If checked, then the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span>  <span data-ttu-id="dd5eb-255">Se a caixa de seleção estiver desmarcada, o cliente procurará na Biblioteca do TechNet para obter a Ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-255">If the checkbox is cleared, then the client looks on the TechNet library for the cmdlet help.</span></span>

<span data-ttu-id="dd5eb-256">**Qual é o valor adicionado por esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-256">**What value does this change add?**</span></span>

<span data-ttu-id="dd5eb-257">A ajuda contextual sem deixar seu cmdlet ou script atual fornece uma experiência de aprendizado contínuo.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-257">Context-sensitive Help without leaving your current cmdlet or script provides a seamless learning experience.</span></span>

<span data-ttu-id="dd5eb-258">**O que passou a funcionar de maneira diferente?**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-258">**What works differently?**</span></span>

<span data-ttu-id="dd5eb-259">Pressionar o F1 em versões anteriores do ISE do Windows PowerShell abria o arquivo de ajuda no computador local.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-259">Pressing F1 in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="dd5eb-260">No ISE do Windows PowerShell 3.0 e posterior, é aberta uma janela que contém a ajuda para o cmdlet que é configurável e pesquisável.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-260">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="dd5eb-261">Essa experiência da ajuda é uma novidade no ISE do Windows PowerShell 3.0 e a Ajuda Atualizável é uma novidade no Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-261">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

### <a name="show-command-cmdlet"></a><span data-ttu-id="dd5eb-262">Cmdlet Show-Command</span><span class="sxs-lookup"><span data-stu-id="dd5eb-262">Show-Command cmdlet</span></span>
<span data-ttu-id="dd5eb-263">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-263">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="dd5eb-264">O cmdlet **Show-Command** permite compor ou executar um cmdlet ou função preenchendo um formulário gráfico.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-264">The **Show-Command** cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="dd5eb-265">O formulário permite que os usuários trabalhem com o Windows PowerShell em um ambiente gráfico.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-265">The form lets users work with Windows PowerShell in a graphical environment.</span></span> <span data-ttu-id="dd5eb-266">**Show-Command** também permite que os desenvolvedores de scripts avançados criem rapidamente uma GUI baseada no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-266">**Show-Command** also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="dd5eb-267">**Qual é o valor adicionado por esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-267">**What value does this change add?**</span></span>

<span data-ttu-id="dd5eb-268">Usando **Show-Command** em seus scripts do Windows PowerShell, você pode fornecer aos usuários o ambiente gráfico com o qual eles estão familiarizados.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-268">By using **Show-Command** in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they are familiar.</span></span> <span data-ttu-id="dd5eb-269">**Show-Command** também pode ajudar os usuários iniciantes a aprender sobre o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-269">**Show-Command** can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="dd5eb-270">**O que passou a funcionar de maneira diferente?**</span><span class="sxs-lookup"><span data-stu-id="dd5eb-270">**What works differently?**</span></span>

<span data-ttu-id="dd5eb-271">O Show-Command é uma novidade no ISE do Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-271">Show-Command is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd5eb-272">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd5eb-272">See also</span></span>
<span data-ttu-id="dd5eb-273">Para mais informações sobre o ISE do Windows PowerShell no Windows PowerShell, consulte os links a seguir.</span><span class="sxs-lookup"><span data-stu-id="dd5eb-273">For more information about using Windows PowerShell ISE in Windows PowerShell, see the following links.</span></span>

- [<span data-ttu-id="dd5eb-274">Explorando o Ambiente de Script Integrado do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd5eb-274">Exploring the Windows PowerShell Integrated Scripting Environment</span></span>](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
- [<span data-ttu-id="dd5eb-275">ISE no TechNet Wiki</span><span class="sxs-lookup"><span data-stu-id="dd5eb-275">ISE on the TechNet Wiki</span></span>](http://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [<span data-ttu-id="dd5eb-276">Central de Scripts</span><span class="sxs-lookup"><span data-stu-id="dd5eb-276">Script Center</span></span>](http://technet.microsoft.com/scriptcenter/default)