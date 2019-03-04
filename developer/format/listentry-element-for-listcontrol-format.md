---
title: Elemento ListEntry para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862242"
---
# <a name="listentry-element-for-listcontrol-format"></a>Elemento ListEntry para ListControl (formato)

Fornece uma definição da exibição de lista.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento ListControl (formato) elemento ListEntries (formato) ListEntry elemento de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `ListEntry` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento EntrySelectedBy para ListEntry (formato)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Define os objetos do .NET que usam essa definição de exibição de lista ou a condição que deve existir para essa definição a ser usado.|
|[Elemento ListItems (formato)](./listitems-element-for-listentry-for-listcontrol-format.md)|Elemento necessário.<br /><br /> Define as propriedades e os scripts cujos valores são exibidos pela exibição de lista.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento ListEntries (formato)](./listentries-element-for-listcontrol-format.md)|Fornece as definições de exibição de lista.|

## <a name="remarks"></a>Comentários

Uma exibição de lista é um formato de lista que exibe valores de propriedade ou script para cada objeto. Para obter mais informações sobre modos de exibição de lista, consulte [criando uma exibição de lista](./creating-a-list-view.md).

## <a name="example"></a>Exemplo

Este exemplo mostra os elementos XML que definem o modo de exibição de lista para o [ServiceProcess](/dotnet/api/System.ServiceProcess.ServiceController) objeto.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Consulte Também

[Criando uma exibição de lista](./creating-a-list-view.md)

[Elemento EntrySelectedBy para ListEntry (formato)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Elemento ListEntries (formato)](./listentries-element-for-listcontrol-format.md)

[Elemento ListItems (formato)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Escrevendo um formatação do Windows PowerShell e tipos de arquivo](./writing-a-powershell-formatting-file.md)
