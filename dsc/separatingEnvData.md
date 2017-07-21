---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Separando Dados de Configuração e de Ambiente"
ms.openlocfilehash: df3cfea08419c37716b408fdbd6b43e78be2331c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="separating-configuration-and-environment-data"></a><span data-ttu-id="b457a-103">Separando Dados de Configuração e de Ambiente</span><span class="sxs-lookup"><span data-stu-id="b457a-103">Separating configuration and environment data</span></span>

><span data-ttu-id="b457a-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b457a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b457a-105">Isto pode ser útil para separar os dados usados em uma configuração do DSC da configuração em si usando dados da configuração.</span><span class="sxs-lookup"><span data-stu-id="b457a-105">It can be useful to separate the data used in a DSC configuration from the configuration itself by using configuration data.</span></span>
<span data-ttu-id="b457a-106">Fazendo isso, você pode usar uma configuração simples para vários ambientes.</span><span class="sxs-lookup"><span data-stu-id="b457a-106">By doing this, you can use a single configuration for multiple environments.</span></span>

<span data-ttu-id="b457a-107">Por exemplo, se estiver desenvolvendo um aplicativo, você pode usar uma configuração para os ambientes de desenvolvimento e produção e usar dados de configuração para especificar dados para cada ambiente.</span><span class="sxs-lookup"><span data-stu-id="b457a-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

## <a name="what-is-configuration-data"></a><span data-ttu-id="b457a-108">O que são dados de configuração?</span><span class="sxs-lookup"><span data-stu-id="b457a-108">What is configuration data?</span></span>

<span data-ttu-id="b457a-109">Dados de configuração são dados definidos em uma tabela de hash e passados a uma configuração de DSC ao compilar a configuração.</span><span class="sxs-lookup"><span data-stu-id="b457a-109">Configuration data is data that is defined in a hashtable and passed to a DSC configuration when you compile that configuration.</span></span>

<span data-ttu-id="b457a-110">Para obter uma descrição detalhada da tabela de hash **ConfigurationData**, veja [Usar dados de configuração](configData.md).</span><span class="sxs-lookup"><span data-stu-id="b457a-110">For a detailed description of the **ConfigurationData** hashtable, see [Using configuration data](configData.md).</span></span>

## <a name="a-simple-example"></a><span data-ttu-id="b457a-111">Um exemplo simples</span><span class="sxs-lookup"><span data-stu-id="b457a-111">A simple example</span></span>

<span data-ttu-id="b457a-112">Vamos observar um exemplo muito simples para ver como isso funciona.</span><span class="sxs-lookup"><span data-stu-id="b457a-112">Let's look at a very simple example to see how this works.</span></span> <span data-ttu-id="b457a-113">Vamos criar uma única configuração que garante que **IIS** esteja presente em alguns nós e que **Hyper-V** esteja presente em outros:</span><span class="sxs-lookup"><span data-stu-id="b457a-113">We'll create a single configuration that ensures that **IIS** is present on some nodes, and that **Hyper-V** is present on others:</span></span> 

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

<span data-ttu-id="b457a-114">A última linha desse script compila a configuração, passando `$MyData` como o valor do parâmetro **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="b457a-114">The last line in this script compiles the configuration, passing `$MyData` as the value **ConfigurationData** parameter.</span></span>

