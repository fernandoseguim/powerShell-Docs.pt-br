---
title: Como escrever um módulo de Script do PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: e8b7151538235cdf7183b78aa8df7e596d6bcfd9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859002"
---
# <a name="how-to-write-a-powershell-script-module"></a>Como escrever um módulo de script do Windows PowerShell

Um módulo de script é, essencialmente, qualquer script do PowerShell válido salvo em uma extensão. psm1. Essa extensão permite que o mecanismo do PowerShell usar um número de regras e cmdlets em seu arquivo. A maioria desses recursos está lá para ajudá-lo a instalar o código em outros sistemas, bem como gerenciar o escopo. Você também pode usar um arquivo de manifesto de módulo, que pode descrever instalações ainda mais complexas e soluções.

## <a name="writing-a-powershell-script-module"></a>Escrevendo um módulo de Script do PowerShell

Você pode criar um módulo de script salvando um script do PowerShell válido para um arquivo. psm1, e, em seguida, salvar esse arquivo em um diretório localizado onde o PowerShell pode encontrá-lo. Nessa pasta, que você também pode colocar os recursos que necessários para executar o script, bem como um arquivo de manifesto que descreve PowerShell funcionamento do seu módulo.

#### <a name="to-create-a-basic-powershell-module"></a>Para criar um módulo do PowerShell básico

1. Executar um script PowerShell existente e salve o script com uma extensão. psm1.

   Salvar um script com o. psm1 extensão significa que você pode usar os cmdlets do módulo, como [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), nele. Esses cmdlets existem principalmente para que você pode facilmente importar e exportar seu código em sistemas de outros usuários. (A solução alternativa seria carregar seu código em outros sistemas e, em seguida, a origem do ponto-la na memória ativa, o que não é uma solução particularmente escalonável.) Para obter mais informações, consulte o **Cmdlets do módulo e as variáveis** seção [módulos do Windows PowerShell](./understanding-a-windows-powershell-module.md) Observe que, por padrão, todas as funções em seu script será acessíveis a usuários que importar seu. psm1 arquivo, mas as propriedades não funcionará.

   Um exemplo de script do PowerShell, o direito de Show-Calendar, está disponível no final deste tópico.

   ```powershell
   function Show-Calendar {
   param(
       [DateTime] $start = [DateTime]::Today,
       [DateTime] $end = $start,
       $firstDayOfWeek,
       [int[]] $highlightDay,
       [string[]] $highlightDate = [DateTime]::Today.ToString()
       )

       #actual code for the function goes here see the end of the topic for the complete code sample
   }
   ```

2. Se você quiser controlar o acesso de usuário a determinadas funções ou propriedades, chame [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) no final do seu script.

   O exemplo de código na parte inferior da página tem apenas uma função, que deve ser exposta por padrão. No entanto, é recomendável que você chama explicitamente quais funções você deseja expor, conforme descrito no código a seguir:

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   Você também pode restringir o que é importado usando um manifesto de módulo. Para obter mais informações, consulte [importação de um módulo do PowerShell](./importing-a-powershell-module.md) e [como escrever um manifesto de módulo do PowerShell](./how-to-write-a-powershell-module-manifest.md).

3. Se você tiver os módulos que seu próprio módulo precisa ter carregado, você pode usá-los com uma chamada para `Import-Module`, na parte superior do seu próprio módulo.

   `Import-Module` é um cmdlet que importa um módulo em um sistema de destino. Como tal, ele também é usado em um momento posterior no procedimento para instalar seu próprio módulo também. O código de exemplo na parte inferior desta página não usa quaisquer módulos de importação. Se tivesse, no entanto, eles são listados na parte superior do arquivo, conforme descrito no código a seguir:

   ```powershell
   Import-Module GenericModule
   ```

4. Se você deseja descrever seu módulo para o sistema de Ajuda do PowerShell, você pode fazer isso com os comentários de ajuda padrão dentro do arquivo, ou com um arquivo de ajuda adicional.

   O exemplo de código na parte inferior deste tópico inclui as informações da Ajuda nos comentários. Se preferir, você também pode escrever arquivos expandidos de XML que contêm o conteúdo de ajuda adicional. Para obter mais informações, consulte [Ajuda do escrita para o Windows PowerShell módulos](./writing-help-for-windows-powershell-modules.md).

5. Se você tiver outros módulos, arquivos XML ou outro conteúdo que você deseja empacotar com o módulo, você pode fazer isso com um manifesto de módulo.

   Um manifesto de módulo é um arquivo que contém os nomes de outros módulos, layouts de diretório, os números de controle de versão, dados de autor e outras partes de informação. PowerShell usa o arquivo de manifesto de módulo para organizar e implantar sua solução. No entanto, devido à natureza relativamente simple neste exemplo, um arquivo de manifesto não foi necessária. Para obter mais informações, consulte [manifestos de módulo](./how-to-write-a-powershell-module-manifest.md).

