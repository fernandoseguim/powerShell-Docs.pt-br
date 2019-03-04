---
title: Formato de referência do esquema XML | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac6f7aaa-d0cc-4c7b-a341-85e736174579
caps.latest.revision: 21
ms.openlocfilehash: 4dfe27a5105d82fa18e35f965f92fad16d390a2a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857782"
---
# <a name="format-schema-xml-reference"></a>Referência XML de esquema de formato

Os tópicos nesta seção descrevem os elementos XML usados por formatação Format.ps1xml (arquivos). Arquivos de formatação definem como o objeto .NET é exibido; elas não alteram o próprio objeto.

## <a name="in-this-section"></a>Nesta seção

[Elemento de alinhamento para TableColumnHeader para TableControl (formato)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) define como os dados em um cabeçalho de coluna são exibidos.

[Elemento de alinhamento para TableColumnItem para TableControl (formato)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) define como os dados na linha são exibidos.

[Elemento AutoSize para TableControl (formato)](./autosize-element-for-tablecontrol-format.md) Especifica se o tamanho da coluna e o número de colunas são ajustadas com base no tamanho dos dados.

[Elemento AutoSize para WideControl (formato)](./autosize-element-for-widecontrol-format.md) Especifica se o tamanho da coluna e o número de colunas são ajustadas com base no tamanho dos dados.

[Elemento ColumnNumber para WideControl (formato)](./columnnumber-element-for-widecontrol-format.md) Especifica o número de colunas exibidas no modo de exibição amplo.

[O elemento de configuração (formato)](./configuration-element-format.md) representa o elemento de nível superior do arquivo de formatação.

[Controlar o elemento para controles de configuração (formato)](./control-element-for-controls-for-configuration-format.md) define um controle comum que pode ser usado por todas as exibições do arquivo de formatação e o nome que é usado para fazer referência ao controle.

[Controle elemento controles para exibição (formato)](./control-element-for-controls-for-view-format.md) define um controle que pode ser usado pelo modo de exibição e o nome que é usado para fazer referência ao controle.

[Controla o elemento de configuração (formato)](./controls-element-for-configuration-format.md) define os controles comuns que podem ser usados por todos os modos de exibição do arquivo de formatação.

[Controla o elemento para o modo de exibição (formato)](./controls-element-for-view-format.md) define os controles de exibição podem ser usados por uma exibição específica.

[Elemento CustomControl para controle de configuração (formato)](./customcontrol-element-for-control-for-controls-for-configuration-format.md) define um controle. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento CustomControl para o controle para controles para exibição (formato)](./customcontrol-element-for-control-for-controls-for-view-format.md) define um controle que é usado pela exibição.

[Elemento CustomControl para GroupBy (formato)](./customcontrol-element-for-groupby-format.md) define o controle personalizado que exibe o novo grupo.

[Elemento CustomControl (formato)](./customcontrol-element-for-groupby-format.md) define um formato de controle personalizado para o modo de exibição.

[Elemento CustomControlName para ExpressionBinding para controles de configuração (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md) Especifica o nome de um controle comum. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento CustomControlName para ExpressionBindine controles para exibição (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md) Especifica o nome de um controle comum ou um controle de exibição. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento CustomControlName de GroupBy (formato)](./customcontrolname-element-for-groupby-format.md) Especifica o nome de um controle personalizado que é usado para exibir o novo grupo. Esse elemento é usado durante a definição de uma tabela, a lista, o modo de exibição de controle personalizado ou largos.

[Elemento CustomEntry para CustomControl para controles de configuração (formato)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md) fornece uma definição do controle comum. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento CustomEntry para CustomEntries controles para exibição (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md) fornece uma definição do controle. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento CustomEntry para CustomEntries para exibição (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md) fornece uma definição da exibição de controle personalizado.

[Elemento CustomEntry para CustomControl para GroupBy (formato)](./customentry-element-for-customcontrol-for-groupby-format.md) fornece uma definição do controle. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento CustomEntries para CustomControl para configuração (formato)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md) fornece as definições de um controle comum. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento CustomEntries para CustomControl controles para exibição (formato)](./customentries-element-for-customcontrol-for-controls-for-view-format.md) fornece as definições para o controle. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento CustomEntries para CustomControl para GroupBy (formato)](./customentries-element-for-customcontrol-for-groupby-format.md) fornece as definições para o controle. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento CustomEntries para CustomControl para exibição (formato)](./customentries-element-for-customcontrol-for-view-format.md) fornece as definições do modo de exibição de controle personalizado. O modo de exibição do controle personalizado deve especificar uma ou mais definições.

