---
title: Criando uma caixa de entrada personalizada
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 0b12e56c-299f-40ee-afbf-d30d23ed2565
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 628062cfadcadcec3311dcb8bfdd6bd3b9a9e567

---

# Criando uma caixa de entrada personalizada
Crie o script de uma caixa de entrada gráfica personalizada usando recursos de criação de formulário do Microsoft .NET Framework no Windows PowerShell 3.0 e versões posteriores.

## Criar uma caixa de entrada gráfica personalizada
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
$label.Text = "Please enter the information in the space below:"
$form.Controls.Add($label) 

$textBox = New-Object System.Windows.Forms.TextBox 
$textBox.Location = New-Object System.Drawing.Point(10,40) 
$textBox.Size = New-Object System.Drawing.Size(260,20) 
$form.Controls.Add($textBox) 

$form.Topmost = $True

$form.Add_Shown({$textBox.Select()})
$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
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
$OKButton.Location = New-Object System.Drawing.Point(75,120)
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
$label.Text = "Please enter the information in the space below:"
$form.Controls.Add($label)
```

Adicione o controle (no caso, uma caixa de texto) que permite que os usuários forneçam as informações descritas no texto do rótulo. Há muitos outros controles que você pode aplicar além de caixas de texto. Para ver mais controles, consulte [Namespace System.Windows.Forms](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) no MSDN.

```
$textBox = New-Object System.Windows.Forms.TextBox 
$textBox.Location = New-Object System.Drawing.Point(10,40) 
$textBox.Size = New-Object System.Drawing.Size(260,20) 
$form.Controls.Add($textBox)
```

Defina a propriedade **Topmost** como **$True** para forçar a janela a abrir por cima de outras janelas e caixas de diálogo abertas.

```
$form.Topmost = $True
```

Em seguida, adicione esta linha de código para ativar o formulário e defina o foco para a caixa de texto que você criou.

```
$form.Add_Shown({$textBox.Select()})
```

Adicione a seguinte linha de código para exibir o formulário do Windows.

```
$result = $form.ShowDialog()
```

Por fim, o código dentro do bloco **If** instrui o Windows sobre o que fazer com o formulário depois que os usuários fornecem texto na caixa de texto e clicam no botão **OK** ou pressionam a tecla **Enter**.

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## Consulte Também
[Hey Scripting Guy: Why don’t these PowerShell GUI examples work? (Ei, você responsável pelo script: por que esses exemplos de GUI do PowerShell não funcionam?)](http://go.microsoft.com/fwlink/?LinkId=506644)
[GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
[Windows PowerShell Tip of the Week: Creating a Custom Input Box (Dica da semana do Windows PowerShell: criando uma caixa de entrada personalizada)](http://technet.microsoft.com/library/ff730941.aspx)




<!--HONumber=Jun16_HO4-->


