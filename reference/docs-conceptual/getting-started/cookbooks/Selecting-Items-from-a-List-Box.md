---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: Selecionando itens de uma caixa de listagem
ms.assetid: 327c7cc5-21d0-4ace-b151-aa1491d1d3c2
ms.openlocfilehash: 5b41ebfb193062a17abcc6ad6ddf1a2d9241a39e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2017
---
# <a name="selecting-items-from-a-list-box"></a><span data-ttu-id="b10e3-103">Selecionando itens de uma caixa de listagem</span><span class="sxs-lookup"><span data-stu-id="b10e3-103">Selecting Items from a List Box</span></span>
<span data-ttu-id="b10e3-104">Use o Windows PowerShell 3.0 e versões posteriores para criar uma caixa de diálogo que permite aos usuários selecionar itens de um controle de caixa de listagem.</span><span class="sxs-lookup"><span data-stu-id="b10e3-104">Use Windows PowerShell 3.0 and later releases to create a dialog box that lets users select items from a list box control.</span></span>

## <a name="create-a-list-box-control-and-select-items-from-it"></a><span data-ttu-id="b10e3-105">Criar um controle de caixa de listagem e selecionar itens dela</span><span class="sxs-lookup"><span data-stu-id="b10e3-105">Create a list box control, and select items from it</span></span>
<span data-ttu-id="b10e3-106">Copie e cole o seguinte no Windows PowerShell ISE e salve-o como um script do Windows PowerShell (.ps1).</span><span class="sxs-lookup"><span data-stu-id="b10e3-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form 
$form.Text = "Select a Computer"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please select a computer:"
$form.Controls.Add($label) 

$listBox = New-Object System.Windows.Forms.ListBox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 
$listBox.Height = 80

[void] $listBox.Items.Add("atl-dc-001")
[void] $listBox.Items.Add("atl-dc-002")
[void] $listBox.Items.Add("atl-dc-003")
[void] $listBox.Items.Add("atl-dc-004")
[void] $listBox.Items.Add("atl-dc-005")
[void] $listBox.Items.Add("atl-dc-006")
[void] $listBox.Items.Add("atl-dc-007")

$form.Controls.Add($listBox) 

$form.Topmost = $True

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

<span data-ttu-id="b10e3-107">O script começa carregando duas classes do .NET Framework: **System.Drawing** e **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="b10e3-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="b10e3-108">Inicie uma nova instância da classe do .NET Framework **System.Windows.Forms.Form**, que fornece um formulário em branco ou janela ao qual você pode começar a adicionar controles.</span><span class="sxs-lookup"><span data-stu-id="b10e3-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

<span data-ttu-id="b10e3-109">Depois de criar uma instância da classe Form, atribua valores a três propriedades dessa classe.</span><span class="sxs-lookup"><span data-stu-id="b10e3-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="b10e3-110">**Text.**</span><span class="sxs-lookup"><span data-stu-id="b10e3-110">**Text.**</span></span> <span data-ttu-id="b10e3-111">Isso se torna o título da janela.</span><span class="sxs-lookup"><span data-stu-id="b10e3-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="b10e3-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="b10e3-112">**Size.**</span></span> <span data-ttu-id="b10e3-113">Esse é o tamanho do formulário, em pixels.</span><span class="sxs-lookup"><span data-stu-id="b10e3-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="b10e3-114">O script anterior cria um formulário que possui 300 pixels de largura por 200 pixels de altura.</span><span class="sxs-lookup"><span data-stu-id="b10e3-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="b10e3-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="b10e3-115">**StartingPosition.**</span></span> <span data-ttu-id="b10e3-116">Esta propriedade opcional é definida para **CenterScreen** no script precedente.</span><span class="sxs-lookup"><span data-stu-id="b10e3-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="b10e3-117">Se você não adicionar essa propriedade, o Windows seleciona um local quando o formulário aberto.</span><span class="sxs-lookup"><span data-stu-id="b10e3-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="b10e3-118">Ao configurar o **StartingPosition** para **CenterScreen**, você está exibindo automaticamente o formulário no meio da tela cada vez que ela é carregada.</span><span class="sxs-lookup"><span data-stu-id="b10e3-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```
$form.Text = "Select a Computer"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