[Elemento CustomItem para CustomEntry para controles para a configuração](./customitem-element-for-customentry-for-controls-for-configuration-format.md) define quais dados são exibidos pelo controle e como ele é exibido. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento CustomItem para CustomEntry controles para exibição (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md) define quais dados são exibidos pelo controle e como ele é exibido. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento CustomItem para CustomEntry para exibição (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md) define quais dados são exibidos com o modo de exibição do controle personalizado e como ele é exibido. Esse elemento é usado ao definir uma exibição de controle personalizado.

[Elemento CustomItem para CustomEntry para GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md) define quais dados são exibidos com o modo de exibição do controle personalizado e como ele é exibido. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento DefaultSettings (formato)](./defaultsettings-element-format.md) define as configurações comuns que se aplicam a todas as exibições do arquivo de formatação. Configurações comuns incluem a exibição de erros, quebra automática de texto em tabelas, definindo como coleções são expandidas e muito mais.

[Elemento DisplayError (Frmat)](./displayerror-element-format.md) Especifica que a cadeia de caracteres #ERR é exibida quando ocorre um erro exibindo uma parte dos dados.

[Elemento EntrySelectedBy para CustomEntry para controles de configuração (formato)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md) define os tipos de .NET que usam a definição do controle comum ou a condição que deve existir para esse controle a ser usado. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento EntrySelectedBy para CustomEntry controles para exibição (formato)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md) define os tipos de .NET que usam essa definição de controle ou a condição que deve existir para essa definição a ser usado. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento EntrySelectedBy para CustomEntry para exibição (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) define os tipos de .NET que usam essa entrada personalizada ou a condição que deve existir para essa entrada a ser usado.

[Elemento EntrySelectedBy para EnumerableExpansion (formato)](./entryselectedby-element-for-enumerableexpansion-format.md) define os tipos de .NET que usam essa definição ou a condição que deve existir para essa definição a ser usado.

[Elemento EntrySelectedBy para CustomEntry para GroupBy (formato)](./entryselectedby-element-for-customentry-for-groupby-format.md) define os tipos de .NET que usam essa definição de controle ou a condição que deve existir para essa definição a ser usado. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento EntrySelectedBy para ListEntry para ListControl (formato)](./entryselectedby-element-for-listentry-for-listcontrol-format.md) define os tipos de .NET que usam essa definição de exibição de lista ou a condição que deve existir para essa definição a ser usado. Na maioria dos casos, apenas uma definição é necessária para uma exibição de lista. No entanto, você pode fornecer várias definições para o modo de exibição de lista, se você quiser usar a mesma exibição de lista para exibir dados diferentes para objetos diferentes.

[Elemento EntrySelectedBy para TableRowEntry (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) define os tipos de .NET cujos valores de propriedade são exibidos na linha.

[Elemento EntrySelectedBy para WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md) define os tipos de .NET que usam essa definição de exibição ampla ou a condição que deve existir para essa definição a ser usado.

[Elemento EnumerableExpansion (formato)](./enumerableexpansion-element-format.md) define os objetos são expandidos quando eles são exibidos em uma exibição de coleção de .NET como específica.

[Elemento EnumerableExpansions (formato)](./enumerableexpansions-element-format.md) define como os objetos de coleção do .NET são expandidos quando eles são exibidos em uma exibição.

[Elemento EnumerateCollection para ExpressionBinding para controles de configuração (formato)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md) especificado que os elementos das coleções são exibidos pelo controle. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento EnumerateCollection para ExpressionBinding controles para exibição (formato)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md) especificado que os elementos das coleções são exibidos. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento EnumerateCollection para expressão de associação para CustomControl para exibição (formato)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md) Especifica que os elementos das coleções são exibidos. Esse elemento é usado ao definir uma exibição de controle personalizado.

[Elemento EnumerateCollection para ExpressionBinding para GroupBy (formato)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) Especifica que os elementos das coleções são exibidos. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Expanda o elemento (formato)](./expand-element-format.md) Especifica como o objeto de coleção é expandido para esta definição.

[Elemento ExpressionBinding para CustomItem para controles de configuração (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md) define os dados que são exibidos pelo controle. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento ExpressionBinding para CustomItem controles para exibição (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) define os dados que são exibidos pelo controle. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento ExpressionBinding para CustomItem para CustomControl para exibição (formato)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md) define os dados que são exibidos pelo controle. Esse elemento é usado ao definir uma exibição de controle personalizado.

