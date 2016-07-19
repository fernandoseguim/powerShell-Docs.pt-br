---
title: "Separando Dados de Configuração e de Ambiente"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: ebd74549e2671a332ef6abf131ab984a4d0865a6
ms.openlocfilehash: 8a3ae5fdf5d70de999ca6b992efb14533408c305

---

# Separando Dados de Configuração e de Ambiente

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Na Configuração de Estado Desejado (DSC) do Windows PowerShell, é possível separar dados de configuração da lógica da sua configuração. Outra forma de encarar isso é considerar a configuração estrutural (por exemplo, uma configuração pode exigir que o IIS seja instalado) como algo separado da configuração do ambiente (ou seja, se a situação é um ambiente de teste ou de produção — os nomes dos nós seriam diferentes, mas a configuração aplicada a eles seria a mesma). Tem estas vantagens:

* Permite que você reutilize os dados de configuração para diferentes recursos, nós e configuração.
* A lógica de configuração será mais reutilizável se não contiver dados embutidos em código. Isso é semelhante a boas diretrizes de script para funções.
* Se alguns dos dados precisarem ser alterados, será possível fazer as mudanças em um local, economizando tempo e reduzindo os erros.

## Exemplos e conceitos básicos

Para especificar a parte ambiental da configuração, a DSC usa o parâmetro **ConfigurationData**, que é uma tabela de hash (ou pode utilizar um arquivo .psd1 que contém a tabela de hash). Essa tabela de hash deve ter pelo menos uma chave **AllNodes**, que tem um valor estruturado. Por exemplo:

```powershell
$MyData = 
@{
    AllNodes = @()
    NonNodeData = ""   
}
```

Anote a chave AllNodes, cujo valor é uma matriz. Cada elemento dessa matriz também é uma tabela de hash, que exige NodeName como uma chave:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
        },

 
        @{
            NodeName = "VM-2"
        },

 
        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""   
}
```

Cada entrada da tabela de hash em AllNodes corresponde aos dados de configuração para um nó na configuração. Além da chave NodeName necessária, você pode adicionar outras chaves à tabela de hash, tais como:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },

 
        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""   
}
```

A DSC oferece três variáveis especiais para usar no script de configuração:

* **$AllNodes**: refere-se a todos os nós. É possível usar a filtragem com **.Where()** e **.ForEach()**; portanto, em vez de embutir em código nomes de nós para selecionar nós específicos para ação, você poderia escrever algo parecido para selecionar VM-1 e VM-3 no exemplo acima:

```powershell
configuration MyConfiguration
{
    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
    }
}
```

* **$Node**: depois que o conjunto de nós é filtrado, é possível utilizar $Node para fazer referência à entrada específica. Por exemplo:

```powershell
configuration MyConfiguration
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite
    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }
    }
}
```

Para aplicar uma propriedade a todos os nós, é possível configurar NodeName = “*”. Por exemplo, para atribuir a propriedade LogPath a cada nós, você pode fazer o seguinte:

```
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

 
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },

 
        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3"
            Role     = "WebServer"
            SiteContents = "C:\Site2"
            SiteName = "Website3"
        }
    );
}
```

* **$ConfigurationData**: essa variável pode ser utilizada dentro de uma configuração para acessar a tabela de hash de dados de configuração passada como parâmetro. Por exemplo:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

 
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },

 
        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },
 

        @{
            NodeName = "VM-3"
            Role     = "WebServer"
            SiteContents = "C:\Site2"
            SiteName = "Website3"
        }
    );

    NonNodeData = 
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }   
} 

configuration MyConfiguration
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite

    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + "\\config.xml"
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```

É possível encontrar um exemplo completo incluído no [módulo xWebAdministration](https://powershellgallery.com/packages/xWebAdministration).




<!--HONumber=Jun16_HO4-->


