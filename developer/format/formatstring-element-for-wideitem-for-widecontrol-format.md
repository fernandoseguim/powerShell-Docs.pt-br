---
title: Elemento FormatString para WideItem para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860932"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a>Elemento FormatString para WideItem para WideControl (formato)

Especifica um padrão de formato que define como o valor da propriedade ou o script é exibido no modo de exibição.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento WideControl (formato) elemento WideEntries (formato) WideEntry elemento de configuração para WideControl (formato) WideItem elemento para o elemento de FormatString WideControl (formato) para WideItem para WideControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `FormatString` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento WideItem para WideControl (formato)](./wideitem-element-for-widecontrol-format.md)|Define a propriedade ou o script cujo valor é exibido em uma linha da exibição de lista.|

## <a name="text-value"></a>Valor de texto

Especifique o padrão que é usado para formatar os dados. Por exemplo, você pode usar esse padrão para formatar o valor de qualquer propriedade que é do tipo [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {0:mm}.

## <a name="remarks"></a>Comentários

Cadeias de caracteres de formato podem ser usadas ao criar modos de exibição de tabela, exibições de lista, modos de exibição amplos ou modos de exibição personalizados. Para obter mais informações sobre como formatar um valor exibido em uma exibição, consulte [formatação exibidos dados](./formatting-displayed-data.md).

Para obter mais informações sobre como usar cadeias de caracteres de formato em modos de exibição amplos, consulte [criando uma exibição ampla](./creating-a-wide-view.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como definir uma cadeia de caracteres de formatação para o valor da `StartTime` propriedade.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a>Consulte Também

[Criando uma exibição ampla](./creating-a-wide-view.md)

[Elemento WideItem para WideControl (formato)](./wideitem-element-for-widecontrol-format.md)

[Escrevendo um formatação do Windows PowerShell e tipos de arquivo](./writing-a-powershell-formatting-file.md)
