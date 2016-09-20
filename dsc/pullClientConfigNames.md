---
title: "Configurando um cliente de pull usando nomes de configuração"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: b617ae80ae6a555e531469efde07e443d83c51d8
ms.openlocfilehash: 02721f0f6f68cc78ae0430205d06f079e3e7465a

---

# Configurando um cliente de pull usando nomes de configuração

> Aplica-se a: Windows PowerShell 5.0

Cada nó de destino deve ser instruído a usar o modo de pull e receber a URL em que possa contatar o servidor de pull para obter as configurações. Para fazer isso, você precisa configurar o Gerenciador de Configurações Local (LCM) com as informações necessárias. Para configurar o LCM, crie um tipo especial de configuração, decorada com o atributo **DSCLocalConfigurationManager**. Para obter mais informações sobre como configurar o LCM, consulte [Configurando o Gerenciador de Configurações Local](metaConfig.md).

> **Observação**: este tópico se aplica ao PowerShell 5.0. Para obter informações sobre como configurar um cliente de pull no PowerShell 4.0, consulte [Configurando um cliente de pull usando uma ID de configuração no PowerShell 4.0](pullClientConfigID4.md).

O script a seguir configura o LCM para efetuar o pull de configurações de um servidor chamado "CONTOSO-PullSrv":

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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
    }
}
PullClientConfigNames
```

No script, o bloco **ConfigurationRepositoryWeb** define o servidor de pull. A propriedade **ServerURL** especifica o ponto de extremidade para o servidor de pull.

A propriedade **RegistrationKey** é uma chave compartilhada entre todos os nós de cliente para um servidor de pull e esse servidor de pull. O mesmo valor é armazenado em um arquivo no servidor de pull. 

A propriedade **ConfigurationNames** em uma matriz que especifica os nomes das configurações destinadas ao nó do cliente. No servidor de pull, o arquivo MOF de configuração para esse nó do cliente deve ser nomeado *ConfigurationNames*.mof, em que *ConfigurationNames* corresponde ao valor da propriedade **ConfigurationNames** definida nessa metaconfiguração.

>**Observação:** se você especificar mais de um valor em **ConfigurationNames**, também será necessário especificar blocos **PartialConfiguration** na configuração. Para obter informações sobre configurações parciais, veja [Configurações parciais da Configuração de Estado Desejado do PowerShell](partialConfigs.md).

Depois de ser executado, esse script cria uma nova pasta de saída chamada **PullClientConfigNames** e coloca um arquivo MOF de metaconfiguração nela. Nesse caso, o arquivo MOF de metaconfiguração será nomeado `localhost.meta.mof`.

Para aplicar a configuração, chame o cmdlet **Set-DscLocalConfigurationManager**, com **Path** definido como a localização do arquivo MOF de metaconfiguração. Por exemplo: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.`

> **Observação**: as chaves de registro funcionam apenas com servidores de pull da Web. Você ainda deve usar **ConfigurationID** com um servidor de pull de SMB. Para obter informações sobre como configurar um servidor de pull usando **ConfigurationID**, consulte [Configurando um cliente de pull usando uma ID de configuração](PullClientConfigNames.md)

## Servidores de recurso e relatório

Se você especificar apenas um bloco **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** em sua configuração LCM (como no exemplo anterior), o cliente de pull efetuará pull dos recursos do servidor especificado, mas não enviará relatórios a ele. Você pode usar um único servidor de pull para emissão de relatórios, recursos e configurações, mas é preciso criar um bloco **ReportRepositoryWeb** para configurar o relatório. O exemplo a seguir mostra uma metaconfiguração que configura um cliente para efetuar pull de recursos e configurações, além de enviar dados de relatórios, para um único servidor de pull.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
        
        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigNames
```

Também é possível especificar servidores de pull diferentes para recursos e relatórios. Para especificar um servidor de recurso, utilize um bloco **ResourceRepositoryWeb** (para um servidor de pull da Web) ou um bloco **ResourceRepositoryShare** (para um servidor de pull de SMB).
Para especificar um servidor de relatório, utilize um bloco **ReportRepositoryWeb**. Um servidor de relatório não pode ser um servidor de SMB.
A metaconfiguração a seguir configura um cliente de pull para obter suas configurações de **CONTOSO PullSrv** e seus recursos de **CONTOSO ResourceSrv**, bem como enviar relatórios de status para **CONTOSO ReportSrv**:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
        
        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigNames
```

## Consulte Também

* [Configurando um cliente de pull com uma ID de configuração](PullClientConfigNames.md)
* [Configurando um servidor de pull da Web de DSC](pullServer.md)




<!--HONumber=Sep16_HO3-->


