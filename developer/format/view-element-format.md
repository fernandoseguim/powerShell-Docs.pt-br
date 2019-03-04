---
title: Exibir o elemento (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856142"
---
# <a name="view-element-format"></a>Elemento View (formato)

Define uma exibição que exibe um ou mais objetos do .NET. Não há nenhum limite para o número de exibições que podem ser definidas em um arquivo de formatação.

Elemento de exibição de ViewDefinitions elemento (formato) de (formato) do elemento de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `View` elemento. Você deve especificar apenas um dos elementos de filhos do controle, e você deve especificar o nome da exibição e os objetos que usam o modo de exibição. Definindo controles personalizados, como agrupar objetos, e especifica se o modo de exibição é out-of-band são opcionais.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de controles para exibição (formato)](./controls-element-for-view-format.md)|Elemento opcional.<br /><br /> Define um conjunto de controles que podem ser referenciados por seu nome de dentro da exibição.|
|[Elemento CustomControl (formato)](./customcontrol-element-for-groupby-format.md)|Elemento opcional.<br /><br /> Define um formato de controle personalizado para o modo de exibição.|
|[Elemento GroupBy para exibição (formato)](./groupby-element-for-view-format.md)|Elemento opcional.<br /><br /> Define como os membros dos objetos .NET são agrupados.|
|[Elemento ListControl (formato)](./listcontrol-element-format.md)|Elemento opcional.<br /><br /> Define um formato de lista para o modo de exibição.|
|[Elemento de nome para exibição (formato)](./name-element-for-view-format.md)|Elemento necessário.<br /><br /> Especifica o nome usado para referenciar o modo de exibição.|
|[Elemento TableControl (formato)](./tablecontrol-element-format.md)|Elemento opcional.<br /><br /> Define um formato de tabela para o modo de exibição.|
|[Elemento ViewSelectedBy para exibição (formato)](./viewselectedby-element-format.md)|Elemento necessário.<br /><br /> Define os objetos do .NET que essa exibição exibe.|
|[Elemento WideControl (formato)](./widecontrol-element-format.md)|Elemento opcional.<br /><br /> Define uma ampla (único valor) formato de lista para o modo de exibição.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento ViewDefinitions (formato)](./viewdefinitions-element-format.md)|Define os modos de exibição usados para exibir os objetos.|

## <a name="remarks"></a>Comentários

Para obter mais informações sobre os componentes de diferentes modos de exibição e controles personalizados, consulte os tópicos a seguir:

- [Componentes de exibição de tabela](./creating-a-table-view.md)

- [Componentes de exibição de lista](./creating-a-list-view.md)

- [Componentes de exibição ampla](./creating-a-wide-view.md)

- [Controles personalizados](./creating-custom-controls.md)

## <a name="example"></a>Exemplo

Este exemplo mostra uma `View` elemento que define uma exibição de tabela para o [ServiceProcess](/dotnet/api/System.ServiceProcess.ServiceController) objeto.

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>Consulte Também

[Elemento ViewDefinitions (formato)](./viewdefinitions-element-format.md)

[Elemento de nome para exibição (formato)](./name-element-for-view-format.md)

[Elemento ViewSelectedBy (formato)](./viewselectedby-element-format.md)

[Elemento de controles para exibição (formato)](./controls-element-for-view-format.md)

[Elemento GroupBy para exibição (formato)](./groupby-element-for-view-format.md)

[Elemento TableControl (formato)](./tablecontrol-element-format.md)

[Elemento ListControl (formato)](./listcontrol-element-format.md)

[Elemento WideControl (formato)](./widecontrol-element-format.md)

[Elemento CustomControl (formato)](./customcontrol-element-for-groupby-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
