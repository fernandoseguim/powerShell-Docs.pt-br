---
title: Elemento SelectionSet (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861152"
---
# <a name="selectionset-element-format"></a>Elemento SelectionSet (formato)

Define um conjunto de objetos .NET que pode ser referenciado pelo nome do conjunto.

Configuração (formato) elemento SelectionSets (formato) SelectionSet elemento (formato)

## <a name="syntax"></a>Sintaxe

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `SelectionSet` elemento. Cada conjunto de seleção deve ter um nome, e ele deve especificar os objetos do .NET do conjunto.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento Name para SelectionSet (formato)](./name-element-for-selectionset-format.md)|Elemento necessário.<br /><br /> Especifica o nome usado para referenciar o conjunto de seleção.|
|[Tipos de elemento (formato)](./types-element-for-selectionset-format.md)|Elemento necessário.<br /><br /> Define os objetos .NET na seleção definidos.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Formato do elemento SelectionSets](./selectionsets-element-format.md)|Define os conjuntos de objetos .NET que podem ser usados por todos os modos de exibição do arquivo de formatação comuns.|

## <a name="remarks"></a>Comentários

Você pode usar conjuntos de seleção quando você tem um conjunto de objetos relacionados que você deseja referenciar, usando um nome único, como um conjunto de objetos que estão relacionadas por meio da herança. Ao definir seus modos de exibição, você pode especificar o conjunto de objetos usando o nome da seleção definida em vez de listar todos os objetos dentro de cada modo de exibição.

Conjuntos de seleção comuns são especificados por seu nome ao definir os modos de exibição do arquivo de formatação ou as definições dos modos de exibição. Nesses casos, o `SelectionSetName` elemento filho do `ViewSelectedBy` e `EntrySelectedBy` elementos especifica o conjunto a ser usado. Para obter mais informações sobre conjuntos de seleção, consulte [definindo define de objetos](./defining-selection-sets.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra um `SelectionSet` elemento que define quatro tipos de .NET.

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

[Elemento de nome do SelectionSet (formato)](./name-element-for-selectionset-format.md)

[Elemento SelectionSets (formato)](./selectionsets-element-format.md)

[Tipos de elemento (formato)](./types-element-for-selectionset-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
