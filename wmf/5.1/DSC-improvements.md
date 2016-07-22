---
title: Melhorias da DSC no WMF 5.1 (Preview)
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 1f00f2706f3c3ece783590f3a2b0bdb6734402b0

---

#Melhorias na DSC (Configuração de Estado Desejado) no WMF 5.1

## Melhorias de recursos de classe da DSC

No 5.1 WMF, corrigimos os seguintes problemas conhecidos:
* O Get-DscConfiguration poderá retornar valores vazios (nulos) ou erros se um tipo complexo/de tabela de hash for retornado pela função Get() de um recurso da DSC baseado em classe.
* O Get-DscConfiguration retornará um erro se a credencial RunAs for usada na Configuração da DSC.
* Os recursos baseados em classe não podem ser usados em uma Configuração de Composição.
* O Start-DscConfiguration será suspenso se o recurso baseado em Classe tiver uma propriedade de seu próprio tipo.
* O recurso baseado em classe não pode ser usado como um recurso exclusivo.


## Melhorias de depuração de recursos da DSC

No WMF 5.0, o depurador do PowerShell não interrompeu o método Recurso de Classe (Get/Set/Test) diretamente.
No WMF 5.1, o depurador interromperá o método Recurso de Classe da mesma forma que faz com os métodos de recursos baseados em MOF.

## O cliente pull da DSC dá suporte para TLS 1.1 e para TLS 1.2 
Anteriormente, o cliente pull da DSC dava suporte apenas para SSL3.0 e TLS1.0 por meio de conexões HTTPS. Se fosse forçado a usar protocolos mais seguros, o cliente pull pararia de funcionar. No WMF 5.1, o cliente pull da DSC não dá mais suporte para SSL 3.0 e adiciona suporte para os protocolos mais seguros TLS 1.1 e TLS 1.2.  

## Registro do servidor de pull aprimorado ##

Nas versões anteriores do WMF, as solicitações de registros/relatórios simultâneas em um servidor de pull da DSC durante o uso do banco de dados ESENT provocariam uma falha de LCM para registrar e/ou reportar. Nesses casos, os logs de eventos no servidor de pull terão o erro "O nome da instância já está em uso."
Isso ocorria porque um padrão incorreto era usado para acessar o banco de dados ESENT em um cenário Multi-Threaded. No WMF 5.1, esse problema foi corrigido. Os registros ou relatórios simultâneos (que envolvem o banco de dados ESENT) funcionarão bem no WMF 5.1. Esse problema é aplicável somente ao banco de dados ESENT e não se aplica ao banco de dados OLEDB. 

##Convenção de nomenclatura de configuração parcial de pull
Na versão anterior, a convenção de nomenclatura para uma configuração parcial era que o nome do arquivo MOF no servidor de pull/serviço deveria ser compatível com o nome de configuração parcial especificado nas configurações do gerenciador de configuração local que, por sua vez, deve ser compatível com o nome de configuração inserido no arquivo MOF. 

Confira os instantâneos abaixo:- •   Definições da configuração local, que determina uma configuração parcial que um nó está autorizado a receber.

![Metaconfiguração de exemplo](../../images/MetaConfigPartialOne.png)

•   Definição da configuração parcial de exemplo 

```Powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test 
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

•   ‘ConfigurationName’ incorporado no arquivo MOF gerado.

![Arquivo mof de exemplo gerado](../../images/PartialGeneratedMof.png)

•   FileName no repositório de configuração de pull 

![FileName no Repositório de Configuração](../../images/PartialInConfigRepository.png)

O nome do serviço de Automação do Azure gerou arquivos mof como <ConfigurationName>.<NodeName>.mof. Portanto, a configuração a seguir compilará para PartialOne.Localhost.mof.

Ela tornou isso impossível para extrair uma de suas configurações parciais do serviço de Automação do Azure.

```Powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test 
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

