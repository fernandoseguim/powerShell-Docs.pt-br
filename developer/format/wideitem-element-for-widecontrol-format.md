---
title: Elemento WideItem para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862622"
---
# <a name="wideitem-element-for-widecontrol-format"></a>Elemento WideItem para WideControl (formato)

Define a propriedade ou o script cujo valor é exibido.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) WideItem elemento de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `WideItem` elemento. O elemento `FormatString` é opcional. No entanto, você deve especificar uma `PropertyName` ou `ScriptBlock` elemento, mas você não é possível especificar ambos.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento FormatString para WideItem para WideControl (formato)](./formatstring-element-for-wideitem-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Especifica um padrão de formato que define como o valor da propriedade ou o script é exibido no modo de exibição.|
|[Elemento PropertyName para WideItem (formato)](./propertyname-element-for-wideitem-for-widecontrol-format.md)|Especifica a propriedade do objeto cujo valor é exibido no modo de exibição amplo.|
|[Elemento ScriptBlock para WideItem (formato)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|Especifica o script cujo valor é exibido no modo de exibição amplo.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)|Fornece uma definição da exibição ampla.|

## <a name="remarks"></a>Comentários

Para obter mais informações sobre os componentes de uma exibição ampla, consulte [exibição ampla](./creating-a-wide-view.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra uma `WideEntry` que define um único elemento `WideItem` elemento. O `WideItem` elemento define a propriedade ou cujo valor é exibido no modo de exibição de script.

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

Para obter um exemplo completo de uma exibição ampla, consulte [exibição ampla (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Consulte Também

[Elemento FormatString para WideItem para WideControl (formato)](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[Elemento PropertyName para WideItem (formato)](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[Elemento ScriptBlock para WideItem (formato)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
