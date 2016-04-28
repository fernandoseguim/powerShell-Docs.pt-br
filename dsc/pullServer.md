# Configurando um servidor de pull da Web de DSC

> Aplica-se a: Windows PowerShell 5.0

Um servidor de pull da Web de DSC é um serviço Web no IIS que utiliza uma interface OData para disponibilizar arquivos de configuração DSC para nós de destino quando são pedidos por tais nós.

Requisitos para usar um servidor de pull:

* Um servidor que execute:
  - WMF/PowerShell 5.0 ou posterior
  - Função de servidor do IIS
  - Serviço de DSC
* Idealmente, alguns meios de gerar um certificado para proteger as credenciais passadas para o Gerenciador de Configurações Local (LCM) em nós de destino

É possível adicionar a função de servidor do IIS e o Serviço de DSC com o assistente Adicionar funções e recursos no Gerenciador do Servidor ou usando PowerShell. Os scripts de exemplo incluídos neste tópico também cuidarão dessas duas etapas.

## Usando o recurso xWebService
A maneira mais fácil de configurar um servidor de pull da Web é usar o recurso xWebService, incluído no módulo xPSDesiredStateConfiguration. As etapas a seguir explicam como usar o recurso em uma configuração que configure o serviço Web.

1. Chame o cmdlet [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) para instalar o módulo **xPSDesiredStateConfiguration**. **Observação**: **Install-Module** está incluído no módulo **PowerShellGet**, que está incluído no PowerShell 5.0. É possível baixar o módulo **PowerShellGet** para o PowerShell 3.0 e 4.0 em [Visualização de Módulos do PowerShell do PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186). 
1. Obtenha um certificado SSL para o servidor de Pull de DSC de uma Autoridade de Certificação confiável, seja de dentro de sua organização ou de uma autoridade pública. O certificado recebido da autoridade geralmente está no formato PFX. Instale o certificado no nó que se tornará o servidor de Pull de DSC no local padrão, que deve ser CERT: \LocalMachine\My. Anote a impressão digital do certificado.
1. Selecione um GUID a ser usado como a Chave de Registro. Para gerar uma usando o PowerShell, insira o seguinte no prompt do PS e pressione enter: '``` [guid]::newGuid()```'. Essa chave será usada por nós de cliente como uma chave compartilhada para autenticação durante o registro. Para obter mais informações, consulte a seção [Chave de Registro](#RegKey) abaixo.
1. No ISE do PowerShell, inicie (F5) o script de configuração a seguir (incluído na pasta Example do módulo **xPSDesiredStateConfiguration** como Sample_xDscWebService.ps1). Esse script configura o servidor de pull.
  
```powershell
configuration Sample_xDscWebService 
{ 
    param  
    ( 
            [string[]]$NodeName = 'localhost', 
            
            [ValidateNotNullOrEmpty()] 
            [string] $certificateThumbPrint,
            
            [Parameter(Mandatory)]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey 
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
         } 

        File RegistrationKeyFile
        {
            Ensure          ='Present'
            Type            = 'File'
            DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
            Contents        = $RegistrationKey
        }
    }
}

```

1. Execute a configuração, passando a impressão digital do certificado SSL como o parâmetro **certificateThumbPrint** e uma chave de Registro GUID como o parâmetro **RegistrationKey**:

```powershell
# To find the Thumbprint for an installed SSL certificate for use with the pull server list all certifcates in your local store 
# and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
dir Cert:\LocalMachine\my

# Then include this thumbprint when running the configuration
Sample_xDSCService -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutpuPath c:\Configs\PullServer
```

## Chave de Registro
Para permitir que nós clientes sejam registrados com o servidor para poderem utilizar nomes de configuração em vez de uma ID de configuração, uma chave de registro que foi criada pela configuração acima é salva em um arquivo chamado `RegistrationKeys.txt` em `C:\Program Files\WindowsPowerShell\DscService`. A chave de registro funciona como um segredo compartilhado usado durante o registro inicial pelo cliente com o servidor de pull. O cliente gerará um certificado autoassinado, que será usado para autenticar de modo exclusivo com o servidor de pull depois que o registro for concluído com êxito. A impressão digital do certificado é armazenada localmente e associada à URL do servidor de pull.
> **Observação**: não há suporte para chaves do registro no PowerShell 4.0. 

Para configurar a um nó para autenticar com o servidor de pull, a chave de registro deve estar na metaconfiguração para qualquer nó de destino que será registrado com esse servidor de pull. Observe que a **RegistrationKey** na metaconfiguração abaixo é removida depois de o computador de destino ser registrado com sucesso, e o valor “140a952b-b9d6-406b-b416-e0f759c9c0e4” deve corresponder ao valor armazenado no arquivo RegistrationKeys.txt no servidor pull. Sempre trate o valor da chave do registro com segurança, porque o conhecimento permite que qualquer computador de destino seja registrado com o servidor de pull.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }   
        
        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL         = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey   = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
        }
    }
}

