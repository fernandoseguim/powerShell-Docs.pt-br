---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet
ms.date: 2016-12-12
title: "Outros objetos de script úteis"
ms.technology: powershell
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: a1e3ad310303fe02ee61bcd6d2681df6d91a4924
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="other-useful-scripting-objects"></a>Outros objetos de script úteis
  Os seguintes objetos fornecem funcionalidade adicional de script no ISE do Windows PowerShell. Eles não fazem parte da hierarquia **$psISE**.

## <a name="useful-scripting-objects"></a>Objetos de scripts úteis

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications
 Existem algumas limitações sobre como o ISE do Windows PowerShell interage com os aplicativos do console. Um comando ou um script de automação que requer a intervenção do usuário pode não funcionar da maneira que funciona no console do Windows PowerShell. Você pode impedir que esses comandos ou scripts sejam executados no painel de comando ISE do Windows PowerShell. O objeto **$psUnsupportedConsoleApplications** mantém uma lista de tais comandos. Se você tentar executar os comandos nesta lista, receberá uma mensagem de que eles não tem suporte. O script a seguir adiciona uma entrada à lista.

```
# List the unsupported commands
psUnsupportedConsoleApplications
# Add a command to this list
psUnsupportedConsoleApplications.Add(“Mycommand”)
#Show the augmented list of commands
psUnsupportedConsoleApplications

```

### <a name="pslocalhelp"></a>$psLocalHelp
 Esse é um objeto de dicionário que mantém um mapeamento contextual entre os tópicos da Ajuda e seus links associados no arquivo de ajuda local HTML compilado. Ele é usado para localizar a Ajuda local para determinado tópico. Você pode adicionar ou excluir tópicos desta lista. O exemplo de código a seguir mostra alguns exemplos de pares de chave-valor contidos em **$psLocalHelp**.

```
# See the local help map
$psLocalHelp | Format-List

```

### <a name="sample-output"></a>Saída de exemplo

|||
|-|-|
|Chave: Add-Computer|Valor: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm|
|Chave: Add-Content|Valor: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm|

 O script a seguir adiciona uma entrada à lista.

```
$psLocalHelp.Add("get-myNoun","c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp
 Este é um objeto de dicionário que mantém um mapeamento contextual entre títulos de tópicos dos tópicos de ajuda e suas URLs externas associadas. Ele é usado para localizar a ajuda para um tópico específico na Web. Você pode adicionar ou excluir tópicos desta lista.

```
$psOnlineHelp | Format-List

```

### <a name="sample-output"></a>Saída de exemplo

|||
|-|-|
|Chave: Add-Computer|Valor : http://go.microsoft.com/fwlink/p/?LinkID=135194|
|Chave: Add-Content|Valor: http://go.microsoft.com/fwlink/p/?LinkID=113278|

 O script a seguir adiciona uma entrada à lista.

```
$psOnlineHelp.Add("get-myNoun","http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Consulte Também
- [O modelo de objeto de script do ISE do Windows PowerShell](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
