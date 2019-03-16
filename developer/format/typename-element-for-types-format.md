---
title: Elemento TypeName para tipos (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057919"
---
# <a name="typename-element-for-types-format"></a>Elemento TypeName para Types (formato)

Especifica o tipo de .NET de um objeto que pertence ao conjunto de seleção.

Tipos de configuração (formato) elemento SelectionSets (formato) SelectionSet elemento (formato) (formato) TypeName do elemento de tipos (formato)

## <a name="syntax"></a>Sintaxe

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `TypeName` elemento. Pelo menos um `TypeName` elemento deve ser incluído no conjunto de seleção.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Tipos de elemento (formato)](./types-element-for-selectionset-format.md)|Define os objetos .NET na seleção definidos.|

## <a name="text-value"></a>Valor de texto

Especifique o nome totalmente qualificado para o tipo .NET.

## <a name="remarks"></a>Comentários

Você pode usar conjuntos de seleção quando você tem um conjunto de objetos relacionados que você deseja referenciar, usando um nome único, como um conjunto de objetos que estão relacionadas por meio da herança. Ao definir seus modos de exibição, você pode especificar o conjunto de objetos usando o nome da seleção definida em vez de listar todos os objetos dentro de cada modo de exibição.

Conjuntos de seleção comuns são especificados por seu nome ao definir os modos de exibição do arquivo de formatação. Nesses casos, o `SelectionSetName` elemento filho do `ViewSelectedBy` elemento para o modo de exibição Especifica o conjunto. No entanto, diferentes entradas de uma exibição também podem especificar um conjunto de seleção se aplica a apenas a entrada do modo de exibição. Para obter mais informações sobre conjuntos de seleção, consulte [definindo define de objetos](./defining-selection-sets.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra um `SelectionSet` elemento que define quatro tipos de .NET.

```
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a>Consulte Também

[Definindo conjuntos de seleção](./defining-selection-sets.md)

[Elemento SelectionSet (formato)](./selectionset-element-format.md)

[Elemento SelectionSets (formato)](./selectionsets-element-format.md)

[Tipos de elemento (formato)](./types-element-for-selectionset-format.md)

[Gravar um arquivo de formatação do Windows PowerShell](./writing-a-powershell-formatting-file.md)
