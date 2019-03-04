---
title: Elemento ViewDefinitions (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862082"
---
# <a name="viewdefinitions-element-format"></a>Elemento ViewDefinitions (formato)

Define os modos de exibição usados para exibir objetos do .NET. Esses modos de exibição podem exibir as propriedades e valores de script de um objeto em um formato de tabela, formato de lista, formato amplo e formato de controle personalizado.

Configuração (formato) ViewDefinitions (formato XML) do elemento

## <a name="syntax"></a>Sintaxe

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `ViewDefinitions` elemento. Não há nenhum limite para o número de exibições que podem ser definidas em um arquivo de formatação, e eles podem ser adicionados em qualquer ordem.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de exibição (formato)](./view-element-format.md)|Define uma exibição que é usada para exibir um ou mais objetos do .NET.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de configuração (formato)](./configuration-element-format.md)|Representa o elemento de nível superior de um arquivo de formatação.|

## <a name="remarks"></a>Comentários

Para obter mais informações sobre os componentes de diferentes tipos de modos de exibição, consulte os tópicos a seguir:

- [Criando uma exibição de tabela](./creating-a-table-view.md)

- [Criando uma exibição de lista](./creating-a-list-view.md)

- [Criando uma exibição ampla](./creating-a-wide-view.md)

- [Controles personalizados](./creating-custom-controls.md)

## <a name="example"></a>Exemplo

Este exemplo mostra um `ViewDefinitions` elemento que contém os elementos pai para uma exibição de tabela e uma exibição de lista.

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a>Consulte Também

[Elemento de configuração (formato)](./configuration-element-format.md)

[Elemento de exibição (formato)](./view-element-format.md)

[Criando uma exibição de tabela](./creating-a-table-view.md)

[Criando uma exibição de lista](./creating-a-list-view.md)

[Criando uma exibição ampla](./creating-a-wide-view.md)

[Controles personalizados](./creating-custom-controls.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
