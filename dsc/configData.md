---
title: "Separando Dados de Configuração e de Ambiente"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 72555a36819c9717fafdd3daede8fa2f02c692b2
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="separating-configuration-and-environment-data"></a>Separando Dados de Configuração e de Ambiente

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Usando o parâmetro **ConfigurationData** da DSC interna, você pode definir os dados que podem ser usados dentro de uma configuração. Isso permite que você crie uma única configuração que pode ser usada para vários nós ou para ambientes diferentes. Por exemplo, se estiver desenvolvendo um aplicativo, você pode usar uma configuração para os ambientes de desenvolvimento e produção e usar dados de configuração para especificar dados para cada ambiente.

Vamos observar um exemplo muito simples para ver como isso funciona. Vamos criar uma única configuração que garante que **IIS** esteja presente em alguns nós e que **Hyper-V** esteja presente em outros: 

```powershell
Configuration MyDscConfiguration {
    
    Node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        WindowsFeature IISInstall {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
        
    }
    Node $AllNodes.Where($_.Role -eq "VMHost").NodeName
    {
        WindowsFeature HyperVInstall {
            Ensure = 'Present'
            Name   = 'Hyper-V'
        }
    }
}

$MyData = 
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            Role = 'WebServer'
        }

        @{
            NodeName    = 'VM-2'
            FeatureName = 'VMHost'
        }
    )
}

MyDscConfiguration -ConfigurationData $MyData
```

A última linha desse script compila a configuração em documentos MOF, passando `$MyData` como o valor do parâmetro **ConfigurationData**. O `$MyData` especifica dois nós diferentes, cada um com seu próprio `NodeName` e `Role`. A configuração cria dinamicamente blocos de **Nó** por meio da coleção de nós que obtém do `$MyData` (especificamente, `$AllNodes`) e filtra essa coleção em relação à propriedade `Role`.

Agora vamos ver como isso funciona com mais detalhes.

## <a name="the-configurationdata-parameter"></a>O parâmetro ConfigurationData

Uma configuração DSC leva um parâmetro chamado **ConfigurationData**, que você especifica quando compila a configuração. Para obter informações sobre configurações de compilação, consulte [configurações DSC](configurations.md).

O parâmetro **ConfigurationData** é uma tabela de hash que deve ter pelo menos uma chave chamada **AllNodes**. Ele também pode ter outras chaves:

```powershell
$MyData = 
@{
    AllNodes = @()
    NonNodeData = ""   
}
```

O valor da chave **AllNodes** é uma matriz. Cada elemento dessa matriz também é uma tabela de hash que deve ter pelo menos uma chave chamada **NodeName**:

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

Você também pode adicionar outras chaves para cada tabela de hash:

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

Para aplicar uma propriedade para todos os nós, você pode criar um membro da matriz **AllNodes** que possua um **NodeName** de `*`. Por exemplo, para atribuir uma propriedade `LogPath` a cada nó, você pode fazer o seguinte:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },

 
        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },

 
        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },

 
        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

Isso é o equivalente a adicionar uma propriedade com um nome de `LogPath` com um valor de `"C:\Logs"` para cada um dos outros blocos (`VM-1`, `VM-2` e `VM-3`).

## <a name="defining-the-configurationdata-hashtable"></a>Definição da tabela de hash de ConfigurationData

Você pode definir **ConfigurationData** como uma variável dentro do mesmo arquivo de script como uma configuração (como em nossos exemplos anteriores) ou em um arquivo .psd1 separado. Para definir **ConfigurationData** em um arquivo .psd1, crie um arquivo que contém somente a tabela de hash que representa os dados de configuração.

Por exemplo, você poderia criar um arquivo chamado `MyData.psd1` com o seguinte conteúdo:

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        }

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

Para usar dados de configuração que são definidos em um arquivo .psd1, você passa o caminho e o nome desse arquivo como o valor do parâmetro **ConfigurationData** ao compilar a configuração:

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>Usando variáveis de ConfigurationData em uma configuração

A DSC fornece três variáveis especiais que podem ser usadas em um script de configuração: **$AllNodes**, **$Node** e **$ConfigurationData**.

