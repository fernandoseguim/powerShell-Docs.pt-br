---
title: Recurso Package de DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: bcaf82cbafe67cc309765e16b3c9cd6eff0a982a

---

# Recurso Package de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso **Package** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para instalar ou desinstalar pacotes, tais como os pacotes do Windows Installer e setup.exe, em um nó de destino.

## Sintaxe

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## Propriedades
|  Propriedade  |  Descrição   | 
|---|---| 
| Nome| Indica o nome do pacote para o qual você deseja garantir um estado específico.| 
| Caminho| Indica o caminho em que o pacote reside.| 
| ProductId| Indica a ID do produto que identifica o pacote com exclusividade.| 
| Argumentos| Lista uma cadeia de caracteres de argumentos que será passada para o pacote exatamente conforme fornecido.| 
| Credential| Fornece acesso ao pacote em uma fonte remota. Essa propriedade não é usada para instalar o pacote. O pacote é sempre instalado no sistema local.| 
| Ensure| Indica se o pacote foi instalado. Defina esta propriedade como "Absent" para garantir que o pacote não seja instalado (ou desinstalar o pacote, se ele estiver instalado). Defina-a como "Present" (o valor padrão) para garantir que o pacote seja instalado.| 
| LogPath| Indica o caminho completo em que você deseja que o provedor salve um arquivo de log para instalar ou desinstalar o pacote.| 
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"``.| 
| ReturnCode| Indica o código de retorno esperado. Se o código de retorno real não corresponder ao valor esperado fornecido aqui, a configuração gerará um erro.| 

## Exemplo

Este exemplo executa o instalador .msi que está localizado no caminho especificado e tem a ID do produto especificado.

```powershell
Package PackageExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path  = "$Env:SystemDrive\TestFolder\TestProject.msi"
    Name = "TestPackage"
    ProductId = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
} 
```




<!--HONumber=Jun16_HO4-->


