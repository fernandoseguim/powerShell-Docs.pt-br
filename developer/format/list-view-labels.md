---
title: (Rótulos) de exibição de lista | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 2bb62ab3e4fa1db9b3af8c82eb9035aa4f3e31c0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860122"
---
# <a name="list-view-labels"></a>Exibição de lista (rótulos)

Este exemplo mostra como implementar uma exibição de lista que exibe um rótulo personalizado para cada linha da lista. Este modo de exibição de lista exibe as propriedades do [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) que é retornado pelo objeto de [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet. Para obter mais informações sobre os componentes de uma exibição de lista, consulte [criando uma exibição de lista](./creating-a-list-view.md).
Este exemplo mostra como implementar uma exibição de lista que exibe um rótulo personalizado para cada linha da lista. Este modo de exibição de lista exibe as propriedades do [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) que é retornado pelo objeto de [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet. Para obter mais informações sobre os componentes de uma exibição de lista, consulte [criando uma exibição de lista](./creating-a-list-view.md).

### <a name="to-load-this-formatting-file"></a>Para carregar este arquivo de formatação

1. Copie o XML da seção do exemplo deste tópico para um arquivo de texto.

2. Salve o arquivo de texto. Certifique-se de adicionar o `format.ps1xml` extensão para o arquivo de para identificá-lo como um arquivo de formatação.

3. Abra o Windows PowerShell e execute o seguinte comando para carregar o arquivo de formatação para a sessão atual: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Esse arquivo de formatação define a exibição de um objeto que já está definido por um arquivo de formatação do Windows PowerShell. Você deve usar o `prependPath` parâmetro quando você executar o cmdlet, e você não pode carregar essa formatação de arquivo como um módulo.

## <a name="demonstrates"></a>Demonstra

Esse arquivo de formatação demonstra os seguintes elementos XML:

- O [nome](./name-element-for-view-format.md) elemento para o modo de exibição.

- O [ViewSelectedBy](./viewselectedby-element-format.md) elemento que define quais objetos são exibidos pela exibição.

- O [ListControl](./listcontrol-element-format.md) elemento que define a propriedade que é exibida pelo modo de exibição.

- O [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento que define o que é exibido em uma linha da exibição de lista.

- O [rótulo](./label-element-for-listitem-for-listcontrol-format.md) elemento que define o que é exibido em uma linha da exibição de lista.

- O [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento que define qual propriedade é exibida.

## <a name="example"></a>Exemplo

O XML a seguir define uma exibição de lista que exibe um rótulo personalizado em cada linha. Nesse caso, o rótulo inclui o nome da propriedade com cada letra maiuscula e a palavra "propriedade". Em cada linha, o nome da propriedade é exibido seguido pelo valor da propriedade.

```xml
<Configuration>
  <ViewDefinitions>
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
            <Label>NAME property</Label>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <Label>DISPLAYNAME property</Label>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <Label>STATUS property</Label>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <Label>SERVICETYPE property</Label>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>

  </ViewDefinitions>
</Configuration>
```

O exemplo a seguir mostra como o Windows PowerShell exibe o [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos depois que esse arquivo de formato é carregado.

```powershell
Get-Service f*
```

```output
NAME property        : Fax
DISPLAYNAME property : Fax
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FCSAM
DISPLAYNAME property : Microsoft Antimalware Service
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : fdPHost
DISPLAYNAME property : Function Discovery Provider Host
STATUS property      : Stopped
SERVICETYPE property : Win32ShareProcess

NAME property        : FDResPub
DISPLAYNAME property : Function Discovery Resource Publication
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache
DISPLAYNAME property : Windows Font Cache Service
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache3.0.0.0
DISPLAYNAME property : Windows Presentation Foundation Font Cache 3.0.0.0
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FSysAgent
DISPLAYNAME property : Microsoft Forefront System Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : FwcAgent
DISPLAYNAME property : Firewall Client Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess
```

## <a name="see-also"></a>Consulte Também

[Exemplos de arquivos de formatação](./examples-of-formatting-files.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
