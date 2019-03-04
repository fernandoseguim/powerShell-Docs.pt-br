---
title: Elemento TypeName para EntrySelectedBy para WideEntry (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862642"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a>Elemento TypeName para EntrySelectedBy para WideEntry (formato)

Especifica um tipo .NET para a definição. A definição é usada sempre que esse objeto é exibido.

Configuração (formato) do elemento elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento do elemento WideEntry (formato) TypeName para WideEntry ( Formato)

## <a name="syntax"></a>Sintaxe

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `TypeName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento EntrySelectedBy para WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md)|Define os tipos de .NET que usam essa entrada ampla ou a condição que deve existir para essa entrada a ser usado.|

## <a name="text-value"></a>Valor de texto

Especifique o nome totalmente qualificado do tipo .NET, como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Comentários

Cada entrada ampla deve especificar um ou mais tipos de .NET, um conjunto de seleção ou a condição de seleção que deve existir para a definição a ser usado.

Para obter mais informações sobre outros componentes de uma exibição ampla, consulte [criando uma exibição ampla](./creating-a-wide-view.md).

## <a name="see-also"></a>Consulte Também

[Criando uma exibição ampla](./creating-a-wide-view.md)

[Elemento EntrySelectedBy para WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
