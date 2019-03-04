---
title: Elemento CustomEntries para CustomControl controles para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861802"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>Elemento CustomEntries para CustomControl para Controls para View (formato)

Fornece as definições para o controle. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento controles elemento (formato) controle elemento de configuração para controles para exibição (formato) CustomControl elemento de controle para controles para elemento CustomEntries de exibição (formato) CustomControl controles para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai do `CustomEntries` elemento. Não há nenhum limite máximo ao número de elementos filho que podem ser especificados.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CustomEntry para CustomEntries controles para exibição (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Elemento necessário.<br /><br /> Fornece uma definição do controle.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CustomControl para o controle para controles para exibição (formato)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Define o controle usado pela exibição.|

## <a name="remarks"></a>Comentários

Na maioria dos casos, um controle tem apenas uma definição, que é especificada em um único `CustomEntry` elemento. No entanto, é possível fornecer várias definições, se você quiser usar o mesmo controle para exibir objetos diferentes do .NET. Nesses casos, você pode definir um `CustomEntry` elemento para cada objeto ou conjunto de objetos.

## <a name="see-also"></a>Consulte Também

[Elemento CustomEntry para CustomEntries controles para exibição (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Elemento CustomControl para o controle para controles para exibição (formato)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