[Elemento ExpressionBinding para CustomItem para GroupBy (formato)](./expressionbinding-element-for-customitem-for-groupby-format.md) define os dados que são exibidos pelo controle. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento FirstLineHanging de quadro para controles de configuração (formato)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) Especifica quantos caracteres, a primeira linha de dados é deslocada para a esquerda. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento FirstLineHanging do quadro de controles de modo de exibição (formato)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) Especifica quantos caracteres, a primeira linha de dados é deslocada para a esquerda. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento FirstLineHanging de quadro para CustomControl para exibição (formato)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) Especifica quantos caracteres, a primeira linha de dados é deslocada para a esquerda. Esse elemento é usado ao definir uma exibição de controle personalizado.

[Elemento FirstLineHanging para quadro de GroupBy (formato)](./firstlinehanging-element-for-frame-for-groupby-format.md) Especifica quantos caracteres, a primeira linha de dados é deslocada para a esquerda. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento FirstLineIndent de quadro para controles de configuração (formato)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) Especifica quantos caracteres, a primeira linha de dados é deslocada para a direita. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento FirstLineIndent do quadro de controles de modo de exibição (formato)](./firstlineindent-element-for-frame-for-controls-for-view-format.md) Especifica quantos caracteres, a primeira linha de dados é deslocada para a direita. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) Especifica quantos caracteres, a primeira linha de dados é deslocada para a direita. Esse elemento é usado ao definir uma exibição de controle personalizado.

[Elemento FirstLineIndent para quadro de GroupBy (formato)](./firstlineindent-element-for-frame-for-groupby-format.md) Especifica quantos caracteres, a primeira linha de dados é deslocada para a direita. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento FormatString para ListItem (formato)](./formatstring-element-for-listitem-for-listcontrol-format.md) Especifica um padrão de formato que define como o valor da propriedade ou o script é exibido.

[Elemento FormatString para TableColumnItem (formato)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md) Especifica um padrão de formato que define como o valor da propriedade ou o script da tabela é exibido.

[Elemento FormatString para WideItem para WideControl (formato)](./formatstring-element-for-wideitem-for-widecontrol-format.md) Especifica um padrão de formato que define como o valor da propriedade ou o script é exibido no modo de exibição.

[Elemento de quadros para CustomItem para controles de configuração (formato)](./frame-element-for-customitem-for-controls-for-configuration-format.md) define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento de quadros para CustomItem controles para exibição (formato)](./frame-element-for-customitem-for-controls-for-view-format.md) define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento de quadro para CustomItem para CustomControl para exibição (formato)](./frame-element-for-customitem-for-customcontrol-for-view-format.md) define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita. Esse elemento é usado ao definir uma exibição de controle personalizado.

[Elemento de quadro para CustomItem para GroupBy (formato)](./frame-element-for-customitem-for-groupby-format.md) define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento GroupBy para exibição (formato)](./groupby-element-for-view-format.md) define como o Windows PowerShell exibe um novo grupo de objetos.

[Elemento HideTableHeaders (formato)](./hidetableheaders-element-format.md) Especifica que os cabeçalhos da tabela não são exibidos.

[Elemento ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md) define a condição que deve existir para esse controle a ser usado. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento ItemSelectionCondition de ExpressionBinding controles para exibição (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md) define a condição que deve existir para esse controle a ser usado. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento ItemSelectionCondition para expressão de associação para CustomControl para exibição (formato)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md) define a condição que deve existir para esse controle a ser usado. Não há nenhum limite para o número de condições de seleção que pode ser especificado para um item de controle. Esse elemento é usado ao definir uma exibição de controle personalizado.

[Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (formato)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md) define a condição que deve existir para esse controle a ser usado. Não há nenhum limite para o número de condições de seleção que pode ser especificado para um item de controle. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento ItemSelectionCondition para ListItem (formato)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) define a condição que deve existir para esse item de lista a ser usado.

[Elemento de rótulo para o item de lista para ListControl(Format)](./label-element-for-listitem-for-listcontrol-format.md) Especifica o rótulo para o valor da propriedade ou o script na linha.

[Elemento de rótulo para GroupBy (formato)](./label-element-for-groupby-format.md) Especifica um rótulo que é exibido quando um novo grupo é encontrado.

[Elemento de rótulo para TableColumnHeader (formato)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) define o rótulo que é exibido na parte superior de uma coluna.

[Elemento LeftIndent de quadro para controles de configuração (formato)](./leftindent-element-for-frame-for-controls-for-configuration-format.md) Especifica quantos caracteres os dados são deslocados da margem esquerda. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento LeftIndent do quadro de controles de modo de exibição (formato)](./leftindent-element-for-frame-for-controls-for-view-format.md) Especifica quantos caracteres os dados são deslocados da margem esquerda. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento LeftIndent de quadro para CustomControl para exibição (formato)](./leftindent-element-for-frame-for-customcontrol-for-view-format.md) Especifica quantos caracteres os dados são deslocados da margem esquerda. Esse elemento é usado ao definir uma exibição de controle personalizado.

