---
title: Aprendendo a usar nomes do Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
---
# Aprendendo a usar nomes do Windows PowerShell
Aprender os nomes de comandos e parâmetros é um investimento de tempo significativo com a maioria das interfaces de linha de comando. O problema é que há pouquíssimos padrões, portanto, a única maneira aprender é memorizar cada comando e cada parâmetro que você precisa usar regularmente.

Quando você trabalha com um novo comando ou o parâmetro, geralmente não é possível usar o que você já sabe; é necessário encontrar e aprender um novo nome. Se você observar como as interfaces aumentam de um pequeno conjunto de ferramentas com adições incrementais de funcionalidade, será fácil ver por que a estrutura é diferente do padrão. Especialmente com nomes de comando, isso pode parecer lógico porque cada comando é uma ferramenta separada, mas há uma maneira melhor de lidar com eles.

A maioria dos comandos são criados para gerenciar os elementos do sistema operacional ou aplicativos, como serviços ou processos. Os comandos têm uma variedade de nomes que podem ou não caber em uma família. Por exemplo, em sistemas Windows, você pode usar os comandos **net start** e **net stop** para iniciar e parar um serviço. Há outra ferramenta de controle de serviço mais generalizada para Windows que tem um nome completamente diferente, **sc**, que não se ajusta ao padrão de nomenclatura para os comandos de serviço **net**. Para o gerenciamento de processo, o Windows tem o comando **tasklist** para listar processos e **taskkill** para interromper processos.

Comandos que usam parâmetros têm especificações de parâmetro irregulares. Não é possível usar o comando **net start** para iniciar um serviço em um computador remoto. O comando **sc** iniciará um serviço em um computador remoto, mas para especificá-lo, você deve prefixar o nome com uma barra invertida dupla. Por exemplo, para iniciar o serviço de spooler em um computador remoto denominado DC01, você digitaria **sc \\DC01 start spooler**. Para listar as tarefas em execução no DC01, você precisa usar o parâmetro **/S** (para o "sistema") e fornecer o nome DC01 sem barras invertidas, desta forma: **tasklist /S DC01**.

Embora existam distinções técnicas importantes entre um serviço e um processo, ambos são exemplos de elementos gerenciáveis em um computador com um ciclo de vida bem definido. Você pode deseja iniciar ou parar um serviço ou processo, ou então obter uma lista de todos os serviços ou processos em execução no momento. Em outras palavras, embora um serviço e um processo sejam coisas diferentes, as ações que executamos em um serviço ou um processo são geralmente conceitualmente as mesmas. Além disso, as escolhas que podemos fazer para personalizar uma ação especificando parâmetros de opções também podem ser conceitualmente semelhantes.

O Windows PowerShell explora essas semelhanças para reduzir o número de nomes distintos que você precisa conhecer para compreender e usar os cmdlets.

### Cmdlets usam nomes com Verbo-Substantivo para reduzir a memorização de comandos
O Windows PowerShell usa um sistema de nomenclatura de “verbo-substantivo”, no qual cada nome de cmdlet consiste em um verbo padrão hifenizado com um substantivo específico. Os verbos do Windows PowerShell nem sempre são verbos em inglês, mas eles expressam ações específicas no Windows PowerShell. Os substantivos são muito parecido com os substantivos de qualquer idioma e descrevem tipos específicos de objetos que são importantes na administração do sistema. É fácil demonstrar como esses nomes em duas partes reduzem o esforço de aprendizagem examinando alguns exemplos de verbos e substantivos.

Substantivos são menos restritos, mas sempre devem descrever sobre o que um comando atua. O Windows PowerShell tem comandos como **Get-Process (Obter-Processo)**, **Stop-Process (Parar-Processo)**, **Get-Service (Obter-Serviço)** e **Stop-Service (Parar-Serviço)**.

No caso de dois substantivos e dois verbos, a consistência não simplifica muito o aprendizado. No entanto, se você examinar um conjunto padrão de 10 substantivos e 10 verbos, você terá apenas 20 palavras para entender, mas elas podem ser usadas para formar 100 nomes distintos de comando.

