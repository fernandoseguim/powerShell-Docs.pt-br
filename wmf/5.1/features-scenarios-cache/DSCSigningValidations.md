---
title: "Validações do Módulo de DSC e da Assinatura de Configuração"
author: jaimeo
contributor: berheabra
translationtype: Human Translation
ms.sourcegitcommit: 5c97ca6e93d31aaffc7e2207facc7658ee36dfb4
ms.openlocfilehash: 817fadb79716e41ce8cc8f4245dedc66347ac413

---

##Validações do Módulo de DSC e da Assinatura de Configuração
No DSC, módulos e documentos de configuração são distribuídos para computadores gerenciados do servidor de pull (no caso do serviço de pull da Automação do Azure). Se o serviço/servidor de pull estiver comprometido, um invasor poderia modificar as configurações e módulos no servidor de pull e distribuí-las para todos os computadores gerenciados, comprometendo assim ainda mais computadores do cliente. 

 Esta ameaça é tratada no WMF 5.1. O DSC dá suporte para a validação de assinaturas digitais no catálogo e nos arquivos de configuração (.MOF). Este recurso evitará que os nós executem arquivos de módulo e configuração que não são assinados por um signatário confiável ou que foram adulterados depois de assinados por um signatário confiável. 



###Como assinar a configuração e o módulo 
***
1. Arquivos de Configuração (.MOFS):- o cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) existente do PowerShell é estendido para dar suporte à assinatura de arquivos MOF.  
2. Módulos:- a assinatura dos módulos é feita ao assinar o catálogo de módulo correspondente por meio das seguintes etapas:- 
    * Crie um arquivo de catálogo: um arquivo de catálogo contém uma coleção de hashes criptográficos ou de impressões digitais. Cada impressão digital corresponde a um arquivo que está incluído no módulo.  Um novo cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) foi adicionado para permitir que os usuários criem um arquivo de catálogo para seu módulo. Consulte os cmdlets de catálogo [um link relativo](catalog-cmdlets.md) para criar arquivos de catálogo. 
    * Assine o arquivo de catálogo: usando [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx), assine o arquivo de catálogo.
    * Coloque o arquivo de catálogo dentro da pasta do módulo.
Por convenção, o arquivo de catálogo do Módulo deve ser colocado na pasta do módulo, com o mesmo nome que o módulo.

###Configurações de LocalConfigurationManager para habilitar as validações de assinatura.

####PULL
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

A definição da metaconfiguração acima em um nó habilita a validação da assinatura nas configurações e nos módulos baixados. O localconfigurationmanager executará as seguintes etapas para verificar as assinaturas digitais.
* Verifique se a assinatura em um arquivo de configuração (. MOF) é válida. Ela usa o cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) do Powershell, que é estendido na versão 5.1 para dar suporte à validação de assinatura do MOF.
* Verifique se a autoridade de certificação que autorizou o signatário é confiável.
* Baixe as dependências de módulo/recurso da configuração para uma localização temporária.
* Verifique se a assinatura do catálogo foi incluída dentro do módulo.
    * Localize um arquivo <moduleName>.cat e verifique sua assinatura usando o cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).
    * Verifique se a autoridade de certificação que autenticou o signatário é confiável.
    * Verifique se o conteúdo dos módulos não foi violado usando o novo cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).
* Módulo de instalação para $env:ProgramFiles\WindowsPowerShell\Modules\
* Configuração do processo.

Observação: - a validação da assinatura no catálogo de módulo e na configuração é realizada somente quando a configuração é aplicada ao sistema pela primeira vez ou quando o módulo é baixado e instalado. A execução de consistência não valida a assinatura de Current.mof ou de suas dependências do módulo.
Se a verificação tiver falhado em qualquer estágio, por exemplo, se a configuração extraída do servidor de pull não estiver assinada, o processamento da configuração será encerrado com o erro mostrado abaixo e todos os arquivos temporários serão excluídos.

![Configuração de Saída de Erro de Exemplo](../../images/PullUnsignedConfigFail.PNG)

Da mesma forma, a extração de um módulo cujo catálogo não está assinado resultará no seguinte erro:-

![Módulo de Saída de Erro de Exemplo](../../images/PullUnisgnedCatalog.PNG)

####PUSH
Uma configuração entregue por push pode ser adulterada em sua origem antes de ser fornecida ao nó. O gerenciador de configurações local executará etapas semelhantes de validação de assinatura para as configurações enviadas por push ou publicadas.
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
![ErrorUnsignedMofPushed](../../images/PushUnsignedMof.PNG)

* Assine o arquivo de configuração usando um certificado de assinatura de código.

![SignMofFile](../../images/SignMofFile.PNG)

* Tente enviar o arquivo mof assinado por push.

![SignMofFile](../../images/PushSignedMof.PNG)




<!--HONumber=Aug16_HO3-->


