---
title: Nome de elemento para o modo de exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859502"
---
# <a name="name-element-for-view-format"></a>Elemento Name para View (formato)

Especifica o nome que é usado para identificar o modo de exibição.

Configuração (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento nome elemento (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `Name` elemento. Apenas um `Name` elemento é permitido para cada modo de exibição.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de exibição (formato)](./view-element-format.md)|Define uma exibição que é usada para exibir os membros de um ou mais objetos do .NET.|

## <a name="text-value"></a>Valor de texto

Especifique um nome amigável exclusivo para o modo de exibição. Esse nome pode incluir uma referência para o tipo de exibição (como um modo de exibição de tabela ou exibição de lista), qual objeto ou conjunto de objetos usam o modo de exibição, o comando retorna os objetos ou uma combinação desses elementos.

## <a name="remarks"></a>Comentários

Para obter mais informações sobre os diferentes tipos de modos de exibição, consulte os tópicos a seguir: [Exibição de tabela](./creating-a-table-view.md), [exibição de lista](./creating-a-list-view.md), [exibição ampla](./creating-a-wide-view.md), e [exibição personalizada](./creating-custom-controls.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra uma `View` elemento que define uma exibição de tabela para o [ServiceProcess](/dotnet/api/System.ServiceProcess.ServiceController) objeto. O nome do modo de exibição é "serviço".

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a>Consulte Também

[Criando uma exibição de lista](./creating-a-list-view.md)

[Criando uma exibição de tabela](./creating-a-table-view.md)

[Criando uma exibição ampla](./creating-a-wide-view.md)

[Criação de controles personalizados](./creating-custom-controls.md)

[Elemento de exibição (formato)](./view-element-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
