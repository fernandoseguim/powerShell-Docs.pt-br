---
title: Obtendo informações sobre comandos
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
---
# Obtendo informações sobre comandos
O cmdlet **Get-Command** do Windows PowerShell obtém todos os comandos que estão disponíveis na sessão atual. Quando você digita **Get-Command** em um prompt do Windows PowerShell, você verá uma saída semelhante à seguinte:

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

Esta saída se parece muito como a saída de Ajuda do Cmd.exe: um resumo tabular de comandos internos. No trecho do resultado do comando **Get-Command** mostrado acima, todos os comandos mostrados tem um CommandType do Cmdlet. Um cmdlet é o tipo de comando intrínseco do Windows PowerShell, um tipo que corresponde aproximadamente aos comandos **dir** e **cd** de Cmd.exe e shells integrados do UNIX como BASH.

Na saída do comando **Get-Command**, todas as definições terminam com reticências (...) para indicar que o PowerShell não consegue exibir todo o conteúdo no espaço disponível. Quando o Windows PowerShell exibe a saída, ele formata o resultado como texto e o organiza para ajustar os dados corretamente na janela. Falaremos sobre isso mais tarde na seção sobre formatadores.

O cmdlet **Get-Command** tem um parâmetro **Syntax** que obtém a sintaxe de cada cmdlet. Para obter a sintaxe do cmdlet Get-Help, use o seguinte comando:

**Get-Command Get-Help -Syntax**

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### Exibindo tipos de comando disponíveis
O comando **Get-Command** não lista todos os comandos disponíveis no Windows PowerShell. Em vez disso, o comando **Get-Command** lista somente os cmdlets da sessão atual. Na verdade, o Windows PowerShell oferece suporte a vários outros tipos de comandos. Aliases, funções e scripts também são comandos do Windows PowerShell, embora eles não sejam discutidos em detalhes no Guia do Usuário do Windows PowerShell. Arquivos externos executáveis ou que possuem um manipulador do tipo de arquivo registrado também são classificados como comandos.

Para obter todos os comandos na sessão, digite:

```
Get-Command *
```

Como essa lista inclui arquivos externos em seu caminho de pesquisa, ela pode conter milhares de itens. É mais útil examinar um conjunto reduzido de comandos.

Para obter comandos nativos de outros tipos, use o parâmetro **CommandType** do cmdlet **Get-Command**.

> [!NOTE]
> O asterisco (*) é usado para correspondência de curingas nos argumentos de comando do Windows PowerShell. O * corresponde a "um ou mais caracteres quaisquer". Você pode digitar **Get-Command a&#42;** para encontrar todos os comandos que começam com a letra "a". Diferentemente da correspondência de curingas no Cmd.exe, curingas do Windows PowerShell também serão compatíveis com um ponto.

Para obter os aliases de comando, que são os apelidos atribuídos a comandos, digite:

```
Get-Command -CommandType Alias
```

Para obter as funções na sessão atual, digite:

```
Get-Command -CommandType Function
```

Para exibir os scripts no caminho de pesquisa do Windows PowerShell, digite:

```
Get-Command -CommandType Script
```



<!--HONumber=Apr16_HO1-->


