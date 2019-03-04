---
title: Elemento PropertyName para WideItem para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860952"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>Elemento PropertyName para WideItem para WideControl (formato)

Especifica a propriedade do objeto cujo valor é exibido no modo de exibição amplo.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) elemento WideItem (formato) PropertyName elemento de configuração para WideItem (formato)

## <a name="syntax"></a>Sintaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `PropertyName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento WideItem (formato)](./wideitem-element-for-widecontrol-format.md)|Define a propriedade ou cujo valor é exibido no modo de exibição amplo de script.|

## <a name="text-value"></a>Valor de texto

Especifique o nome da propriedade cujo valor é exibido.

## <a name="remarks"></a>Comentários

Para obter mais informações sobre os componentes de uma exibição ampla, consulte [criando uma exibição ampla](./creating-a-wide-view.md).

## <a name="example"></a>Exemplo

Este exemplo mostra uma exibição ampla que exibe o valor da propriedade ProcessName do [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a>Consulte Também

[Elemento WideItem (formato)](./wideitem-element-for-widecontrol-format.md)

[Criando uma exibição ampla](./creating-a-wide-view.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
