---
ms.date: 08/27/2018
keywords: powershell, cmdlet
title: Usando nomes familiares de comando
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: b61d647d882d4b2f7ea423a48319e3c104ce96c7
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795667"
---
# <a name="using-familiar-command-names"></a>Usando nomes de comando familiares

O PowerShell dá suporte a aliases para se referir aos comandos por nomes alternativos. Usar alias permite que usuários com experiência em outros shells utilizem nomes de comando comuns que já conhecem para operações semelhantes no PowerShell.

O alias associa um novo nome a outro comando. Por exemplo, o PowerShell tem uma função interna denominada `Clear-Host` que limpa a janela de saída. Você pode digitar o alias `cls` ou `clear` em um prompt de comando. O PowerShell interpreta esses aliases e executa a função `Clear-Host`.

Esse recurso ajuda os usuários a aprender sobre o PowerShell. Primeiro, a maioria dos usuários de **cmd.exe** e do Unix conhece um grande repertório de comandos por nome. Talvez os equivalentes do PowerShell não produzam resultados idênticos. No entanto, os resultados são bem parecidos, e os usuários podem fazer o trabalho sem conhecer o nome de comando do PowerShell. "Memória dos dedos" é outra grande fonte de frustração ao aprender um novo shell de comando. Se você tiver usado o **cmd.exe** durante anos, talvez digite de forma reflexiva o comando `cls` para limpar a tela. Sem o alias para `Clear-Host`, você receberá uma mensagem de erro e não saberá o que fazer para limpar a saída.

A lista a seguir mostra alguns comandos comuns do **cmd.exe** e Unix que podem ser usados no PowerShell:

|||||
|-|-|-|-|
|cat|dir|montagem|rm|
|cd|echo|move|rmdir|
|chdir|erase|popd|sleep|
|clear|h|ps|sort|
|cls|history|pushd|tee|
|copy|kill|pwd|tipo|
|del|lp|r|write|
|diff|ls|ren||

O cmdlet `Get-Alias` mostra o nome real do comando nativo do PowerShell associado a um alias.

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a>Interpretar aliases padrão

Os aliases descritos anteriormente foram criados de maneira a terem compatibilidade de nomenclatura com outros shells de comando.
A maioria dos aliases criados no PowerShell é projetada para manter a brevidade. Os nomes mais curtos são mais fáceis de digitar, mas são difíceis de ler se você não souber a que se referem.

Os aliases do PowerShell tentam equilibrar a clareza e a brevidade. O PowerShell usa um conjunto padrão de aliases para substantivos e verbos comum.

Exemplo de abreviações:

| Substantivo ou verbo | Abreviação |
|--------------|--------------|
| Get          | g            |
| Set          | s            |
| Item         | i            |
| Local     | l            |
| Comando      | cm           |
| Alias        | al           |

Esses aliases são compreensíveis quando você conhece os nomes abreviados.

| Nome do cmdlet    | Alias |
|----------------|-------|
| `Get-Item`     | gi    |
| `Set-Item`     | si    |
| `Get-Location` | gl    |
| `Set-Location` | sl    |
| `Get-Command`  | gcm   |
| `Get-Alias`    | gal   |

Quando você estiver familiarizado com o alias do PowerShell, será fácil imaginar que o alias **sal** se refere a `Set-Alias`.

## <a name="creating-new-aliases"></a>Criar um novo alias

Você pode criar seus próprios aliases usando o cmdlet `Set-Alias`. Por exemplo, as instruções a seguir criam os aliases de cmdlet padrão discutidos anteriormente:

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

Internamente, o PowerShell usa comandos parecidos com esses durante a inicialização, mas esses aliases não são mutáveis.
Se você tentar executar um desses comandos, receberá um erro explicando que o alias não pode ser modificado. Por exemplo:

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```