[Elemento LeftIndent para quadro de GroupBy (formato)](./leftindent-element-for-frame-for-groupby-format.md) Especifica quantos caracteres os dados são deslocados da margem esquerda. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento ListControl (formato)](./listcontrol-element-format.md) define um formato de lista para o modo de exibição.

[Elemento ListEntry (formato)](./listentry-element-for-listcontrol-format.md) fornece uma definição da exibição de lista.

[Elemento ListEntries (formato)](./listentries-element-for-listcontrol-format.md) define como as linhas da exibição de lista são exibidas.

[Elemento ListItem (formato)](./listitem-element-for-listitems-for-listcontrol-format.md) define a propriedade ou o script cujo valor é exibido em uma linha da exibição de lista.

[Elemento ListItems (formato)](./listitems-element-for-listentry-for-listcontrol-format.md) define as propriedades e os scripts que são exibidos na exibição de lista.

[Nome de elemento para o controle para controles de configuração (formato)](./name-element-for-control-for-controls-for-configuration-format.md) Especifica o nome do controle. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Nome de elemento para SelectionSet (formato)](./name-element-for-selectionset-format.md) Especifica o nome usado para referenciar o conjunto de seleção.

[Nome de elemento para o modo de exibição (formato)](./name-element-for-view-format.md) Especifica o nome que é usado para identificar o modo de exibição.

[Elemento de nova linha para CustomItem para controles de configuração (formato)](./newline-element-for-customitem-for-controls-for-configuration-format.md) adiciona uma linha em branco para a exibição do controle. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento de nova linha para CustomItem controles para exibição (formato)](./newline-element-for-customitem-for-controls-for-view-format.md) adiciona uma linha em branco para a exibição do controle. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento de nova linha para CustomItem para CustomControl para exibição (formato)](./newline-element-for-customitem-for-customcontrol-for-view-format.md) adiciona uma linha em branco para a exibição do controle. Esse elemento é usado ao definir uma exibição de controle personalizado.

[Elemento de nova linha para CustomItem para GroupBy (formato)](./newline-element-for-customitem-for-groupby-format.md) adiciona uma linha em branco para a exibição do controle. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento PropertyName para ExpressionBinding para controles de configuração (formato)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md) Especifica a propriedade cujo valor é exibido pelo controle comum do .NET. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento PropertyName para ExpressionBinding controles para exibição (formato)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md) Especifica a propriedade .NET cujo valor é exibido pelo controle. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento PropertyName para ExpressionBinding para CustomControl para exibição (formato)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md) Especifica a propriedade .NET cujo valor é exibido pelo controle. Esse elemento é usado ao definir uma exibição de controle personalizado

[Elemento PropertyName para ExpressionBinding para GroupBy (formato)](./propertyname-element-for-expressionbinding-for-groupby-format.md) Especifica a propriedade .NET cujo valor é exibido pelo controle. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento PropertyName para GroupBy (formato)](./propertyname-element-for-groupby-format.md) Especifica a propriedade do .NET que inicia um novo grupo sempre que seu valor é alterado.

[Elemento PropertyName para ItemSeclectionCondition para controles de configuração (formato)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) Especifica a propriedade do .NET que dispara a condição. Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição é atendida e o controle é usado. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento PropertyName para ItemSelectionCondition controles para exibição (formato)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) Especifica a propriedade do .NET que dispara a condição. Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição é atendida e o controle é usado. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento PropertyName para ItemSelectionCondition para CustomControl para exibição (formato](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) Especifica a propriedade do .NET que dispara a condição. Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição é atendida e o controle é usado. Esse elemento é usado ao definir uma exibição de controle personalizado.

[Elemento PropertyName para ItemSelectionCondition para GroupBy (formato)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) Especifica a propriedade do .NET que dispara a condição. Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição é atendida e o controle é usado. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento PropertyName para ItemSelectionCondition para ListItem (formato)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md) Especifica a propriedade do .NET que dispara a condição. Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição é atendida e o modo de exibição é usado. Esse elemento é usado ao definir uma exibição de lista.

[Elemento PropertyName para ListItem para ListControl (formato)](./propertyname-element-for-listitem-for-listcontrol-format.md) Especifica a propriedade .NET cujo valor é exibido na lista.

