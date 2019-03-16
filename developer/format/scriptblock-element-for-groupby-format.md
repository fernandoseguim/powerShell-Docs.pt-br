---
title: Elemento ScriptBlock para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: f2f6b9af7740b1231881294c2f32bf97b5a1568b
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054418"
---
# <a name="scriptblock-element-for-groupby-format"></a>Elemento ScriptBlock para GroupBy (formato)

Especifica o script que inicia um novo grupo sempre que seu valor é alterado.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento GroupBy elemento de configuração para o modo de exibição (formato) ScriptBlock elemento GroupBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `ScriptBlock` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento GroupBy para exibição (formato)](./groupby-element-for-view-format.md)|Define como um grupo de objetos do .NET é exibido.|

## <a name="text-value"></a>Valor de texto

Especifique o script que é avaliado.

## <a name="remarks"></a>Comentários

Windows PowerShell inicia um novo grupo sempre que o valor desse script é alterado.

Quando esse elemento for especificado, é possível especificar o [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) elemento para iniciar um novo grupo.

## <a name="see-also"></a>Consulte Também

[Elemento PropertyName para GroupBy (formato)](./propertyname-element-for-groupby-format.md)

[Elemento GroupBy para exibição (formato)](./groupby-element-for-view-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