No WMF 5.1, a configuração parcial no servidor de pull/serviço pode ser nomeada como <ConfigurationName>.<NodeName>.mof. Além disso, se um computador estiver extraindo uma única configuração de um servidor de pull/serviço, então, o arquivo de configuração no repositório de configuração do servidor de pull poderá ter qualquer nome de arquivo. Esta flexibilidade de nomenclatura permite que você gerencie seus nós parcialmente pelo Serviço de Automação do Azure, no qual algumas configurações para o nó virão da DSC de Automação do Azure e você terá uma configuração parcial que poderá ser gerenciada localmente.

A metaconfiguração abaixo configurará um nó para ser gerenciado tanto localmente quanto pelo Serviço de Automação do Azure.

```Powershell
  [DscLocalConfigurationManager()]
   Configuration RegistrationMetaConfig
   {
        Settings
        {
            RefreshFrequencyMins = 30;
            RefreshMode = "PULL";            
        }

        ConfigurationRepositoryWeb web
        {
            ServerURL =  $endPoint
            RegistrationKey = $registrationKey
            ConfigurationNames = $configurationName
        }

        # Partial configuration managed by Azure Automation Service.
        PartialConfiguration PartialCOnfigurationManagedByAzureAutomation
        {
            ConfigurationSource = "[ConfigurationRepositoryWeb]Web"   
        }
    
        # This partial configuration is managed locally.
        PartialConfiguration OnPremConfig
        {
            RefreshMode = "PUSH"
            ExclusiveResources = @("Script")
        }

   }

   RegistrationMetaConfig
   slcm -Path .\RegistrationMetaConfig -Verbose
 ```

# Usando a PsDscRunAsCredential com os recursos de composição da DSC   

Adicionamos um suporte para usar a [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) com os recursos de [Composição](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) da DSC.    

Os usuários agora podem especificar o valor para a PsDscRunAsCredential ao usarem recursos de composição nas configurações. Quando especificado, todos os recursos serão executados dentro de um recurso de composição como um usuário RunAs. Se o recurso de composição chamar outro recurso de composição, todos os seus recursos também serão executados como usuário RunAs.  As credenciais RunAs são propagadas para qualquer nível da hierarquia do recurso de composição. Se qualquer recurso dentro de um recurso de composição especificar seu próprio valor para a PsDscRunAsCredential, ocorrerá um erro de mesclagem durante a compilação da configuração.

Este exemplo mostra o uso com o recurso de composição [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) incluído no módulo PSDesiredStateConfiguration. 



```powershell

Configuration InstallWindowsFeature     
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        WindowsFeatureSet features 
        {  
            Name = @("Telnet-Client","SNMP-Service")  
            Ensure = "Present"  
            IncludeAllSubFeature = $true  
            PsDscRunAsCredential = Get-Credential   
        }  
    }

}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost';
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}


InstallWindowsFeature -ConfigurationData $configData 

```

##Validações do módulo da DSC e da assinatura de configuração
Na DSC, as configurações e os módulos são distribuídos para computadores gerenciados do servidor de pull. Se o servidor de pull estiver comprometido, um invasor possivelmente poderá modificar as configurações e os módulos no servidor de pull e distribuí-los para todos os nós gerenciados, comprometendo todos eles. 

 No WMF 5.1, a DSC dá suporte para a validação de assinaturas digitais no catálogo e nos arquivos de configuração (.MOF). Este recurso evitará que os nós executem as configurações ou os arquivos de módulo que não são assinados por um signatário confiável ou que foram violados depois de assinados por um signatário confiável. 



###Como assinar a configuração e o módulo 
***
* Arquivos de Configuração (.MOFS):- o cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) existente do PowerShell é estendido para dar suporte à assinatura de arquivos MOF.  
* Módulos:- a assinatura dos módulos é feita ao assinar o catálogo de módulo correspondente por meio das seguintes etapas:- 
    1. Crie um arquivo de catálogo: um arquivo de catálogo contém uma coleção de hashes criptográficos ou impressões digitais. Cada impressão digital corresponde a um arquivo que está incluído no módulo. O novo cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) foi adicionado para permitir que os usuários criem um arquivo de catálogo para seu módulo.
    2. Assine o arquivo de catálogo: use a [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) para assinar o arquivo de catálogo.
    3. Coloque o arquivo de catálogo dentro da pasta do módulo.
