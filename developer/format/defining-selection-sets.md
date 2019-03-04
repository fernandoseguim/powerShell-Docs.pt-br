---
title: Definindo conjuntos de seleção | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858922"
---
# <a name="defining-selection-sets"></a>Definir conjuntos de seleção

Durante a criação de vários modos de exibição e controles, você pode definir conjuntos de objetos que são conhecidos como conjuntos de seleção. Um conjunto de seleção permite que você defina os objetos de uma vez, sem a necessidade de defini-las repetidamente para cada modo de exibição ou controle. Normalmente, os conjuntos de seleção são usados quando você tem um conjunto de objetos relacionados do .NET. Por exemplo, o `FileSystem` arquivo de formatação (FileSystem.format.ps1xml) define um conjunto de seleção dos tipos de sistema de arquivos que usam vários modos de exibição.

## <a name="where-selection-sets-are-defined-and-referenced"></a>Onde os conjuntos de seleção são definidos e referenciada

Você pode definir conjuntos de seleção como parte dos dados comuns que podem ser usados por todos os modos de exibição e os controles definidos no arquivo de formatação. O exemplo a seguir mostra como definir três conjuntos de seleção.

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

Você pode fazer referência a uma seleção define das seguintes maneiras:

- Cada exibição tem um `ViewSelectedBy` elemento que define quais objetos são exibidos por meio da exibição. O `ViewSelectedBy` elemento tem um `SelectionSetName` elemento filho que especifica a seleção de conjunto de que todas as definições do uso do modo de exibição. Não há nenhuma restrição no número de conjuntos de seleção que você pode fazer referência a partir de um modo de exibição.

- Em cada definição de uma exibição ou controle, o `EntrySelectedBy` elemento define quais objetos são exibidos por meio dessa definição. Normalmente um modo de exibição ou o controle tem apenas uma definição para que os objetos são definidos pelo `ViewSelectedBy` elemento. O `EntrySelectedBy` elemento da definição tem um `SelectionSetName` elemento filho que especifica o conjunto de seleção. Se você especificar a seleção definida para uma definição, não é possível especificar qualquer um dos outros elementos filho do `EntrySelectedBy` elemento.

- Em cada definição de uma exibição ou controle, o `SelectionCondition` elemento pode ser usado para especificar uma condição para quando a definição é usada. O `SelectionCondition` elemento tem um `SelectionSetName` elemento filho que especifica a seleção de conjunto que dispara a condição. A condição é disparada quando qualquer um dos objetos definidos no conjunto de seleção são exibidas. Para obter mais informações sobre como definir essas condições, consulte [definindo condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md).

## <a name="selection-set-example"></a>Exemplo de conjunto de seleção

O exemplo a seguir mostra um conjunto de seleção que é obtido diretamente do `FileSystem` formatação de arquivo fornecido pelo Windows PowerShell. Para obter mais informações sobre outros PowerShell Windows arquivos de formatação, consulte [arquivos de formatação do Windows PowerShell](./powershell-formatting-files.md).

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

O conjunto anterior de seleção é referenciado no `ViewSelectedBy` elemento de uma exibição de tabela.

```xml
<ViewDefinitions>
  <View>
    <Name>Files</Name>
    <ViewSelectedBy>
      <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="xml-elements"></a>Elementos XML

 Não há nenhum limite para o número de conjuntos de seleção que você pode definir. Os seguintes elementos XML são usados para criar um conjunto de seleção.

- O [SelectionSets](./selectionsets-element-format.md) elemento define os conjuntos de objetos .NET que são referenciados pelas exibições e controles com o arquivo de formatação.

- O [SelectionSet](./selectionset-element-format.md) elemento define um único conjunto de objetos .NET.

- O [nome](./name-element-for-selectionset-format.md) elemento Especifica o nome que é usado para referenciar o conjunto de seleção.

- O [tipos](./types-element-for-selectionset-format.md) elemento Especifica os tipos do .NET dos objetos do conjunto de seleção. (Em arquivos de formatação, objetos são especificados pelo seu tipo de .NET.)

 Os seguintes elementos XML são usados para especificar um conjunto de seleção.

- O elemento a seguir especifica a seleção definida para usar em todas as definições do modo de exibição:

    - [Elemento SelectionSetName para ViewSelectedBy (formato)](./selectionsetname-element-for-viewselectedby-format.md)

    - [Elemento SelectionSetName para EntrySelectedBy para GroupBy (formato)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- Os elementos a seguir especificam o conjunto de seleção usado por uma definição de exibição única:

    - [Elemento SelectionSetName para EntrySelectedBy para ListControl (formato)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [Elemento SelectionSetName para EntrySelectedBy para TableControl (formato)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [Elemento SelectionSetName para EntrySelectedBy para WideControl (formato)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [Elemento SelectionSetName para EntrySelectedBy para CustomControl para exibição (formato)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- Os elementos a seguir especificam o conjunto de seleção usado pelo comum e exibir as definições de controle:

    - [Elemento SelectionSetName para EntrySelectedBy controles para exibição (formato)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [Elemento SelectionSetName para EntrySelectedBy para controles de configuração (formato)](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- Os elementos a seguir especificam o conjunto de seleção usado quando você define qual objeto expandir:

    - [Elemento SelectionSetName para EntrySelectedBy para EnumerableExpansion (formato)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Os seguintes elementos de especificam o conjunto de seleção usado pelas condições de seleção.

    - [Elemento SelectionSetName para SelectionCondition para controles de configuração (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [Elemento SelectionSetName para SelectionCondition controles para exibição (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [Elemento SelectionSetName para SelectionCondition para CustomControl para exibição (formato)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableControl (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [Elemento SelectionSetName para SelectionCondition para GroupBy (formato)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>Consulte Também

[SelectionSets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[Nome](./name-element-for-selectionset-format.md)

[Tipos](./types-element-for-selectionset-format.md)

[Arquivos de formatação do PowerShell](./powershell-formatting-files.md)

[Definir condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md)

[Escrevendo uma formatação de PowerShell e tipos de arquivo](./writing-a-powershell-formatting-file.md)
