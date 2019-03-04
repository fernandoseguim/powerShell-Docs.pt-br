---
title: Os tipos de elemento de SelectionSet (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862372"
---
# <a name="types-element-for-selectionset-format"></a>Elemento Types para SelectionSet (formato)

Define os objetos .NET na seleção definidos.

Tipos de configuração (formato) elemento SelectionSets (formato) SelectionSet elemento (formato) elemento (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `Types` elemento. Deve haver pelo menos um elemento filho, mas não há nenhum limite máximo ao número de elementos filho que podem ser adicionados.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento TypeName de tipos (formato)](./typename-element-for-types-format.md)|Elemento necessário.<br /><br /> Especifica o objeto .NET que pertence ao conjunto de seleção.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento SelectionSet (formato)](./selectionset-element-format.md)|Define um conjunto de objetos .NET que pode ser referenciado pelo nome do conjunto.|

## <a name="remarks"></a>Comentários

Os objetos definidos por esse elemento compõem um conjunto de seleção que pode ser usado por uma exibição, por uma definição de uma exibição (modos de exibição podem ter várias definições), ou ao especificar uma condição de seleção.  Para obter mais informações sobre conjuntos de seleção, consulte [definindo define de objetos](./defining-selection-sets.md).

## <a name="example"></a>Exemplo

Este exemplo mostra um `SelectionSet` elemento que define quatro tipos de .NET.

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

[Definindo conjuntos de objetos](./defining-selection-sets.md)

[Elemento SelectionSet (formato)](./selectionset-element-format.md)

[Elemento TypeName de tipos (formato)](./typename-element-for-types-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