Por convenção, o arquivo de catálogo do Módulo deve ser colocado na pasta do módulo, com o mesmo que o módulo.

###Configurações de LocalConfigurationManager para habilitar as validações de assinatura

####Recepção
O LocalConfigurationManager de um nó executa a validação da assinatura dos módulos e das configurações com base em suas configurações atuais. Por padrão, a validação da assinatura está desabilitada. A validação da assinatura pode ser habilitada adicionando o bloco 'SignatureValidation' na definição de metaconfiguração do nó, conforme mostrado abaixo:-

```PowerShell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'        
    } 
    
    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # By default,LCM will use default Windows trusted publisher store to validate the certificate chain. If TrustedStorePath property is specified, LCM will use this custom store for retrieving the trusted publishers to validate the content.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'            
        SignedItemType =  'Configuration','Module'         # Those are list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.       
    }
 
}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose 
 ```

A definição da metaconfiguração acima em um nó habilita a validação da assinatura nas configurações e nos módulos baixados. O Gerenciador de Configurações Local executará as seguintes etapas para verificar as assinaturas digitais.
1. Verifique se a assinatura em um arquivo de configuração (. MOF) é válida. Ela usa o cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) do Powershell, que é estendido na versão 5.1 para dar suporte à validação de assinatura do MOF.
2. Verifique se a autoridade de certificação que autorizou o signatário é confiável.
3. Baixe as dependências de módulo/recurso da configuração para uma localização temporária.
4. Verifique se a assinatura do catálogo foi incluída dentro do módulo.
    * Localize um arquivo <moduleName>.cat e verifique sua assinatura usando o cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).
    * Verifique se a autoridade de certificação que autenticou o signatário é confiável.
    * Verifique se o conteúdo dos módulos não foi violado usando o novo cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).
5. Módulo de instalação para $env:ProgramFiles\WindowsPowerShell\Modules\
6. Configuração do processo

> Observação: a validação da assinatura no catálogo de módulo e na configuração é realizada somente quando a configuração é aplicada ao sistema pela primeira vez ou quando o módulo é baixado e instalado. As execuções de consistência não validam a assinatura de Current.mof ou de suas dependências de módulo.
Se a verificação tiver falhado em qualquer estágio, por exemplo, se a configuração extraída do servidor de pull não estiver assinada, então o processamento da configuração será encerrado com o erro mostrado abaixo e todos os arquivos temporários serão excluídos.

![Configuração de Saída de Erro de Exemplo](../../images/PullUnsignedConfigFail.png)

Da mesma forma, a extração de um módulo cujo catálogo não está assinado resultará no seguinte erro:-

![Módulo de Saída de Erro de Exemplo](../../images/PullUnisgnedCatalog.png)

####Push
Uma configuração entregue por push pode ser violada em sua origem antes de ser fornecida para o nó. O Gerenciador de Configurações Local executará etapas semelhantes de validação de assinatura para as configurações enviadas por push ou publicadas.
Veja abaixo um exemplo completo de validação de assinatura para envio por push.

* Habilite a validação da assinatura no nó.

```Powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PUSH'        
    } 
    SignatureValidation validations{
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'   
        SignedItemType =  'Configuration','Module'             
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
``` 
* Crie um arquivo de configuração de exemplo.

```Powershell
# Sample configuration
Configuration Test{

    File foo
    {
        DestinationPath =  "$env:TEMP\signingTest.txt"
        Contents = "ABC"
    }
}
Test
```

* Tente enviar o arquivo de configuração não assinado por push para o nó. 

```Powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
``` 
![ErrorUnsignedMofPushed](../../images/PushUnsignedMof.png)

* Assine o arquivo de configuração usando um certificado de assinatura de código.

![SignMofFile](../../images/SignMofFile.png)

* Tente enviar o arquivo mof assinado por push.

![SignMofFile](../../images/PushSignedMof.png)




<!--HONumber=Jul16_HO3-->


