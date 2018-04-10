---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Separando Dados de Configuração e de Ambiente
ms.openlocfilehash: c89e26105611eae59a926be1432079913c40671f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="separating-configuration-and-environment-data"></a>Separando Dados de Configuração e de Ambiente

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Isto pode ser útil para separar os dados usados em uma configuração do DSC da configuração em si usando dados da configuração.
Fazendo isso, você pode usar uma configuração simples para vários ambientes.

Por exemplo, se estiver desenvolvendo um aplicativo, você pode usar uma configuração para os ambientes de desenvolvimento e produção e usar dados de configuração para especificar dados para cada ambiente.

## <a name="what-is-configuration-data"></a>O que são dados de configuração?

Dados de configuração são dados definidos em uma tabela de hash e passados a uma configuração de DSC ao compilar a configuração.

Para obter uma descrição detalhada da tabela de hash **ConfigurationData**, veja [Usar dados de configuração](configData.md).

## <a name="a-simple-example"></a>Um exemplo simples

Vamos observar um exemplo muito simples para ver como isso funciona.
Vamos criar uma única configuração que garante que **IIS** esteja presente em alguns nós e que **Hyper-V** esteja presente em outros:

```powershell
Configuration MyDscConfiguration {

    Node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        WindowsFeature IISInstall {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }

    }
    Node $AllNodes.Where{$_.Role -eq "VMHost"}.NodeName
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
        },

        @{
            NodeName    = 'VM-2'
            Role = 'VMHost'
        }
    )
}

MyDscConfiguration -ConfigurationData $MyData
```

A última linha desse script compila a configuração, passando `$MyData` como o valor do parâmetro **ConfigurationData**.

O resultado é a criação de dois arquivos MOF:

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

O `$MyData` especifica dois nós diferentes, cada um com seu próprio `NodeName` e `Role`. A configuração cria dinamicamente blocos de **Nó** por meio da coleção de nós que obtém do `$MyData` (especificamente, `$AllNodes`) e filtra essa coleção em relação à propriedade `Role`.

## <a name="using-configuration-data-to-define-development-and-production-environments"></a>Usar dados de configuração para definir os ambientes de desenvolvimento e produção

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
        WebSiteName     = "New website"
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
        },

        @{
            NodeName         = "Dev"
            Role             = "MSSQL", "Web"
            SiteContents     = "C:\Website\Dev\SiteContents\"
            SitePath         = "\\Dev\Website\"
        }
    )
}
```

### <a name="configuration-script-file"></a>Arquivo de script para configuração

Agora, na configuração, definida por um arquivo `.ps1`, filtramos os nós que definimos em `DevProdEnvData.psd1` por função (`MSSQL`, `Dev` ou ambas) e os configuramos adequadamente.
O ambiente de desenvolvimento tem o SQL Server e o IIS em um nó, enquanto que o ambiente de produção os tem em dois nós diferentes.
O conteúdo do site também é diferente, conforme especificado pelas propriedades `SiteContents`.

No final do script de configuração, chamamos a configuração (compilamos isso em um documento MOF), passando o `DevProdEnvData.psd1` como o parâmetro `$ConfigurationData`.

>**Observação:** essa configuração requer que os módulos `xSqlPs` e `xWebAdministration` estejam instalados no nó de destino.

Vamos definir a configuração em um arquivo chamado `MyWebApp.ps1`:

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs
    Import-DscResource -Module xWebAdministration

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.NodeName
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

   Node $AllNodes.Where{$_.Role -contains "Web"}.NodeName
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
            Name            = $Node.WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

Ao executar essa configuração, são criados três arquivos MOF (um para cada entrada nomeada na matriz **AllNodes**):

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a>Usar dados sem nós

Você pode adicionar mais chaves à tabela de hash **ConfigurationData** para dados que não são específicos de um nó.
A configuração a seguir garante a presença dos dois sites.
Os dados de cada site são definidos na matriz **AllNodes**.
O arquivo `Config.xml` é usado para ambos os sites, portanto podemos defini-lo em uma outra chave com o nome `NonNodeData`.
Observe que você pode ter quantas chaves adicionais quiser, e pode nomeá-las como desejar.
`NonNodeData` não é uma palavra reservada, é apenas o que decidimos usar como nome da chave adicional.

Acesse as chaves adicionais usando a variável especial **$ConfigurationData**.
Neste exemplo, `ConfigFileContents` é acessado com a linha:
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 no bloco de recurso `File`.


```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName           = “*”
            LogPath            = “C:\Logs”
        },

        @{
            NodeName = “VM-1”
            SiteContents = “C:\Site1”
            SiteName = “Website1”
        },


        @{
            NodeName = “VM-2”;
            SiteContents = “C:\Site2”
            SiteName = “Website2”
        }
    );

    NonNodeData =
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }
}

configuration WebsiteConfig
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite

    node $AllNodes.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = “Present”
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + “\\config.xml”
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```


## <a name="see-also"></a>Consulte Também
- [Usar dados de configuração](configData.md)
- [Opções de credenciais nos dados de configuração](configDataCredentials.md)
- [Configurações DSC](configurations.md)