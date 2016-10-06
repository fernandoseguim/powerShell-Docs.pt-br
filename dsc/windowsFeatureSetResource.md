---
title: Recurso do WindowsFeatureSet DSC
ms.date: 2016-05-24
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 97714d3fa9a1c00fb3d2e79cc873280ca945a840
ms.openlocfilehash: df6869cdf1d1f6c823704e4de2882e90cb672ad2

---

# Recurso do WindowsFeatureSet DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso **WindowsFeatureSet** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para garantir que funções e recursos sejam adicionados ou removidos em um nó de destino.
Esse recurso é um [recurso composto](authoringResourceComposite.md) que chama o [recurso WindowsFeature](windowsfeatureResource.md) para cada recurso especificado na propriedade `Name`.

Use esse recurso quando desejar configurar vários Recursos do Windows para o mesmo estado.

## Sintaxe

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]] 
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    
}
```

## Propriedades

|  Propriedade  |  Descrição   | 
|---|---| 
| Nome| Os nomes de funções ou recursos que você deseja garantir são adicionados ou removidos. É igual à propriedade **Name** do cmdlet [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx), e não o nome de exibição das funções ou recursos.| 
| Credential| As credenciais que devem ser usadas para adicionar ou remover as funções ou os recursos.| 
| Ensure| Indica se as funções ou os recursos são adicionados. Para garantir que as funções ou os recursos sejam adicionados, defina essa propriedade como "Presente"; para garantir que as funções ou os recursos sejam removido, defina a propriedade como "Ausente".| 
| IncludeAllSubFeature| Defina essa propriedade como **$true** para incluir todos os sub-recursos com os recursos especificados com a propriedade **Nome**.| 
| LogPath| O caminho até um arquivo de log em que você deseja que o provedor de recursos registre a operação.| 
| DependsOn| Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.| 
| Origem| Indica o local do arquivo de origem que deve ser usado para a instalação, se necessário.| 

## Exemplo

A configuração a seguir garante que os recursos **Servidor Web** (IIS) e **Servidor SMTP** e todos os sub-recursos de cada um sejam instalados.

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        } 
    }
}
```




<!--HONumber=Aug16_HO3-->


