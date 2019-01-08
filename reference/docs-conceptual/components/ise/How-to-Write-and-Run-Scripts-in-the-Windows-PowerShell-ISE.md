---
ms.date: 08/14/2018
keywords: powershell, cmdlet
title: Como gravar e executar scripts no ISE do Windows PowerShell
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 61db5e18f05e8e334cd9ba6dab2cf15dee7390cc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400216"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="deabc-103">Como gravar e executar scripts no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="deabc-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="deabc-104">Este artigo descreve como criar, editar, executar e salvar scripts no Painel de Script.</span><span class="sxs-lookup"><span data-stu-id="deabc-104">This article describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="deabc-105">Como criar e executar scripts</span><span class="sxs-lookup"><span data-stu-id="deabc-105">How to create and run scripts</span></span>

<span data-ttu-id="deabc-106">Você pode abrir e editar arquivos do Windows PowerShell no Painel de Script.</span><span class="sxs-lookup"><span data-stu-id="deabc-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="deabc-107">Tipos de arquivos específicos de interesse no Windows PowerShell são arquivos de script (.ps1), arquivos de dados de script (.psd1) e arquivos de módulo de script (.psm1).</span><span class="sxs-lookup"><span data-stu-id="deabc-107">Specific file types of interest in Windows PowerShell are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="deabc-108">Esses tipos de arquivo são coloridos por sintaxe no editor do Painel de Script.</span><span class="sxs-lookup"><span data-stu-id="deabc-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="deabc-109">Outros tipos de arquivo comuns que você pode abrir no Painel de Script são arquivos de configuração (.ps1xml), arquivos XML e arquivos de texto.</span><span class="sxs-lookup"><span data-stu-id="deabc-109">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="deabc-110">A política de execução do Windows PowerShell determina se você pode executar scripts e carregar perfis e arquivos de configuração do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="deabc-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="deabc-111">A política de execução padrão, Restricted, impede a execução de todos os scripts e impede o carregamento dos perfis.</span><span class="sxs-lookup"><span data-stu-id="deabc-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="deabc-112">Para alterar a política de execução para permitir que os perfis sejam carregados usados, consulte [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) e [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span><span class="sxs-lookup"><span data-stu-id="deabc-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) and [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="deabc-113">Para criar um novo arquivo de script</span><span class="sxs-lookup"><span data-stu-id="deabc-113">To create a new script file</span></span>

<span data-ttu-id="deabc-114">Na barra de ferramentas, clique em **Novo** ou, no menu **Arquivo**, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="deabc-114">On the toolbar, click **New**, or on the **File** menu, click **New**.</span></span> <span data-ttu-id="deabc-115">O arquivo criado aparece em uma nova guia do arquivo sob a guia atual do PowerShell. Lembre-se de que as guias do PowerShell são visíveis apenas quando há mais de uma.</span><span class="sxs-lookup"><span data-stu-id="deabc-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="deabc-116">Por padrão, um arquivo de script de tipo (.ps1) é criado, mas pode ser salvo com um novo nome e uma extensão.</span><span class="sxs-lookup"><span data-stu-id="deabc-116">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="deabc-117">Vários arquivos de script podem ser criados na mesma guia do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="deabc-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="deabc-118">Para abrir um script existente</span><span class="sxs-lookup"><span data-stu-id="deabc-118">To open an existing script</span></span>

<span data-ttu-id="deabc-119">Na barra de ferramentas, clique em **Abrir** ou, no menu **Arquivo**, clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="deabc-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="deabc-120">Na caixa de diálogo **Abrir**, selecione o arquivo que você deseja abrir.</span><span class="sxs-lookup"><span data-stu-id="deabc-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="deabc-121">O arquivo aberto aparece em uma nova guia.</span><span class="sxs-lookup"><span data-stu-id="deabc-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="deabc-122">Para fechar uma guia de script</span><span class="sxs-lookup"><span data-stu-id="deabc-122">To close a script tab</span></span>

<span data-ttu-id="deabc-123">Clique no ícone **Fechar** (X) da guia de arquivo que você quer fechar ou selecione o menu **Arquivo** e clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="deabc-123">Click the **Close** icon (X) of the file tab you want to close or select the **File** menu and click **Close**.</span></span>

<span data-ttu-id="deabc-124">Se o arquivo tiver sido alterado desde que foi salvo pela última vez, você precisará salvá-lo ou descartá-lo.</span><span class="sxs-lookup"><span data-stu-id="deabc-124">If the file has been altered since it was last saved, you're prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="deabc-125">Para exibir o caminho do arquivo</span><span class="sxs-lookup"><span data-stu-id="deabc-125">To display the file path</span></span>

<span data-ttu-id="deabc-126">Na guia arquivo, aponte para o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="deabc-126">On the file tab, point to the file name.</span></span> <span data-ttu-id="deabc-127">O caminho totalmente qualificado para o arquivo de script é exibido em uma dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="deabc-127">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="deabc-128">Para executar um script</span><span class="sxs-lookup"><span data-stu-id="deabc-128">To run a script</span></span>

<span data-ttu-id="deabc-129">Na barra de ferramentas, clique em **Executar Script** ou, no menu **Arquivo**, clique em **Executar**.</span><span class="sxs-lookup"><span data-stu-id="deabc-129">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="deabc-130">Para executar uma parte de um script</span><span class="sxs-lookup"><span data-stu-id="deabc-130">To run a portion of a script</span></span>

1. <span data-ttu-id="deabc-131">No Painel de Script, selecione uma parte de um script.</span><span class="sxs-lookup"><span data-stu-id="deabc-131">In the Script Pane, select a portion of a script.</span></span>
2. <span data-ttu-id="deabc-132">No menu **Arquivo**, clique em **Executar Seleção** ou, na barra de ferramentas, clique em **Executar Seleção**.</span><span class="sxs-lookup"><span data-stu-id="deabc-132">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="deabc-133">Para interromper um script em execução</span><span class="sxs-lookup"><span data-stu-id="deabc-133">To stop a running script</span></span>

<span data-ttu-id="deabc-134">Há várias maneiras para interromper um script em execução.</span><span class="sxs-lookup"><span data-stu-id="deabc-134">There are several ways to stop a running script.</span></span>

- <span data-ttu-id="deabc-135">Clique em **Parar Operação** na barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="deabc-135">Click **Stop Operation** on the toolbar</span></span>
- <span data-ttu-id="deabc-136">Pressione Ctrl+Break</span><span class="sxs-lookup"><span data-stu-id="deabc-136">Press CTRL+BREAK</span></span>
- <span data-ttu-id="deabc-137">Selecione o menu **Arquivo** e clique em **Parar Operação**.</span><span class="sxs-lookup"><span data-stu-id="deabc-137">Select the **File** menu and click **Stop Operation**.</span></span>

<span data-ttu-id="deabc-138">Pressionar **Ctrl+C** também funciona, a menos que algum texto esteja selecionado no momento, quando então **Ctrl+C** é mapeado para a função de cópia do texto selecionado.</span><span class="sxs-lookup"><span data-stu-id="deabc-138">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="deabc-139">Como gravar e editar texto no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="deabc-139">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="deabc-140">Você pode copiar, recortar, colar, localizar e substituir texto no Painel de Script.</span><span class="sxs-lookup"><span data-stu-id="deabc-140">You can copy, cut, paste, find, and replace text in the Script Pane.</span></span> <span data-ttu-id="deabc-141">Você também pode desfazer e refazer a última ação que você acabou de executar.</span><span class="sxs-lookup"><span data-stu-id="deabc-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="deabc-142">Os atalhos de teclado para essas ações são os mesmos usados para todos os aplicativos do Windows.</span><span class="sxs-lookup"><span data-stu-id="deabc-142">The keyboard shortcuts for these actions are the same shortcuts used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="deabc-143">Para inserir texto no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="deabc-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="deabc-144">Mova o cursor para o Painel de Script clicando em qualquer lugar no Painel de Script ou clicando em **Ir para o Painel de Script** no menu **Exibição**.</span><span class="sxs-lookup"><span data-stu-id="deabc-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>
2. <span data-ttu-id="deabc-145">Crie um script.</span><span class="sxs-lookup"><span data-stu-id="deabc-145">Create a script.</span></span> <span data-ttu-id="deabc-146">A coloração de sintaxe e o preenchimento com tabulação fornece uma experiência mais avançada de edição no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="deabc-146">Syntax coloring and tab completion provide a richer editing experience in Windows PowerShell ISE.</span></span>
3. <span data-ttu-id="deabc-147">Consulte [Como usar o preenchimento com Tab no Painel de Script e no Painel de Console](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) para obter detalhes sobre como usar o recurso de preenchimento com Tab para ajudar na digitação.</span><span class="sxs-lookup"><span data-stu-id="deabc-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="deabc-148">Para localizar texto no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="deabc-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="deabc-149">Para localizar texto em qualquer lugar, pressione **Ctrl+F** ou, no menu **Editar**, clique em **Localizar no Script**.</span><span class="sxs-lookup"><span data-stu-id="deabc-149">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>
2. <span data-ttu-id="deabc-150">Para localizar texto após o cursor, pressione **F3** ou, no menu **Editar**, clique em **Localizar Próximo no Script**.</span><span class="sxs-lookup"><span data-stu-id="deabc-150">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>
3. <span data-ttu-id="deabc-151">Para localizar o texto antes do cursor, pressione **Shift+F3** ou, no menu **Editar**, clique em **Localizar Anterior no Script**.</span><span class="sxs-lookup"><span data-stu-id="deabc-151">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="deabc-152">Para localizar e substituir texto no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="deabc-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="deabc-153">Pressione **Ctrl+H** ou, no menu **Editar**, clique em **Substituir no Script**.</span><span class="sxs-lookup"><span data-stu-id="deabc-153">Press **CTRL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="deabc-154">Insira o texto que você deseja localizar e o texto de substituição, depois pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="deabc-154">Enter the text you want to find and the replacement text, then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="deabc-155">Para ir para uma determinada linha de texto no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="deabc-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="deabc-156">No Painel de Script, pressione **Ctrl+G** ou, no menu **Editar**, clique em **Ir para a Linha**.</span><span class="sxs-lookup"><span data-stu-id="deabc-156">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="deabc-157">Insira um número de linha.</span><span class="sxs-lookup"><span data-stu-id="deabc-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="deabc-158">Para copiar o texto no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="deabc-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="deabc-159">No Painel de Script, selecione o texto que você deseja copiar.</span><span class="sxs-lookup"><span data-stu-id="deabc-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="deabc-160">Pressione **Ctrl+C** ou, na barra de ferramentas, clique no ícone **Copiar** ou, no menu **Editar**, clique em **Copiar**.</span><span class="sxs-lookup"><span data-stu-id="deabc-160">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="deabc-161">Para recortar texto no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="deabc-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="deabc-162">No Painel de Script, selecione o texto que você deseja recortar.</span><span class="sxs-lookup"><span data-stu-id="deabc-162">In the Script Pane, select the text that you want to cut.</span></span>
2. <span data-ttu-id="deabc-163">Pressione **Ctrl+X** ou, na barra de ferramentas, clique no ícone **Recortar** ou, no menu **Editar**, clique em **Recortar**.</span><span class="sxs-lookup"><span data-stu-id="deabc-163">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="deabc-164">Para colar o texto no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="deabc-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="deabc-165">Pressione **Ctrl+V** ou, na barra de ferramentas, clique no ícone **Colar** ou, no menu **Editar**, clique em **Colar**.</span><span class="sxs-lookup"><span data-stu-id="deabc-165">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="deabc-166">Para desfazer uma ação no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="deabc-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="deabc-167">Pressione **Ctrl+Z** ou, na barra de ferramentas, clique no ícone **Desfazer** ou, no menu **Editar**, clique em **Desfazer**.</span><span class="sxs-lookup"><span data-stu-id="deabc-167">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="deabc-168">Para refazer uma ação no Painel de Script</span><span class="sxs-lookup"><span data-stu-id="deabc-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="deabc-169">Pressione **Ctrl+Y** ou, na barra de ferramentas, clique no ícone **Refazer** ou, no menu **Editar**, clique em **Refazer**.</span><span class="sxs-lookup"><span data-stu-id="deabc-169">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="deabc-170">Como salvar um script</span><span class="sxs-lookup"><span data-stu-id="deabc-170">How to save a script</span></span>

<span data-ttu-id="deabc-171">Um asterisco é exibido ao lado do nome do script para marcar um arquivo que não foi salvo desde que ele foi alterado.</span><span class="sxs-lookup"><span data-stu-id="deabc-171">An asterisk appears next to the script name to mark a file that hasn't been saved since it was changed.</span></span> <span data-ttu-id="deabc-172">O asterisco desaparece quando o arquivo é salvo.</span><span class="sxs-lookup"><span data-stu-id="deabc-172">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="deabc-173">Para salvar um script</span><span class="sxs-lookup"><span data-stu-id="deabc-173">To save a script</span></span>

<span data-ttu-id="deabc-174">Pressione **Ctrl+S** ou, na barra de ferramentas, clique no ícone **Salvar** ou, no menu **Arquivo**, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="deabc-174">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="deabc-175">Para salvar e nomear um script</span><span class="sxs-lookup"><span data-stu-id="deabc-175">To save and name a script</span></span>

1. <span data-ttu-id="deabc-176">No menu **Arquivo**, clique em **Salvar Como**.</span><span class="sxs-lookup"><span data-stu-id="deabc-176">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="deabc-177">A caixa de diálogo **Salvar Como** é exibida.</span><span class="sxs-lookup"><span data-stu-id="deabc-177">The **Save As** dialog box will appear.</span></span>
2. <span data-ttu-id="deabc-178">Na caixa **Nome do arquivo**, insira um nome para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="deabc-178">In the **File name** box, enter a name for the file.</span></span>
3. <span data-ttu-id="deabc-179">Na caixa **Salvar como tipo**, selecione um tipo de arquivo.</span><span class="sxs-lookup"><span data-stu-id="deabc-179">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="deabc-180">Por exemplo, na caixa **Salvar como tipo**, selecione "Scripts do PowerShell (\*.ps1)".</span><span class="sxs-lookup"><span data-stu-id="deabc-180">For example, in the **Save as type** box, select 'PowerShell Scripts (\*.ps1)'.</span></span>
4. <span data-ttu-id="deabc-181">Clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="deabc-181">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="deabc-182">Para salvar um script em codificação ASCII</span><span class="sxs-lookup"><span data-stu-id="deabc-182">To save a script in ASCII encoding</span></span>

<span data-ttu-id="deabc-183">Por padrão, o ISE do Windows PowerShell salva novos arquivos de script (.ps1), arquivos de dados de script (.psd1) e arquivos de módulo de script (.psm1) como Unicode (BigEndianUnicode). Para salvar um script em outra codificação, como ASCII (ANSI), use os métodos **Save** ou **SaveAs** no objeto [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="deabc-183">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.Â To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) object.</span></span>

<span data-ttu-id="deabc-184">O comando a seguir salva um novo script como MyScript.ps1 com codificação ASCII.</span><span class="sxs-lookup"><span data-stu-id="deabc-184">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="deabc-185">O comando a seguir substitui o arquivo de script atual por um arquivo com o mesmo nome, mas com codificação ASCII.</span><span class="sxs-lookup"><span data-stu-id="deabc-185">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="deabc-186">O comando a seguir obtém a codificação do arquivo atual.</span><span class="sxs-lookup"><span data-stu-id="deabc-186">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="deabc-187">Windows PowerShell ISE suporta as seguintes opções de codifica: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 e padrão.</span><span class="sxs-lookup"><span data-stu-id="deabc-187">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8, and Default.</span></span> <span data-ttu-id="deabc-188">O valor da opção Padrão varia de acordo com o sistema.</span><span class="sxs-lookup"><span data-stu-id="deabc-188">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="deabc-189">O ISE do Windows PowerShell não altera a codificação dos arquivos de script quando você usa os comandos Salvar ou Salvar como.</span><span class="sxs-lookup"><span data-stu-id="deabc-189">Windows PowerShell ISE doesn't change the encoding of script files when you use the Save or Save As commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="deabc-190">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="deabc-190">See Also</span></span>

- [<span data-ttu-id="deabc-191">Explorando o ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="deabc-191">Exploring the Windows PowerShell ISE</span></span>](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
