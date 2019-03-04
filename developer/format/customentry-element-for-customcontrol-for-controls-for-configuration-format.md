---
title: Elemento CustomEntry para CustomControl para controles de configuração (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859802"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>Elemento CustomEntry para CustomControl para Controls para Configuration (formato)

Fornece uma definição do controle comum. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

Elemento de controles de (formato) do elemento de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para o controle para o elemento de configuração (formato) de CustomEntries para CustomControl para configuração ( Elemento de CustomEntry Format) para CustomControl para controles de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `CustomEntry` elemento. Você deve especificar os itens exibidos pela definição.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento EntrySelectedBy para CustomEntry para controles de configuração (formato)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Define os tipos de .NET que usam a definição do controle comum ou a condição que deve existir para esse controle a ser usado.|
|[Elemento CustomItem para CustomEntry para controles de configuração](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Elemento necessário.<br /><br /> Define quais dados são exibidos pelo controle e como ele é exibido.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CustomEntries para CustomControl para configuração (formato)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|Fornece as definições do controle comum.|

## <a name="remarks"></a>Comentários

Na maioria dos casos, apenas uma definição é necessária para cada controle personalizado comum, mas é possível ter várias definições, se você quiser usar o mesmo controle para exibir objetos diferentes do .NET. Nesses casos, você pode fornecer uma definição separada para cada objeto ou conjunto de objetos.

## <a name="see-also"></a>Consulte Também

[Elemento CustomEntries para CustomControl para configuração (formato)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[Elemento CustomItem para CustomEntry para controles de configuração](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
