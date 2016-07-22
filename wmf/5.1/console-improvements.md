---
title: Melhorias do Console no WMF 5.1 (Preview)
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 221b8095c15a810c032bd93aafe8ec886af233d9

---

# Melhorias do Console no WMF 5.1 (Preview)#

## Melhorias do console do PowerShell

As seguintes alterações foram feitas ao powershell.exe no WMF 5.1 para melhorar a experiência do console:

###Suporte a VT100

O Windows 10 adicionou suporte para [sequências de escape VT100](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).
PowerShell ignorará determinadas sequências de escape de formatação do VT100 ao calcular larguras da tabela.

O PowerShell também adicionou uma nova API que pode ser usada no código de formatação para determinar se há suporte para VT100. Por exemplo:

```
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```
Aqui está um [exemplo](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) completo que pode ser usado para realçar correspondências de Select-String.
Salve o exemplo em um arquivo chamado `MatchInfo.format.ps1xml`, então, para usá-lo em seu perfil ou em outro local, execute `Update-FormatData -Prepend MatchInfo.format.ps1xml`.

Observe que as sequências de escape do VT100 têm suporte apenas a partir da atualização de Aniversário do Windows 10; elas não têm suporte em sistemas anteriores.   

### Suporte ao modo vi em PSReadline

[PSReadline](https://github.com/lzybkr/PSReadLine) adiciona suporte para o modo vi. Para usar o modo vi, execute `Set-PSReadline -EditMode vi`.

### Stdin redirecionado c/entrada interativa 

Em versões anteriores, iniciar o PowerShell com `powershell -File -` era necessário quando stdin era redirecionado e você queria inserir comandos interativamente.

Com 5.1 WMF, essa opção difícil de descobrir não é mais necessária, e você pode iniciar o PowerShell sem nenhuma opção, por exemplo, `powershell`.

Observe que o PSReadline atualmente não dá suporte a stdin redirecionado, e a experiência de edição de linha de comando interna com stdin redirecionado é extremamente limitada, por exemplo, as teclas de seta não funcionam.  Uma versão futura do PSReadline deve resolver esse problema.   



<!--HONumber=Jul16_HO3-->


