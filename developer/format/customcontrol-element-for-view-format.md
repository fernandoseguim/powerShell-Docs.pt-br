---
title: Elemento CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861252"
---
# <a name="customcontrol-element-for-view-format"></a>Elemento CustomControl para View (formato)

Define um formato de controle personalizado para o modo de exibição.

Configuração (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento CustomControl elemento (formato)

## <a name="syntax"></a>Sintaxe

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `CustomControl` elemento. Você deve especificar um elemento filho.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CustomEntries para CustomControl para exibição (formato)](./customentries-element-for-customcontrol-for-view-format.md)|Elemento necessário.<br /><br /> Fornece as definições do modo de exibição de controle personalizado.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de exibição (formato)](./view-element-format.md)|Define uma exibição que é usada para exibir um ou mais objetos do .NET.|

## <a name="remarks"></a>Comentários

Na maioria dos casos, somente uma definição, é necessária para cada modo de exibição de controle, mas é possível fornecer várias definições, se você quiser usar a mesma exibição para exibir objetos diferentes do .NET. Nesses casos, você pode fornecer uma definição separada para cada objeto ou conjunto de objetos.

## <a name="see-also"></a>Consulte Também

[Elemento CustomEntries para CustomControl para exibição (formato)](./customentries-element-for-customcontrol-for-view-format.md)

[Elemento de exibição (formato)](./view-element-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
