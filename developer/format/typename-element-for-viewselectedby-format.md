---
title: Elemento TypeName para ViewSelectedBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857892"
---
# <a name="typename-element-for-viewselectedby-format"></a>Elemento TypeName para ViewSelectedBy (formato)

Especifica um objeto .NET que é exibido pelo modo de exibição.

Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento ViewSelectedBy (formato) TypeName do elemento de configuração para ViewSelectedBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e os elementos pai do `TypeName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento ViewSelectedBy (formato)](./viewselectedby-element-format.md)|Define os objetos do .NET que são exibidos pela exibição.|

## <a name="text-value"></a>Valor de texto

Especifique o nome totalmente qualificado do tipo .NET, como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Comentários

Para obter mais informações sobre como esse elemento é usado em diferentes modos de exibição, consulte [criando uma exibição de tabela](./creating-a-table-view.md), [criando um modo de exibição de lista](./creating-a-list-view.md), [criando uma exibição ampla](./creating-a-wide-view.md), e [ Componentes de exibição personalizado](./creating-custom-controls.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como especificar o [ServiceProcess](/dotnet/api/System.ServiceProcess.ServiceController) objeto para uma exibição de lista. O mesmo esquema é usado para exibições de tabela, ampla e personalizadas.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Consulte Também

[Criando uma exibição de lista](./creating-a-list-view.md)

[Criando uma exibição de tabela](./creating-a-table-view.md)

[Criando uma exibição ampla](./creating-a-wide-view.md)

[Criação de controles personalizados](./creating-custom-controls.md)

[Elemento ViewSelectedBy (formato)](./viewselectedby-element-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
