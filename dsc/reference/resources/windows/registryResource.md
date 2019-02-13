---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso Registry de DSC
ms.openlocfilehash: e0ae1a4a27edc08c4e6ccd47786426917eb1ccb4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676342"
---
# <a name="dsc-registry-resource"></a>Recurso Registry de DSC

_Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0_

O recurso **Registry** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para gerenciar chaves e valores do registro em um nó de destino.

## <a name="syntax"></a>Sintaxe

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a>Propriedades

| Propriedade | Descrição |
| --- | --- |
| Chave| Indica o caminho da chave do Registro para o qual você deseja garantir um estado específico. Esse caminho deve incluir o hive.|
| ValueName| Indica o nome do valor de registro. Para adicionar ou remover uma chave do Registro, especifique essa propriedade como uma cadeia de caracteres vazia sem especificar ValueType ou ValueData. Para modificar ou remover o valor padrão de uma chave do Registro, especifica essa propriedade como uma cadeia de caracteres vazia e também especifique ValueType ou ValueData.|
| Ensure| Indica se a chave e o valor existem. Para garantir que existam, defina essa propriedade como "Present". Para garantir que não existam, defina a propriedade como "Absent". O valor padrão é "Present".|
| Force| Se a chave do Registro especificada estiver presente, **Force** a substituirá pelo novo valor. Para excluir uma chave do Registro com subchaves, isso deve ser **$true** |
| Hex| Indica se os dados serão expressos em formato hexadecimal. Se especificado, os dados do valor DWORD/QWORD são apresentados em formato hexadecimal. Não é válido para outros tipos. O valor padrão é **$false**.|
| DependsOn| Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.|
| ValueData| Os dados para o valor de registro.|
| ValueType| Indica o tipo de valor. Há suporte para estes tipos: Cadeia de caracteres (REG_SZ), o binário (REG-BINARY), Dword de 32 bits (REG_DWORD), Qword de 64 bits (REG_QWORD), cadeia de caracteres múltipla (REG_MULTI_SZ), cadeia de caracteres expansível (REG_EXPAND_SZ) |

## <a name="example"></a>Exemplo

Este exemplo assegura que uma chave chamada "ExampleKey" está presente no hive **HKEY\_LOCAL\_MACHINE**.

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> Alterar uma configuração do registro no hive `HKEY\CURRENT\USER` requer que a configuração seja executada com credenciais de usuário, em vez de como o sistema. Você pode usar a propriedade **PsDscRunAsCredential** para especificar credenciais de usuário para a configuração. Por exemplo, veja [Executar DSC com as credenciais do usuário](../../../configurations/runAsUser.md).
