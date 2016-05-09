---
title: Caixas de listagem de seleção múltipla
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f74cd5d9-da57-4802-b614-0b194a7bc8f8
---
# Caixas de listagem de seleção múltipla
Use o Windows PowerShell 3.0 e versões posteriores para criar um controle de caixa de listagem de seleção múltipla em um formulário personalizado do Windows.

## Criar controles de caixa de listagem que permitem seleção múltipla
Copie e cole o seguinte no Windows PowerShell ISE e salve-o como um script do Windows PowerShell (.ps1).

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form 
$form.Text = "Data Entry Form"
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
$label.Text = "Please make a selection from the list below:"
$form.Controls.Add($label) 

$listBox = New-Object System.Windows.Forms.Listbox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 

$listBox.SelectionMode = "MultiExtended"

[void] $listBox.Items.Add("Item 1")
[void] $listBox.Items.Add("Item 2")
[void] $listBox.Items.Add("Item 3")
[void] $listBox.Items.Add("Item 4")
[void] $listBox.Items.Add("Item 5")

$listBox.Height = 70
$form.Controls.Add($listBox) 
$form.Topmost = $True

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

O script começa carregando duas classes do .NET Framework: **System.Drawing** e **System.Windows.Forms**. Inicie uma nova instância da classe do .NET Framework **System.Windows.Forms.Form**, que fornece um formulário em branco ou janela ao qual você pode começar a adicionar controles.

```
$form = New-Object System.Windows.Forms.Form
```

Depois de criar uma instância da classe Form, atribua valores a três propriedades dessa classe.

-   **Text.** Isso se torna o título da janela.

-   **Size.** Esse é o tamanho do formulário, em pixels. O script anterior cria um formulário que possui 300 pixels de largura por 200 pixels de altura.

-   **StartingPosition.** Esta propriedade opcional é definida para **CenterScreen** no script precedente. Se você não adicionar essa propriedade, o Windows seleciona um local quando o formulário aberto. Ao configurar o **StartingPosition** para **CenterScreen**, você está exibindo automaticamente o formulário no meio da tela cada vez que ela é carregada.

```
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

Em seguida, crie um botão **OK** para seu formulário. Especifique o tamanho e comportamento do botão **OK**. Neste exemplo, a posição do botão é de 120 pixels a partir da borda superior do formulário e 75 pixels a partir da borda esquerda. A altura do botão é de 23 pixels, enquanto seu comprimento é de 75 pixels. O script usa tipos predefinidos de formulários do Windows para determinar os comportamentos do botão.

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Crie o botão **Cancelar** da mesma maneira. O botão **Cancelar** fica a 120 pixels da parte superior e 150 pixels da borda esquerda da janela.

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Em seguida, forneça o texto de rótulo na janela que descreve as informações que você deseja que os usuários forneçam.

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please make a selection from the list below:"
$form.Controls.Add($label)
```

Adicione o controle (no caso, uma caixa de listagem) que permite que os usuários forneçam as informações descritas no texto do rótulo. Há muitos outros controles que você pode aplicar além de caixas de texto. Para ver mais controles, consulte [Namespace System.Windows.Forms](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) no MSDN.

```
$listBox = New-Object System.Windows.Forms.Listbox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20)
```

Veja como especificar que você deseja que os usuários selecionem múltiplos valores na lista.

```
$listBox.SelectionMode = "MultiExtended"
```

Na próxima seção, você deve especificar os valores que você deseja que a caixa de listagem mostre para os usuários.

```
[void] $listBox.Items.Add("Item 1")
[void] $listBox.Items.Add("Item 2")
[void] $listBox.Items.Add("Item 3")
[void] $listBox.Items.Add("Item 4")
[void] $listBox.Items.Add("Item 5")
```

Especifica a altura máxima do controle de caixa de listagem.

```
$listBox.Height = 70
```

Adicione o controle de caixa de listagem ao formulário e instrua o Windows a abrir o formulário sobre outras janelas e caixas de diálogo quando ela é aberta.

```
$form.Controls.Add($listBox) 
$form.Topmost = $True
```

Adicione a seguinte linha de código para exibir o formulário do Windows.

```
$result = $form.ShowDialog()
```

Por fim, o código dentro do bloco **If** instrui o Windows sobre o que fazer com o formulário depois que os usuários selecionam uma opção ou mais opções na caixa de listagem e clicam no botão **OK** ou pressionam a tecla **Enter**.

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## Consulte Também
[Hey Scripting Guy: por que esses exemplos de GUI do PowerShell não funcionam?](http://go.microsoft.com/fwlink/?LinkId=506644)
[GitHub: WinFormsExampleUpdates do Dave Wyatt](https://github.com/dlwyatt/WinFormsExampleUpdates)
[Dica da semana do Windows PowerShell: caixas de listagem de seleção múltipla e muito mais!](http://technet.microsoft.com/library/ff730950.aspx)



<!--HONumber=Apr16_HO1-->


