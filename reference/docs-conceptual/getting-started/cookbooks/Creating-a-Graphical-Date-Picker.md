---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: "Criando um seletor de data gráfico"
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 5cb952264092d345945318968cf0b3028b11f3e9
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="4f266-103">Criando um seletor de data gráfico</span><span class="sxs-lookup"><span data-stu-id="4f266-103">Creating a Graphical Date Picker</span></span>
<span data-ttu-id="4f266-104">Use o Windows PowerShell 3.0 e versões posteriores para criar um formulário com um controle de calendário de estilo gráfico, que permite aos usuários selecionar um dia do mês.</span><span class="sxs-lookup"><span data-stu-id="4f266-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="4f266-105">Crie um controle de seletor de data gráfico</span><span class="sxs-lookup"><span data-stu-id="4f266-105">Create a graphical date-picker control</span></span>
<span data-ttu-id="4f266-106">Copie e cole o seguinte no Windows PowerShell ISE e salve-o como um script do Windows PowerShell (.ps1).</span><span class="sxs-lookup"><span data-stu-id="4f266-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form 

$form.Text = "Select a Date" 
$form.Size = New-Object Drawing.Size @(243,230) 
$form.StartPosition = "CenterScreen"

$calendar = New-Object System.Windows.Forms.MonthCalendar 
$calendar.ShowTodayCircle = $False
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar) 

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$form.Topmost = $True

$result = $form.ShowDialog() 

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

<span data-ttu-id="4f266-107">O script começa carregando duas classes do .NET Framework: **System.Drawing** e **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="4f266-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="4f266-108">Inicie uma nova instância da classe do .NET Framework **Windows.Forms.Form**, que fornece um formulário em branco ou ao qual você pode começar a adicionar controles de janela.</span><span class="sxs-lookup"><span data-stu-id="4f266-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```
$form = New-Object Windows.Forms.Form
```

<span data-ttu-id="4f266-109">Depois de criar uma instância da classe Form, atribua valores a três propriedades dessa classe.</span><span class="sxs-lookup"><span data-stu-id="4f266-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

-   <span data-ttu-id="4f266-110">**Text.**</span><span class="sxs-lookup"><span data-stu-id="4f266-110">**Text.**</span></span> <span data-ttu-id="4f266-111">Isso se torna o título da janela.</span><span class="sxs-lookup"><span data-stu-id="4f266-111">This becomes the title of the window.</span></span>

-   <span data-ttu-id="4f266-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="4f266-112">**Size.**</span></span> <span data-ttu-id="4f266-113">Esse é o tamanho do formulário, em pixels.</span><span class="sxs-lookup"><span data-stu-id="4f266-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="4f266-114">O script anterior cria um formulário que possui 243 pixels de largura por 230 pixels de altura.</span><span class="sxs-lookup"><span data-stu-id="4f266-114">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

-   <span data-ttu-id="4f266-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="4f266-115">**StartingPosition.**</span></span> <span data-ttu-id="4f266-116">Esta propriedade opcional é definida para **CenterScreen** no script precedente.</span><span class="sxs-lookup"><span data-stu-id="4f266-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="4f266-117">Se você não adicionar essa propriedade, o Windows seleciona um local quando o formulário aberto.</span><span class="sxs-lookup"><span data-stu-id="4f266-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="4f266-118">Ao configurar o **StartingPosition** para **CenterScreen**, você está exibindo automaticamente o formulário no meio da tela cada vez que ela é carregada.</span><span class="sxs-lookup"><span data-stu-id="4f266-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```
$form.Text = "Select a Date" 
$form.Size = New-Object Drawing.Size @(243,230) 
$form.StartPosition = "CenterScreen"
```

<span data-ttu-id="4f266-119">Em seguida, crie e adicione um controle de calendário ao seu formulário.</span><span class="sxs-lookup"><span data-stu-id="4f266-119">Next, create and then add a calendar control in your form.</span></span> <span data-ttu-id="4f266-120">Neste exemplo, o dia atual não é realçado ou circulado.</span><span class="sxs-lookup"><span data-stu-id="4f266-120">In this example, the current day is not highlighted or circled.</span></span> <span data-ttu-id="4f266-121">Os usuários podem selecionar somente um dia por vez no calendário.</span><span class="sxs-lookup"><span data-stu-id="4f266-121">Users can select only one day on the calendar at one time.</span></span>

```
$calendar = New-Object System.Windows.Forms.MonthCalendar 
$calendar.ShowTodayCircle = $False
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

<span data-ttu-id="4f266-122">Em seguida, crie um botão **OK** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="4f266-122">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="4f266-123">Especifique o tamanho e comportamento do botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="4f266-123">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="4f266-124">Neste exemplo, a posição do botão é de 165 pixels a partir da borda superior do formulário e 38 pixels a partir da borda esquerda.</span><span class="sxs-lookup"><span data-stu-id="4f266-124">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span> <span data-ttu-id="4f266-125">A altura do botão é de 23 pixels, enquanto seu comprimento é de 75 pixels.</span><span class="sxs-lookup"><span data-stu-id="4f266-125">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="4f266-126">O script usa tipos predefinidos de formulários do Windows para determinar os comportamentos do botão.</span><span class="sxs-lookup"><span data-stu-id="4f266-126">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="4f266-127">Crie o botão **Cancelar** da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="4f266-127">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="4f266-128">O botão **Cancelar** fica a 165 pixels da parte superior e 113 pixels da borda esquerda da janela.</span><span class="sxs-lookup"><span data-stu-id="4f266-128">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="4f266-129">Defina a propriedade **Topmost** como **$True** para forçar a janela a abrir por cima de outras janelas e caixas de diálogo abertas.</span><span class="sxs-lookup"><span data-stu-id="4f266-129">Set the **Topmost** property to **$True** to force the window to open atop other open windows and dialog boxes.</span></span>

```
$form.Topmost = $True
```

<span data-ttu-id="4f266-130">Adicione a seguinte linha de código para exibir o formulário do Windows.</span><span class="sxs-lookup"><span data-stu-id="4f266-130">Add the following line of code to display the form in Windows.</span></span>

```
$result = $form.ShowDialog()
```

<span data-ttu-id="4f266-131">Por fim, o código dentro do bloco **If** instrui o Windows sobre o que fazer com o formulário depois que os usuários selecionam um dia no calendário e clicam no botão **OK** ou pressionam a tecla **Enter**.</span><span class="sxs-lookup"><span data-stu-id="4f266-131">Finally, the code inside the **If** block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span> <span data-ttu-id="4f266-132">O Windows PowerShell exibe as datas selecionadas para os usuários.</span><span class="sxs-lookup"><span data-stu-id="4f266-132">Windows PowerShell displays the selected date to users.</span></span>

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="4f266-133">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="4f266-133">See Also</span></span>
- [<span data-ttu-id="4f266-134">Ei Scripting Guy: por que esses exemplos de GUI do PowerShell não funcionam?</span><span class="sxs-lookup"><span data-stu-id="4f266-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="4f266-135">GitHub: WinFormsExampleUpdates do Dave Wyatt</span><span class="sxs-lookup"><span data-stu-id="4f266-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="4f266-136">Windows PowerShell Tip of the Week: Creating a Graphical Date Picker</span><span class="sxs-lookup"><span data-stu-id="4f266-136">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](http://technet.microsoft.com/library/ff730942.aspx) (Dica da Semana do Windows PowerShell: criar um seletor de data gráfico)

