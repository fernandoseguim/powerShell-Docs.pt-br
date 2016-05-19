---
title: Outros objetos de script úteis
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
---
# Outros objetos de script úteis
  Os seguintes objetos fornecem funcionalidade adicional de script no ISE do Windows PowerShell. Eles não fazem parte da hierarquia **$psISE**.

## Objetos de scripts úteis

### $psUnsupportedConsoleApplications
 Existem algumas limitações sobre como o ISE do Windows PowerShell interage com os aplicativos do console. Um comando ou um script de automação que requer a intervenção do usuário pode não funcionar da maneira que funciona no console do Windows PowerShell. Você pode impedir que esses comandos ou scripts sejam executados no painel de comando ISE do Windows PowerShell. O objeto **$psUnsupportedConsoleApplications** mantém uma lista de tais comandos. Se você tentar executar os comandos nesta lista, receberá uma mensagem de que eles não tem suporte. O script a seguir adiciona uma entrada à lista.

```
# List the unsupported commands
psUnsupportedConsoleApplications
# Add a command to this list
psUnsupportedConsoleApplications.Add(“Mycommand”)
#Show the augmented list of commands
psUnsupportedConsoleApplications

```

### $psLocalHelp
 Esse é um objeto de dicionário que mantém um mapeamento contextual entre os tópicos da Ajuda e seus links associados no arquivo de ajuda local HTML compilado. Ele é usado para localizar a Ajuda local para determinado tópico. Você pode adicionar ou excluir tópicos desta lista. O exemplo de código a seguir mostra alguns exemplos de pares chave-valor contidos em **$psLocalHelp**.

```
# See the local help map
$psLocalHelp |Format-List

```

### Saída de exemplo

|||
|-|-|
|Chave: Add-Computer|Valor: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm|
|Chave: Add-Content|Valor: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm|

 O script a seguir adiciona uma entrada à lista.

```
$psLocalHelp.Add("get-myNoun","c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### $psOnlineHelp
 Este é um objeto de dicionário que mantém um mapeamento contextual entre títulos de tópicos dos tópicos de ajuda e suas URLs externas associadas. Ele é usado para localizar a ajuda para um tópico específico na Web. Você pode adicionar ou excluir tópicos desta lista.

```
$psOnlineHelp |format-list

```

### Saída de exemplo

|||
|-|-|
|Chave: Add-Computer|Valor: http://go.microsoft.com/fwlink/p/?LinkID=135194|
|Chave: Add-Content|Valor: http://go.microsoft.com/fwlink/p/?LinkID=113278|

 O script a seguir adiciona uma entrada à lista.

```
$psOnlineHelp.Add("get-myNoun","http://www.mydomain.com/MyNoun.html")
```

## Consulte Também
 [O modelo de objeto de script do ISE do Windows PowerShell](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  


<!--HONumber=May16_HO2-->


