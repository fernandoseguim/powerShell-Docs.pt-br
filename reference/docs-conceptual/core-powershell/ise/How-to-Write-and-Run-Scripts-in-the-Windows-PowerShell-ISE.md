---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: Como gravar e executar scripts no ISE do Windows PowerShell
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 577ecf96027618a0a8f98d5bcefe7ec949f337cc
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2017
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="26f6f-103">Como gravar e executar scripts no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="26f6f-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>
<span data-ttu-id="26f6f-104">Este tópico descreve como criar, editar, executar e salvar scripts no Painel de Script.</span><span class="sxs-lookup"><span data-stu-id="26f6f-104">This topic describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

-   [<span data-ttu-id="26f6f-105">Como criar e executar scripts</span><span class="sxs-lookup"><span data-stu-id="26f6f-105">How to create and run scripts</span></span>]()

-   [<span data-ttu-id="26f6f-106">Como escrever e editar texto no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="26f6f-106">How to write and edit text in the Script Pane</span></span>]()

-   [<span data-ttu-id="26f6f-107">Como salvar um script</span><span class="sxs-lookup"><span data-stu-id="26f6f-107">How to save a script</span></span>]()

## <span data-ttu-id="26f6f-108"><a name="bkmk_1"></a>Como criar e executar scripts</span><span class="sxs-lookup"><span data-stu-id="26f6f-108"><a name="bkmk_1"></a>How to create and run scripts</span></span>
<span data-ttu-id="26f6f-109">Você pode abrir e editar arquivos do Windows PowerShell® no Painel de Script.</span><span class="sxs-lookup"><span data-stu-id="26f6f-109">You can open and edit Windows PowerShell® files in the Script Pane.</span></span> <span data-ttu-id="26f6f-110">Tipos de arquivos específicos de interesse no Windows PowerShell® são arquivos de script (.ps1), arquivos de dados de script (.psd1) e arquivos de módulo de script (.psm1).</span><span class="sxs-lookup"><span data-stu-id="26f6f-110">Specific file types of interest in Windows PowerShell® are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="26f6f-111">Esses tipos de arquivo são coloridos por sintaxe no editor do Painel de Script.</span><span class="sxs-lookup"><span data-stu-id="26f6f-111">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="26f6f-112">Outros tipos de arquivo comuns que você pode abrir no Painel de Script são arquivos de configuração (.ps1xml), arquivos XML e arquivos de texto.</span><span class="sxs-lookup"><span data-stu-id="26f6f-112">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="26f6f-113">A política de execução do Windows PowerShell determina se você pode executar scripts e carregar perfis e arquivos de configuração do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26f6f-113">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="26f6f-114">A política de execução padrão, Restricted, impede a execução de todos os scripts e impede o carregamento dos perfis.</span><span class="sxs-lookup"><span data-stu-id="26f6f-114">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="26f6f-115">Para alterar a política de execução para permitir que os perfis sejam carregados usados, consulte [Set-ExecutionPolicy [PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) e [about_Signing [v4]](https://technet.microsoft.com/en-us/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span><span class="sxs-lookup"><span data-stu-id="26f6f-115">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) and [about_Signing [v4]](https://technet.microsoft.com/en-us/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="26f6f-116">Para criar um novo arquivo de script</span><span class="sxs-lookup"><span data-stu-id="26f6f-116">To create a new script file</span></span>
<span data-ttu-id="26f6f-117">Na barra de ferramentas, clique em **Novo** ou, no menu **Arquivo**, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-117">On the toolbar, click **New** , or on the **File** menu, click **New**.</span></span> <span data-ttu-id="26f6f-118">O arquivo criado aparece em uma nova guia do arquivo sob a guia atual do PowerShell. Lembre-se de que as guias do PowerShell são visíveis apenas quando há mais de uma.</span><span class="sxs-lookup"><span data-stu-id="26f6f-118">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="26f6f-119">Por padrão, um arquivo de script de tipo (.ps1) é criado, mas pode ser salvo com um novo nome e uma extensão.</span><span class="sxs-lookup"><span data-stu-id="26f6f-119">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="26f6f-120">Vários arquivos de script podem ser criados na mesma guia do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26f6f-120">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="26f6f-121">Para abrir um script existente</span><span class="sxs-lookup"><span data-stu-id="26f6f-121">To open an existing script</span></span>
<span data-ttu-id="26f6f-122">Na barra de ferramentas, clique em **Abrir...** ou, no menu **Arquivo**, clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-122">On the toolbar, click **Open…**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="26f6f-123">Na caixa de diálogo **Abrir**, selecione o arquivo que você deseja abrir.</span><span class="sxs-lookup"><span data-stu-id="26f6f-123">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="26f6f-124">O arquivo aberto aparece em uma nova guia.</span><span class="sxs-lookup"><span data-stu-id="26f6f-124">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="26f6f-125">Para fechar uma guia de script</span><span class="sxs-lookup"><span data-stu-id="26f6f-125">To close a script tab</span></span>
<span data-ttu-id="26f6f-126">Clique na guia script do script que deseja fechar e siga um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="26f6f-126">Click the script tab of the script you want to close, then do one of the following:</span></span>

