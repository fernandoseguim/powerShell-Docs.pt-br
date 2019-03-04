---
title: Elemento ItemSelectionCondition para ListItem para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861862"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>Elemento ItemSelectionCondition para ListItem para ListControl (formato)

Define a condição que deve existir para esse item de lista a ser usado.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento ListControl elemento (formato) ListEntries elemento de configuração para ListControl (formato) elemento ListEntry ListEntries para elemento de ListItems ListControl (formato) ListEntry para elemento ListItem ListControl (formato) ListItems para ListControl (formato) ItemSelectionCondition elemento ListItem para ListControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `ItemSelectionCondition` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento PropertyName para ItemSelectionCondition para ListControl (formato)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica a propriedade do .NET que dispara a condição.|
|[Elemento ScriptBlock para ItemSelectionCondition para ListControl (formato)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica o script que dispara a condição.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento ListItem para ListItems para ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)|Define a propriedade ou o script cujo valor é exibido em uma linha da exibição de lista.|

## <a name="remarks"></a>Comentários

Você pode especificar um nome de propriedade ou um script para essa condição, mas não é possível especificar ambos.

## <a name="see-also"></a>Consulte Também

[Elemento ListItem para ListItems para ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Elemento PropertyName para ItemSelectionCondition para ListControl (formato)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[Elemento ScriptBlock para ItemSelectionCondition para ListControl (formato)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
