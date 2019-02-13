---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso Service de DSC
ms.openlocfilehash: 09571bd0eaa428e7d0bb7a533d6ad1c0c936e2cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676412"
---
# <a name="dsc-service-resource"></a>Recurso Service de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0


O recurso **Service** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para gerenciar serviços no nó de destino.

## <a name="syntax"></a>Sintaxe

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| Nome| Indica o nome do serviço. Observe que, às vezes, é diferente do nome de exibição. É possível obter uma lista dos serviços e seus estados atuais com o cmdlet Get-Service.|
| BuiltInAccount| Indica a conta de entrada que deve ser usada para o serviço. Os valores permitidos para essa propriedade são: **LocalService**, **LocalSystem**, e **NetworkService**.|
| Credential| Indica as credenciais para a conta em que o serviço será executado. Essa propriedade e a propriedade __BuiltinAccount__ não podem ser usadas juntas.|
| DependsOn| Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.|
| StartupType| Indica o tipo de inicialização para o serviço. Os valores permitidos para essa propriedade são: **Automática**, **desabilitado**, e **Manual**|
| Estado| Indica o estado que você deseja garantir para o serviço.|
| Descrição | Indica a descrição do serviço de destino.|
| DisplayName | Indica o nome de exibição do serviço de destino.|
| Ensure | Indica se o serviço de destino existe no sistema. Defina essa propriedade como **Ausente** para garantir que o serviço de destino não exista. Configurá-la como **Present** (o valor padrão) garante que o grupo exista.|
| Caminho | Indica o caminho para o arquivo binário para um novo serviço.|

## <a name="example"></a>Exemplo

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```