[Elemento PropertyName para SelectionCondition para EntrySelectedBy para ListEntry (formato)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md) Especifica a propriedade do .NET que dispara a condição. Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição for atendida e a entrada é usada. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento PropertyName para SelectionCondition controles para exibição (formato)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md) Especifica a propriedade do .NET que dispara a condição. Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição for atendida e a entrada é usada. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento PropertyName para SelectionCondition para CustomControl para exibição (formato)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md) Especifica a propriedade do .NET que dispara a condição. Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição for atendida e a definição é usada. Esse elemento é usado ao definir uma exibição de controle personalizado.

[Elemento PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Especifica a propriedade do .NET que dispara a condição. Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição for atendida e a definição é usada.

[Elemento PropertyName para SelectionCondition para GroupBy (formato)](./propertyname-element-for-selectioncondition-for-groupby-format.md) Especifica a propriedade do .NET que dispara a condição. Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição for atendida e a definição é usada. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento PropertyName para SelectionCondition para EmtrySelectedBy para ListEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Especifica a propriedade do .NET que dispara a condição. Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição for atendida e a entrada da lista é usada.

[Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md) Especifica a propriedade do .NET que dispara a condição. Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição for atendida e a entrada da tabela é usada.

[Elemento PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) Especifica a propriedade do .NET que dispara a condição. Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição for atendida e a definição é usada.

[Elemento PropertyName para TableColumnItem (formato)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) Especifica a propriedade cujo valor é exibido na coluna da linha.

[Elemento PropertyName para WideItem (formato)](./propertyname-element-for-wideitem-for-widecontrol-format.md) Especifica a propriedade do objeto cujo valor é exibido no modo de exibição amplo.

[Elemento RightIndent de quadro para controles de configuração (formato)](./rightindent-element-for-frame-for-controls-for-configuration-format.md) Especifica quantos caracteres os dados são deslocados da margem direita. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento RightIndent do quadro de controles de modo de exibição (formato)](./rightindent-element-for-frame-for-controls-for-view-format.md) Especifica quantos caracteres os dados são deslocados da margem direita. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md) Especifica quantos caracteres os dados são deslocados da margem direita. Esse elemento é usado ao definir uma exibição de controle personalizado.

[Elemento RightIndent para quadro de GroupBy (formato)](./rightindent-element-for-frame-for-groupby-format.md) Especifica quantos caracteres os dados são deslocados da margem direita. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento ScriptBlock para ExpressionBinding para controles de configuração (formato)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md) Especifica o script cujo valor é exibido pelo controle comum. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento ScriptBlock para ExpressionBinding controles para exibição (formato)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md) Especifica o script cujo valor é exibido pelo controle. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento ScriptBlock para ExpressionBinding para CustomCustomControl para exibição (formato)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md) Especifica o script cujo valor é exibido pelo controle. Esse elemento é usado ao definir uma exibição de controle personalizado.

[Elemento ScriptBlock para ExpressionBinding para GroupBy (formato)](./scriptblock-element-for-expressionbinding-for-groupby-format.md) Especifica o script cujo valor é exibido pelo controle. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento ScriptBlock para GroupBy (formato)](./scriptblock-element-for-groupby-format.md) Especifica o script que inicia um novo grupo sempre que seu valor é alterado.

[Elemento ScriptBlock para ItemSelectionCondition para controles de configuração (formato)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) Especifica o script que dispara a condição. Quando esse script é avaliado para `true`, a condição é atendida e o controle é usado. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento ScriptBlock para ItemSelectionCondition controles para exibição (formato)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) Especifica o script que dispara a condição. Quando esse script é avaliado para `true`, a condição é atendida e o controle é usado. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento ScriptBlock para ItemSelectionCondition para CustomControl para exibição (formato)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) Especifica o script que dispara a condição. Quando esse script é avaliado para `true`, a condição é atendida e o controle é usado. Esse elemento é usado ao definir uma exibição de controle personalizado.

[Elemento ScriptBlock para ItemSelectionCondition para GroupBy (formato)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) Especifica o script que dispara a condição. Quando esse script é avaliado para `true`, a condição é atendida e o controle é usado. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento ScriptBlock para ItemSelectionCondition para ListControl (formato)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) Especifica o script que dispara a condição. Quando esse script é avaliado para `true`, a condição é atendida e o item de lista é usado. Esse elemento é usado ao definir uma exibição de lista.

[Elemento ScriptBlock para ListItem (formato)](./scriptblock-element-for-listitem-for-listcontrol-format.md) Especifica o script cujo valor é exibido na linha da lista.

