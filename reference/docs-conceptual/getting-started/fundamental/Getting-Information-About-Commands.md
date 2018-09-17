---
ms.date: 08/27/2018
keywords: powershell, cmdlet
title: Obtendo informações sobre comandos
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 7af83e3a0e776d96e580b442430357b4ea063a72
ms.sourcegitcommit: c170a1608d20d3c925d79c35fa208f650d014146
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43353163"
---
# <a name="getting-information-about-commands"></a>Obtendo informações sobre comandos

O `Get-Command` do PowerShell exibe os comandos disponíveis na sessão atual.
Ao executar o cmdlet `Get-Command`, você verá algo semelhante à seguinte saída:

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

Esta saída se parece muito como a saída de Ajuda do **cmd.exe**: um resumo tabular de comandos internos. No trecho do resultado do comando `Get-Command` mostrado acima, todos os comandos mostrados têm um CommandType de Cmdlet. Um cmdlet é o tipo de comando intrínseco do PowerShell. Este tipo corresponde aproximadamente a comandos como `dir` e `cd` no **cmd.exe** ou aos comandos internos de shells de Unix, como bash.

O cmdlet `Get-Command` tem um parâmetro **Syntax** que retorna a sintaxe de cada cmdlet. O exemplo a seguir mostra como obter a sintaxe do cmdlet `Get-Help`:

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a>Exibir o comando disponível por tipo

O comando `Get-Command` lista somente os cmdlets na sessão atual. Na verdade, o PowerShell dá suporte a vários outros tipos de comandos:

- Aliases
- Funções
- Scripts

Arquivos externos executáveis, ou arquivos que possuem um manipulador de tipo de arquivo registrado, também são classificados como comandos.

Para obter todos os comandos na sessão, digite:

```powershell
Get-Command *
```

Essa lista inclui comandos externos em seu caminho de pesquisa, portanto pode conter milhares de itens.
É mais útil examinar um conjunto reduzido de comandos.

> [!NOTE]
> O asterisco (\*) é usado para correspondência de curingas nos argumentos de comando do PowerShell. O \* corresponde a “um ou mais caracteres quaisquer”. Você pode digitar `Get-Command a*` para encontrar todos os comandos que começam com a letra "a". Diferentemente da correspondência de curingas no **cmd.exe**, curingas do PowerShell também serão compatíveis com um ponto.

Use o parâmetro **CommandType** de `Get-Command` para obter comandos nativos de outros tipos.
.

Para obter os aliases de comando, que são os apelidos atribuídos a comandos, digite:

```powershell
Get-Command -CommandType Alias
```

Para obter as funções na sessão atual, digite:

```powershell
Get-Command -CommandType Function
```

Para exibir os scripts no caminho de pesquisa do PowerShell, digite:

```powershell
Get-Command -CommandType Script
```