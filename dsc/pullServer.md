---
ms.date: 04/11/2018
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Serviço de Pull de DSC
ms.openlocfilehash: 61b4c0e9cfe1d1d7539cd32da35d2fe50da4b0e3
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="desired-state-configuration-pull-service"></a>Serviço de Pull de Desired State Configuration

> Aplica-se a: Windows PowerShell 5.0

> [!IMPORTANT]
> O Servidor de Recepção (Recurso do Windows *Serviço DSC*) é um componente compatível com o Windows Server, no entanto, não há planos de oferecer novos recursos ou funcionalidades. É recomendável começar a fazer a transição dos clientes gerenciados para o [DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started) (inclui recursos além do Servidor de Recepção no Windows Server) ou para uma das soluções da comunidade listadas [aqui](pullserver.md#community-solutions-for-pull-service).

O Gerenciador de Configurações Local pode ser gerenciado centralmente por uma solução de Serviço de Pull.
Ao usar essa abordagem, o nó que está sendo gerenciado é registrado com um serviço e uma configuração é atribuída a ele em configurações de LCM.
A configuração e todos os recursos de DSC necessários como dependências para a configuração são baixados para o computador e usados pelo LCM para gerenciar a configuração.
As informações sobre o estado do computador que está sendo gerenciado são carregadas no serviço para relatório.
Esse conceito é conhecido como "serviço de pull".

As opções atuais para o serviço de pull incluem:

- Serviço de Configuração de Estado Desejado da Automação do Azure
- Um serviço de pull em execução no Windows Server
- Soluções de software livre mantidas pela comunidade
- Um compartilhamento SMB

**A solução recomendada**, e a opção com a maioria dos recursos disponíveis, é [DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started).

O serviço do Azure pode gerenciar nós localmente em datacenters privados ou em nuvens públicas, como AWS e o Azure.
Para ambientes privados, onde os servidores não podem se conectar diretamente à Internet, considere limitar o tráfego de saída apenas ao intervalo de IPs do Azure publicado (consulte [Intervalos de IP de Datacenter do Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).

Entre os recursos do serviço online que não estão disponíveis no serviço de pull no Windows Server estão:
- Todos os dados são criptografados em trânsito e em repouso
- Certificados de cliente são criados e gerenciados automaticamente
- Armazenamento de segredos para gerenciar centralmente [senhas/credenciais](/azure/automation/automation-credentials), ou [variáveis](/azure/automation/automation-variables) como nomes de servidor ou cadeias de conexão
- Gerenciar centralmente o nó [Configuração do LCM](metaConfig.md#basic-settings)
- Atribuir centralmente configurações a nós do cliente
- Alterações na configuração de versão de "grupos canário" para teste antes de chegar à produção
- Relatório gráfico
  - Detalhes de status no nível de granularidade de recursos de DSC
  - Mensagens de erro detalhadas de computadores cliente para solução de problemas
- [Integração com o Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) para alertas, tarefas automatizadas, aplicativo para Android/iOS para relatórios e alertas

## <a name="dsc-pull-service-in-windows-server"></a>Serviço de pull de DSC no Windows Server

É possível configurar um serviço de pull para ser executado no Windows Server.
Fique ciente de que a solução de serviço de pull incluída no Windows Server inclui apenas as funcionalidades de armazenamento de configurações/módulos para download e de captura de dados de relatório para o banco de dados.
Ela não inclui muitas das funcionalidades oferecidas pelo serviço no Azure e, portanto, não é uma boa ferramenta para avaliar o modo como o serviço seria usado.

O serviço de pull oferecido no Windows Server é um serviço Web no IIS que utiliza uma interface OData para disponibilizar arquivos de configuração DSC para nós de destino quando são pedidos por tais nós.

Requisitos para usar um servidor de pull:

- Um servidor que execute:
  - WMF/PowerShell 5.0 ou posterior
  - Função de servidor do IIS
  - Serviço de DSC
- Idealmente, alguns meios de gerar um certificado para proteger as credenciais passadas para o Gerenciador de Configurações Local (LCM) em nós de destino

A melhor maneira de configurar o Windows Server para hospedar o serviço de pull é usar uma configuração DSC.
Um script de exemplo é fornecido abaixo.

### <a name="supported-database-systems"></a>Sistemas de banco de dados com suporte

|WMF 4.0   |WMF 5.0  |WMF 5.1 |WMF 5.1 (Windows Server Insider Preview 17090)|
|---------|---------|---------|---------|
|MDB     |ESENT (padrão), MDB |ESENT (padrão), MDB|ESENT (padrão), SQL Server, MDB

Começando na versão 17090 do [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), o SQL Server é uma opção compatível com o serviço de pull (Recurso do Windows *Serviço de DSC*).  Essa é uma nova opção para dimensionar grandes ambientes de DSC que não foram migrados para o [DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started).

> **Observação**: o suporte ao SQL Server não será adicionado às versões anteriores do WMF 5.1 (ou mais antigas) e só estará disponível nas versões do Windows Server maiores ou iguais à 17090.

Para configurar o servidor de recepção para usar o SQL Server, defina **SqlProvider** para `$true` e **SqlConnectionString** para uma cadeia de conexão válida do SQL Server.  Para obter mais informações, confira [Cadeias de conexão SqlClient](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).
Para obter um exemplo de configuração do SQL Server com **xDscWebService**, primeiro leia [Usando o recurso xDscWebService](#using-the-xdscwebservice-resource) e, em seguida, examine [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 no GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).

### <a name="using-the-xdscwebservice-resource"></a>Usando o recurso xDscWebService

A maneira mais fácil de configurar um servidor de recepção Web é usar o recurso **xDscWebService**, incluído no módulo **xPSDesiredStateConfiguration**.
As etapas a seguir explicam como usar o recurso em uma configuração que configure o serviço Web.

1. Chame o cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module) para instalar o módulo **xPSDesiredStateConfiguration**. **Observação**: **Install-Module** está incluído no módulo **PowerShellGet**, que está incluído no PowerShell 5.0. É possível baixar o módulo **PowerShellGet** para o PowerShell 3.0 e 4.0 em [Visualização de Módulos do PowerShell do PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).
1. Obtenha um certificado SSL para o servidor de Pull de DSC de uma Autoridade de Certificação confiável, seja de dentro de sua organização ou de uma autoridade pública. O certificado recebido da autoridade geralmente está no formato PFX. Instale o certificado no nó que se tornará o servidor de recepção de DSC no local padrão, que deve ser CERT:\LocalMachine\My. Anote a impressão digital do certificado.
1. Selecione um GUID a ser usado como a Chave de Registro. Para gerar um, usando o PowerShell, insira o seguinte no prompt do PS e pressione enter: '``` [guid]::newGuid()```' ou '```New-Guid```'. Essa chave será usada por nós de cliente como uma chave compartilhada para autenticação durante o registro. Para obter mais informações, confira a seção Chave de registro abaixo.
1. No ISE do PowerShell, inicie (F5) o script de configuração a seguir (incluído na pasta Exemplos do módulo **xPSDesiredStateConfiguration** como Sample_xDscWebServiceRegistration.ps1). Esse script configura o servidor de pull.

```powershell
configuration Sample_xDscWebServiceRegistration
{
    param
    (
        [string[]]$NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $certificateThumbPrint,

        [Parameter(HelpMessage='This should be a string with enough entropy (randomness) to protect the registration of clients to the pull server.  We will use new GUID by default.')]
        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey   # A guid that clients use to initiate conversation with pull server
    )

    Import-DSCResource -ModuleName xPSDesiredStateConfiguration

    Node $NodeName
    {
        WindowsFeature DSCServiceFeature
        {
            Ensure = "Present"
            Name   = "DSC-Service"
        }

        xDscWebService PSDSCPullServer
        {
            Ensure                  = "Present"
            EndpointName            = "PSDSCPullServer"
            Port                    = 8080
            PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer"
            CertificateThumbPrint   = $certificateThumbPrint
            ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
            ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
            State                   = "Started"
            DependsOn               = "[WindowsFeature]DSCServiceFeature"
            RegistrationKeyPath     = "$env:PROGRAMFILES\WindowsPowerShell\DscService"
            AcceptSelfSignedCertificates = $true
            Enable32BitAppOnWin64   = $false
        }

        File RegistrationKeyFile
        {
            Ensure          = 'Present'
            Type            = 'File'
            DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
            Contents        = $RegistrationKey
        }
    }
}
```

1. Execute a configuração, passando a impressão digital do certificado SSL como o parâmetro **certificateThumbPrint** e uma chave de Registro GUID como o parâmetro **RegistrationKey**:

```powershell
# To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
# and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
dir Cert:\LocalMachine\my

# Then include this thumbprint when running the configuration
Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

# Run the compiled configuration to make the target node a DSC Pull Server
Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
```

#### <a name="registration-key"></a>Chave de Registro

Para permitir que os nós clientes sejam registrados no servidor para poderem usar nomes de configuração em vez de uma ID de configuração, uma chave de registro que foi criada pela configuração acima é salva em um arquivo chamado `RegistrationKeys.txt` em `C:\Program Files\WindowsPowerShell\DscService`. A chave de registro funciona como um segredo compartilhado usado durante o registro inicial pelo cliente com o servidor de pull. O cliente gerará um certificado autoassinado, que será usado para realizar uma autenticação exclusiva no servidor de recepção depois que o registro for concluído com êxito. A impressão digital do certificado é armazenada localmente e associada à URL do servidor de pull.
> **Observação**: não há suporte para chaves do registro no PowerShell 4.0.

Para configurar um nó para ser autenticado no servidor de recepção, a chave de registro deverá estar na metaconfiguração do nó de destino que será registrado nesse servidor de recepção. Observe que a **RegistrationKey** na metaconfiguração abaixo é removida depois de o computador de destino ser registrado com sucesso, e o valor “140a952b-b9d6-406b-b416-e0f759c9c0e4” deve corresponder ao valor armazenado no arquivo RegistrationKeys.txt no servidor pull. Sempre trate o valor da chave do registro com segurança, porque o conhecimento permite que qualquer computador de destino seja registrado com o servidor de pull.

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to setup pull server in previous configuration

        [ValidateNotNullOrEmpty()]
        [string] $ServerName = 'localhost' #node name of the pull server, same as $NodeName used in previous configuration
    )

    Node $NodeName
    {
        Settings
        {
            RefreshMode        = 'Pull'
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey    = $RegistrationKey
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey = $RegistrationKey
        }
    }
}

Sample_MetaConfigurationToRegisterWithLessSecurePullServer -RegistrationKey $RegistrationKey -OutputPath c:\Configs\TargetNodes
```

> **Observação**: a seção **ReportServerWeb** permite que dados de relatório sejam enviados ao servidor pull.

A falta da propriedade **ConfigurationID** no arquivo de metaconfiguração significa implicitamente que esse servidor pull dá suporte à versão V2 do protocolo de servidor pull, de modo que um registro inicial é necessário.
Por outro lado, a presença de uma **ConfigurationID** significa que a versão V1 do protocolo do servidor de pull é usada e não há nenhum processamento de registro.

>**Observação**: em um cenário de PUSH, existe um bug na versão atual que exige a definição de uma propriedade ConfigurationID no arquivo de metaconfiguração para nós que nunca foram registrados em um servidor recepção. Isso forçará o uso do protocolo de Servidor de Pull V1 e evitará mensagens de falha de registro.

## <a name="placing-configurations-and-resources"></a>Colocando configurações e recursos

Após a instalação do servidor pull ser concluída, as pastas definidas pelas propriedades **ConfigurationPath** e **ModulePath** na configuração do servidor pull são onde você colocará módulos e configurações que estarão disponíveis para pull pelos nós de destino.
Esses arquivos precisam estar em um formato específico para que o servidor de recepção processe-os corretamente.

### <a name="dsc-resource-module-package-format"></a>Formato de pacote do módulo de recursos DSC

Cada módulo de recurso precisa ser compactado e nomeado de acordo com o seguinte padrão `{Module Name}_{Module Version}.zip`.
Por exemplo, um módulo chamado xWebAdminstration com uma versão do módulo correspondente a 3.1.2.0 seria nomeado 'xWebAdministration_3.2.1.0.zip'.
Cada versão de um módulo deve estar contido em um único arquivo zip.
Como há apenas uma única versão de um recurso em cada arquivo zip, não há suporte para o formato do módulo adicionado ao WMF 5.0 com suporte para várias versões de módulo em um único diretório.
Isso significa que antes de empacotar módulos de recursos DSC para uso com o servidor de pull, você precisará fazer uma pequena alteração na estrutura de diretórios.
O formato padrão dos módulos contendo o recurso DSC no WMF 5.0 é '{Pasta do Módulo}\{{Versão do Módulo}\DscResources\{{Pasta do Recurso DSC}\'.
Antes de realizar o empacotamento para o servidor de recepção, remova a pasta **{Module version}** para que o caminho se torne '{Module Folder}\DscResources\{DSC Resource Folder}\'.
Com essa alteração, compacte a pasta conforme descrito acima e coloque esses arquivos zip na pasta **ModulePath**.

Use `New-DscChecksum {module zip file}` para criar um arquivo de soma de verificação para o módulo recém-adicionado.

### <a name="configuration-mof-format"></a>Formato MOF de configuração

Um arquivo MOF de configuração precisa ser emparelhado com um arquivo de soma de verificação para que um LCM em um nó de destino possa validar a configuração.
Para criar uma soma de verificação, chame o cmdlet [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum).
O cmdlet usa um parâmetro **Path** que especifica a pasta na qual se encontra o MOF de configuração.
O cmdlet cria um arquivo de soma de verificação chamado `ConfigurationMOFName.mof.checksum`, em que `ConfigurationMOFName` é o nome do arquivo MOF de configuração.
Se houver mais de um arquivo MOF de configuração na pasta especificada, será criada uma soma de verificação para cada configuração na pasta.
Coloque os arquivos MOF e os arquivos de soma de verificação associados na pasta **ConfigurationPath**.

>**Observação**: se alterar o arquivo MOF de configuração de qualquer forma, você também deverá recriar o arquivo de soma de verificação.

### <a name="tooling"></a>Ferramentas

Para facilitar a configuração, validação e gerenciamento do servidor de pull, as ferramentas a seguir são incluídas como exemplos na versão mais recente do módulo xPSDesiredStateConfiguration:

1. Um módulo que ajudará com empacotamento de módulos de recursos DSC e arquivos de configuração para uso no servidor de pull. [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1). Exemplos abaixo:

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Um script que valida o Servidor de Pull está configurado corretamente. [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).

## <a name="community-solutions-for-pull-service"></a>Soluções da comunidade para o Serviço de Pull

A comunidade de DSC criou várias soluções para implementar o protocolo de serviço de pull.
Para ambientes locais, elas oferecem funcionalidades de serviço de pull e uma oportunidade de retribuir à comunidade, contribuindo com melhorias incrementais.

- [Tug](https://github.com/powershellorg/tug)
- [DSC-TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>Configuração do cliente de pull

Os tópicos a seguir descrevem em detalhes a configuração de clientes de pull:

- [Configurando um cliente de pull de DSC usando uma ID de configuração](pullClientConfigID.md)
- [Configurando um cliente de pull de DSC usando nomes de configuração](pullClientConfigNames.md)
- [Configurações parciais](partialConfigs.md)

## <a name="see-also"></a>Consulte também

- [Visão Geral da Configuração de Estado Desejado do Windows PowerShell](overview.md)
- [Aplicando configurações](enactingConfigurations.md)
- [Usando um servidor de relatório de DSC](reportServer.md)