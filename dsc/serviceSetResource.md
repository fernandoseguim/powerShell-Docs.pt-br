---
title: Recurso do ServiceSet DSC
ms.date: 2016-05-23
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 12438bc9c6e4211b6a31550fa25334a20fde6846
ms.openlocfilehash: 871d697626a0376e8f1f27bdbbf16d8612a56a79

---

# Recurso do ServiceSet DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0


O recurso **ServiceSet** na DSC (Configuração de Estado Desejado) do Windows PowerShell oferece um mecanismo para gerenciar serviços no nó de destino. Esse recurso é um [recurso composto](authoringResourceComposite.md) que chama o [Recurso de serviço](serviceResource.md) para cada serviço especificado na propriedade `Name`.

Use esse recurso quando desejar configurar vários serviços para o mesmo estado.

## Sintaxe

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

## Propriedades

|  Propriedade  |  Descrição   | 
|---|---| 
| Nome| Indica os nomes do serviço. Observe que, às vezes, isso é diferente dos nomes de exibição. É possível obter uma lista dos serviços e seus estados atuais com o cmdlet [Get-Service](https://technet.microsoft.com/en-us/library/hh849804.aspx).|
| StartupType| Indica o tipo de inicialização para o serviço. Os valores permitidos para essa propriedade são: **Automatic**, **Disabled** e **Manual**|  
| BuiltInAccount| Indica a conta de credenciais a ser usada para os serviços. Os valores permitidos para essa propriedade são: **LocalService**, **LocalSystem** e **NetworkService**.| 
| Estado| Indica o estado que você deseja garantir para os serviços: **Parado** ou **Em execução**.| 
| Ensure| Indica se os serviços existem no sistema. Defina essa propriedade como **Ausente** para garantir que os serviços não existam. Configurá-la como **Present** (o valor padrão) garantirá que os serviços de destino existam.|
| Credential| Indica as credenciais para a conta sob a qual o serviço será executado. Essa propriedade e a propriedade **BuiltinAccount** não podem ser usadas juntas.| 
| DependsOn| Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for *ResourceName* e seu tipo for *ResourceType*, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.| 



## Exemplo

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




<!--HONumber=Aug16_HO3-->

