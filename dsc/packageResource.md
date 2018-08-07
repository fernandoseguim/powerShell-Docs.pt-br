---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso Package de DSC
ms.openlocfilehash: 9285df71a303c9a53dd50d450272575a64e962e7
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268663"
---
# <a name="dsc-package-resource"></a>Recurso Package de DSC

_Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0_

O recurso **Package** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para instalar ou desinstalar pacotes, tais como os pacotes do Windows Installer e setup.exe, em um nó de destino.

## <a name="syntax"></a>Sintaxe

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

## <a name="properties"></a>Propriedades

| Propriedade | Descrição |
| --- | --- |
| Nome| Indica o nome do pacote para o qual você deseja garantir um estado específico.|
| Caminho| Indica o caminho em que o pacote reside.|
| ProductId| Indica a ID do produto que identifica o pacote com exclusividade.|
| Argumentos| Lista uma cadeia de caracteres de argumentos que será passada para o pacote exatamente conforme fornecido.|
| Credential| Fornece acesso ao pacote em uma fonte remota. Essa propriedade não é usada para instalar o pacote. O pacote é sempre instalado no sistema local.|
| Ensure| Indica se o pacote foi instalado. Defina esta propriedade como "Absent" para garantir que o pacote não seja instalado (ou desinstalar o pacote, se ele estiver instalado). Defina-a como "Present" (o valor padrão) para garantir que o pacote seja instalado.|
| LogPath| Indica o caminho completo em que você deseja que o provedor salve um arquivo de log para instalar ou desinstalar o pacote.|
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.|
| ReturnCode| Indica o código de retorno esperado. Se o código de retorno real não corresponder ao valor esperado fornecido aqui, a configuração gerará um erro.|

## <a name="example"></a>Exemplo

Este exemplo executa o instalador .msi que está localizado no caminho especificado e tem a ID do produto especificado.

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```