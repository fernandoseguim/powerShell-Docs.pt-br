---
title: O elemento de configuração (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856322"
---
# <a name="configuration-element-format"></a>Elemento Configuration (formato)

Representa o elemento de nível superior de um arquivo de formatação.

Elemento de configuração

## <a name="syntax"></a>Sintaxe

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `Configuration` elemento. Esse elemento deve ser o elemento raiz para cada arquivo de formatação, e esse elemento deve conter pelo menos um elemento filho.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de controles para configuração (formato)](./controls-element-for-configuration-format.md)|Elemento opcional.<br /><br /> Define os controles comuns que podem ser usados por todos os modos de exibição do arquivo de formatação.|
|[Elemento DefaultSettings (formato)](./defaultsettings-element-format.md)|Elemento opcional.<br /><br /> Define as configurações comuns que se aplicam a todas as exibições do arquivo de formatação.|
|[Formato do elemento SelectionSets](./selectionsets-element-format.md)|Elemento opcional.<br /><br /> Define os conjuntos de objetos .NET que podem ser usados por todos os modos de exibição do arquivo de formatação comuns.|
|[Elemento ViewDefinitions (formato)](./viewdefinitions-element-format.md)|Elemento opcional.<br /><br /> Define os modos de exibição usados para exibir os objetos.|

### <a name="parent-elements"></a>Elementos pais

Nenhum.

## <a name="remarks"></a>Comentários

Arquivos de formatação definem como os objetos são exibidos. Na maioria dos casos, esse elemento de raiz contém uma [ViewDefinitions](./viewdefinitions-element-format.md) elemento que define a tabela, lista e modos de exibição amplos do arquivo de formatação. Além das definições de exibição, o arquivo de formatação pode definir conjuntos de seleção, configurações e controles que essas exibições podem usar comuns.

## <a name="see-also"></a>Consulte Também

[Elemento de controles para configuração (formato)](./controls-element-for-configuration-format.md)

[Elemento DefaultSettings (formato)](./defaultsettings-element-format.md)

[Elemento SelectionSets (formato)](./selectionsets-element-format.md)

[Elemento ViewDefinitions (formato)](./viewdefinitions-element-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
