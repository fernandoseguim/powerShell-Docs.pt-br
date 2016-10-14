---
title: "Convenção de Nomenclatura de Configuração Parcial de Pull"
author: jaimeo
contributor: berheabrha
translationtype: Human Translation
ms.sourcegitcommit: dfa487a11528e26faf5b0e8637b75983abe0b1c8
ms.openlocfilehash: 368c26766961e760fd2de8c99057121bea076158

---

##Convenção de Nomenclatura de Configuração Parcial de Pull
Nas versões anteriores, a convenção de nomenclatura para uma configuração parcial era que o nome do arquivo MOF no serviço/servidor de pull deveria ser compatível com o nome de configuração parcial especificado nas configurações do gerenciador de configuração local que, por sua vez, deve ser compatível com o nome de configuração inserido no arquivo MOF. Confira os instantâneos abaixo:- •   Definições da configuração local, que determina uma configuração parcial que um nó está autorizado a receber.

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

O nome do serviço da Automação do Azure gerou arquivos MOF, como ``<ConfigurationName>.<NodeName>.mof``. Portanto, a configuração a seguir compilará para PartialOne.Localhost.mof.  
Isso tornou impossível efetuar o pull de uma configuração parcial do serviço da Automação do Azure.

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

No WMF 5.1, a configuração parcial no servidor de pull/serviço pode ser nomeada ``<ConfigurationName>.<NodeName>.mof``. Além disso, se um computador estiver efetuando o pull de uma única configuração de um serviço/servidor de pull, o documento de configuração no repositório de configuração do servidor de pull poderá ter qualquer nome. Essa flexibilidade de nomenclatura permite gerenciar a configuração parcial de um nó usando onprem e o serviço de pull da Automação do Azure. Por exemplo, você pode ter a configuração parcial "base" que é enviada localmente por push e outra configuração parcial que é retirada do Serviço de Automação do Azure.

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





<!--HONumber=Aug16_HO3-->


