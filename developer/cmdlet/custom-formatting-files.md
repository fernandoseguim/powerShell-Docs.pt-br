---
title: Arquivos de formatação personalizada | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860602"
---
# <a name="custom-formatting-files"></a>Arquivos de formatação personalizada

O formato de exibição para os objetos retornados pelo cmdlets, funções e scripts são definidas usando arquivos de formatação (format.ps1xml arquivos). Vários desses arquivos são fornecidos pelo Windows PowerShell para definir o formato de exibição padrão para os objetos retornados pelos cmdlets do Windows PowerShell. No entanto, você também pode criar seus próprios arquivos de formatação personalizados para substituir os formatos de exibição padrão ou para definir a exibição de objetos retornados pelos seus próprios comandos.

Windows PowerShell usa os dados nesses arquivos de formatação para determinar o que é exibido e como os dados são formatados. Os dados exibidos podem incluir as propriedades de um objeto ou o valor de um bloco de script.  Blocos de script são usados se você quiser exibir algum valor que não está disponível diretamente das propriedades de um objeto. Por exemplo, você talvez queira adicionar o valor de duas propriedades de um objeto e exibir a soma como uma parte separada dos dados. Quando você escreve sua própria formatação de arquivo, você precisará definir *modos de exibição* para os objetos que você deseja exibir. Você pode definir uma exibição única para cada objeto, você pode definir uma exibição única para vários objetos, ou você pode definir vários modos de exibição para o mesmo objeto. Não há nenhum limite para o número de modos de exibição que você pode definir.

> [!IMPORTANT]
> Arquivos de formatação não determinam os elementos de um objeto que são retornados para o pipeline. Quando um objeto é retornado para o pipeline, todos os membros desse objeto estão disponíveis.

## <a name="format-views"></a>Modos de exibição de formato

Formatação de modos de exibição podem exibir objetos em um formato de tabela, um formato de lista, um formato amplo e um formato personalizado. Geralmente, cada definição de formatação é descrita por um conjunto de marcas XML que descrevem um modo de exibição. Cada modo de exibição contém o nome da exibição, os objetos que usam o modo de exibição e os elementos da exibição, como as informações de linha e coluna para uma exibição de tabela.

As exibições a seguir estão disponíveis.

Exibição de tabela lista as propriedades de um objeto ou um valor de bloco de script em uma ou mais colunas. Cada coluna representa uma propriedade do objeto ou um valor de bloco de script. Você pode definir uma exibição de tabela que exibe todas as propriedades de um objeto, um subconjunto das propriedades de um objeto ou uma combinação de propriedades e valores de bloco de script. Cada linha da tabela representa um objeto retornado. Para obter mais informações sobre este modo de exibição, consulte [exibição de tabela](../format/creating-a-table-view.md).

Exibição de lista lista as propriedades de um objeto ou um valor de bloco de script em uma única coluna. Cada linha da lista exibe o nome da propriedade seguido pelo valor do bloco de script ou de propriedade ou um rótulo opcional. Para obter mais informações sobre este modo de exibição, consulte [exibição de lista](../format/creating-a-list-view.md).

Exibição ampla com a lista de uma única propriedade de um objeto ou um valor de bloco de script em uma ou mais colunas. Não há nenhum rótulo ou o cabeçalho para este modo de exibição. Para obter mais informações sobre este modo de exibição, consulte [exibição ampla](../format/creating-a-wide-view.md).

Exibição personalizada mostra uma exibição personalizável de propriedades do objeto ou valores de bloco de script que não seguem a estrutura rígida de modos de exibição de tabela, exibições de lista ou exibições amplas. Você pode definir uma exibição personalizada de autônomo, ou você pode definir uma exibição personalizada que é usada por outro modo de exibição, como uma exibição de tabela ou exibição de lista. Para obter mais informações sobre este modo de exibição, consulte [modo de exibição personalizado](../format/creating-custom-controls.md).

## <a name="view-xml-elements"></a>Elementos XML de modo de exibição

O exemplo a seguir mostra as marcas XML usadas para definir uma exibição de tabela que contém duas colunas. O [ViewDefinitions](../format/viewdefinitions-element-format.md) é o elemento de contêiner para todas as exibições definidas no arquivo de formatação. O [exibição](../format/view-element-format.md) elemento define a tabela específica, a lista, o modo de exibição amplo ou personalizado. Dentro de cada exibição, o [nome](../format/name-element-for-view-format.md) elemento Especifica o nome da exibição, o [ViewSelectedBy](../format/viewselectedby-element-format.md) elemento define os objetos que usam o modo de exibição e os elementos de controle diferentes (como o `TableControl` elemento) definem o formato da exibição.

```xml
ViewDefinitions
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>Consulte Também

[Exibição de tabela](../format/creating-a-table-view.md)

[Exibição de lista](../format/creating-a-list-view.md)

[Exibição ampla](../format/creating-a-wide-view.md)

[Modo de exibição personalizado](../format/creating-custom-controls.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
