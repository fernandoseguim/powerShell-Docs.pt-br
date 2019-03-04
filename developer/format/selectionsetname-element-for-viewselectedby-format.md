---
title: Elemento SelectionSetName para ViewSelectedBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858332"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>Elemento SelectionSetName para ViewSelectedBy (formato)

Especifica um conjunto de objetos .NET que são exibidos pela exibição.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento ViewSelectedBy (formato) SelectionSetName elemento de configuração para ViewSelectedBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `SelectionSetName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento ViewSelectedBy (formato)](./viewselectedby-element-format.md)|Define os objetos do .NET que são exibidos pela exibição.|

## <a name="text-value"></a>Valor de texto

Especifique o nome do conjunto de seleção que é definido pelo `Name` elemento para o conjunto de seleção.

## <a name="remarks"></a>Comentários

Você pode usar conjuntos de seleção quando você tem um conjunto de objetos relacionados que você deseja referenciar, usando um nome único, como um conjunto de objetos que estão relacionadas por meio da herança. Para obter mais informações sobre como definir e referenciar conjuntos de seleção, consulte [definindo define de objetos](./defining-selection-sets.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como especificar uma seleção definida para uma exibição de lista. O mesmo esquema é usado para exibições de tabela, ampla e personalizadas.

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Consulte Também

[Definindo conjuntos de seleção](./defining-selection-sets.md)

[Elemento ViewSelectedBy (formato)](./viewselectedby-element-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
