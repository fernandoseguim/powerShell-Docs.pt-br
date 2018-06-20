---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Outros objetos de script úteis
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 0e87e9919199e011ab5abec5b07dccc8494ad64a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30949818"
---
# <a name="other-useful-scripting-objects"></a>Outros objetos de script úteis

Os seguintes objetos fornecem funcionalidade adicional de script no ISE do Windows PowerShell. Eles não fazem parte da hierarquia **$psISE**.

## <a name="useful-scripting-objects"></a>Objetos de scripts úteis

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications

Existem algumas limitações sobre como o ISE do Windows PowerShell interage com os aplicativos do console. Um comando ou um script de automação que requer a intervenção do usuário pode não funcionar da maneira que funciona no console do Windows PowerShell. Você pode impedir que esses comandos ou scripts sejam executados no painel de comando ISE do Windows PowerShell. O objeto **$psUnsupportedConsoleApplications** mantém uma lista de tais comandos. Se você tentar executar os comandos nesta lista, receberá uma mensagem de que eles não tem suporte. O script a seguir adiciona uma entrada à lista.

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a>$psLocalHelp

Esse é um objeto de dicionário que mantém um mapeamento contextual entre os tópicos da Ajuda e seus links associados no arquivo de ajuda local HTML compilado. Ele é usado para localizar a Ajuda local para determinado tópico. Você pode adicionar ou excluir tópicos desta lista. O exemplo de código a seguir mostra alguns exemplos de pares de chave-valor contidos em **$psLocalHelp**.

```powershell
# See the local help map
$psLocalHelp | Format-List
```

### <a name="sample-output"></a>Saída de exemplo

|||
|-|-|
|Chave: Add-Computer|Valor: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm|
|Chave: Add-Content|Valor: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm|

O script a seguir adiciona uma entrada à lista.

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp

Este é um objeto de dicionário que mantém um mapeamento contextual entre títulos de tópicos dos tópicos de ajuda e suas URLs externas associadas. Ele é usado para localizar a ajuda para um tópico específico na Web. Você pode adicionar ou excluir tópicos desta lista.

```powershell
$psOnlineHelp | Format-List
```

### <a name="sample-output"></a>Saída de exemplo

|||
|-|-|
|Chave: Add-Computer|Valor: http://go.microsoft.com/fwlink/p/?LinkID=135194|
|Chave: Add-Content|Valor: http://go.microsoft.com/fwlink/p/?LinkID=113278|

 O script a seguir adiciona uma entrada à lista.

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Consulte Também

- [Objetivo do modelo de objeto de script do ISE do Windows PowerShell](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)