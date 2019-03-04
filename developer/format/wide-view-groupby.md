---
title: Exibição ampla (GroupBy) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861622"
---
# <a name="wide-view-groupby"></a>Exibição ampla (GroupBy)

Este exemplo mostra como implementar uma exibição ampla que exibe os grupos de [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos retornados pelo `Get-Service` cmdlet. Para obter mais informações sobre os componentes de uma exibição ampla, consulte [criando uma exibição ampla](./creating-a-wide-view.md).

### <a name="to-load-this-formatting-file"></a>Para carregar este arquivo de formatação

1. Copie o XML da seção do exemplo deste tópico para um arquivo de texto.

2. Salve o arquivo de texto. Certifique-se de adicionar o `format.ps1xml` extensão para o arquivo de para identificá-lo como um arquivo de formatação.

3. Abra o Windows PowerShell e execute o seguinte comando para carregar o arquivo de formatação para a sessão atual: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Esse arquivo de formatação define a exibição de um objeto que já está definido por um arquivos de formatação do Windows PowerShell. Você deve usar o `prependPath` parâmetro quando você executar o cmdlet, e você não pode carregar essa formatação de arquivo como um módulo.

## <a name="demonstrates"></a>Demonstra

Esse arquivo de formatação demonstra os seguintes elementos XML:

- O [nome](./name-element-for-view-format.md) elemento para o modo de exibição.

- O [ViewSelectedBy](./viewselectedby-element-format.md) elemento que define quais objetos são exibidos pela exibição.

- O [GroupBy](./groupby-element-for-view-format.md) elemento que define quando um novo grupo é exibido.

- O [WideItem](./wideitem-element-for-widecontrol-format.md) elemento que define a propriedade que é exibida pelo modo de exibição.

## <a name="example"></a>Exemplo

O XML a seguir define uma exibição ampla que exibe os grupos de objetos. Cada novo grupo é iniciado quando o valor de [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) alterações de propriedade.

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <Label>Service Type</Label>
        <PropertyName>ServiceType</PropertyName>
      </GroupBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

O exemplo a seguir mostra como o Windows PowerShell exibe o [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos depois que esse arquivo de formato é carregado.

```powershell
Get-Service f*
```

```output
   Service Type: Win32OwnProcess

Fax                             FCSAM

   Service Type: Win32ShareProcess

fdPHost                         FDResPub
FontCache

   Service Type: Win32OwnProcess

FontCache3.0.0.0                FSysAgent
FwcAgent
```

## <a name="see-also"></a>Consulte Também

[Exemplos de arquivos de formatação](./examples-of-formatting-files.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