6. Para instalar e executar seu módulo, salvar o módulo em um dos caminhos do PowerShell apropriados e fazer uma chamada para `Import-Module`.

   Os caminhos onde você pode instalar o módulo estão localizados no `$env:PSModulePath` variável global. Por exemplo, um caminho comum para salvar um módulo em um sistema seria `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`. Certifique-se de criar uma pasta para o seu módulo existir, mesmo se ele é apenas um arquivo. psm1 único. Se você não salvar seu módulo para um desses caminhos, você teria que passar no local do seu módulo na chamada para `Import-Module`. (Caso contrário, PowerShell não seria capaz de encontrá-lo.) Começando com o PowerShell 3.0, se você tiver colocado o seu módulo em um dos caminhos de módulo do PowerShell, você não precisará explicitamente importá-lo: basta ter um usuário chama sua função e carregará automaticamente. Para obter mais informações sobre o caminho do módulo, consulte [importação de um módulo do PowerShell](./importing-a-powershell-module.md) e [variável de ambiente PSModulePath](./modifying-the-psmodulepath-installation-path.md).

7. Para remover um módulo de serviço do Active Directory, faça uma chamada para [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).

Observe que [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) remove o módulo de memória ativa - ele não exclui-lo de onde você salvou os arquivos de módulo.

### <a name="show-calendar-code-example"></a>Exemplo de código show-Calendar

O exemplo a seguir é um módulo de script simples que contém uma única função denominada Show-Calendar. Esta função exibe uma representação visual de um calendário. Além disso, o exemplo contém as cadeias de caracteres de Ajuda do PowerShell para a Sinopse, descrição, valores de parâmetro e exemplo. Observe que a última linha do código indica que a função Show-Calendar será exportada como um membro de módulo quando o módulo é importado.

```powershell
<#
 .Synopsis
  Displays a visual representation of a calendar.

 .Description
  Displays a visual representation of a calendar. This function supports multiple months
  and lets you highlight specific date ranges or days.

 .Parameter Start
  The first month to display.

 .Parameter End
  The last month to display.

 .Parameter FirstDayOfWeek
  The day of the month on which the week begins.

 .Parameter HighlightDay
  Specific days (numbered) to highlight. Used for date ranges like (25..31).
  Date ranges are specified by the Windows PowerShell range syntax. These dates are
  enclosed in square brackets.

 .Parameter HighlightDate
  Specific days (named) to highlight. These dates are surrounded by asterisks.

 .Example
   # Show a default display of this month.
   Show-Calendar

 .Example
   # Display a date range.
   Show-Calendar -Start "March, 2010" -End "May, 2010"

 .Example
   # Highlight a range of days.
   Show-Calendar -HighlightDay (1..10 + 22) -HighlightDate "December 25, 2008"
#>
function Show-Calendar {
param(
    [DateTime] $start = [DateTime]::Today,
    [DateTime] $end = $start,
    $firstDayOfWeek,
    [int[]] $highlightDay,
    [string[]] $highlightDate = [DateTime]::Today.ToString()
    )

## Determine the first day of the start and end months.
$start = New-Object DateTime $start.Year,$start.Month,1
$end = New-Object DateTime $end.Year,$end.Month,1

## Convert the highlighted dates into real dates.
[DateTime[]] $highlightDate = [DateTime[]] $highlightDate

## Retrieve the DateTimeFormat information so that the
## calendar can be manipulated.
$dateTimeFormat  = (Get-Culture).DateTimeFormat
if($firstDayOfWeek)
{
    $dateTimeFormat.FirstDayOfWeek = $firstDayOfWeek
}

$currentDay = $start

## Process the requested months.
while($start -le $end)
{
    ## Return to an earlier point in the function if the first day of the month
    ## is in the middle of the week.
    while($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek)
    {
        $currentDay = $currentDay.AddDays(-1)
    }

    ## Prepare to store information about this date range.
    $currentWeek = New-Object PsObject
    $dayNames = @()
    $weeks = @()

    ## Continue processing dates until the function reaches the end of the month.
    ## The function continues until the week is completed with
    ## days from the next month.
    while(($currentDay -lt $start.AddMonths(1)) -or
        ($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek))
    {
        ## Determine the day names to use to label the columns.
        $dayName = "{0:ddd}" -f $currentDay
        if($dayNames -notcontains $dayName)
        {
            $dayNames += $dayName
        }

        ## Pad the day number for display, highlighting if necessary.
        $displayDay = " {0,2} " -f $currentDay.Day

        ## Determine whether to highlight a specific date.
        if($highlightDate)
        {
            $compareDate = New-Object DateTime $currentDay.Year,
                $currentDay.Month,$currentDay.Day
            if($highlightDate -contains $compareDate)
            {
                $displayDay = "*" + ("{0,2}" -f $currentDay.Day) + "*"
            }
        }

        ## Otherwise, highlight as part of a date range.
        if($highlightDay -and ($highlightDay[0] -eq $currentDay.Day))
        {
            $displayDay = "[" + ("{0,2}" -f $currentDay.Day) + "]"
            $null,$highlightDay = $highlightDay
        }

        ## Add the day of the week and the day of the month as note properties.
        $currentWeek | Add-Member NoteProperty $dayName $displayDay

        ## Move to the next day of the month.
        $currentDay = $currentDay.AddDays(1)

        ## If the function reaches the next week, store the current week
        ## in the week list and continue.
        if($currentDay.DayOfWeek -eq $dateTimeFormat.FirstDayOfWeek)
        {
            $weeks += $currentWeek
            $currentWeek = New-Object PsObject
        }
    }

    ## Format the weeks as a table.
    $calendar = $weeks | Format-Table $dayNames -AutoSize | Out-String

    ## Add a centered header.
    $width = ($calendar.Split("'n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " 'n" + $padding + $header + "'n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