1.  <span data-ttu-id="26f6f-127">Clique no ícone **Fechar** (X) na guia do script.</span><span class="sxs-lookup"><span data-stu-id="26f6f-127">Click the **Close** icon (X) on the script tab.</span></span>

2.  <span data-ttu-id="26f6f-128">No menu **Arquivo**, clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-128">On the **File** menu, click **Close**.</span></span>

<span data-ttu-id="26f6f-129">Se o arquivo tiver sido alterado desde que foi salvo pela última vez, você precisará salvá-lo ou descartá-lo.</span><span class="sxs-lookup"><span data-stu-id="26f6f-129">If the file has been altered since it was last saved, you are prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="26f6f-130">Para exibir o caminho do arquivo</span><span class="sxs-lookup"><span data-stu-id="26f6f-130">To display the file path</span></span>
<span data-ttu-id="26f6f-131">Na guia arquivo, aponte para o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="26f6f-131">On the file tab, point to the file name.</span></span> <span data-ttu-id="26f6f-132">O caminho totalmente qualificado para o arquivo de script é exibido em uma dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="26f6f-132">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="26f6f-133">Para executar um script</span><span class="sxs-lookup"><span data-stu-id="26f6f-133">To run a script</span></span>
<span data-ttu-id="26f6f-134">Na barra de ferramentas, clique em **Executar Script** ou, no menu **Arquivo**, clique em **Executar**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-134">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="26f6f-135">Para executar uma parte de um script</span><span class="sxs-lookup"><span data-stu-id="26f6f-135">To run a portion of a script</span></span>

1.  <span data-ttu-id="26f6f-136">No Painel de Script, selecione uma parte de um script.</span><span class="sxs-lookup"><span data-stu-id="26f6f-136">In the Script Pane, select a portion of a script.</span></span>

2.  <span data-ttu-id="26f6f-137">No menu **Arquivo**, clique em **Executar Seleção** ou, na barra de ferramentas, clique em **Executar Seleção**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-137">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="26f6f-138">Para interromper um script em execução</span><span class="sxs-lookup"><span data-stu-id="26f6f-138">To stop a running script</span></span>
<span data-ttu-id="26f6f-139">Na barra de ferramentas, clique em **Parar Operação**, pressione Ctrl+Break ou, no menu **Arquivo**, clique em **Parar Operação**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-139">On the toolbar, click **Stop Operation**, press CTRL+BREAK, or on the **File** menu, click **Stop Operation**.</span></span> <span data-ttu-id="26f6f-140">Pressionar **Ctrl+C** também funciona, a menos que algum texto esteja selecionado no momento, quando então **Ctrl+C** é mapeado para a função de cópia do texto selecionado.</span><span class="sxs-lookup"><span data-stu-id="26f6f-140">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <span data-ttu-id="26f6f-141"><a name="bkmk_2"></a>Como gravar e editar texto no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="26f6f-141"><a name="bkmk_2"></a>How to write and edit text in the Script Pane</span></span>
<span data-ttu-id="26f6f-142">Use as etapas a seguir para editar texto no Painel de Script.</span><span class="sxs-lookup"><span data-stu-id="26f6f-142">Use the following steps to edit text in the Script Pane.</span></span> <span data-ttu-id="26f6f-143">Você pode copiar, recortar, colar, localizar e substituir texto.</span><span class="sxs-lookup"><span data-stu-id="26f6f-143">You can copy, cut, paste, find, and replace text.</span></span> <span data-ttu-id="26f6f-144">Você também pode desfazer e refazer a última ação que você acabou de executar.</span><span class="sxs-lookup"><span data-stu-id="26f6f-144">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="26f6f-145">Os atalhos de teclado para executar essas ações são os mesmos usados para todos os aplicativos do Windows.</span><span class="sxs-lookup"><span data-stu-id="26f6f-145">The keyboard shortcuts for performing these actions are the same as those used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="26f6f-146">Para inserir texto no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="26f6f-146">To enter text in the Script Pane</span></span>

1.  <span data-ttu-id="26f6f-147">Mova o cursor para o Painel de Script clicando em qualquer lugar no Painel de Script ou clicando em **Ir para o Painel de Script** no menu **Exibição**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-147">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>

