---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso do ServiceSet DSC
ms.openlocfilehash: 5694c2abc5c0caf0098670b629af464b35125583
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047000"
---
# <a name="dsc-serviceset-resource"></a>Recurso do ServiceSet DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso **ServiceSet** na DSC (Configuração de Estado Desejado) do Windows PowerShell oferece um mecanismo para gerenciar serviços no nó de destino. Esse recurso é um [recurso composto](../../../resources/authoringResourceComposite.md) que chama o [Recurso de serviço](serviceResource.md) para cada serviço especificado na propriedade `Name`.

Use esse recurso quando desejar configurar vários serviços para o mesmo estado.

## <a name="syntax"></a>Sintaxe

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| Nome| Indica os nomes do serviço. Observe que, às vezes, isso é diferente dos nomes de exibição. É possível obter uma lista dos serviços e seus estados atuais com o cmdlet [Get-Service](https://technet.microsoft.com/library/hh849804.aspx).|
| StartupType| Indica o tipo de inicialização para o serviço. Os valores permitidos para essa propriedade são: **Automática**, **desabilitado**, e **Manual**|
| BuiltInAccount| Indica a conta de credenciais a ser usada para os serviços. Os valores permitidos para essa propriedade são: **LocalService**, **LocalSystem**, e **NetworkService**.|
| Estado| Indica o estado que você deseja garantir para o serviço. **Interrompido** ou **executando**.|
| Ensure| Indica se os serviços existem no sistema. Defina essa propriedade como **Ausente** para garantir que os serviços não existam. Configurá-la como **Present** (o valor padrão) garantirá que os serviços de destino existam.|
| Credential| Indica as credenciais para a conta sob a qual o serviço será executado. Essa propriedade e a propriedade **BuiltinAccount** não podem ser usadas juntas.|
| DependsOn| Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for *ResourceName* e seu tipo for *ResourceType*, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.|



## <a name="example"></a>Exemplo

A configuração a seguir inicia os serviços "Áudio do Windows" e "Serviços de Área de Trabalho Remota".

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```
