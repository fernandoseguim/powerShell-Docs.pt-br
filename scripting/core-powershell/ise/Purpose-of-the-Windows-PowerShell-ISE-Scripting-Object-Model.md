---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: Objetivo do modelo de objeto de script do ISE do Windows PowerShell
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: 65535948d681ec63c6cc36583c6d145cfa19b937
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a><span data-ttu-id="c7f52-103">Objetivo do modelo de objeto de script do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7f52-103">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>
  <span data-ttu-id="c7f52-104">Objetos são associados com a forma e a função do ISE (Ambiente de Script Integrado) do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c7f52-104">Objects are associated with the form and function of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="c7f52-105">A referência de modelo de objeto fornece detalhes sobre as propriedades e os métodos de membros que esses objetos expõem.</span><span class="sxs-lookup"><span data-stu-id="c7f52-105">The object model reference provides details about the member properties and methods that these objects expose.</span></span> <span data-ttu-id="c7f52-106">Exemplos são fornecidos para mostrar como você pode usar scripts para acessar diretamente esses métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="c7f52-106">Examples are provided to show how you can use scripts to directly access these methods and properties.</span></span> <span data-ttu-id="c7f52-107">O modelo de objeto de script facilita a gama de tarefas a seguir.</span><span class="sxs-lookup"><span data-stu-id="c7f52-107">The scripting object model makes the following range of tasks easier.</span></span>

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a><span data-ttu-id="c7f52-108">Personalizando a aparência do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7f52-108">Customizing the appearance of Windows PowerShell ISE</span></span>
 <span data-ttu-id="c7f52-109">Você pode usar o modelo de objeto para modificar as configurações e opções do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c7f52-109">You can use the object model to modify the application settings and options.</span></span> <span data-ttu-id="c7f52-110">Por exemplo, você pode modificá-las da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c7f52-110">For example, you can modify them as follows:</span></span>

-   <span data-ttu-id="c7f52-111">Você pode mudar a cor de erros, avisos, saídas detalhadas e saídas de depuração.</span><span class="sxs-lookup"><span data-stu-id="c7f52-111">You can change the color of errors, warnings, verbose outputs, and debug outputs.</span></span>

-   <span data-ttu-id="c7f52-112">Você pode obter ou definir cores de tela de fundo para o painel de Comando, painel de Saída e o painel de Script.</span><span class="sxs-lookup"><span data-stu-id="c7f52-112">You can get or set the background colors for the Command pane, the Output pane, and the Script pane.</span></span>

-   <span data-ttu-id="c7f52-113">Você pode definir a cor de primeiro plano para o painel de Saída.</span><span class="sxs-lookup"><span data-stu-id="c7f52-113">You can set the foreground color for the Output pane.</span></span>

-   <span data-ttu-id="c7f52-114">Você pode definir o nome e tamanho da fonte para o ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c7f52-114">You can set the font name and font size for Windows PowerShell ISE.</span></span>

-   <span data-ttu-id="c7f52-115">Você pode configurar alertas.</span><span class="sxs-lookup"><span data-stu-id="c7f52-115">You can configure warnings.</span></span> <span data-ttu-id="c7f52-116">Essa configuração inclui advertências que são emitidas quando um arquivo é aberto em várias guias do PowerShell ou quando um script no arquivo é executado antes que o arquivo seja salvo.</span><span class="sxs-lookup"><span data-stu-id="c7f52-116">This setting includes warnings that are issued when a file is opened in multiple PowerShell tabs or when a script in the file is run before the file has been saved.</span></span>

-   <span data-ttu-id="c7f52-117">Você pode alternar entre uma exibição em que o painel Script e Painel de saída estão lado em uma exibição em que o painel Script está na parte superior do Painel de saída.</span><span class="sxs-lookup"><span data-stu-id="c7f52-117">You can switch between a view where the Script pane and the Output pane are side-by-side and a view where the Script pane is on top of the Output pane.</span></span> <span data-ttu-id="c7f52-118">Você pode encaixar o painel de Comando na parte inferior ou superior do painel de Saída.</span><span class="sxs-lookup"><span data-stu-id="c7f52-118">You can dock the Command pane to the bottom or the top of the Output pane.</span></span>

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a><span data-ttu-id="c7f52-119">Melhorando a funcionalidade do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7f52-119">Enhancing the functionality of Windows PowerShell ISE</span></span>
 <span data-ttu-id="c7f52-120">Você pode usar o modelo de objeto para melhorar a funcionalidade do ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c7f52-120">You can use the object model to enhance the functionality of Windows PowerShell ISE.</span></span> <span data-ttu-id="c7f52-121">Por exemplo, você pode:</span><span class="sxs-lookup"><span data-stu-id="c7f52-121">For example, you can:</span></span>

-   <span data-ttu-id="c7f52-122">Adicionar e modificar a instância do próprio ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c7f52-122">Add and modify the instance of Windows PowerShell ISE itself.</span></span> <span data-ttu-id="c7f52-123">Por exemplo, para alterar os menus, você pode adicionar novos itens de menu e mapear os novos itens de menu para os scripts.</span><span class="sxs-lookup"><span data-stu-id="c7f52-123">For example, to change the menus, you can add new menu items and map the new menu items to scripts.</span></span>