[Elemento ScriptBlock para SelectionCondition para controles de configuração (formato)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md) Especifica o script que dispara a condição. Quando esse script é avaliado para `true`, a condição for atendida e a definição é usada. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento ScriptBlock para SelectionCondition controles para exibição (formato)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md) Especifica o script que dispara a condição. Quando esse script é avaliado para `true`, a condição for atendida e a definição é usada. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento ScriptBlock para SelectionCondition para CustomControl para exibição (formato)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md) Especifica o script que dispara a condição. Quando esse script é avaliado para `true`, a condição for atendida e a definição é usada. Esse elemento é usado ao definir uma exibição de controle personalizado.

[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Especifica o script que dispara a condição.

[Elemento ScriptBlock para SelectionCondition para GroupBy (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md) Especifica o script que dispara a condição. Quando esse script é avaliado para `true`, a condição for atendida e a definição é usada. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para ListEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Especifica o script que dispara a condição. Quando esse script é avaliado para `true`, a condição for atendida e a entrada da lista é usada.

[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Especifica o bloco de script que dispara a condição. Quando esse script é avaliado para `true`, a condição for atendida e a entrada da tabela é usada.

[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) Especifica o script que dispara a condição. Quando esse script é avaliado para `true`, a condição for atendida e a definição ampla de entrada é usada.

[Elemento ScriptBlock para TableColumnItem (formato)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) Especifica o script cujo valor é exibido na coluna da linha.

[Elemento ScriptBlock para WideItem (formato)](./scriptblock-element-for-wideitem-for-widecontrol-format.md) Especifica o script cujo valor é exibido no modo de exibição amplo.

[Elemento SelectionCondition para EntrySelectedBy para CustomEntry para configuração (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md) define uma condição que deve existir para uma definição de controle comum a ser usado. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento SelectionCondition para EntrySelectedBy controles para exibição (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md) define uma condição que deve existir para a definição de controle a ser usado. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md) define uma condição que deve existir para uma definição de controle a ser usado. Esse elemento é usado ao definir uma exibição de controle personalizado.

[Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md) define a condição que deve existir para expandir os objetos da coleção desta definição.

[Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md) define uma condição que deve existir para uma definição de controle a ser usado. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento SelectionCondition para EntrySelectedBy para ListEntry (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) define a condição que deve existir para usar essa definição da exibição de lista. Não há nenhum limite para o número de condições de seleção que pode ser especificado para uma definição de lista.

[Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md) define a condição que deve existir para usar para esta definição da exibição de tabela. Não há nenhum limite para o número de condições de seleção que pode ser especificado para uma definição de tabela.

[Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) define a condição que deve existir para essa definição a ser usado. Não há nenhum limite para o número de condições de seleção que pode ser especificado para uma definição ampla de entrada.

[Elemento SelectionSet (formato)](./selectionset-element-format.md) define um conjunto de objetos .NET que pode ser referenciado pelo nome do conjunto.

[Elemento SelectionSetName para EntrySelectedBy para controles de configuração (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) Especifica um conjunto de tipos do .NET que usam essa definição do controle. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento SelectionSetName para EntrySelectedBy controles para exibição (formato)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md) Especifica um conjunto de tipos do .NET que usam essa definição do controle. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento SelectionSetName para EntrySelectedBy para CustomEntry (formato)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md) Especifica um conjunto de objetos .NET para a entrada da lista. Não há nenhum limite para o número de conjuntos de seleção que pode ser especificado para uma entrada.

[Elemento SelectionSetName para EntrySelectedBy para EnumerableExpansion (formato)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md) Especifica o conjunto de tipos .NET que são expandidos por essa definição.

[Elemento SelectionSetName para EntrySelectedBy para GroupBy (formato)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md) Especifica um conjunto de objetos .NET para a entrada da lista. Não há nenhum limite para o número de conjuntos de seleção que pode ser especificado para uma entrada. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento SelectionSetName para EntrySelectedBy para ListEntry (formato)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) Especifica um conjunto de objetos .NET para a entrada da lista. Não há nenhum limite para o número de conjuntos de seleção que pode ser especificado para uma entrada.

[Elemento SelectionSetName para EntrySelectedBy para TableRowEntry (formato)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md) Especifica um conjunto de .NET tipos de uso essa entrada da exibição de tabela. Não há nenhum limite para o número de conjuntos de seleção que pode ser especificado para uma entrada.

[Elemento SelectionSetName para EntrySelectedBy para WideEntry (formato)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md) Especifica um conjunto de objetos do .NET para a definição. A definição é usada sempre que um desses objetos é exibido.

[Elemento SelectionSetName para SelectionCondition para controles de configuração (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) Especifica o conjunto de tipos do .NET que disparam a condição. Quando qualquer um dos tipos neste conjunto estiver presente, a condição é atendida e o objeto é exibido usando esse controle. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento SelectionSetName para SelectionCondition controles para exibição (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md) Especifica o conjunto de tipos do .NET que disparam a condição. Quando qualquer um dos tipos neste conjunto estiver presente, a condição é atendida e o objeto é exibido usando o controle. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento EntrySelectedBy para CustomEntry para exibição (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) Especifica o conjunto de tipos do .NET que disparam a condição. Quando qualquer um dos tipos neste conjunto estiver presente, a condição é atendida e o objeto é exibido usando o controle. Esse elemento é usado ao definir uma exibição de controle personalizado.

[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Especifica o conjunto de tipos do .NET que disparam a condição. Quando qualquer um dos tipos neste conjunto estiver presente, a condição for atendida.

[Elemento SelectionSetName para SelectionCondition para GroupBy (formato)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md) Especifica o conjunto de tipos do .NET que disparam a condição. Quando qualquer um dos tipos neste conjunto estiver presente, a condição é atendida e o objeto é exibido usando esse controle. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md) Especifica o conjunto de tipos do .NET que disparam a condição. Quando qualquer um dos tipos neste conjunto estiver presente, a condição é atendida e o objeto é exibido usando essa definição da exibição de lista.

[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Especifica o conjunto de tipos do .NET que disparam a condição. Quando qualquer um dos tipos neste conjunto estiver presente, a condição é atendida e o objeto é exibido usando essa definição da exibição de tabela.

[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) Especifica o conjunto de tipos do .NET que disparam a condição. Quando qualquer um dos tipos neste conjunto estiver presente, a condição é atendida e o objeto é exibido usando esta definição da exibição ampla.

[Elemento SelectionSetName para ViewSelectedBy (formato)](./selectionsetname-element-for-viewselectedby-format.md) Especifica um conjunto de objetos .NET que são exibidos pela exibição.

[Elemento SelectionSets (formato)](./selectionsets-element-format.md) define os conjuntos de objetos .NET que podem ser usados por modos de exibição de formato individuais.

[Elemento ShowError (formato)](./showerror-element-format.md) Especifica que o registro completo de erro é exibido quando ocorre um erro ao exibir uma parte dos dados.

[Elemento TableColumnHeader para TableHeaders para TableControl (formato)](./tablecolumnheader-element-format.md) define o rótulo, a largura da coluna e o alinhamento do rótulo de uma coluna da tabela.

[Elemento TableColumnItem (formato)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) define a propriedade ou cujo valor é exibido na coluna da linha do script.

[Elemento TableColumnItems (formato)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) define as propriedades ou os scripts cujos valores são exibidos na linha.

[Elemento TableControl (formato)](./tablecontrol-element-format.md) define um formato de tabela para um modo de exibição.

[Elemento TableHeaders (formato)](./tableheaders-element-format.md) define os cabeçalhos para as colunas de uma tabela.

[Elemento TableRowEntries (formato)](./tablerowentries-element-for-tablecontrol-format.md) define as linhas da tabela.

[Elemento TableRowEntry (formato)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md) define os dados que são exibidos em uma linha da tabela.

[Elemento de texto para CustomItem para controles de configuração (formato)](./text-element-for-customitem-for-controls-for-configuration-format.md) Especifica texto que é adicionado aos dados que são exibidos pelo controle, como um rótulo, colchetes para colocar os dados e espaços para recuar os dados. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento de texto para CustomItem controles para exibição (formato)](./text-element-for-customitem-for-controls-for-view-format.md) Especifica texto que é adicionado aos dados que são exibidos pelo controle, como um rótulo, colchetes para colocar os dados e espaços para recuar os dados. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento de texto para CustomItem (formato)](./text-element-for-customitem-for-customview-for-view-format.md) Especifica texto que é adicionado aos dados que são exibidos pelo controle, como um rótulo, colchetes para colocar os dados e espaços para recuar os dados. Esse elemento é usado ao definir uma exibição de controle personalizado.

[Elemento de texto para CustomItem para GroupBy (formato)](./text-element-for-customitem-for-groupby-format.md) Especifica texto que é adicionado aos dados que são exibidos pelo controle, como um rótulo, colchetes para colocar os dados e espaços para recuar os dados. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento TypeName para EntrySelectedBy para controles de configuração (formato)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md) Especifica um tipo .NET que usa essa definição do controle. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento TypeName para EntrySelectedBy controles para exibição (formato)](./typename-element-for-entryselectedby-for-controls-for-view-format.md) Especifica um tipo .NET que usa essa definição do controle. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento TypeName para EntrySelectedBy para CustomEntry para exibição (formato)](./typename-element-for-entryselectedby-for-customentry-for-view-format.md) Especifica um tipo .NET que usa essa definição da exibição de controle personalizado. Não há nenhum limite para o número de tipos que podem ser especificados para uma definição.

