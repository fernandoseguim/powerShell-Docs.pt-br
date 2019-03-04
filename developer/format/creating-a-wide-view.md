---
title: Criando uma exibição ampla com | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858492"
---
# <a name="creating-a-wide-view"></a>Criar uma exibição ampla

Uma exibição ampla exibe um único valor para cada objeto que é exibido. O valor exibido pode ser o valor de uma propriedade de objeto do .NET ou o valor de um script. Por padrão, não há nenhum rótulo ou o cabeçalho para este modo de exibição.

## <a name="a-wide-view-display"></a>Uma exibição ampla com a exibição

O exemplo a seguir mostra como o Windows PowerShell exibe o [Diagnostics](/dotnet/api/System.Diagnostics.Process) que é retornado pelo objeto de [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet quando sua saída é canalizada para o [ Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet. (Por padrão, o [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet retorna uma exibição de tabela.) Neste exemplo, as duas colunas são usadas para exibir o nome do processo para cada objeto retornado. O nome da propriedade do objeto não for exibido, apenas o valor da propriedade.

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a>Definindo o modo de exibição amplo

O XML a seguir mostra o esquema de exibição ampla para a [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

Os seguintes elementos XML são usados para definir uma exibição ampla com:

- O [exibição](./view-element-format.md) é o elemento pai do modo de exibição ampla. (Isso é o mesmo elemento pai para a tabela, lista e modos de exibição do controle personalizado.)

- O [nome](./name-element-for-view-format.md) elemento Especifica o nome da exibição. Esse elemento é necessário para todas as exibições.

- O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define os objetos que usam o modo de exibição. Esse elemento é necessário.

- O [GroupBy](./groupby-element-for-view-format.md) elemento define quando um novo grupo de objetos é exibido. Um novo grupo é iniciado sempre que o valor de uma propriedade específica ou um script é alterado. Esse elemento é opcional.

- O [controles](./controls-element-for-view-format.md) elementos define os controles personalizados que são definidos pela exibição ampla. Controles oferecem uma maneira de especificar como os dados são exibidos. Esse elemento é opcional. Um modo de exibição pode definir seus próprios controles personalizados, ou ele pode usar controles comuns que podem ser usados por qualquer modo de exibição no arquivo de formatação. Para obter mais informações sobre controles personalizados, consulte [criação de controles personalizados](./creating-custom-controls.md).

- O [WideControl](./widecontrol-element-format.md) elemento e seus elementos filho definem o que é exibido no modo de exibição. No exemplo anterior, o modo de exibição é projetado para exibir o [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) propriedade.

Para obter um exemplo de um arquivo de formatação completo que define uma simple exibição ampla, consulte [exibição ampla (Basic)](./wide-view-basic.md).

## <a name="providing-definitions-for-your-wide-view"></a>Fornece definições para o modo de exibição ampla

Modos de exibição amplos podem fornecer uma ou mais definições usando os elementos filho do [WideControl](./widecontrol-element-format.md) elemento. Normalmente, um modo de exibição terá apenas uma definição. No exemplo a seguir, a exibição fornece uma única definição que exibe o valor de [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) propriedade. Uma exibição ampla com a pode exibir o valor de uma propriedade ou o valor de um script (não mostrado no exemplo).

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

Os seguintes elementos XML podem ser usados para fornecer definições para uma exibição ampla com:

- O [WideControl](./widecontrol-element-format.md) elemento e seus elementos filho definem o que é exibido no modo de exibição.

- O [AutoSize](./autosize-element-for-widecontrol-format.md) elemento Especifica se o tamanho da coluna e o número de colunas são ajustados com base no tamanho dos dados. Esse elemento é opcional.

- O [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) elemento Especifica o número de colunas exibidas no modo de exibição amplo. Esse elemento é opcional.

- O [WideEntries](./wideentries-element-for-widecontrol-format.md) elemento fornece as definições do modo de exibição. Na maioria dos casos, um modo de exibição terá apenas uma definição. Esse elemento é necessário.

- O [WideEntry](./wideentry-element-for-widecontrol-format.md) elemento fornece uma definição da exibição. Pelo menos um [WideEntry](./wideentry-element-for-widecontrol-format.md) é necessária; no entanto, não há nenhum limite máximo ao número de elementos que podem ser adicionados. Na maioria dos casos, um modo de exibição terá apenas uma definição.

- O [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento Especifica os objetos que são exibidos por uma definição específica. Esse elemento é opcional e é necessário somente quando você define vários [WideEntry](./wideentry-element-for-widecontrol-format.md) elementos que exibem objetos diferentes.

- O [WideItem](./wideitem-element-for-widecontrol-format.md) elemento Especifica os dados que são exibidos pelo modo de exibição. Em contraste com outros tipos de modos de exibição, um grande controle pode exibir apenas um item.

- O [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) elemento Especifica a propriedade cujo valor é exibido pelo modo de exibição. Você deve especificar uma propriedade ou um script, mas não é possível especificar ambos.

- O [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento Especifica o script cujo valor é exibido pelo modo de exibição. Você deve especificar um script ou uma propriedade, mas não é possível especificar ambos.

- O [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) elemento Especifica um padrão que é usado para exibir os dados. Esse elemento é opcional.

Para obter um exemplo de um arquivo de formatação completo que define uma definição de exibição ampla, consulte [exibição ampla (Basic)](./wide-view-basic.md).

## <a name="defining-the-objects-that-use-the-wide-view"></a>Definindo os objetos que usam o modo de exibição amplo

Há duas maneiras de definir quais objetos .NET usam o modo de exibição amplo. Você pode usar o [ViewSelectedBy](./viewselectedby-element-format.md) elemento para definir os objetos que podem ser exibidos por todas as definições de exibição, ou você pode usar o [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento para definir quais objetos são exibidos por um definição específica do modo de exibição. Na maioria dos casos, um modo de exibição tem apenas uma definição, para que os objetos são normalmente definidos pelo [ViewSelectedBy](./viewselectedby-element-format.md) elemento.

O exemplo a seguir mostra como definir os objetos que são exibidos usando a exibição ampla com a [ViewSelectedBy](./viewselectedby-element-format.md) e [TypeName](./typename-element-for-viewselectedby-format.md) elementos. Não há nenhum limite para o número de [TypeName](./typename-element-for-viewselectedby-format.md) elementos que você pode especificar, e sua ordem não é significativa.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Os seguintes elementos XML podem ser usados para especificar os objetos que são usados pela exibição ampla:

- O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define quais objetos são exibidos pela exibição ampla.

- O [TypeName](./typename-element-for-viewselectedby-format.md) elemento Especifica o .NET que é exibido pelo modo de exibição. O nome do tipo .NET totalmente qualificado é necessário. Você deve especificar pelo menos um tipo ou seleção definida para o modo de exibição, mas há um número máximo de elementos que podem ser especificados.

Para obter um exemplo de um arquivo de formatação completo, consulte [exibição ampla (Basic)](./wide-view-basic.md).

O exemplo a seguir usa o [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementos. Use conjuntos de seleção em que você tem um conjunto de objetos que são exibidos usando várias exibições, como quando você define uma exibição ampla e uma exibição de tabela para os mesmos objetos relacionados. Para obter mais informações sobre como criar um conjunto de seleção, consulte [definindo conjuntos de seleção](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Os seguintes elementos XML podem ser usados para especificar os objetos que são usados pela exibição ampla:

- O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define quais objetos são exibidos pela exibição ampla.

- O [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento Especifica um conjunto de objetos que podem ser exibidos pela exibição. Você deve especificar pelo menos um conjunto de seleção ou tipo para o modo de exibição, mas há um número máximo de elementos que podem ser especificados.

O exemplo a seguir mostra como definir os objetos exibidos por uma definição específica de exibição ampla usando o [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento. Usando esse elemento, você pode especificar o nome do tipo .NET do objeto, um conjunto de seleção de objetos ou uma condição de seleção que especifica quando a definição é usada. Para obter mais informações sobre como criar condições de uma seleção, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

Os seguintes elementos XML podem ser usados para especificar os objetos que são usados por uma definição específica do modo de exibição ampla:

- O [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento define quais objetos são exibidos pela definição.

- O [TypeName](./typename-element-for-viewselectedby-format.md) .NET que é exibido pela definição do elemento especifica. Ao usar esse elemento, o nome do tipo .NET totalmente qualificado é necessário. Você deve especificar pelo menos um tipo, conjunto de seleção ou condição de seleção para a definição, mas há um número máximo de elementos que podem ser especificados.

- O [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento (não mostrado) especifica um conjunto de objetos que podem ser exibidos por essa definição. Você deve especificar pelo menos um tipo, conjunto de seleção ou condição de seleção para a definição, mas há um número máximo de elementos que podem ser especificados.

- O [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) (não mostrado) do elemento Especifica uma condição que deve existir para essa definição a ser usado. Você deve especificar pelo menos um tipo, conjunto de seleção ou condição de seleção para a definição, mas há um número máximo de elementos que podem ser especificados. Para obter mais informações sobre como definir as condições de seleção, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>Exibir grupos de objetos em uma exibição ampla

Você pode separar os objetos que são exibidos pela exibição ampla em grupos. Isso não significa que você defina um grupo, somente se o Windows PowerShell inicia um novo grupo sempre que o valor de uma propriedade específica ou um script é alterado. No exemplo a seguir, um novo grupo é iniciado sempre que o valor de [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) alterações de propriedade.

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

Para obter um exemplo de um arquivo de formatação completo que define grupos, consulte [exibição ampla (GroupBy)](./wide-view-groupby.md).

## <a name="using-format-strings"></a>Usando cadeias de caracteres de formato

Cadeias de caracteres de formatação podem ser adicionadas a uma exibição ampla para definir como os dados são exibidos. O exemplo a seguir mostra como definir uma cadeia de caracteres de formatação para o valor da `StartTime` propriedade.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

Os seguintes elementos XML podem ser usados para especificar um padrão de formato:

- O [WideItem](./wideitem-element-for-widecontrol-format.md) elemento Especifica os dados que são exibidos pelo modo de exibição.

- O [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) elemento Especifica a propriedade cujo valor é exibido pelo modo de exibição. Você deve especificar uma propriedade ou um script, mas não é possível especificar ambos.

- O [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) elemento Especifica um padrão de formato que define como o valor da propriedade ou o script é exibido no modo de exibição

- O [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento (não mostrado) Especifica o script cujo valor é exibido pelo modo de exibição. Você deve especificar um script ou uma propriedade, mas não é possível especificar ambos.

No exemplo a seguir, o `ToString` método é chamado para formatar o valor do script. Scripts podem chamar qualquer método de um objeto. Portanto, se um objeto tem um método, como `ToString`, que tem parâmetros de formatação, o script pode chamar esse método para formatar o valor de saída do script.

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

O seguinte elemento XML pode ser usado para chamar o `ToString` método:

- O [WideItem](./wideitem-element-for-widecontrol-format.md) elemento Especifica os dados que são exibidos pelo modo de exibição.

- O [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento (não mostrado) Especifica o script cujo valor é exibido pelo modo de exibição. Você deve especificar um script ou uma propriedade, mas não é possível especificar ambos.

## <a name="see-also"></a>Consulte Também

[Exibição ampla (Basic)](./wide-view-basic.md)

[Exibição ampla (GroupBy)](./wide-view-groupby.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
