---
title: Elemento WideEntries para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853272"
---
# <a name="wideentries-element-for-widecontrol-format"></a>Elemento WideEntries para WideControl (formato)

Fornece as definições do modo de exibição ampla. O modo de exibição amplo deve especificar uma ou mais definições.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento WideControl (formato) WideEntries elemento de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `WideEntries` elemento. Pelo menos um elemento filho deve ser especificado.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)|Fornece uma definição da exibição ampla.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento WideControl (formato)](./widecontrol-element-format.md)|Define uma ampla (único valor) formato de lista para o modo de exibição.|

## <a name="remarks"></a>Comentários

Uma exibição ampla é um formato de lista que exibe um valor de propriedade única ou script para cada objeto. Para obter mais informações sobre os componentes de uma exibição ampla, consulte [componentes de exibição ampla](./creating-a-wide-view.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra uma `WideEntries` que define um único elemento `WideEntry` elemento. O `WideEntry` elemento contém um único `WideItem` elemento que define qual valor de propriedade ou o script é exibido no modo de exibição.

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

Para obter um exemplo completo de uma exibição ampla, consulte [exibição ampla (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Consulte Também

[Criando uma exibição ampla](./creating-a-wide-view.md)

[Elemento WideControl (formato)](./widecontrol-element-format.md)

[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