[Elemento TypeName para EntrySelectedBy para EnumerableExpansion (formato)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md) Especifica um tipo .NET que é expandido por essa definição. Esse elemento é usado ao definir uma configuração padrão.

[Elemento TypeName para EntrySelectedBy para GroupBy (formato)](./typename-element-for-entryselectedby-for-groupby-format.md) Especifica um tipo .NET que usa essa definição do controle personalizado. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento TypeName para EntrySelectedBy para ListControl (formato)](./typename-element-for-entryselectedby-for-listcontrol-format.md) Especifica um tipo .NET que usa essa entrada da exibição de lista. Não há nenhum limite para o número de tipos que podem ser especificados para uma entrada da lista.

[Elemento TypeName para EntrySelectedBy para TableRowEntry (formato)](./typename-element-for-entryselectedby-for-tablecontrol-format.md) Especifica um tipo .NET que usa essa entrada da exibição de tabela. Não há nenhum limite para o número de tipos que podem ser especificados para uma entrada de tabela.

[Elemento TypeName para EntrySelectedBy para WideEntry (formato)](./typename-element-for-entryselectedby-for-wideentry-format.md) Especifica um tipo .NET para a definição. A definição é usada sempre que esse objeto é exibido.

[Elemento TypeName para SelectionCondition para controles de configuração (formato)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md) Especifica um tipo .NET que dispara a condição. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

