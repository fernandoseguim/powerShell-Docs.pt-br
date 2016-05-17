---
title:  Usando comandos de formatação para alterar a exibição de saída
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  63515a06-a6f7-4175-a45e-a0537f4f6d05
---

# Usando comandos de formatação para alterar a exibição de saída
O Windows PowerShell tem um conjunto de cmdlets que permite controlar quais propriedades são exibidas para objetos específicos. Os nomes de todos os cmdlets começam com o verbo **Format**. Eles permitem selecionar uma ou mais propriedades para mostrar.

Os cmdlets **Format** são **Format-Wide**, **Format-List**, **Format-Table** e **Format-Custom**. Descrevemos apenas os cmdlets **Format-Wide**, **Format-List** e **Format-Table** neste guia do usuário.

Cada cmdlet de formato tem propriedades padrão que serão usadas se você não definir propriedades específicas a serem exibidas. Cada cmdlet também usa o mesmo nome de parâmetro, **Property**, para especificar quais propriedades você deseja exibir. Como **Format-Wide** mostra apenas uma única propriedade, seu parâmetro **Property** tem apenas um único valor, mas os parâmetros de propriedade de **Format-List** e **Format-Table** aceita uma lista de nomes de propriedade.

Se você usar o comando **Get-Process -Name powershell** com duas instâncias do Windows PowerShell em execução, obterá uma saída parecida com esta:

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

No restante desta seção, exploraremos como usar cmdlets **Format** para alterar a maneira como a saída desse comando é exibida.

### Usando Format-Wide para Saída Single-Item
O cmdlet **Format-Wide**, por padrão, exibe apenas a propriedade padrão de um objeto. As informações associadas a cada objeto são exibidas em uma única coluna:

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

Você também pode especificar uma propriedade não padrão:

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### Controlando a exibição Format-Wide com Column
Com o cmdlet **Format-Wide**, é possível exibir apenas uma única propriedade por vez. Isso é útil para exibir listas simples que mostram apenas um elemento por linha. Para obter uma lista simples, defina o valor do parâmetro **Column** para 1 digitando:

```
Get-Command Format-Wide -Property Name -Column 1
```

### Usando Format-List para uma exibição de lista
O cmdlet **Format-List** exibe um objeto em forma de uma lista, com cada propriedade rotulada e exibida em uma linha separada:

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

Você pode especificar quantas propriedades quiser:

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

#### Obtendo informações detalhadas usando Format-List com curingas
O cmdlet **Format-List** permite usar um caractere curinga como o valor do parâmetro **Property**. Isso permite exibir informações detalhadas. Geralmente, os objetos incluem mais informações do que você precisa, por isso, o Windows PowerShell não mostra todos os valores de propriedade por padrão. Para mostrar todas as propriedades de um objeto, use o comando **Format-List -Property &#42;**. O comando a seguir gera mais de 60 linhas de saída para um único processo:

```
Get-Process -Name powershell | Format-List -Property *
```

Embora o comando **Format-List** seja útil para mostrar os detalhes, se você quiser obter uma visão geral de saída que inclui muitos itens, uma exibição tabular simples geralmente será mais útil.

### Usando Format-Table para saída tabular
Caso você use o cmdlet **Format-Table** sem nenhum nome de propriedade especificado para formatar a saída do comando **Get-Process**, você obtém exatamente a mesma saída que receberia sem executar qualquer formatação de saída. O motivo disso é que os processos normalmente são exibidos em um formato tabular, assim como a maioria dos objetos do Windows PowerShell.

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### Melhorando a saída do Format-Table (AutoSize)
Embora uma exibição tabular seja útil para exibir muitas informações comparáveis, ela poderá ser difícil de interpretar se a exibição for muito estreita para os dados. Por exemplo, se você tentar exibir o caminho do processo, ID, nome e empresa, você receberá uma saída truncada para o caminho do processo e a coluna da empresa:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

Se você especificar o parâmetro **AutoSize** ao executar o comando **Format-Table**, o Windows PowerShell calculará as larguras das colunas com base nos dados reais que serão exibidos. Isso torna a coluna **Path** legível, mas a coluna de empresa permanece truncada:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

O cmdlet **Format-Table** ainda pode truncar os dados, mas ele só fará isso ao final da tela. Propriedades, além da última exibida, recebem o tamanho correspondente ao que precisam para seu elemento de dados mais longo ser exibido corretamente. Você pode ver que o nome da empresa estará visível e o caminho ficará truncado se você trocar os locais de **Path** e **Company** na lista de valores **Property**:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

O comando **Format-Table** supõe que quanto mais próxima uma propriedade está do início da lista de propriedades, mais importante ela é. Portanto, ele tenta exibir as propriedades mais próximo ao início completamente. Se o comando **Format-Table** não conseguir exibir todas as propriedades, ele removerá algumas colunas da exibição e fornecerá um aviso. Você pode ver esse comportamento se colocar a propriedade **Name** por último na lista:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

Na saída acima, a coluna ID é truncada para ajustá-la para a listagem e os cabeçalhos de coluna são empilhados. Redimensionar automaticamente as colunas nem sempre produz o resultado desejado.

#### Quebra automática de linha na saída de Format-Table em colunas (Wrap)
Você pode forçar dados do **Format-Table** longos a serem exibidos com encapsulamento em sua coluna de exibição usando o parâmetro **Wrap**. Usar o parâmetro **Wrap** sozinho não necessariamente fará o que você espera, já que ele usará as configurações padrão se você não especificar **AutoSize**:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

Uma vantagem de usar o parâmetro **Wrap** sozinho é que ele não retarda muito o processamento. Se você realizar uma listagem recursiva dos arquivos de um sistema de diretório, isso poderá levar muito tempo e usar muita memória antes de exibir os primeiros itens de saída se você usar **AutoSize**.

Se você não estiver preocupado com a carga do sistema, **AutoSize** funcionará bem com o parâmetro **Wrap**. As colunas iniciais sempre são alocadas com o máximo de largura necessário para exibir os itens em uma linha, da mesma forma que ao especificar **AutoSize** sem o parâmetro **Wrap**. A única diferença é que a coluna final terá quebra de linha se necessário:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

Algumas colunas poderão não ser exibidas se você especificar as colunas mais amplas primeiro, portanto, é mais seguro especificar os elementos com menos dados primeiro. No exemplo a seguir, especificamos o elemento de caminho do elemento extremamente amplo primeiro e, até mesmo com quebra automática, ainda perdemos a coluna final **Name**:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### Organizando a saída da tabela (-GroupBy)
Outro parâmetro útil para controlar a saída tabular é **GroupBy**. Listagens de tabela mais longas podem ser especialmente difíceis de comparar. O parâmetro **GroupBy** agrupa a saída com base em um valor da propriedade. Por exemplo, é possível agrupar processos pela empresa para inspeção mais fácil, omitindo o valor da empresa na lista de propriedade:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```



<!--HONumber=May16_HO2-->


