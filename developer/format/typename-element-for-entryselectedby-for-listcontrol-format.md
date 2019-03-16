---
title: Elemento TypeName para EntrySelectedBy para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059687"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a>Elemento TypeName para EntrySelectedBy para ListControl (formato)

Especifica um tipo .NET que usa essa entrada da exibição de lista. Não há nenhum limite para o número de tipos que podem ser especificados para uma entrada da lista.

Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento ListControl (formato) elemento ListEntries (formato) elemento ListEntry (formato) EntrySelectedBy elemento de configuração para elemento de TypeName ListEntry (formato) EntrySelectedBy para ListControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `TypeName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento EntrySelectedBy para ListEntry (formato)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Define os tipos de .NET que usam essa entrada de lista ou a condição que deve existir para essa entrada a ser usado.|

## <a name="text-value"></a>Valor de texto

Especifique o nome totalmente qualificado do tipo .NET, como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Comentários

Cada entrada da lista deve ter pelo menos um nome de tipo, conjunto de seleção ou condição de seleção definida.

Para obter mais informações sobre como esse elemento é usado em uma exibição de lista, consulte [exibição de lista](./creating-a-list-view.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como especificar uma seleção definida para uma entrada de uma exibição de lista.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>Consulte Também

[Criando uma exibição de lista](./creating-a-list-view.md)

[Elemento EntrySelectedBy para ListEntry (formato)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Elemento SelectionSetName para EntrySelectedBy para ListEntry (formato)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
