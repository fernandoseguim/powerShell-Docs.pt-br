---
title: Nome de elemento para SelectionSet (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858162"
---
# <a name="name-element-for-selectionset-format"></a>Elemento Name para SelectionSet (formato)

Especifica o nome usado para referenciar o conjunto de seleção.

Elemento (formato) elemento SelectionSets (formato) elemento SelectionSet (formato) nome elemento de configuração SelectionSet (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `Name` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento SelectionSet (formato)](./selectionset-element-format.md)|Define um único conjunto de objetos .NET que pode ser referenciado pelo nome do conjunto.|

## <a name="text-value"></a>Valor de texto

Especifique o nome para referenciar o conjunto de seleção. Há não há restrições em relação a quais caracteres podem ser usadas.

## <a name="remarks"></a>Comentários

O nome especificado aqui é usado no `SelectionSetName` elemento. O conjunto de seleção que pode ser usado por uma exibição, por uma definição de uma exibição (modos de exibição podem ter várias definições), ou ao especificar uma condição de seleção. Para obter mais informações sobre conjuntos de seleção, consulte [definindo define de objetos](./defining-selection-sets.md).

## <a name="example"></a>Exemplo

Este exemplo mostra um `SelectionSet` elemento que define quatro tipos de .NET. O nome do conjunto de seleção é "FileSystemTypes".

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

## <a name="see-also"></a>Consulte Também

[Definindo conjuntos de seleção](./defining-selection-sets.md)

[Elemento SelectionSet (formato)](./selectionset-element-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