<span data-ttu-id="b10e3-119">Em seguida, crie um botão **OK** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="b10e3-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="b10e3-120">Especifique o tamanho e comportamento do botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="b10e3-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="b10e3-121">Neste exemplo, a posição do botão é de 120 pixels a partir da borda superior do formulário e 75 pixels a partir da borda esquerda.</span><span class="sxs-lookup"><span data-stu-id="b10e3-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="b10e3-122">A altura do botão é de 23 pixels, enquanto seu comprimento é de 75 pixels.</span><span class="sxs-lookup"><span data-stu-id="b10e3-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="b10e3-123">O script usa tipos predefinidos de formulários do Windows para determinar os comportamentos do botão.</span><span class="sxs-lookup"><span data-stu-id="b10e3-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="b10e3-124">Crie o botão **Cancelar** da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="b10e3-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="b10e3-125">O botão **Cancelar** fica a 120 pixels da parte superior e 150 pixels da borda esquerda da janela.</span><span class="sxs-lookup"><span data-stu-id="b10e3-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="b10e3-126">Em seguida, forneça o texto de rótulo na janela que descreve as informações que você deseja que os usuários forneçam.</span><span class="sxs-lookup"><span data-stu-id="b10e3-126">Next, provide label text on your window that describes the information you want users to provide.</span></span> <span data-ttu-id="b10e3-127">Nesse caso, é recomendável que os usuários selecionem um computador.</span><span class="sxs-lookup"><span data-stu-id="b10e3-127">In this case, you want users to select a computer.</span></span>

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please select a computer:"
$form.Controls.Add($label)
```

<span data-ttu-id="b10e3-128">Adicione o controle (no caso, uma caixa de listagem) que permite que os usuários forneçam as informações descritas no texto do rótulo.</span><span class="sxs-lookup"><span data-stu-id="b10e3-128">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="b10e3-129">Há muitos outros controles que você pode aplicar além de caixas de listagem. Para ver mais controles, consulte [Namespace System.Windows.Forms](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) no MSDN.</span><span class="sxs-lookup"><span data-stu-id="b10e3-129">There are many other controls you can apply besides list boxes; for more controls, see [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```
$listBox = New-Object System.Windows.Forms.ListBox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 
$listBox.Height = 80
```

<span data-ttu-id="b10e3-130">Na próxima seção, você deve especificar os valores que você deseja que a caixa de listagem mostre para os usuários.</span><span class="sxs-lookup"><span data-stu-id="b10e3-130">In the next section, you specify the values you want the list box to display to users.</span></span>

> [!NOTE]
> <span data-ttu-id="b10e3-131">A caixa de listagem criada por esse script permite somente uma seleção.</span><span class="sxs-lookup"><span data-stu-id="b10e3-131">The list box created by this script allows only one selection.</span></span> <span data-ttu-id="b10e3-132">Para criar um controle de caixa de listagem que permita várias seleções, especifique um valor para a propriedade **SelectionMode**, de forma semelhante à seguinte: `$listBox.SelectionMode = "MultiExtended"`.</span><span class="sxs-lookup"><span data-stu-id="b10e3-132">To create a list box control that allows multiple selections, specify a value for the **SelectionMode** property, similarly to the following:  `$listBox.SelectionMode = "MultiExtended"`.</span></span> <span data-ttu-id="b10e3-133">Para obter mais informações, consulte [Caixas de listagem de seleção múltipla](Multiple-selection-List-Boxes.md).</span><span class="sxs-lookup"><span data-stu-id="b10e3-133">For more information, see [Multiple-selection List Boxes](Multiple-selection-List-Boxes.md).</span></span>

```
[void] $listBox.Items.Add("atl-dc-001")
[void] $listBox.Items.Add("atl-dc-002")
[void] $listBox.Items.Add("atl-dc-003")
[void] $listBox.Items.Add("atl-dc-004")
[void] $listBox.Items.Add("atl-dc-005")
[void] $listBox.Items.Add("atl-dc-006")
[void] $listBox.Items.Add("atl-dc-007")
```

<span data-ttu-id="b10e3-134">Adicione o controle de caixa de listagem ao formulário e instrua o Windows a abrir o formulário sobre outras janelas e caixas de diálogo quando ela é aberta.</span><span class="sxs-lookup"><span data-stu-id="b10e3-134">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```
$form.Controls.Add($listBox) 
$form.Topmost = $True
```

<span data-ttu-id="b10e3-135">Adicione a seguinte linha de código para exibir o formulário do Windows.</span><span class="sxs-lookup"><span data-stu-id="b10e3-135">Add the following line of code to display the form in Windows.</span></span>

```
$result = $form.ShowDialog()
```

<span data-ttu-id="b10e3-136">Por fim, o código dentro do bloco **If** instrui o Windows sobre o que fazer com o formulário depois que os usuários selecionam uma opção na caixa de listagem e clicam no botão **OK** ou pressionam a tecla **Enter**.</span><span class="sxs-lookup"><span data-stu-id="b10e3-136">Finally, the code inside the **If** block instructs Windows what to do with the form after users select an option from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="b10e3-137">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="b10e3-137">See Also</span></span>
- [<span data-ttu-id="b10e3-138">Ei Scripting Guy: por que esses exemplos de GUI do PowerShell não funcionam?</span><span class="sxs-lookup"><span data-stu-id="b10e3-138">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="b10e3-139">GitHub: WinFormsExampleUpdates do Dave Wyatt</span><span class="sxs-lookup"><span data-stu-id="b10e3-139">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- <span data-ttu-id="b10e3-140">[Windows PowerShell Tip of the Week: Selecting Items from a List Box](http://technet.microsoft.com/library/ff730949.aspx) (Dica da semana do Windows PowerShell: selecionando itens de uma caixa de listagem)</span><span class="sxs-lookup"><span data-stu-id="b10e3-140">[Windows PowerShell Tip of the Week:  Selecting Items from a List Box](http://technet.microsoft.com/library/ff730949.aspx)</span></span>

