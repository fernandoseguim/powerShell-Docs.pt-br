---
title: Elemento ViewSelectedBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863182"
---
# <a name="viewselectedby-element-format"></a>Elemento ViewSelectedBy (formato)

Define os objetos do .NET que são exibidos pela exibição. Cada modo de exibição deve especificar pelo menos um objeto .NET.

Elemento ViewDefinitions (formato) modo de exibição (formato) ViewSelectedBy elemento (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `ViewSelectedBy` elemento. Esse elemento deve conter pelo menos um `TypeName` ou `SelectionSetName` elemento filho. Não há nenhum limite para o número de elementos filho que podem ser especificados, nem é sua ordem significativa.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento TypeName para ViewSelectedBy (formato)](./typename-element-for-viewselectedby-format.md)|Elemento opcional.<br /><br /> Especifica um objeto .NET que é exibido pelo modo de exibição.|
|[Elemento SelectionSetName para ViewSelectedBy (formato)](./selectionsetname-element-for-viewselectedby-format.md)|Elemento opcional.<br /><br /> Especifica um conjunto de objetos .NET que são exibidos pela exibição.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de exibição (formato)](./view-element-format.md)|Define uma exibição que exibe um ou mais objetos do .NET.|

## <a name="remarks"></a>Comentários

Para obter mais informações sobre como esse elemento é usado em diferentes modos de exibição, consulte [componentes de exibição de tabela](./creating-a-table-view.md), [componentes de exibição de lista](./creating-a-list-view.md), [componentes de exibição ampla](./creating-a-wide-view.md)e [Componentes de controle personalizado](./creating-custom-controls.md).

O `SelectionSetName` elemento é usado quando o arquivo de formatação define um conjunto de objetos que são exibidos por vários modos de exibição. Para obter mais informações sobre como os conjuntos de seleção são definidos e referenciados, consulte [definindo define de objetos](./defining-selection-sets.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como especificar o [ServiceProcess](/dotnet/api/System.ServiceProcess.ServiceController) objeto para uma exibição de lista. O mesmo esquema é usado para exibições de tabela, ampla e personalizadas.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Consulte Também

[Criando uma exibição de lista](./creating-a-list-view.md)

[Criando uma exibição de tabela](./creating-a-table-view.md)

[Criando uma exibição ampla](./creating-a-wide-view.md)

[Criação de controles personalizados](./creating-custom-controls.md)

[Definindo conjuntos de seleção](./defining-selection-sets.md)

[Elemento SelectionSetName para ViewSelectedBy (formato)](./selectionsetname-element-for-viewselectedby-format.md)

[Elemento TypeName (formato)](./typename-element-for-viewselectedby-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
