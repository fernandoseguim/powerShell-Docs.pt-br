---
title: Elemento WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859822"
---
# <a name="widecontrol-element-format"></a>Elemento WideControl (formato)

Define uma ampla (único valor) formato de lista para o modo de exibição. Essa exibição mostra um valor de propriedade única ou script para cada objeto.

Configuração (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento WideControl elemento (formato)

## <a name="syntax"></a>Sintaxe

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `WideControl` elemento. Não é possível especificar o `AutoSize` e `ColumnNumber` elementos ao mesmo tempo.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento AutoSize para WideControl (formato)](./autosize-element-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Especifica se o tamanho da coluna e o número de colunas são ajustados com base no tamanho dos dados.|
|[Elemento ColumnNumber para WideControl (formato)](./columnnumber-element-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Especifica o número de colunas exibidas no modo de exibição amplo.|
|[Elemento WideEntries (formato)](./wideentries-element-for-widecontrol-format.md)|Elemento necessário.<br /><br /> Fornece as definições do modo de exibição ampla.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de exibição (formato)](./view-element-format.md)|Define uma exibição que é usada para exibir um ou mais objetos do .NET.|

## <a name="remarks"></a>Comentários

Ao definir uma exibição ampla, você pode adicionar o `AutoSize` elemento ou o `ColumnNumber` , mas não é possível adicionar ambos.

Na maioria dos casos, somente uma definição, é necessária para cada exibição ampla, mas é possível ter várias definições, se você quiser usar a mesma exibição para exibir objetos diferentes do .NET. Nesses casos, você pode fornecer uma definição separada para cada objeto ou conjunto de objetos.

Para obter mais informações sobre os componentes de uma exibição ampla, consulte [componentes de exibição ampla](./creating-a-wide-view.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra uma `WideControl` que é usado para exibir uma propriedade do elemento de [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

Para obter um exemplo completo de uma exibição ampla, consulte [exibição ampla (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Consulte Também

[Elemento AutoSize para WideControl (formato)](./autosize-element-for-widecontrol-format.md)

[Elemento ColumnNumber para WideControl (formato)](./columnnumber-element-for-widecontrol-format.md)

[Elemento de exibição (formato)](./view-element-format.md)

[Elemento WideEntries (formato)](./wideentries-element-for-widecontrol-format.md)

[Exibição ampla (Basic)](./wide-view-basic.md)

[Criando uma exibição ampla](./creating-a-wide-view.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
