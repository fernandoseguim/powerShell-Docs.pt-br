---
title: Criando uma exibição de tabela | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 832527ea4b042812c39934cd7e124201c6dc2ea4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861492"
---
# <a name="creating-a-table-view"></a>Criar uma exibição de tabela

Uma exibição de tabela exibe dados em uma ou mais colunas. Cada linha na tabela representa um objeto .NET, e cada coluna da tabela representa uma propriedade do objeto ou um valor de script. Você pode definir uma exibição de tabela que exibe todas as propriedades de um objeto ou um subconjunto das propriedades de um objeto.

## <a name="a-table-view-display"></a>Uma exibição do modo de exibição de tabela

O exemplo a seguir mostra como o Windows PowerShell exibe a [ServiceProcess](/dotnet/api/System.ServiceProcess.ServiceController) que é retornado pelo objeto de [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet. Para esse objeto, o Windows PowerShell tenha definido uma exibição de tabela que exibe a `Status` propriedade, o `Name` propriedade (essa propriedade é uma propriedade de alias para o `ServiceName` propriedade) e o `DisplayName` propriedade. Cada linha na tabela representa um objeto retornado pelo cmdlet.

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>Definindo o modo de exibição de tabela

O XML a seguir mostra o esquema de exibição de tabela para exibir o [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objeto. Você deve especificar cada propriedade que você deseja exibir no modo de exibição de tabela.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

Os seguintes elementos XML são usados para definir uma exibição de lista:

- O [exibição](./view-element-format.md) é o elemento pai da exibição de tabela. (Isso é o mesmo elemento pai para a lista de modos de exibição do controle ampla e personalizadas).

- O [nome](./name-element-for-view-format.md) elemento Especifica o nome da exibição. Esse elemento é necessário para todas as exibições.

- O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define os objetos que usam o modo de exibição. Esse elemento é necessário.

- O [GroupBy](./groupby-element-for-view-format.md) elemento (não mostrado neste exemplo) que define quando um novo grupo de objetos é exibido. Um novo grupo é iniciado sempre que o valor de uma propriedade específica ou um script é alterado. Esse elemento é opcional.

- O [controles](./controls-element-for-view-format.md) elemento (não mostrado neste exemplo) define os controles personalizados que são definidos pela exibição de tabela. Controles oferecem uma maneira de especificar como os dados são exibidos. Esse elemento é opcional. Um modo de exibição pode definir seus próprios controles personalizados, ou ele pode usar controles comuns que podem ser usados por qualquer modo de exibição no arquivo de formatação. Para obter mais informações sobre controles personalizados, consulte [criação de controles personalizados](./creating-custom-controls.md).

- O [HideTableHeaders](./hidetableheaders-element-format.md) elemento (não mostrado neste exemplo) Especifica que a tabela não mostrará todos os rótulos na parte superior da tabela. Esse elemento é opcional.

- O [TableControl](./tablecontrol-element-format.md) elemento que define as informações de cabeçalho e linha da tabela. Semelhante a outros modos de exibição, uma exibição de tabela pode exibir os valores das propriedades do objeto ou valores gerados por scripts.

## <a name="defining-column-headers"></a>Definindo cabeçalhos de coluna

1. O [TableHeaders](./tableheaders-element-format.md) elemento e seus elementos filho definem o que é exibido na parte superior da tabela.

2. O [TableColumnHeader](./tablecolumnheader-element-format.md) elemento define o que é exibido na parte superior de uma coluna da tabela. Especifique esses elementos na ordem em que você deseja que os cabeçalhos exibidos.

   Não há nenhum limite para o número desses elementos que você pode usar, mas o número de [TableColumnHeader](./tablecolumnheader-element-format.md) elementos no modo de exibição de tabela devem ser igual ao número de [TableRowEntry](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md) elementos que você usa.

3. O [rótulo](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento Especifica o texto que é exibido. Esse elemento é opcional.

4. O [largura](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento Especifica a largura (em caracteres) da coluna. Esse elemento é opcional.

5. O [alinhamento](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento Especifica como o rótulo é exibido. O rótulo pode ser alinhado à esquerda, para a direita ou centralizado. Esse elemento é opcional.

## <a name="defining-the-table-rows"></a>Definindo as linhas da tabela

Modos de exibição de tabela podem fornecer uma ou mais definições que especificam quais dados são exibidos nas linhas da tabela por meio dos filhos de [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elemento. Observe que você pode especificar várias definições para as linhas da tabela, mas os cabeçalhos de linhas permanece a mesma, independentemente de qual definição de linha é usada. Normalmente, uma tabela terá apenas uma definição.

No exemplo a seguir, a exibição fornece uma única definição que exibe os valores de várias propriedades do [Diagnostics? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) objeto. Uma exibição de tabela pode exibir o valor de uma propriedade ou o valor de um script (não mostrado no exemplo) em suas linhas.

```xml
<TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>

```

Os seguintes elementos XML podem ser usados para fornecer definições para uma linha:

- O [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elemento e seus elementos filho definem o que é exibido nas linhas da tabela.

- O [TableRowEntry](./listentry-element-for-listcontrol-format.md) elemento fornece uma definição de linha. Pelo menos um [TableRowEntry](./listentry-element-for-listcontrol-format.md) é necessária; no entanto, não há nenhum limite máximo ao número de elementos que podem ser adicionados. Na maioria dos casos, um modo de exibição terá apenas uma definição.

- O [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento Especifica os objetos que são exibidos por uma definição específica. Esse elemento é opcional e é necessário somente quando você define vários [TableRowEntry](./listentry-element-for-listcontrol-format.md) elementos que exibem objetos diferentes.

- O [encapsular](./wrap-element-for-tablerowentry-for-tablecontrl-format.md) elemento Especifica que o texto que excede a largura da coluna é exibido na próxima linha. Por padrão, o texto que excede a largura da coluna é truncado.

- O [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) elemento define as propriedades ou os scripts cujos valores são exibidos na linha.

- O [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento define a propriedade ou cujo valor é exibido na coluna da linha do script. Um [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento é necessário para cada coluna da linha. A primeira entrada é exibida na primeira coluna, a segunda entrada na segunda coluna e assim por diante.

- O [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento Especifica a propriedade cujo valor é exibido na linha. Você deve especificar uma propriedade ou um script, mas não é possível especificar ambos.

- O [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento Especifica o script cujo valor é exibido na linha. Você deve especificar um script ou uma propriedade, mas não é possível especificar ambos.

- O [FormatString](./label-element-for-listitem-for-listcontrol-format.md) elemento Especifica um padrão de formato que define como o valor da propriedade ou o script é exibido. Esse elemento é opcional.

- O [alinhamento](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento Especifica como o valor da propriedade ou do script é exibido. O valor pode ser alinhado à esquerda, para a direita ou centralizado. Esse elemento é opcional.

## <a name="defining-the-objects-that-use-the-table-view"></a>Definindo os objetos que usam o modo de exibição de tabela

Há duas maneiras de definir quais objetos .NET usam o modo de exibição de tabela. Você pode usar o [ViewSelectedBy](./viewselectedby-element-format.md) elemento para definir os objetos que podem ser exibidos por todas as definições de exibição, ou você pode usar o [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento para definir quais objetos são exibidos por um definição específica do modo de exibição. Na maioria dos casos, um modo de exibição tem apenas uma definição, para que os objetos são normalmente definidos pelo [ViewSelectedBy](./viewselectedby-element-format.md) elemento.

O exemplo a seguir mostra como definir os objetos exibidos pela exibição de tabela usando o [ViewSelectedBy](./viewselectedby-element-format.md) e [TypeName](./typename-element-for-viewselectedby-format.md) elementos. Não há nenhum limite para o número de [TypeName](./typename-element-for-viewselectedby-format.md) elementos que você pode especificar, e sua ordem não é significativa.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Os seguintes elementos XML podem ser usados para especificar os objetos que são usados pelo modo de exibição de tabela:

- O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define quais objetos são exibidos pela exibição de lista.

- O [TypeName](./typename-element-for-viewselectedby-format.md) elemento Especifica o objeto .NET que é exibido pelo modo de exibição. O nome do tipo .NET totalmente qualificado é necessário. Você deve especificar pelo menos um tipo ou seleção definida para o modo de exibição, mas há um número máximo de elementos que podem ser especificados.

O exemplo a seguir usa o [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementos. Use conjuntos de seleção em que você tem um conjunto de objetos que são exibidos usando várias exibições, como quando você define uma exibição de lista e uma exibição de tabela para os mesmos objetos relacionados. Para obter mais informações sobre como criar um conjunto de seleção, consulte [definindo conjuntos de seleção](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Os seguintes elementos XML podem ser usados para especificar os objetos que são usados pelo modo de exibição de lista:

- O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define quais objetos são exibidos pela exibição de lista.

- O [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento Especifica um conjunto de objetos que podem ser exibidos pela exibição. Você deve especificar pelo menos um conjunto de seleção ou tipo para o modo de exibição, mas há um número máximo de elementos que podem ser especificados.

O exemplo a seguir mostra como definir os objetos exibidos por uma definição específica de exibição de tabela usando o [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento. Usando esse elemento, você pode especificar o nome do tipo .NET do objeto, um conjunto de seleção de objetos ou uma condição de seleção que especifica quando a definição é usada. Para obter mais informações sobre como criar condições de uma seleção, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).

> [!NOTE]
> Ao criar várias definições de exibição de tabela que não é possível especificar cabeçalhos de coluna diferente. Você pode especificar apenas o que é exibido nas linhas da tabela, como quais objetos são exibidos.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

Os seguintes elementos XML podem ser usados para especificar os objetos que são usados por uma definição específica de exibição de lista:

- O [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento define quais objetos são exibidos pela definição.

- O [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) elemento Especifica o objeto .NET que é exibido pela definição. Ao usar esse elemento, o nome do tipo .NET totalmente qualificado é necessário. Você deve especificar pelo menos um tipo, conjunto de seleção ou condição de seleção para a definição, mas há um número máximo de elementos que podem ser especificados.

- O [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) elemento (não mostrado) especifica um conjunto de objetos que podem ser exibidos por essa definição. Você deve especificar pelo menos um tipo, conjunto de seleção ou condição de seleção para a definição, mas há um número máximo de elementos que podem ser especificados.

- O [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (não mostrado) do elemento Especifica uma condição que deve existir para essa definição a ser usado. Você deve especificar pelo menos um tipo, conjunto de seleção ou condição de seleção para a definição, mas há um número máximo de elementos que podem ser especificados. Para obter mais informações sobre como definir as condições de seleção, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).

## <a name="using-format-strings"></a>Usando cadeias de caracteres de formato

Cadeias de caracteres de formatação podem ser adicionadas a uma exibição para definir como os dados são exibidos. O exemplo a seguir mostra como definir uma cadeia de caracteres de formatação para o valor da `StartTime` propriedade.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

Os seguintes elementos XML podem ser usados para especificar um padrão de formato:

- O [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento define a propriedade ou cujo valor é exibido na coluna da linha do script. Um [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento é necessário para cada coluna da linha. A primeira entrada é exibida na primeira coluna, a segunda entrada na segunda coluna e assim por diante.

- O [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento Especifica a propriedade cujo valor é exibido na linha. Você deve especificar uma propriedade ou um script, mas não é possível especificar ambos.

- O [FormatString](./label-element-for-listitem-for-listcontrol-format.md) elemento Especifica um padrão de formato que define como o valor da propriedade ou o script é exibido.

No exemplo a seguir, o `ToString` método é chamado para formatar o valor do script. Scripts podem chamar qualquer método de um objeto. Portanto, se um objeto tem um método, como `ToString`, que tem parâmetros de formatação, o script pode chamar esse método para formatar o valor de saída do script.

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

O seguinte elemento XML pode ser usado para chamar o `ToString` método:

- O [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento define a propriedade ou cujo valor é exibido na coluna da linha do script. Um [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento é necessário para cada coluna da linha. A primeira entrada é exibida na primeira coluna, a segunda entrada na segunda coluna e assim por diante.

- O [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento Especifica o script cujo valor é exibido na linha. Você deve especificar um script ou uma propriedade, mas não é possível especificar ambos.

## <a name="see-also"></a>Consulte Também

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
