---
title: "Criando um seletor de data gráfico"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: f359254900dce0ef0a28af3e16b8ef4095e85309

---

# Criando um seletor de data gráfico
Use o Windows PowerShell 3.0 e versões posteriores para criar um formulário com um controle gráfico do estilo calendário, que permite aos usuários selecionar um dia do mês.

## Criar um controle gráfico de seletor de data
Copie e cole o seguinte no Windows PowerShell ISE e salve-o como um script do Windows PowerShell (.ps1).

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

O script começa carregando duas classes do .NET Framework: **System.Drawing** e **System.Windows.Forms**. Inicie uma nova instância da classe do .NET Framework **Windows.Forms.Form**, que fornece um formulário em branco ou ao qual você pode começar a adicionar controles de janela.

```
$form = New-Object Windows.Forms.Form
```

Depois de criar uma instância da classe Form, atribua valores a três propriedades dessa classe.

-   **Text.** Isso se torna o título da janela.

-   **Size.** Esse é o tamanho do formulário, em pixels. O script anterior cria um formulário que possui 243 pixels de largura por 230 pixels de altura.

-   **StartingPosition.** Esta propriedade opcional é definida para **CenterScreen** no script precedente. Se você não adicionar essa propriedade, o Windows seleciona um local quando o formulário aberto. Ao configurar o **StartingPosition** para **CenterScreen**, você está exibindo automaticamente o formulário no meio da tela cada vez que ela é carregada.

```
$form.Text = "Select a Date" 
$form.Size = New-Object Drawing.Size @(243,230) 
$form.StartPosition = "CenterScreen"
```

Em seguida, crie e adicione um controle de calendário ao seu formulário. Neste exemplo, o dia atual não é realçado ou circulado. Os usuários podem selecionar somente um dia por vez no calendário.

```
$calendar = New-Object System.Windows.Forms.MonthCalendar 
$calendar.ShowTodayCircle = $False
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

Em seguida, crie um botão **OK** para seu formulário. Especifique o tamanho e comportamento do botão **OK**. Neste exemplo, a posição do botão é de 165 pixels a partir da borda superior do formulário e 38 pixels a partir da borda esquerda. A altura do botão é de 23 pixels, enquanto seu comprimento é de 75 pixels. O script usa tipos predefinidos de formulários do Windows para determinar os comportamentos do botão.

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Crie o botão **Cancelar** da mesma maneira. O botão **Cancelar** fica a 165 pixels da parte superior e 113 pixels da borda esquerda da janela.

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Defina a propriedade **Topmost** como **$True** para forçar a janela a abrir por cima de outras janelas e caixas de diálogo abertas.

```
$form.Topmost = $True
```

Adicione a seguinte linha de código para exibir o formulário do Windows.

```
$result = $form.ShowDialog()
```

Por fim, o código dentro do bloco **If** instrui o Windows sobre o que fazer com o formulário depois que os usuários selecionam um dia no calendário e clicam no botão **OK** ou pressionam a tecla **Enter**. O Windows PowerShell exibe as datas selecionadas para os usuários.

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## Consulte Também
[Hey Scripting Guy: Why don’t these PowerShell GUI examples work? (Por que esses exemplos de GUI do PowerShell não funcionam?)](http://go.microsoft.com/fwlink/?LinkId=506644)
[GitHub: Dave Wyatt's WinFormsExampleUpdates (As atualizações de exemplos de WinForms de Dave Wyatt)](https://github.com/dlwyatt/WinFormsExampleUpdates)
[Windows PowerShell Tip of the Week: Creating a Graphical Date Picker (Dica da semana do Windows PowerShell: criando um seletor de data gráfico)](http://technet.microsoft.com/library/ff730942.aspx)




<!--HONumber=Jun16_HO4-->


