---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Recurso Registry de DSC
ms.openlocfilehash: 649cb60578c053c04a7fcc7446881fb76daee26a
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2017
---
<a id="dsc-registry-resource" class="xliff"></a>
# Recurso Registry de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso **Registry** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para gerenciar chaves e valores do registro em um nó de destino.

<a id="syntax" class="xliff"></a>
## Sintaxe

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

<a id="properties" class="xliff"></a>
## Propriedades
|  Propriedade  |  Descrição   | 
|---|---| 
| Chave| Indica o caminho da chave do Registro para o qual você deseja garantir um estado específico. Esse caminho deve incluir o hive.| 
| ValueName| Indica o nome do valor de registro. Para adicionar ou remover uma chave do Registro, especifique essa propriedade como uma cadeia de caracteres vazia sem especificar ValueType ou ValueData. Para modificar ou remover o valor padrão de uma chave do Registro, especifica essa propriedade como uma cadeia de caracteres vazia e também especifique ValueType ou ValueData.| 
| Ensure| Indica se a chave e o valor existem. Para garantir que existam, defina essa propriedade como "Present". Para garantir que não existam, defina a propriedade como "Absent". O valor padrão é "Present".| 
| Force| Se a chave do Registro especificada estiver presente, __Force__ a substituirá pelo novo valor. Para excluir uma chave do Registro com subchaves, isso deve ser __$true__| 
| Hex| Indica se os dados serão expressos em formato hexadecimal. Se especificado, os dados do valor DWORD/QWORD são apresentados em formato hexadecimal. Não é válido para outros tipos. O valor padrão é __$false__.| 
| DependsOn| Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.| 
| ValueData| Os dados para o valor de registro.| 
| ValueType| Indica o tipo de valor. Há suporte para estes tipos: 
<ul><li>Cadeia de caracteres (REG_SZ)</li>


<li>Binário (REG-BINARY)</li>


<li>DWORD de 32 bits (REG_DWORD)</li>


<li>QWORD de 64 bits (REG_QWORD)</li>


<li>Cadeia de caracteres múltipla (REG_MULTI_SZ)</li>


<li>Cadeia de caracteres expansível (REG_EXPAND_SZ)</li></ul>

<a id="example" class="xliff"></a>
## Exemplo
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

>**Observação:** alterar uma configuração do Registro no hive **HKEY\_CURRENT\_USER** requer que a configuração seja executada com credenciais de usuário, em vez de como o sistema.
>Você pode usar a propriedade **PsDscRunAsCredential** para especificar credenciais de usuário para a configuração. Por exemplo, veja [Executar DSC com as credenciais do usuário](runAsUser.md)



