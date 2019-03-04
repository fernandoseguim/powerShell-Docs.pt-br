---
title: Criando uma exibição de lista | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861572"
---
# <a name="creating-a-list-view"></a>Criar uma exibição de lista

Uma exibição de lista exibe dados em uma única coluna (em ordem sequencial). Os dados exibidos na lista podem ser o valor de uma propriedade do .NET ou o valor de um script.

## <a name="a-list-view-display"></a>Exibir uma exibição de lista

A saída a seguir mostra como o Windows PowerShell exibe as propriedades de [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos que são retornados pela [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet. Neste exemplo, três objetos foram retornados, com cada objeto separado do objeto anterior por uma linha em branco.

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a>Definindo o modo de exibição de lista

O XML a seguir mostra o esquema de exibição de lista para exibir várias propriedades do [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objeto. Você deve especificar cada propriedade que você deseja exibir na exibição de lista.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

Os seguintes elementos XML são usados para definir uma exibição de lista:

- O [exibição](./view-element-format.md) é o elemento pai da exibição de lista. (Isso é o mesmo elemento pai para a tabela, exibições de controle de largura e personalizadas).

- O [nome](./name-element-for-view-format.md) elemento Especifica o nome da exibição. Esse elemento é necessário para todas as exibições.

- O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define os objetos que usam o modo de exibição. Esse elemento é necessário.

- O [GroupBy](./groupby-element-for-view-format.md) elemento define quando um novo grupo de objetos é exibido. Um novo grupo é iniciado sempre que o valor de uma propriedade específica ou um script é alterado. Esse elemento é opcional.

- O [controles](./controls-element-for-view-format.md) elemento define os controles personalizados que são definidos pela exibição de lista. Controles oferecem uma maneira de especificar como os dados são exibidos. Esse elemento é opcional. Um modo de exibição pode definir seus próprios controles personalizados, ou ele pode usar controles comuns que podem ser usados por qualquer modo de exibição no arquivo de formatação. Para obter mais informações sobre controles personalizados, consulte [criação de controles personalizados](./creating-custom-controls.md).

- O [ListControl](./listcontrol-element-format.md) elemento define o que é exibido no modo de exibição e como ele é formatado. Semelhante a outros modos de exibição, uma exibição de lista pode exibir os valores das propriedades do objeto ou valores gerados pelo script.

Para obter um exemplo de um arquivo de formatação completo que define uma exibição de lista simples, consulte [modo de exibição de lista (Basic)](./list-view-basic.md).

## <a name="providing-definitions-for-your-list-view"></a>Fornece definições para o modo de exibição de lista

Exibições de lista podem fornecer uma ou mais definições usando os elementos filho do [ListControl](./listcontrol-element-format.md) elemento. Normalmente, um modo de exibição terá apenas uma definição. No exemplo a seguir, a exibição fornece uma única definição que exibe várias propriedades do [Diagnostics? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) objeto. Uma exibição de lista pode exibir o valor de uma propriedade ou o valor de um script (não mostrado no exemplo).

```xml
<ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

Os seguintes elementos XML podem ser usados para fornecer definições para uma exibição de lista:

- O [ListControl](./listcontrol-element-format.md) elemento e seus elementos filho definem o que é exibido no modo de exibição.

- O [ListEntries](./listentries-element-for-listcontrol-format.md) elemento fornece as definições do modo de exibição. Na maioria dos casos, um modo de exibição terá apenas uma definição. Esse elemento é necessário.

- O [ListEntry](./listentry-element-for-listcontrol-format.md) elemento fornece uma definição da exibição. Pelo menos um [ListEntry](./listentry-element-for-listcontrol-format.md) é necessária; no entanto, não há nenhum limite máximo ao número de elementos que podem ser adicionados. Na maioria dos casos, um modo de exibição terá apenas uma definição.

- O [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento Especifica os objetos que são exibidos por uma definição específica. Esse elemento é opcional e é necessário somente quando você define vários [ListEntry](./listentry-element-for-listcontrol-format.md) elementos que exibem objetos diferentes.

- O [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) elemento Especifica as propriedades e os scripts cujos valores são exibidos nas linhas da exibição de lista.

- O [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) elemento Especifica uma propriedade ou um script cujo valor é exibido em uma linha da exibição de lista. Uma exibição de lista deve especificar pelo menos uma propriedade ou script. Não há nenhum limite máximo ao número de linhas que podem ser especificados.

- O [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento Especifica a propriedade cujo valor é exibido na linha. Você deve especificar uma propriedade ou um script, mas não é possível especificar ambos.

- O [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento Especifica o script cujo valor é exibido na linha. Você deve especificar um script ou uma propriedade, mas não é possível especificar ambos.

- O [rótulo](./label-element-for-listitem-for-listcontrol-format.md) elemento Especifica o rótulo que é exibido à esquerda do valor de propriedade ou o script na linha. Esse elemento é opcional. Se um rótulo não for especificado, o nome da propriedade ou o script é exibido. Para obter um exemplo completo, consulte [modo de exibição de lista (rótulos)](./list-view-labels.md).

- O [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) elemento Especifica uma condição que deve existir para a linha a ser exibido. Para obter mais informações sobre como adicionar condições à exibição de lista, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md). Esse elemento é opcional.

- O [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) elemento Especifica um padrão que é usado para exibir o valor da propriedade ou do script. Esse elemento é opcional.

Para obter um exemplo de um arquivo de formatação completo que define uma exibição de lista simples, consulte [modo de exibição de lista (Basic)](./list-view-basic.md).

## <a name="defining-the-objects-that-use-the-list-view"></a>Definindo os objetos que usam o modo de exibição de lista

Há duas maneiras de definir quais objetos .NET usam o modo de exibição de lista. Você pode usar o [ViewSelectedBy](./viewselectedby-element-format.md) elemento para definir os objetos que podem ser exibidos por todas as definições de exibição, ou você pode usar o [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento para definir quais objetos são exibidos por um definição específica do modo de exibição. Na maioria dos casos, um modo de exibição tem apenas uma definição, para que os objetos são normalmente definidos pelo [ViewSelectedBy](./viewselectedby-element-format.md) elemento.

O exemplo a seguir mostra como definir os objetos que são exibidos pelo modo de exibição de lista usando o [ViewSelectedBy](./viewselectedby-element-format.md) e [TypeName](./typename-element-for-viewselectedby-format.md) elementos. Não há nenhum limite para o número de [TypeName](./typename-element-for-viewselectedby-format.md) elementos que você pode especificar, e sua ordem não é significativa.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Os seguintes elementos XML podem ser usados para especificar os objetos que são usados pelo modo de exibição de lista:

- O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define quais objetos são exibidos pela exibição de lista.

- O [TypeName](./typename-element-for-viewselectedby-format.md) elemento Especifica o objeto .NET que é exibido pelo modo de exibição. O nome do tipo .NET totalmente qualificado é necessário. Você deve especificar pelo menos um tipo ou seleção definida para o modo de exibição, mas há um número máximo de elementos que podem ser especificados.

Para obter um exemplo de um arquivo de formatação completo, consulte [modo de exibição de lista (Basic)](./list-view-basic.md).

O exemplo a seguir usa o [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementos. Use conjuntos de seleção em que você tem um conjunto de objetos que são exibidos usando várias exibições, como quando você define uma exibição de lista e uma exibição de tabela para os mesmos objetos relacionados. Para obter mais informações sobre como criar um conjunto de seleção, consulte [definindo conjuntos de seleção](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Os seguintes elementos XML podem ser usados para especificar os objetos que são usados pelo modo de exibição de lista:

- O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define quais objetos são exibidos pela exibição de lista.

- O [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento Especifica um conjunto de objetos que podem ser exibidos pela exibição. Você deve especificar pelo menos um conjunto de seleção ou tipo para o modo de exibição, mas há um número máximo de elementos que podem ser especificados.

O exemplo a seguir mostra como definir os objetos exibidos por uma definição específica de exibição de lista usando o [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento. Usando esse elemento, você pode especificar o nome do tipo .NET do objeto, um conjunto de seleção de objetos ou uma condição de seleção que especifica quando a definição é usada. Para obter mais informações sobre como criar condições de uma seleção, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

Os seguintes elementos XML podem ser usados para especificar os objetos que são usados por uma definição específica de exibição de lista:

- O [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento define quais objetos são exibidos pela definição.

- O [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) elemento Especifica o objeto .NET que é exibido pela definição. Ao usar esse elemento, o nome do tipo .NET totalmente qualificado é necessário. Você deve especificar pelo menos um tipo, conjunto de seleção ou condição de seleção para a definição, mas há um número máximo de elementos que podem ser especificados.

- O [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) elemento (não mostrado) especifica um conjunto de objetos que podem ser exibidos por essa definição. Você deve especificar pelo menos um tipo, conjunto de seleção ou condição de seleção para a definição, mas há um número máximo de elementos que podem ser especificados.

- O [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (não mostrado) do elemento Especifica uma condição que deve existir para essa definição a ser usado. Você deve especificar pelo menos um tipo, conjunto de seleção ou condição de seleção para a definição, mas há um número máximo de elementos que podem ser especificados. Para obter mais informações sobre como definir as condições de seleção, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-list-view"></a>Exibir grupos de objetos em uma exibição de lista

Você pode separar os objetos que são exibidos pela exibição de lista em grupos. Isso não significa que você defina um grupo, somente se o Windows PowerShell inicia um novo grupo sempre que o valor de uma propriedade específica ou um script é alterado. No exemplo a seguir, um novo grupo é iniciado sempre que o valor de [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) alterações de propriedade.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Os seguintes elementos XML são usados para definir quando um grupo é iniciado:

- O [GroupBy](./groupby-element-for-view-format.md) elemento define a propriedade ou o script que inicia o novo grupo e a define como o grupo é exibido.

- O [PropertyName](./propertyname-element-for-groupby-format.md) elemento Especifica a propriedade que inicia um novo grupo sempre que seu valor é alterado. Você deve especificar uma propriedade ou um script para iniciar o grupo, mas não é possível especificar ambos.

- O [ScriptBlock](./scriptblock-element-for-groupby-format.md) elemento Especifica o script que inicia um novo grupo sempre que seu valor é alterado. Você deve especificar um script ou uma propriedade para iniciar o grupo, mas não é possível especificar ambos.

- O [rótulo](./label-element-for-groupby-format.md) elemento define um rótulo que é exibido no início de cada grupo. Além do texto especificado por esse elemento, o Windows PowerShell exibe o valor que disparou o novo grupo e adiciona uma linha em branco antes e depois do rótulo. Esse elemento é opcional.

- O [CustomControl](./customcontrol-element-for-groupby-format.md) elemento define um controle que é usado para exibir os dados. Esse elemento é opcional.

- O [CustomControlName](./customcontrolname-element-for-groupby-format.md) elemento Especifica um comum ou controle que é usado para exibir os dados de exibição. Esse elemento é opcional.

Para obter um exemplo de um arquivo de formatação completo que define grupos, consulte [modo de exibição de lista (GroupBy)](./list-view-groupby.md).

## <a name="using-format-strings"></a>Usando cadeias de caracteres de formato

Cadeias de caracteres de formatação podem ser adicionadas a uma exibição para definir como os dados são exibidos. O exemplo a seguir mostra como definir uma cadeia de caracteres de formatação para o valor da `StartTime` propriedade.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

Os seguintes elementos XML podem ser usados para especificar um padrão de formato:

- O [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento Especifica os dados que são exibidos pelo modo de exibição.

- O [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento Especifica a propriedade cujo valor é exibido pelo modo de exibição. Você deve especificar uma propriedade ou um script, mas não é possível especificar ambos.

- O [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) elemento Especifica um padrão de formato que define como o valor da propriedade ou o script é exibido no modo de exibição.

- O [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento (não mostrado) Especifica o script cujo valor é exibido pelo modo de exibição. Você deve especificar um script ou uma propriedade, mas não é possível especificar ambos.

No exemplo a seguir, o `ToString` método é chamado para formatar o valor do script. Scripts podem chamar qualquer método de um objeto. Portanto, se um objeto tem um método, como `ToString`, que tem parâmetros de formatação, o script pode chamar esse método para formatar o valor de saída do script.

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

O seguinte elemento XML pode ser usado para chamar o `ToString` método:

- O [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento Especifica os dados que são exibidos pelo modo de exibição.

- O [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento (não mostrado) Especifica o script cujo valor é exibido pelo modo de exibição. Você deve especificar um script ou uma propriedade, mas não é possível especificar ambos.

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
