---
ms.date: 08/24/2018
keywords: powershell, cmdlet
title: Aprendendo os nomes do PowerShell
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: 6ed1f99513f00c174147876e1982c0d12869cacb
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320475"
---
# <a name="learning-powershell-names"></a>Aprendendo os nomes do PowerShell

Aprender os nomes de comandos e parâmetros exige um investimento considerável de tempo com a maioria das interfaces de linha de comando. O problema é que há alguns padrões. Memorização é a única maneira de aprender os comandos e parâmetros que você precisa usar regularmente.

Ao trabalhar com um novo comando ou parâmetro, nem sempre é possível usar o que você já conhece. Você precisa localizar e aprender um novo nome. Tradicionalmente, as interfaces de linha de comando começam com um pequeno conjunto de ferramentas e aumentam com adições incrementais. É fácil ver por que não há uma estrutura padrão.
Isso parece lógico para nomes de comando, já que cada comando é uma ferramenta separada. O PowerShell oferece uma maneira melhor de lidar com nomes de comando.

## <a name="learning-command-names-in-traditional-shells"></a>Aprender nomes de comando em shells tradicionais

A maioria dos comandos são criados para gerenciar os elementos do sistema operacional ou aplicativos, como serviços ou processos. Os comandos têm nomes que podem ou não se ajustar em uma família. Por exemplo, em sistemas Windows, você pode usar os comandos `net start` e `net stop` para iniciar e parar um serviço. **Sc.exe** é outra ferramenta de controle de serviço para Windows. Esse nome não se ajusta ao padrão de nomenclatura de comandos de serviço do **net.exe**. Para o gerenciamento de processo, o Windows tem o comando **tasklist.exe** para listar processos e o comando **taskkill.exe** para interromper processos.

Além disso, comandos têm especificações de parâmetro irregulares. Não é possível usar o comando `net start` para iniciar um serviço em um computador remoto. O comando **sc.exe** pode iniciar um serviço em um computador remoto. Mas, para especificar o computador remoto, você deve prefixar o nome com uma barra invertida dupla. Para iniciar o serviço de spooler em um computador remoto denominado DC01, digite `sc.exe \\DC01 start spooler`.
Para listar tarefas em execução no DC01, use o parâmetro **/S** e o nome do computador sem barras invertidas. Por exemplo, `tasklist /S DC01`.

> [!NOTE]
> Antes do PowerShell v6, `sc` era um alias para o cmdlet `Set-Content`. Para executar o comando **sc.exe**, você deve incluir a extensão de arquivo.

Os serviços e os processos são exemplos de elementos gerenciáveis em um computador com ciclos de vida bem-definidos. Você pode iniciar ou parar serviços ou processos, ou obter uma lista dos serviços ou processos em execução no momento. Apesar de haver distinções técnicas importantes entre elas, conceitualmente, as ações executadas em serviços e processos são as mesmas. Além disso, as escolhas que fazemos para personalizar uma ação especificando parâmetros também podem ser conceitualmente semelhantes.

O PowerShell explora essas semelhanças para reduzir o número de nomes distintos que você precisa conhecer para compreender e usar os cmdlets.

## <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>Os cmdlets usam nomes com verbo-substantivo para reduzir a memorização de comandos

O PowerShell usa um sistema de nomenclatura de "verbo-substantivo". Cada nome de cmdlet é formado por um verbo padrão hifenizado com um substantivo específico. Os verbos do PowerShell nem sempre são verbos em inglês, mas eles expressam ações específicas no PowerShell. Os substantivos são muito parecidos com substantivos em qualquer idioma. Eles descrevem tipos específicos de objetos que são importantes na administração do sistema. É fácil demonstrar como esses nomes em duas partes reduzem o esforço de aprendizagem examinando alguns exemplos.

O PowerShell tem um conjunto recomendado de verbos padrão. Os substantivos são menos restritos, mas sempre descrevem sobre o que o verbo atua. O PowerShell tem comandos como `Get-Process`, `Stop-Process`, `Get-Service` e `Stop-Service`.

Para este exemplo de dois substantivos e dois verbos, a consistência não simplifica muito o aprendizado. Estenda essa lista para um conjunto padronizado de 10 substantivos e 10 verbos. Agora, você precisa entender apenas 20 palavras.
Mas essas palavras podem ser combinadas para formar os 100 nomes de comando distintos.

É fácil de entender o que um comando do PowerShell faz lendo o nome dele. O comando para desligar um computador é `Stop-Computer`. O comando para listar todos os computadores em uma rede é `Get-Computer`. O comando para obter a data do sistema é `Get-Date`.

Você pode listar todos os comandos que incluem um determinado verbo com o parâmetro **Verb** para `Get-Command`. Por exemplo, para ver todos os cmdlets que usam o verbo `Get`, digite:

```
PS> Get-Command -Verb Get

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

Use o parâmetro **Noun** para ver uma família de comandos que afetam o mesmo tipo de objeto. Por exemplo, execute o seguinte comando para ver os comandos disponíveis para os serviços de gerenciamento:

```
PS> Get-Command -Noun Service

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str...
...
```

## <a name="cmdlets-use-standard-parameters"></a>Os cmdlets usam parâmetros padrão

Conforme observado anteriormente, comandos usados em interfaces de linha de comando tradicionais geralmente não têm nomes de parâmetro consistentes. Geralmente, os parâmetros são caracteres únicos ou palavras abreviadas fáceis de digitar, mas difíceis de compreender para os novos usuários.

Diferentemente de outras interfaces de linha de comando tradicionais, o PowerShell processa parâmetros diretamente e usa esse acesso direto aos parâmetros com as diretrizes para desenvolvedores a fim de padronizar os nomes dos parâmetros. Essa orientação incentiva, mas não garante, que cada cmdlet esteja de acordo com o padrão.

O PowerShell também padroniza o separador de parâmetro. Os nomes de parâmetro sempre têm um '-' acrescentado a eles com um comando do PowerShell. Considere o exemplo a seguir:

```powershell
Get-Command -Name Clear-Host
```

O nome do parâmetro é **Name**, mas ele é digitado como `-Name` quando usado na linha de comando como parâmetro.

Aqui estão algumas das características gerais dos nomes de parâmetro padrão e seus usos.

### <a name="the-help-parameter-"></a>O parâmetro de Ajuda (?)

Quando você especifica o parâmetro `-?` ou qualquer cmdlet, o PowerShell exibe a ajuda para o cmdlet.
O cmdlet não é executado.

### <a name="common-parameters"></a>Parâmetros comuns

O PowerShell tem vários *parâmetros comuns*. Esses parâmetros são controlados pelo mecanismo do PowerShell. Os parâmetros comuns sempre se comportam da mesma maneira. Os parâmetros comuns são **WhatIf**, **Confirm**, **Verbose**, **Debug**, **Warn**, **ErrorAction**, **ErrorVariable**, **OutVariable** e **OutBuffer**.

### <a name="recommended-parameter-names"></a>Nomes de parâmetros recomendados

Os principais cmdlets do PowerShell usam nomes padrão para parâmetros semelhantes. O uso desses nomes padrão não é imposto, mas há diretrizes explícitas para incentivar a padronização.

Por exemplo, o nome recomendado de um parâmetro que se refere a um computador é **ComputerName**, em vez de Server, Host, System, Node ou outras palavras alternativas comuns. Outros nomes de parâmetro importantes recomendados são **Force**, **Exclude**, **Include**, **PassThru**, **Path** e **CaseSensitive**.