Com frequência, você pode reconhecer o que um comando faz simplesmente lendo seu nome, e é geralmente aparente qual nome deve ser usado para um novo comando. Por exemplo, um comando de desligamento do computador poderia ser **Stop-Computer (Parar-Computador)**. Um comando que lista todos os computadores em uma rede poderia ser **Get-Computer (Obter-Computador)**. O comando que obtém a data do sistema é **Get-Date (Obter-Data)**.

Você pode listar todos os comandos que incluem um determinado verbo com o parâmetro **-Verb** para **Get-Command** (abordaremos o **Get-Command** em mais detalhes na próxima seção). Por exemplo, para ver todos os cmdlets que usam o verbo **Get**, digite:

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

O parâmetro **-Noun** parâmetro é ainda mais útil, pois permite ver uma família de comandos que afetam o mesmo tipo de objeto. Por exemplo, se você quiser ver quais comandos estão disponíveis para gerenciar serviços, digite o comando a seguir:

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

Um comando não é necessariamente um cmdlet apenas porque ele tem um esquema de nomenclatura verbo-substantivo. Um exemplo de um comando do Windows PowerShell nativo que não é um cmdlet, mas tem um nome com verbo-substantivo é o comando para limpar uma janela do console, o Clear-Host. O comando Clear-Host é na verdade uma função interna, como podemos ver ao executar o Get-Command para ele:

```
PS> Get-Command -Name Clear-Host

CommandType     Name                            Definition
-----------     ----                            ----------
Function        Clear-Host                      $spaceType = [System.Managem...
```

### Cmdlets usam parâmetros padrão
Conforme observado anteriormente, comandos usados em interfaces de linha de comando tradicionais geralmente não têm nomes de parâmetro consistentes. Às vezes, os parâmetros não têm qualquer nome. Quando isso acontece, eles geralmente são caracteres únicos ou palavras abreviadas que podem ser digitadas rapidamente, mas que não são facilmente compreendidas por novos usuários.

Diferente de outras interfaces de linha de comando tradicionais, o Windows PowerShell processa parâmetros diretamente e usa esse acesso direto aos parâmetros juntamente com as diretrizes para desenvolvedores a fim de padronizar os nomes dos parâmetros. Embora isso não garante que cada cmdlet sempre esteja em conformidade com os padrões, ele estimula que isso ocorra.

> [!NOTE]
> Nomes de parâmetro sempre têm um prefixo “-” acrescentado a eles ao usá-los, para permitir que o Windows PowerShell possa identificá-los claramente como parâmetros. No exemplo **Get-Command -Name Clear-Host**, o nome do parâmetro é **Name**, mas ele é inserido como -**Name**.

Aqui estão algumas das características gerais dos nomes de parâmetro padrão e seus usos.

#### O parâmetro de Ajuda (?)
Ao especificar o parâmetro **-?** para qualquer cmdlet, este não é executado. Em vez disso, o Windows PowerShell exibe a ajuda para o cmdlet.

#### Parâmetros comuns
O Windows PowerShell tem vários parâmetros, conhecidos como *parâmetros comuns*. Como esses parâmetros são controlados pelo mecanismo do Windows PowerShell, sempre que eles são implementados por um cmdlet, eles se comportam da mesma maneira. Os parâmetros comuns são **WhatIf**, **Confirm**, **Verbose**, **Debug**, **Warn**, **ErrorAction**, **ErrorVariable**, **OutVariable** e **OutBuffer**.

#### Parâmetros sugeridos
Os principais cmdlets do Windows PowerShell usam nomes padrão para parâmetros semelhantes. Embora o uso de nomes de parâmetros não seja imposto, há diretrizes explícitas para seu uso a fim de incentivar a padronização.

Por exemplo, as diretrizes recomendam nomear um parâmetro que se refere a um computador pelo nome como **ComputerName**, em vez de Server, Host, System, Node ou outras palavras alternativas comuns. Entre os nomes de parâmetro sugeridos importantes estão **Force**, **Exclude**, **Include**, **PassThru**, **Path** e **CaseSensitive**.



<!--HONumber=Apr16_HO1-->


