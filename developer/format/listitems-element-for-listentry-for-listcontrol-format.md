---
title: Elemento ListItems para ListEntry para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858582"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>Elemento ListItems para ListEntry para ListControl (formato)

Define as propriedades e os scripts cujos valores são exibidos nas linhas da exibição de lista.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento ListControl (formato) ListEntries elemento de configuração para lista (Format) do controle ListEntry elemento do elemento ListControl (formato) ListItems para ListControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `ListItems` elemento. Não há nenhum limite para o número de elementos filho que podem ser especificados. A ordem dos elementos filho define a ordem que os valores são exibidos na exibição de lista.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento ListItem para ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)|Elemento necessário.<br /><br /> Define a propriedade ou o script cujo valor é exibido pelo modo de exibição de lista.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento ListEntry para ListControl (formato)](./listentry-element-for-listcontrol-format.md)|Fornece uma definição da exibição de lista.|

## <a name="remarks"></a>Comentários

Para obter mais informações sobre esse tipo de exibição, consulte [criando uma exibição de lista](./creating-a-list-view.md).

## <a name="example"></a>Exemplo

Este exemplo mostra os elementos XML que definem três linhas da exibição de lista.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a>Consulte Também

[Elemento ListEntry para ListControl (formato)](./listentry-element-for-listcontrol-format.md)

[Elemento ListItem para ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Criando uma exibição de lista](./creating-a-list-view.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