2.  <span data-ttu-id="26f6f-148">Crie um script.</span><span class="sxs-lookup"><span data-stu-id="26f6f-148">Create a script.</span></span> <span data-ttu-id="26f6f-149">A coloração de sintaxe e o preenchimento com Tab tornam esta uma experiência mais avançada no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26f6f-149">Syntax coloring and tab completion make this a richer experience in Windows PowerShell ISE.</span></span>

3.  <span data-ttu-id="26f6f-150">Consulte [Como usar o preenchimento com Tab no Painel de Script e no Painel de Console](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) para obter detalhes sobre como usar o recurso de preenchimento com Tab para ajudar na digitação.</span><span class="sxs-lookup"><span data-stu-id="26f6f-150">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="26f6f-151">Para localizar texto no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="26f6f-151">To find text in the Script Pane</span></span>

1.  <span data-ttu-id="26f6f-152">Para localizar texto em qualquer lugar, pressione **Ctrl+F** ou, no menu **Editar**, clique em **Localizar no Script**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-152">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>

2.  <span data-ttu-id="26f6f-153">Para localizar texto após o cursor, pressione **F3** ou, no menu **Editar**, clique em **Localizar Próximo no Script**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-153">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>

3.  <span data-ttu-id="26f6f-154">Para localizar o texto antes do cursor, pressione **Shift+F3** ou, no menu **Editar**, clique em **Localizar Anterior no Script**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-154">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="26f6f-155">Para localizar e substituir texto no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="26f6f-155">To find and replace text in the Script Pane</span></span>
<span data-ttu-id="26f6f-156">Pressione **CRTL+H** ou, no menu **Editar**, clique em **Substituir no Script**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-156">Press **CRTL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="26f6f-157">Insira o texto que você deseja localizar e o texto com o qual você deseja substituí-lo, e então pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-157">Enter both the text you want to find and the text with which you want to replace it, and then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="26f6f-158">Para ir para uma determinada linha de texto no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="26f6f-158">To go to a particular line of text in the Script Pane</span></span>

1.  <span data-ttu-id="26f6f-159">No Painel de Script, pressione **Ctrl+G** ou, no menu **Editar**, clique em **Ir para a Linha**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-159">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2.  <span data-ttu-id="26f6f-160">Insira um número de linha.</span><span class="sxs-lookup"><span data-stu-id="26f6f-160">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="26f6f-161">Para copiar o texto no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="26f6f-161">To copy text in the Script Pane</span></span>

1.  <span data-ttu-id="26f6f-162">No Painel de Script, selecione o texto que você deseja copiar.</span><span class="sxs-lookup"><span data-stu-id="26f6f-162">In the Script Pane, select the text that you want to copy.</span></span>

2.  <span data-ttu-id="26f6f-163">Pressione **Ctrl+C** ou, na barra de ferramentas, clique no ícone **Copiar** ou, no menu **Editar**, clique em **Copiar**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-163">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="26f6f-164">Para recortar texto no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="26f6f-164">To cut text in the Script Pane</span></span>

1.  <span data-ttu-id="26f6f-165">No Painel de Script, selecione o texto que você deseja recortar.</span><span class="sxs-lookup"><span data-stu-id="26f6f-165">In the Script Pane, select the text that you want to cut.</span></span>

2.  <span data-ttu-id="26f6f-166">Pressione **Ctrl+X** ou, na barra de ferramentas, clique no ícone **Recortar** ou, no menu **Editar**, clique em **Recortar**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-166">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="26f6f-167">Para colar o texto no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="26f6f-167">To paste text into the Script Pane</span></span>
<span data-ttu-id="26f6f-168">Pressione **Ctrl+V** ou, na barra de ferramentas, clique no ícone **Colar** ou, no menu **Editar**, clique em **Colar**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-168">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="26f6f-169">Para desfazer uma ação no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="26f6f-169">To undo an action in the Script Pane</span></span>
<span data-ttu-id="26f6f-170">Pressione **Ctrl+Z** ou, na barra de ferramentas, clique no ícone **Desfazer** ou, no menu **Editar**, clique em **Desfazer**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-170">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="26f6f-171">Para refazer uma ação no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="26f6f-171">To redo an action in the Script Pane</span></span>
<span data-ttu-id="26f6f-172">Pressione **Ctrl+Y** ou, na barra de ferramentas, clique no ícone **Refazer** ou, no menu **Editar**, clique em **Refazer**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-172">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <span data-ttu-id="26f6f-173"><a name="bkmk_3"></a>Como salvar um script</span><span class="sxs-lookup"><span data-stu-id="26f6f-173"><a name="bkmk_3"></a>How to save a script</span></span>
<span data-ttu-id="26f6f-174">Use as etapas a seguir para salvar e nomear um script.</span><span class="sxs-lookup"><span data-stu-id="26f6f-174">Use the following steps to save and name a script.</span></span> <span data-ttu-id="26f6f-175">Um asterisco é exibido ao lado do nome do script para marcar um arquivo que não foi salvo desde que ele foi alterado.</span><span class="sxs-lookup"><span data-stu-id="26f6f-175">An asterisk appears next to the script name to mark a file that has not been saved since it was altered.</span></span> <span data-ttu-id="26f6f-176">O asterisco desaparece quando o arquivo é salvo.</span><span class="sxs-lookup"><span data-stu-id="26f6f-176">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="26f6f-177">Para salvar um script</span><span class="sxs-lookup"><span data-stu-id="26f6f-177">To save a script</span></span>
<span data-ttu-id="26f6f-178">Pressione **Ctrl+S** ou, na barra de ferramentas, clique no ícone **Salvar** ou, no menu **Arquivo**, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-178">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="26f6f-179">Para salvar e nomear um script</span><span class="sxs-lookup"><span data-stu-id="26f6f-179">To save and name a script</span></span>

