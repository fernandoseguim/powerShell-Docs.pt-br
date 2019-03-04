---
title: Elemento ColumnNumber para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856222"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>Elemento ColumnNumber para WideControl (formato)

Especifica o número de colunas exibidas no modo de exibição amplo.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento WideControl (formato) ColumnNumber elemento de configuração para WideControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `ColumnNumber` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento WideControl (formato)](./widecontrol-element-format.md)|Define uma ampla (único valor) formato de lista para o modo de exibição.|

## <a name="text-value"></a>Valor de texto

Especifique um valor inteiro positivo.

## <a name="remarks"></a>Comentários

Ao definir uma exibição ampla, você pode adicionar o `AutoSize` elemento ou o `ColumnNumber` elemento, mas você não pode adicionar ambos.

Para obter mais informações sobre os componentes de uma exibição ampla, consulte [criando uma exibição ampla](./creating-a-wide-view.md).

Para obter um exemplo de uma exibição ampla, consulte [exibição ampla (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Consulte Também

[Elemento AutoSize para WideControl (formato)](./autosize-element-for-widecontrol-format.md)

[Criando uma exibição ampla](./creating-a-wide-view.md)

[Exibição ampla (Basic)](./wide-view-basic.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