[Elemento TypeName para SelectionCondition controles para exibição (formato)](./typename-element-for-selectioncondition-for-controls-for-view-format.md) Especifica um tipo .NET que dispara a condição. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

[Elemento TypeName para SelectionCondition para CustomControl para exibição (formato)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md) Especifica um tipo .NET que dispara a condição. Esse elemento é usado ao definir uma exibição de controle personalizado.

[Elemento TypeName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Especifica um tipo .NET que dispara a condição.

[Elemento TypeName para SelectionCondition para GroupBy (formato)](./typename-element-for-selectioncondition-for-groupby-format.md) Especifica um tipo .NET que dispara a condição. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

[Elemento TypeName para SelectionCondition para EntrySelectedBy para ListControl (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Especifica um tipo .NET que dispara a condição. Quando esse tipo estiver presente, a entrada da lista é usada.

[Elemento TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Especifica um tipo .NET que dispara a condição. Quando esse tipo estiver presente, a condição for atendida, e a linha da tabela é usada.

[Elemento TypeName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) Especifica um tipo .NET que dispara a condição. Quando esse tipo estiver presente, a definição é usada.

[Elemento TypeName para tipos (formato)](./typename-element-for-types-format.md) Especifica o tipo de .NET de um objeto que pertence ao conjunto de seleção.

[Elemento TypeName para ViewSelectedBy (formato)](./typename-element-for-viewselectedby-format.md) Especifica um objeto .NET que é exibido pelo modo de exibição.

[Tipos de elemento (formato)](./types-element-for-selectionset-format.md) define os objetos .NET na seleção definidos.

[Exibir o elemento (formato)](./view-element-format.md) define uma exibição que é usada para exibir um ou mais objetos do .NET.

[Elemento ViewDefinitions (formato)](./viewdefinitions-element-format.md) define os modos de exibição usados para exibir os objetos.

[Elemento ViewSelectedBy (formato)](./viewselectedby-element-format.md) define os objetos do .NET que são exibidos pela exibição.

[Elemento WideControl (formato)](./widecontrol-element-format.md) define uma lista de todos (único valor) de formato para o modo de exibição. Essa exibição mostra um valor de propriedade única ou script para cada objeto.

[Elemento WideEntries (formato)](./wideentries-element-for-widecontrol-format.md) fornece as definições do modo de exibição ampla. O modo de exibição amplo deve especificar uma ou mais definições.

[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md) fornece uma definição da exibição ampla.

[Elemento WideItem (formato)](./wideitem-element-for-widecontrol-format.md) define a propriedade ou o script cujo valor é exibido.

[Elemento width (formato)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) define a largura (em caracteres) de uma coluna.

[Encapsular o elemento (formato)](./wrap-element-for-tablerowentry-for-tablecontrl-format.md) Especifica que o texto que excede a largura da coluna é exibido na próxima linha.

[Elemento WrapTables (formato)](./wraptables-element-format.md) Especifica que os dados em uma célula de tabela são movidos para a próxima linha se os dados for maiores que a largura da coluna.

## <a name="see-also"></a>Consulte Também

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