1.  <span data-ttu-id="26f6f-180">No menu **Arquivo**, clique em **Salvar Como**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-180">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="26f6f-181">A caixa de diálogo **Salvar Como** é exibida.</span><span class="sxs-lookup"><span data-stu-id="26f6f-181">The **Save As** dialog box will appear.</span></span>

2.  <span data-ttu-id="26f6f-182">Na caixa **Nome do arquivo**, insira um nome para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="26f6f-182">In the **File name** box, enter a name for the file.</span></span>

3.  <span data-ttu-id="26f6f-183">Na caixa **Salvar como tipo**, selecione um tipo de arquivo.</span><span class="sxs-lookup"><span data-stu-id="26f6f-183">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="26f6f-184">Por exemplo, na caixa **Salvar como tipo**, selecione "Scripts do PowerShell (\* .ps1)".</span><span class="sxs-lookup"><span data-stu-id="26f6f-184">For example, in the **Save as type** box, select “PowerShell Scripts (\* .ps1)”.</span></span>

4.  <span data-ttu-id="26f6f-185">Clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="26f6f-185">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="26f6f-186">Para salvar um script em codificação ASCII</span><span class="sxs-lookup"><span data-stu-id="26f6f-186">To save a script in ASCII encoding</span></span>
<span data-ttu-id="26f6f-187">Por padrão, o ISE do Windows PowerShell salva os novos arquivos de script (.ps1), arquivos de dados de script (.psd1) e arquivos de módulo de script (.psm1) como Unicode (BigEndianUnicode).</span><span class="sxs-lookup"><span data-stu-id="26f6f-187">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.</span></span> <span data-ttu-id="26f6f-188">Para salvar um script em outra codificação, como ASCII (ANSI), use os métodos **Save** ou **SaveAs** do objeto [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile).</span><span class="sxs-lookup"><span data-stu-id="26f6f-188">To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) object.</span></span>

<span data-ttu-id="26f6f-189">O comando a seguir salva um novo script como MyScript.ps1 com codificação ASCII.</span><span class="sxs-lookup"><span data-stu-id="26f6f-189">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```
$psise.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="26f6f-190">O comando a seguir substitui o arquivo de script atual por um arquivo com o mesmo nome, mas com codificação ASCII.</span><span class="sxs-lookup"><span data-stu-id="26f6f-190">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```
$psise.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="26f6f-191">O comando a seguir obtém a codificação do arquivo atual.</span><span class="sxs-lookup"><span data-stu-id="26f6f-191">The following command gets the encoding of the current file.</span></span>

```
$psise.CurrentFile.encoding
```

<span data-ttu-id="26f6f-192">O ISE do Windows PowerShell dá suporte às seguintes opções de codificação: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 e Padrão.</span><span class="sxs-lookup"><span data-stu-id="26f6f-192">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 and Default.</span></span> <span data-ttu-id="26f6f-193">O valor da opção Padrão varia de acordo com o sistema.</span><span class="sxs-lookup"><span data-stu-id="26f6f-193">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="26f6f-194">O ISE do Windows PowerShell não altera a codificação de scripts criados por outros editores, mesmo quando você usa os comandos Salvar ou Salvar Como no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26f6f-194">Windows PowerShell ISE does not change the encoding of scripts that were created by in other editors, even when you use the Save or Save As commands in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="26f6f-195">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="26f6f-195">See Also</span></span>
- [<span data-ttu-id="26f6f-196">Usando o ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="26f6f-196">Using the Windows PowerShell ISE</span></span>](Using-the-Windows-PowerShell-ISE.md)

