---
title:   Recurso Registry de DSC
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Recurso Registry de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso **Registry** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para gerenciar chaves e valores do registro em um nó de destino.

## Sintaxe

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## Propriedades
|  Propriedade  |  Descrição   | 
|---|---| 
| Chave| Indica o caminho da chave do Registro para o qual você deseja garantir um estado específico. Esse caminho deve incluir o hive.| 
| ValueName| Indica o nome do valor de registro.| 
| Ensure| Indica se a chave e o valor existem. Para garantir que existam, defina essa propriedade como "Present". Para garantir que não existam, defina a propriedade como "Absent". O valor padrão é "Present".| 
| Force| Se a chave do Registro especificada estiver presente, __Force__ a substituirá pelo novo valor.| 
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

## Exemplo
```powershell
Registry RegistryExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Key = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
    ValueName = "TestValue"
    ValueData = "TestData"
}
```



<!--HONumber=May16_HO3-->