<span data-ttu-id="b457a-115">O resultado é a criação de dois arquivos MOF:</span><span class="sxs-lookup"><span data-stu-id="b457a-115">The result is that two MOF files are created:</span></span>

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name                                                                                                                    
----                -------------         ------ ----                                                                                                                    
-a----        3/31/2017   5:09 PM           1968 VM-1.mof                                                                                                                
-a----        3/31/2017   5:09 PM           1970 VM-2.mof  
```
 
<span data-ttu-id="b457a-116">O `$MyData` especifica dois nós diferentes, cada um com seu próprio `NodeName` e `Role`.</span><span class="sxs-lookup"><span data-stu-id="b457a-116">`$MyData` specifies two different nodes, each with its own `NodeName` and `Role`.</span></span> <span data-ttu-id="b457a-117">A configuração cria dinamicamente blocos de **Nó** por meio da coleção de nós que obtém do `$MyData` (especificamente, `$AllNodes`) e filtra essa coleção em relação à propriedade `Role`.</span><span class="sxs-lookup"><span data-stu-id="b457a-117">The configuration dynamically creates **Node** blocks by taking the collection of nodes it gets from `$MyData` (specifically, `$AllNodes`) and filters that collection against the `Role` property..</span></span>

## <a name="using-configuration-data-to-define-development-and-production-environments"></a><span data-ttu-id="b457a-118">Usar dados de configuração para definir os ambientes de desenvolvimento e produção</span><span class="sxs-lookup"><span data-stu-id="b457a-118">Using configuration data to define development and production environments</span></span>

<span data-ttu-id="b457a-119">Vejamos um exemplo completo que usa uma única configuração para configurar ambientes de desenvolvimento e de produção de um site.</span><span class="sxs-lookup"><span data-stu-id="b457a-119">Let's look at a complete example that uses a single configuration to set up both development and production environments of a website.</span></span> <span data-ttu-id="b457a-120">No ambiente de desenvolvimento, o IIS e o SQL Server são instalados em um único nó.</span><span class="sxs-lookup"><span data-stu-id="b457a-120">In the development environment, both IIS and SQL Server are installed on a single nodes.</span></span> <span data-ttu-id="b457a-121">No ambiente de produção, o IIS e o SQL Server são instalados em nós separados.</span><span class="sxs-lookup"><span data-stu-id="b457a-121">In the production environment, IIS and SQL Server are installed on separate nodes.</span></span> <span data-ttu-id="b457a-122">Vamos usar um arquivo de dados de configuração .psd1 para especificar os dados para os dois ambientes diferentes.</span><span class="sxs-lookup"><span data-stu-id="b457a-122">We'll use a configuration data .psd1 file to specify the data for the two different environments.</span></span>

 ### <a name="configuration-data-file"></a><span data-ttu-id="b457a-123">Arquivo de dados de configuração</span><span class="sxs-lookup"><span data-stu-id="b457a-123">Configuration data file</span></span>

<span data-ttu-id="b457a-124">Vamos definir os dados do ambiente de desenvolvimento e de produção em um arquivo chamado `DevProdEnvData.psd1` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b457a-124">We'll define the development and production environment data in a file namd `DevProdEnvData.psd1` as follows:</span></span>

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

### <a name="configuration-script-file"></a><span data-ttu-id="b457a-125">Arquivo de script para configuração</span><span class="sxs-lookup"><span data-stu-id="b457a-125">Configuration script file</span></span>

<span data-ttu-id="b457a-126">Agora, na configuração, definida por um arquivo `.ps1`, filtramos os nós que definimos em `DevProdEnvData.psd1` por função (`MSSQL`, `Dev` ou ambas) e os configuramos adequadamente.</span><span class="sxs-lookup"><span data-stu-id="b457a-126">Now, in the configuration, which is defined in a `.ps1` file, we filter the nodes we defined in `DevProdEnvData.psd1` by their role (`MSSQL`, `Dev`, or both), and configure them accordingly.</span></span> <span data-ttu-id="b457a-127">O ambiente de desenvolvimento tem o SQL Server e o IIS em um nó, enquanto que o ambiente de produção os tem em dois nós diferentes.</span><span class="sxs-lookup"><span data-stu-id="b457a-127">The development environment has both the SQL Server and IIS on one node, while the production environment has them on two different nodes.</span></span> <span data-ttu-id="b457a-128">O conteúdo do site também é diferente, conforme especificado pelas propriedades `SiteContents`.</span><span class="sxs-lookup"><span data-stu-id="b457a-128">The site contents is also different, as specified by the `SiteContents` properties.</span></span>

<span data-ttu-id="b457a-129">No final do script de configuração, chamamos a configuração (compilamos isso em um documento MOF), passando o `DevProdEnvData.psd1` como o parâmetro `$ConfigurationData`.</span><span class="sxs-lookup"><span data-stu-id="b457a-129">At the end of the configuration script, we call the configuration (compile it into a MOF document), passing `DevProdEnvData.psd1` as the `$ConfigurationData` parameter.</span></span>

><span data-ttu-id="b457a-130">**Observação:** essa configuração requer que os módulos `xSqlPs` e `xWebAdministration` estejam instalados no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="b457a-130">**Note:** This configuration requires the modules `xSqlPs` and `xWebAdministration` to be installed on the target node.</span></span>

<span data-ttu-id="b457a-131">Vamos definir a configuração em um arquivo chamado `MyWebApp.ps1`:</span><span class="sxs-lookup"><span data-stu-id="b457a-131">Let's define the configuration in a file named `MyWebApp.ps1`:</span></span>

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs
    Import-DscResource -Module xWebAdministration

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
            Name            = $WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

<span data-ttu-id="b457a-132">Ao executar essa configuração, são criados três arquivos MOF (um para cada entrada nomeada na matriz **AllNodes**):</span><span class="sxs-lookup"><span data-stu-id="b457a-132">When you run this configuration, three MOF files are created (one for each named entry in the **AllNodes** array):</span></span>

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name                                                                                                                    
----                -------------         ------ ----                                                                                                                    
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof                                                                                                            
-a----        3/31/2017   5:47 PM           6994 Dev.mof                                                                                                                 
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a><span data-ttu-id="b457a-133">Usar dados sem nós</span><span class="sxs-lookup"><span data-stu-id="b457a-133">Using non-node data</span></span>

<span data-ttu-id="b457a-134">Você pode adicionar mais chaves à tabela de hash **ConfigurationData** para dados que não são específicos de um nó.</span><span class="sxs-lookup"><span data-stu-id="b457a-134">You can add additional keys to the **ConfigurationData** hashtable for data that is not specific to a node.</span></span>
<span data-ttu-id="b457a-135">A configuração a seguir garante a presença dos dois sites.</span><span class="sxs-lookup"><span data-stu-id="b457a-135">The following configuration ensures the presence of two websites.</span></span>
<span data-ttu-id="b457a-136">Os dados de cada site são definidos na matriz **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="b457a-136">Data for each website are defined in the **AllNodes** array.</span></span>
<span data-ttu-id="b457a-137">O arquivo `Config.xml` é usado para ambos os sites, portanto podemos defini-lo em uma outra chave com o nome `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="b457a-137">The file `Config.xml` is used for both websites, so we define it in an additional key with the name `NonNodeData`.</span></span>
<span data-ttu-id="b457a-138">Observe que você pode ter quantas chaves adicionais quiser, e pode nomeá-las como desejar.</span><span class="sxs-lookup"><span data-stu-id="b457a-138">Note that you can have as many additional keys as you want, and you can name them anything you want.</span></span>
<span data-ttu-id="b457a-139">`NonNodeData` não é uma palavra reservada, é apenas o que decidimos usar como nome da chave adicional.</span><span class="sxs-lookup"><span data-stu-id="b457a-139">`NonNodeData` is not a reserved word, it is just what we decided to name the additional key.</span></span>

<span data-ttu-id="b457a-140">Acesse as chaves adicionais usando a variável especial **$ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="b457a-140">You access additional keys by using the special variable **$ConfigurationData**.</span></span>
<span data-ttu-id="b457a-141">Neste exemplo, `ConfigFileContents` é acessado com a linha:</span><span class="sxs-lookup"><span data-stu-id="b457a-141">In this example, `ConfigFileContents` is accessed with the line:</span></span>
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 <span data-ttu-id="b457a-142">no bloco de recurso `File`.</span><span class="sxs-lookup"><span data-stu-id="b457a-142">in the `File` resource block.</span></span>


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


## <a name="see-also"></a><span data-ttu-id="b457a-143">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="b457a-143">See Also</span></span>
- [<span data-ttu-id="b457a-144">Usar dados de configuração</span><span class="sxs-lookup"><span data-stu-id="b457a-144">Using configuration data</span></span>](configData.md)
- [<span data-ttu-id="b457a-145">Opções de credenciais nos dados de configuração</span><span class="sxs-lookup"><span data-stu-id="b457a-145">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="b457a-146">Configurações DSC</span><span class="sxs-lookup"><span data-stu-id="b457a-146">DSC Configurations</span></span>](configurations.md)

