# Configurando um servidor de pull da Web de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Um servidor de pull da Web de DSC é um serviço Web no IIS que utiliza uma interface OData para disponibilizar arquivos de configuração DSC para nós de destino quando são pedidos por tais nós.

Requisitos para usar um servidor de pull:

* Um servidor que execute:
  - WMF/PowerShell 4.0 ou posterior
  - Função de servidor do IIS
  - Serviço de DSC
* Idealmente, alguns meios de gerar um certificado para proteger as credenciais passadas para o Gerenciador de Configurações Local (LCM) em nós de destino

É possível adicionar a função de servidor do IIS e o Serviço de DSC com o assistente Adicionar funções e recursos no Gerenciador do Servidor ou usando PowerShell. Os scripts de exemplo incluídos neste tópico também cuidarão dessas duas etapas.

## Usando o recurso xWebService
A maneira mais fácil de configurar um servidor de pull da Web é usar o recurso xWebService, incluído no módulo xPSDesiredStateConfiguration. As etapas a seguir explicam como usar o recurso em uma configuração que configure o serviço Web.

1. Chame o cmdlet [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) para instalar o módulo **xPSDesiredStateConfiguration**. **Observação**: **Install-Module** está incluído no módulo **PowerShellGet**, que está incluído no PowerShell 5.0. É possível baixar o módulo **PowerShellGet** para o PowerShell 3.0 e 4.0 em [Visualização de Módulos do PowerShell do PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186). 
1. Crie um certificado autoassinado com o assunto `"CN=PSDSCPullServerCert"` no repositório `CERT:\LocalMachine\MY\`. Isso pode ser feito com o comando `New-SelfSignedCertificate  -CertStoreLocation 'CERT:\LocalMachine\MY' -DnsName "PSDSCPullServerCert"`.
1. No ISE do PowerShell, inicie (F5) o script de configuração a seguir (incluído na pasta Example do módulo **xPSDesiredStateConfiguration** como Sample_xDscWebService.ps1). Esse script configura o servidor de pull e um servidor de conformidade.
  
```powershell
configuration Sample_xDscWebService 
6 { 
7     param  
8     ( 
9         [string[]]$NodeName = 'localhost', 
10 
 
11         [ValidateNotNullOrEmpty()] 
12         [string] $certificateThumbPrint 
13     ) 
14 
 
15     Import-DSCResource -ModuleName xPSDesiredStateConfiguration 
16 
 
17     Node $NodeName 
18     { 
19         WindowsFeature DSCServiceFeature 
20         { 
21             Ensure = "Present" 
22             Name   = "DSC-Service"             
23         } 
24 
 
25         xDscWebService PSDSCPullServer 
26         { 
27             Ensure                  = "Present" 
28             EndpointName            = "PSDSCPullServer" 
29             Port                    = 8080 
30             PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer" 
31             CertificateThumbPrint   = $certificateThumbPrint          
32             ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules" 
33             ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"             
34             State                   = "Started" 
35             DependsOn               = "[WindowsFeature]DSCServiceFeature"                         
36         } 
```

1. Execute a configuração, passando a impressão digital do certificado autoassinado criado como o parâmetro **certificateThumbPrint**:

```powershell
PS:\>$myCert = Get-ChildItem CERT: | Where-Object {$_.Subject -eq 'CN=PSDSCPullServerCert'}
PS:\>Sample_xDSCService -certificateThumbprint $myCert.Thumbprint 
```

## Chave de Registro
Para permitir que nós clientes sejam registrados com o servidor para poderem utilizar nomes de configuração em vez de uma ID de configuração, uma chave de serviço (que é um GUID conhecido pelo nó do servidor e do cliente) precisa ser colocada em um arquivo chamado `RegistrationKeys.txt`. Por padrão, o servidor de pull criado por esse exemplo espera que o arquivo esteja localizado em `C:\Program Files\WindowsPowerShell\DscService`. Crie um arquivo de texto com apenas uma linha que consista da chave do registro e salve-o na pasta.
> **Observação**: não há suporte para chaves do registro no PowerShell 4.0. 

## Colocando configurações e recursos
Com a configuração do servidor de pull concluída, há uma nova pasta em `$env:PROGRAMFILES\WindowsPowerShell` chamada "DscService". Nessa pasta, há duas pastas denominadas "Modules" e "Configuration". Na pasta "Modules", coloque todos os recursos que são necessários para as configurações que os nós extrairão por pull desse servidor. Na pasta "Configuration", coloque os arquivos MOF de configuração para todas as configurações que devem ser extraídas por pull pelos nós. Os nomes dos arquivos MOF dependem do tipo de cliente de pull. Os tópicos a seguir descrevem em detalhes a configuração de clientes de pull:

* [Configurando um cliente de pull de DSC usando uma ID de configuração](pullClientConfigID.md)
* [Configurando um cliente de pull de DSC usando nomes de configuração](pullClientConfigNames.md)
* [Configurações parciais](partialConfigs.md)

## Criando a soma de verificação de MOF
Um arquivo MOF de configuração precisa ser emparelhado com um arquivo de soma de verificação para que um LCM em um nó de destino possa validar a configuração. Para criar uma soma de verificação, chame o cmdlet [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx). O cmdlet usa um parâmetro **Path** que especifica a pasta na qual se encontra o MOF de configuração. O cmdlet cria um arquivo de soma de verificação chamado `ConfigurationMOFName.mof.checksum`, em que `ConfigurationMOFName` é o nome do arquivo MOF de configuração. Se houver mais de um arquivo MOF de configuração na pasta especificada, será criada uma soma de verificação para cada configuração na pasta.

O arquivo de soma de verificação deve estar presente no mesmo diretório em que o arquivo MOF de configuração (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` por padrão) e ter o mesmo nome com a extensão `.checksum` anexada.

>**Observação**: se você alterar o arquivo MOF de configuração de qualquer forma, também deverá recriar o arquivo de soma de verificação.

## Consulte também
* [Visão Geral da Configuração de Estado Desejado do Windows PowerShell](overview.md)
* [Aplicando configurações](enactingConfigurations.md)
* [Como recuperar informações do nó do servidor de pull de DSC](retrieveNodeInfo.md)
<!--HONumber=Feb16_HO4-->
