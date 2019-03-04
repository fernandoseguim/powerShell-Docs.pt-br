---
title: Elemento SelectionSets (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853562"
---
# <a name="selectionsets-element-format"></a>Elemento SelectionSets (formato)

Define os conjuntos de objetos .NET que podem ser usados por todos os modos de exibição do arquivo de formatação comuns. Os controles do arquivo de formatação e modos de exibição podem referenciar o conjunto completo de objetos usando apenas o nome do conjunto de seleção.

Formato do elemento SelectionSets de elemento de configuração

## <a name="syntax"></a>Sintaxe

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `SelectionSets` elemento. Cada elemento filho define um conjunto de objetos que podem ser referenciados pelo nome do conjunto. A ordem dos elementos filho não é significativa.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento SelectionSet (formato)](./selectionset-element-format.md)|Elemento necessário.<br /><br /> Define um único conjunto de objetos .NET que pode ser referenciado pelo nome do conjunto.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de configuração](./configuration-element-format.md)|Representa o elemento de nível superior de um arquivo de formatação.|

## <a name="remarks"></a>Comentários

Você pode usar conjuntos de seleção quando você tem um conjunto de objetos relacionados que você deseja referenciar, usando um nome único, como um conjunto de objetos que estão relacionadas por meio da herança. Ao definir seus modos de exibição, você pode especificar o conjunto de objetos usando o nome da seleção definida em vez de listar todos os objetos dentro de cada modo de exibição.

Conjuntos de seleção comuns são especificados por seu nome ao definir os modos de exibição do arquivo de formatação ou as definições dos modos de exibição. Nesses casos, o `SelectionSetName` elemento filho do `ViewSelectedBy` e `EntrySelectedBy` elementos especifica o conjunto a ser usado. Para obter mais informações sobre conjuntos de seleção, consulte [definindo define de objetos](./defining-selection-sets.md).

## <a name="see-also"></a>Consulte Também

[Elemento de configuração](./configuration-element-format.md)

[Definindo conjuntos de seleção](./defining-selection-sets.md)

[Elemento SelectionSet (formato)](./selectionset-element-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
