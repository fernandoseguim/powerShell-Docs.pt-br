---
title: Visão geral do arquivo de formatação | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863292"
---
# <a name="formatting-file-overview"></a>Visão geral do arquivo de formatação

O formato de exibição para os objetos que são retornados pelos comandos (cmdlets, funções e scripts) são definidas usando arquivos de formatação (format.ps1xml arquivos). Vários desses arquivos são fornecidos pelo PowerShell para definir o formato de exibição para os objetos retornados por comandos fornecidos pelo PowerShell, como o [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto retornado pelo `Get-Process` cmdlet. No entanto, você também pode criar seus próprios arquivos de formatação personalizados para substituir os formatos de exibição padrão, ou você pode escrever um arquivo de formatação personalizado para definir a exibição de objetos retornados pelos seus próprios comandos.

> [!IMPORTANT]
> Arquivos de formatação não determinam os elementos de um objeto que são retornados para o pipeline. Quando um objeto é retornado para o pipeline, todos os membros desse objeto estão disponíveis, mesmo se alguns não são exibidos.

PowerShell usa os dados nesses arquivos de formatação para determinar o que é exibido e como os dados exibidos são formatados. Os dados exibidos podem incluir as propriedades de um objeto ou o valor de um script. Scripts são usados se você quiser exibir algum valor que não está disponível diretamente das propriedades de um objeto, como a adição do valor de duas propriedades de um objeto e, em seguida, exibindo a soma como uma parte dos dados. Formatação dos dados exibidos é feita com a definição de modos de exibição para os objetos que você deseja exibir. Você pode definir uma exibição única para cada objeto, você pode definir uma exibição única para vários objetos, ou você pode definir vários modos de exibição para o mesmo objeto. Não há nenhum limite para o número de modos de exibição que você pode definir.

## <a name="common-features-of-formatting-files"></a>Recursos comuns de arquivos de formatação

Cada arquivo de formatação pode definir os seguintes componentes que podem ser compartilhados entre todas as exibições definidas pelo arquivo:

- O padrão de definição de configuração, como se os dados exibidos nas linhas das tabelas serão exibidos na próxima linha se os dados são maiores que a largura da coluna. Para obter mais informações sobre essas configurações, consulte [definindo as configurações comuns](./defining-common-configuration-features.md).

- Conjuntos de objetos que podem ser exibidos por qualquer um dos modos de exibição do arquivo de formatação. Para obter mais informações sobre esses conjuntos (conhecido como *conjuntos de seleção*), consulte [definindo define de objetos](./defining-selection-sets.md).

- Controles comuns que podem ser usados por todas as exibições do arquivo de formatação. Controles oferecem maior controle sobre como os dados são exibidos. Para obter mais informações sobre controles, consulte [definindo Custom Controls](./creating-custom-controls.md).

## <a name="formatting-views"></a>As exibições de formatação

Formatação de modos de exibição podem exibir objetos em um formato de tabela, o formato de lista, o formato amplo e o formato personalizado. Geralmente, cada definição de formatação é descrita por um conjunto de marcas XML que descrevem o modo de exibição. Cada modo de exibição contém o nome da exibição, os objetos que usam o modo de exibição e os elementos da exibição, como as informações de linha e coluna para uma exibição de tabela.

Modo de exibição lista as propriedades de um objeto ou um valor de bloco de script em uma ou mais colunas da tabela. Cada coluna representa uma única propriedade do objeto ou um valor de script. Você pode definir uma exibição de tabela que exibe todas as propriedades de um objeto, um subconjunto das propriedades de um objeto ou uma combinação de propriedades e valores de script. Cada linha da tabela representa um objeto retornado. Criar uma exibição de tabela é muito semelhante a quando você direciona um objeto para o `Format-Table` cmdlet. Para obter mais informações sobre este modo de exibição, consulte [exibição de tabela](./creating-a-table-view.md).

Liste o modo de exibição lista as propriedades de um objeto ou um valor de script em uma única coluna. Cada linha da lista exibe um rótulo opcional ou o nome da propriedade seguido pelo valor da propriedade ou do script. Criar uma exibição de lista é muito semelhante ao canalizar um objeto para o `Format-List` cmdlet. Para obter mais informações sobre este modo de exibição, consulte [exibição de lista](./creating-a-list-view.md).

Exibição ampla com a lista de uma única propriedade de um objeto ou um valor de script em uma ou mais colunas. Não há nenhum rótulo ou o cabeçalho para este modo de exibição. Criar uma exibição ampla é muito semelhante ao canalizar um objeto para o `Format-Wide` cmdlet. Para obter mais informações sobre este modo de exibição, consulte [exibição ampla](./creating-a-wide-view.md).

Exibição personalizada mostra uma exibição personalizável de propriedades do objeto ou valores de script que não seguem a estrutura rígida de modos de exibição de tabela, exibições de lista ou exibições amplas. Você pode definir uma exibição personalizada autônoma, ou você pode definir uma exibição personalizada que é usada por outro modo de exibição, como uma exibição de tabela ou exibição de lista. Criar um modo de exibição personalizado é muito semelhante ao canalizar um objeto para o `Format-Custom` cmdlet. Para obter mais informações sobre este modo de exibição, consulte [modo de exibição personalizado](./creating-custom-controls.md).

## <a name="components-of-a-view"></a>Componentes de uma exibição

Os exemplos XML a seguir mostram os componentes básicos do XML de uma exibição. Os elementos XML individuais variam, dependendo de qual modo você deseja criar, mas os componentes básicos dos modos de exibição são todas iguais.

Para começar, cada exibição tem um `Name` elemento que especifica um nome de usuário amigável que é usado para referenciar o modo de exibição. uma `ViewSelectedBy` elemento que define quais objetos .NET são exibidos pelo modo de exibição, e uma *controle* elemento que define o modo de exibição.

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

Dentro do elemento de controle, você pode definir um ou mais *entrada* elementos. Se você usar várias definições, você deve especificar quais objetos .NET usam cada definição. Normalmente, apenas uma entrada, com apenas uma definição, é necessário para cada controle.

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

Dentro de cada elemento de entrada de uma exibição, você deve especificar o *item* elementos que definem as propriedades .NET ou scripts que são exibidos pela exibição.

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

Conforme mostrado nos exemplos anteriores, o arquivo de formatação pode conter vários modos de exibição, um modo de exibição pode conter várias definições e cada definição pode conter vários itens.

## <a name="example-of-a-table-view"></a>Exemplo de uma exibição de tabela

O exemplo a seguir mostra as marcas XML usadas para definir uma exibição de tabela que contém duas colunas. O [ViewDefinitions](./viewdefinitions-element-format.md) é o elemento de contêiner para todas as exibições definidas no arquivo de formatação. O [exibição](./view-element-format.md) elemento define a tabela específica, a lista, o modo de exibição amplo ou personalizado. Dentro de cada [modo de exibição](./view-element-format.md) elemento, o [nome](./name-element-for-view-format.md) elemento Especifica o nome da exibição, o [ViewSelectedBy](./viewselectedby-element-format.md) elemento define os objetos que usam o modo de exibição e os diferentes elementos de controle (como o `TableControl` elemento mostrado no exemplo a seguir) definem o tipo de exibição.

```xml
<ViewDefinitions>
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

[Criando uma exibição de lista](./creating-a-list-view.md)

[Criando uma exibição de tabela](./creating-a-table-view.md)

[Criando uma exibição ampla](./creating-a-wide-view.md)

[Criação de controles personalizados](./creating-custom-controls.md)

[Escrevendo uma formatação de PowerShell e tipos de arquivo](./writing-a-powershell-formatting-file.md)
