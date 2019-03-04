---
title: Elemento FormatString para ListItem para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860332"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a>Elemento FormatString para ListItem para ListControl (formato)

Especifica um padrão de formato que define como o valor da propriedade ou o script é exibido.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento ListControl (formato) ListEntries elemento de configuração para ListControl (formato) ListEntry elemento do elemento ListControl (formato) ListItems para ListControl (formato) Elemento ListItem para ListControl (formato) elemento FormatString ListItem para ListControl (formato)

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
|[Elemento ListItem (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)|Define a propriedade ou o script cujo valor é exibido em uma linha da exibição de lista.|

## <a name="text-value"></a>Valor de texto

Especifique o padrão que é usado para formatar os dados. Por exemplo, você pode usar esse padrão para formatar o valor de qualquer propriedade que é do tipo [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {0:mm}.

## <a name="remarks"></a>Comentários

Cadeias de caracteres de formato podem ser usadas ao criar modos de exibição de tabela, exibições de lista, modos de exibição amplos ou modos de exibição personalizados. Para obter mais informações sobre como formatar um valor exibido em uma exibição, consulte [formatação exibidos dados](./formatting-displayed-data.md).

Para obter mais informações sobre como usar cadeias de caracteres de formato em modos de exibição de lista, consulte [criação de exibição de lista](./creating-a-list-view.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como definir uma cadeia de caracteres de formatação para o valor da `StartTime` propriedade.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a>Consulte Também

[Criando uma exibição de lista](./creating-a-list-view.md)

[Elemento ListItem (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Escrevendo um formatação do Windows PowerShell e tipos de arquivo](./writing-a-powershell-formatting-file.md)