PullClientConfigID -OutputPath c:\Configs\TargetNodes
```
> **Observação**: a seção **ReportServerWeb** permite que dados de relatório sejam enviados ao servidor pull. 

A falta da propriedade **ConfigurationID** no arquivo de metaconfiguração significa implicitamente que esse servidor pull dá suporte à versão V2 do protocolo de servidor pull, de modo que um registro inicial é necessário. Por outro lado, a apresentação de uma **ConfigurationID** significa que a versão V1 do protocolo do servidor pull é usada e não há nenhum processamento de registro.

>**Observação**: em um cenário PUSH, existe um bug na versão atual que torna necessário definir uma propriedade ConfigurationID no arquivo de metaconfiguração para nós que nunca foram registrados com um servidor pull. Isso forçará o uso do protocolo de Servidor de Pull V1 e evitará mensagens de falha de registro.

## Colocando configurações e recursos
Após a instalação do servidor pull ser concluída, as pastas definidas pelas propriedades **ConfigurationPath** e **ModulePath** na configuração do servidor pull são onde você colocará módulos e configurações que estarão disponíveis para pull pelos nós de destino. Esses arquivos precisam estar em um formato específico para que o servidor de recepção processe-os corretamente. 

### Formato de pacote do módulo de recursos DSC
Cada módulo de recurso precisa ser compactado e nomeado de acordo com o padrão a seguir: **{Nome do Módulo}_{Versão do Módulo}.zip**. Por exemplo, um módulo chamado xWebAdminstration com uma versão do módulo correspondente a 3.1.2.0 seria nomeado 'xWebAdministration_3.2.1.0.zip'. Cada versão de um módulo deve estar contido em um único arquivo zip. Como há apenas uma única versão de um recurso em cada arquivo zip, não há suporte para o formato do módulo adicionado ao WMF 5.0 com suporte para várias versões de módulo em um único diretório. Isso significa que antes de empacotar módulos de recursos DSC para uso com o servidor de pull, você precisará fazer uma pequena alteração na estrutura de diretórios. O formato padrão dos módulos contendo o recurso DSC no WMF 5.0 é '{Pasta do Módulo}\{Versão do Módulo}\DscResources\{Pasta do Recurso DSC}\'. Antes do empacotamento para o servidor pull, simplesmente remova a pasta **{Versão do módulo}** de modo que o caminho se torne '{Pasta do Módulo}\DscResources\{Pasta do Recurso DSC}\'. Com essa alteração, compacte a pasta conforme descrito acima e coloque esses arquivos zip na pasta **ModulePath**.

### Formato MOF de configuração 
Um arquivo MOF de configuração precisa ser emparelhado com um arquivo de soma de verificação para que um LCM em um nó de destino possa validar a configuração. Para criar uma soma de verificação, chame o cmdlet [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx). O cmdlet usa um parâmetro **Path** que especifica a pasta na qual se encontra o MOF de configuração. O cmdlet cria um arquivo de soma de verificação chamado `ConfigurationMOFName.mof.checksum`, em que `ConfigurationMOFName` é o nome do arquivo MOF de configuração. Se houver mais de um arquivo MOF de configuração na pasta especificada, será criada uma soma de verificação para cada configuração na pasta. Coloque os arquivos MOF e seus arquivos de soma de verificação associados na pasta **ConfigurationPath**.

>**Observação**: se você alterar o arquivo MOF de configuração de qualquer forma, também deverá recriar o arquivo de soma de verificação.

## Ferramentas
Para facilitar a configuração, validação e gerenciamento do servidor de pull, as ferramentas a seguir são incluídas como exemplos na versão mais recente do módulo xPSDesiredStateConfiguration:
1. Um módulo que ajudará com empacotamento de módulos de recursos DSC e arquivos de configuração para uso no servidor de pull. [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1). Exemplos abaixo:

```powershell
    # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
     $moduleList = @("xWebAdministration", "xPhp") 
     Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 
     
     # Example 2 - Package modules and mof documents from c:\LocalDepot
     Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
```

1. Um script que valida o Servidor de Pull está configurado corretamente. [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/Examples/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).


## Configuração do cliente de pull 
Os tópicos a seguir descrevem em detalhes a configuração de clientes de pull:

* [Configurando um cliente de pull de DSC usando uma ID de configuração](pullClientConfigID.md)
* [Configurando um cliente de pull de DSC usando nomes de configuração](pullClientConfigNames.md)
* [Configurações parciais](partialConfigs.md)


## Consulte também
* [Visão Geral da Configuração de Estado Desejado do Windows PowerShell](overview.md)
* [Aplicando configurações](enactingConfigurations.md)
* [Usando um servidor de relatório de DSC](reportServer.md)


<!--HONumber=Mar16_HO5-->


