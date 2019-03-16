---
title: Elemento EntrySelectedBy para CustomEntry para controles de configuração (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059211"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>Elemento EntrySelectedBy para CustomEntry para Controls para Configuration (formato)

Define os tipos de .NET que usam a definição do controle comum ou a condição que deve existir para esse controle a ser usado. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

Elemento de controles de (formato) do elemento de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para o controle para o elemento de configuração (formato) de CustomEntries para CustomControl para configuração ( Elemento de CustomEntry Format) para CustomControl controles para o elemento de configuração (formato) de EntrySelectedBy para CustomEntry para controles de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `EntrySelectedBy` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para controles de configuração (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Define a condição que deve existir para a definição de controle comum a ser usado.|
|[Elemento SelectionSetName para EntrySelectedBy para controles de configuração (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica um conjunto de tipos do .NET que usam essa definição do controle comum.|
|[Elemento TypeName para EntrySelectedBy para controles de configuração (formato)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica um tipo .NET que usa essa definição do controle comum.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CustomEntry para CustomControl para controles de configuração (formato)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Fornece uma definição do controle comum.|

## <a name="remarks"></a>Comentários

No mínimo, cada definição deve ter pelo menos um tipo .NET, conjunto de seleção ou condição de seleção especificada. Não há nenhum limite máximo ao número de tipos, conjuntos de seleção ou condições de seleção que você pode especificar.

## <a name="see-also"></a>Consulte Também

[Elemento SelectionCondition para EntrySelectedBy para controles de configuração (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Elemento SelectionSetName para EntrySelectedBy para controles de configuração (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento CustomEntry para CustomControl para controles de configuração (formato)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Elemento TypeName para EntrySelectedBy para controles de configuração (formato)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
