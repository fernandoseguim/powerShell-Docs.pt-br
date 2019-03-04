---
title: Elemento WideEntry para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856522"
---
# <a name="wideentry-element-for-widecontrol-format"></a>Elemento WideEntry para WideControl (formato)

Fornece uma definição da exibição ampla.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento WideControl (formato) elemento WideEntries (formato) WideEntry elemento de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `WideEntry` elemento. Você deve especificar um único `WideItem` elemento filho.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento EntrySelectedBy para WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md)|Elemento opcional.<br /><br /> Define os tipos de .NET que usam essa definição ampla de entrada ou a condição que deve existir para essa definição a ser usado.|
|[Elemento WideItem (formato)](./wideitem-element-for-widecontrol-format.md)|Elemento necessário.<br /><br /> Define a propriedade ou o script cujo valor é exibido.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento WideEntries (formato)](./wideentries-element-for-widecontrol-format.md)|Fornece as definições do modo de exibição ampla.|

## <a name="remarks"></a>Comentários

Uma exibição ampla é um formato de lista que exibe um valor de propriedade única ou script para cada objeto. Ao contrário de outros tipos de modos de exibição, você pode especificar apenas um elemento de item para cada definição de exibição. Para obter mais informações sobre os outros componentes de uma exibição ampla, consulte [criando uma exibição ampla](./creating-a-wide-view.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra uma `WideEntry` que define um único elemento `WideItem` elemento. O `WideItem` elemento define a propriedade cujo valor é exibido no modo de exibição.

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

Para obter um exemplo completo de uma exibição ampla, consulte [exibição ampla (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Consulte Também

[Criando uma exibição ampla](./creating-a-wide-view.md)

[Elemento SelectionCondition para WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento SelectionSetName para WideEntry (formato)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento TypeName para WideEntry (formato)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Elemento WideEntries (formato)](./wideentries-element-for-widecontrol-format.md)

[Elemento WideItem (formato)](./wideitem-element-for-widecontrol-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
