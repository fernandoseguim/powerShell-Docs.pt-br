---
title: Elemento ListItem para ListItems para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855152"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>Elemento ListItem para ListItems para ListControl (formato)

Define a propriedade ou o script cujo valor é exibido em uma linha da exibição de lista.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento ListControl (formato) ListEntries elemento de configuração para ListControl (formato) ListEntry elemento do elemento ListControl (formato) ListItems para ListControl (formato) ListItem para elemento ListControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `ListItem` elemento. Apenas uma propriedade ou o script pode ser especificado.

### <a name="attributes"></a>Atributos

Não

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento FormatString para ListItem para ListControl (formato)](./formatstring-element-for-listitem-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica uma cadeia de caracteres de formato que define como o valor da propriedade ou o script é exibido.|
|[Elemento ItemSelectionCondition para ListItem para ListControl (formato)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Define a condição que deve existir para esse item de lista a ser usado.|
|[Elemento de rótulo para o item de lista para ListControl (formato)](./label-element-for-listitem-for-listcontrol-format.md)|Elemento opcional<br /><br /> Especifica o rótulo que é exibido à esquerda do valor de propriedade ou o script na linha.|
|[Elemento PropertyName para ListItem para ListControl (formato)](./propertyname-element-for-listitem-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica a propriedade .NET cujo valor é exibido na linha.|
|[Elemento ScriptBlock para ListItem para ListControl (formato)](./scriptblock-element-for-listitem-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica o script cujo valor é exibido na linha.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento ListItems para controle de lista (formato)](./listitems-element-for-listentry-for-listcontrol-format.md)|Define as propriedades e os scripts cujos valores são exibidos na exibição de lista.|

## <a name="remarks"></a>Comentários

Para obter mais informações sobre os componentes de uma exibição de lista, consulte [criando uma exibição de lista](./creating-a-list-view.md).

## <a name="example"></a>Exemplo

Este exemplo mostra os elementos XML que definem três linhas da exibição de lista. As duas primeiras linhas exibirão o valor de uma propriedade do .NET, e a última linha exibe um valor gerado por um script.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a>Consulte Também

[Elemento ListItems (formato)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Elemento FormatString para ListItem (formato)](./formatstring-element-for-listitem-for-listcontrol-format.md)

[Elemento de rótulo para o item de lista (formato)](./label-element-for-listitem-for-listcontrol-format.md)

[Elemento PropertyName para ListItem (formato)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Elemento ScriptBlock para ListItem (formato)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Criando uma exibição de lista](./creating-a-list-view.md)

[Escrevendo um formatação do Windows PowerShell e tipos de arquivo](./writing-a-powershell-formatting-file.md)