- A **$AllNodes** refere-se a toda a coleção de nós definida em **ConfigurationData**. Você pode filtrar a coleção **AllNodes** usando **.Where()** e **.ForEach()**.
- O **Nó** refere-se a uma entrada específica na coleção **AllNodes** depois que ela é filtrada usando **.Where()** ou **.ForEach()**.
- O **ConfigurationData** refere-se à tabela de hash inteira que é passada como parâmetro ao compilar uma configuração.

## <a name="devops-example"></a>Exemplo de DevOps

Vejamos um exemplo completo que usa uma única configuração para configurar ambientes de desenvolvimento e de produção de um site. No ambiente de desenvolvimento, o IIS e o SQL Server são instalados em um único nó. No ambiente de produção, o IIS e o SQL Server são instalados em nós separados. Vamos usar um arquivo de dados de configuração .psd1 para especificar os dados para os dois ambientes diferentes.

### <a name="configuration-data-file"></a>Arquivo de dados de configuração

Vamos definir os dados do ambiente de desenvolvimento e de produção em um arquivo chamado `DevProdEnvData.psd1` da seguinte maneira:

```powershell
@{

    AllNodes = @(

        @{
            NodeName        = "*"
            SQLServerName   = "MySQLServer"
            SqlSource       = "C:\Software\Sql"
            DotNetSrc       = "C:\Software\sxs"
        },

        @{
            NodeName        = "Prod-SQL"
            Role            = "MSSQL"
        },

        @{
            NodeName        = "Prod-IIS"
            Role            = "Web"
            SiteContents    = "C:\Website\Prod\SiteContents\"
            SitePath        = "\\Prod-IIS\Website\"
        }

        @{
            NodeName         = "Dev"
            Role             = "MSSQL", "Web"
            SiteContents     = "C:\Website\Dev\SiteContents\"
            SitePath         = "\\Dev\Website\"

        }

    )

}

    )

}
```

### <a name="configuration-file"></a>Arquivo de configuração

Agora, na configuração, filtramos por suas funções (`MSSQL`, `Dev` ou ambos) os nós que definimos no `DevProdEnvData.psd1` e os configuramos adequadamente. O ambiente de desenvolvimento tem o SQL Server e o IIS em um nó, enquanto que o ambiente de produção os tem em dois nós diferentes. O conteúdo do site também é diferente, conforme especificado pelas propriedades `SiteContents`.

No final do script de configuração, chamamos a configuração (compilamos isso em um documento MOF), passando o `DevProdEnvData.psd1` como o parâmetro `$ConfigurationData`.

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.Nodename
   {
        # Install prerequisites
        WindowsFeature installdotNet35
        {            
            Ensure      = "Present"
            Name        = "Net-Framework-Core"
            Source      = "c:\software\sxs"
        }

        # Install SQL Server
        xSqlServerInstall InstallSqlServer
        {
            InstanceName = $Node.SQLServerName
            SourcePath   = $Node.SqlSource
            Features     = "SQLEngine,SSMS"
            DependsOn    = "[WindowsFeature]installdotNet35"

        }
   }

   Node $AllNodes.Where($_.Role -contains "Web")
   {
        # Install the IIS role
        WindowsFeature IIS
        {
            Ensure       = 'Present'
            Name         = 'Web-Server'
        }

        # Install the ASP .NET 4.5 role
        WindowsFeature AspNet45
        {
            Ensure       = 'Present'
            Name         = 'Web-Asp-Net45'

        }

        # Stop the default website
        xWebsite DefaultSite 
        {
            Ensure       = 'Present'
            Name         = 'Default Web Site'
            State        = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn    = '[WindowsFeature]IIS'

        }

        # Copy the website content
        File WebContent

        {
            Ensure          = 'Present'
            SourcePath      = $Node.SiteContents
            DestinationPath = $Node.SitePath
            Recurse         = $true
            Type            = 'Directory'
            DependsOn       = '[WindowsFeature]AspNet45'

        }       


        # Create the new Website

        xWebsite NewWebsite

        {

            Ensure          = 'Present'
            Name            = $WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

## <a name="see-also"></a>Consulte Também
- [Opções de credenciais nos dados de configuração](configDataCredentials.md)
- [Configurações DSC](configurations.md)