-   <span data-ttu-id="c7f52-124">Crie scripts que realizam algumas das tarefas que podem ser executadas usando os comandos de menu e botões no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c7f52-124">Create scripts that perform some of the tasks that you can perform by using the menu commands and buttons in Windows PowerShell ISE.</span></span> <span data-ttu-id="c7f52-125">Por exemplo, você pode adicionar, remover ou selecionar uma guia PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c7f52-125">For example, you can add, remove, or select a PowerShell tab.</span></span>

-   <span data-ttu-id="c7f52-126">Complemente tarefas que podem ser realizadas usando comandos e botões de menu.</span><span class="sxs-lookup"><span data-stu-id="c7f52-126">Complement tasks that can be performed by using menu commands and buttons.</span></span> <span data-ttu-id="c7f52-127">Por exemplo, você pode renomear uma guia do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c7f52-127">For example, you can rename a PowerShell tab.</span></span>

-   <span data-ttu-id="c7f52-128">Manipule buffers de texto para os painéis de Comando, Saída e Script associados a um arquivo.</span><span class="sxs-lookup"><span data-stu-id="c7f52-128">Manipulate text buffers for the Command pane, the Output pane, and the Script pane that are associated with a file.</span></span> <span data-ttu-id="c7f52-129">Por exemplo, você pode:</span><span class="sxs-lookup"><span data-stu-id="c7f52-129">For example, you can:</span></span>

    -   <span data-ttu-id="c7f52-130">Obtenha ou defina todo o texto.</span><span class="sxs-lookup"><span data-stu-id="c7f52-130">Get or set all text.</span></span>

    -   <span data-ttu-id="c7f52-131">Obtenha ou defina uma seleção de texto.</span><span class="sxs-lookup"><span data-stu-id="c7f52-131">Get or set a text selection.</span></span>

    -   <span data-ttu-id="c7f52-132">Execute um script ou uma parte selecionada de um script.</span><span class="sxs-lookup"><span data-stu-id="c7f52-132">Run a script or run a selected portion of a script.</span></span>

    -   <span data-ttu-id="c7f52-133">Role uma linha até uma exibição.</span><span class="sxs-lookup"><span data-stu-id="c7f52-133">Scroll a line into view.</span></span>

    -   <span data-ttu-id="c7f52-134">Insira texto em uma posição de cursor.</span><span class="sxs-lookup"><span data-stu-id="c7f52-134">Insert text at a caret position.</span></span>

    -   <span data-ttu-id="c7f52-135">Selecione um bloco de texto.</span><span class="sxs-lookup"><span data-stu-id="c7f52-135">Select a block of text.</span></span>

    -   <span data-ttu-id="c7f52-136">Obtenha o último número de linha.</span><span class="sxs-lookup"><span data-stu-id="c7f52-136">Get the last line number.</span></span>

-   <span data-ttu-id="c7f52-137">Execute operações de arquivo.</span><span class="sxs-lookup"><span data-stu-id="c7f52-137">Perform file operations.</span></span> <span data-ttu-id="c7f52-138">Por exemplo, você pode:</span><span class="sxs-lookup"><span data-stu-id="c7f52-138">For example, you can:</span></span>

    -   <span data-ttu-id="c7f52-139">Abrir um arquivo, salvar um arquivo ou salvar um arquivo usando um nome diferente.</span><span class="sxs-lookup"><span data-stu-id="c7f52-139">Open a file, save a file, or save a file by using a different name.</span></span>

    -   <span data-ttu-id="c7f52-140">Determine se um arquivo foi alterado depois que foi salvo pela última vez.</span><span class="sxs-lookup"><span data-stu-id="c7f52-140">Determine whether a file has been changed after it was last saved.</span></span>

    -   <span data-ttu-id="c7f52-141">Obtenha o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="c7f52-141">Get the file name.</span></span>

    -   <span data-ttu-id="c7f52-142">Selecione um arquivo.</span><span class="sxs-lookup"><span data-stu-id="c7f52-142">Select a file.</span></span>

## <a name="automating-tasks"></a><span data-ttu-id="c7f52-143">Automatizando tarefas</span><span class="sxs-lookup"><span data-stu-id="c7f52-143">Automating tasks</span></span>
 <span data-ttu-id="c7f52-144">Você pode usar o modelo de objeto de script para criar atalhos de teclado para operações frequentes.</span><span class="sxs-lookup"><span data-stu-id="c7f52-144">You can use the scripting object model to create keyboard shortcuts for frequent operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7f52-145">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="c7f52-145">See Also</span></span>
- [<span data-ttu-id="c7f52-146">A hierarquia de modelo de objeto do ISE</span><span class="sxs-lookup"><span data-stu-id="c7f52-146">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md) 
- [<span data-ttu-id="c7f52-147">Referência de modelo de objeto do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7f52-147">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="c7f52-148">O modelo de objeto de script do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7f52-148">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
