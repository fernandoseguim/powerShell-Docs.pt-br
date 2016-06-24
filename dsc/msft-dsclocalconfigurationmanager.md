---
title: Classe MSFT_DSCLocalConfigurationManager 
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Classe MSFT_DSCLocalConfigurationManager

O LCM (Gerenciador de Configurações Local) que controla os estados dos arquivos de configuração e usa o Agente de Configuração para aplicar as configurações.

A sintaxe a seguir é simplificada do código MOF (Managed Object Format) e inclui todas as propriedades herdadas.

## Sintaxe
------

``` syntax
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## Membros
-------

A classe **MSFT_DSCLocalConfigurationManager** tem os seguintes membros:

-   [Métodos][]

### Métodos

A classe **MSFT_DSCLocalConfigurationManager** tem os métodos a seguir.

|Método |Descrição |
|:--- |:---|
| [ApplyConfiguration](msft-dsclocalconfigurationmanager-applyconfiguration.md)| Usa o Agente de Configuração para aplicar a configuração pendente.| 
| [DisableDebugConfiguration](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| Desabilita a depuração do recurso DSC.| 
| [EnableDebugConfiguration](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| Habilita a depuração do recurso DSC.| 
| [GetConfiguration](msft-dsclocalconfigurationmanager-getconfiguration.md)| Envia o documento de configuração para o nó gerenciado e usa o método **Get** do Agente de Configuração para aplicar a configuração.| 
| [GetConfigurationResultOutput](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| Obtém a saída do Agente de Configuração relacionada a um trabalho específico.| 
| [GetConfigurationStatus](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| Obtém o histórico do status de configuração.| 
| [GetMetaConfiguration](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| Obtém as configurações LCM que são usadas para controlar o Agente de Configuração.| 
| [PerformRequiredConfigurationChecks](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| Inicia a verificação de consistência.| 
| [RemoveConfiguration](msft-dsclocalconfigurationmanager-removeconfiguration.md)| Remove os arquivo de configuração.| 
| [ResourceGet](msft-dsclocalconfigurationmanager-resourceget.md)| Chama diretamente o método **Get** de um recurso de DSC.| 
| [ResourceSet](msft-dsclocalconfigurationmanager-resourceset.md)| Chama diretamente o método **Set** de um recurso de DSC.| 
| [ResourceTest](msft-dsclocalconfigurationmanager-resourcetest.md)| Chama diretamente o método **Test** de um recurso de DSC.| 
| [Reversão](msft-dsclocalconfigurationmanager-rollback.md)| Reverte a uma configuração anterior.| 
| [SendConfiguration](msft-dsclocalconfigurationmanager-sendconfiguration.md)| Envia o documento de configuração para o nó gerenciado e o salva como alteração pendente.| 
| [SendConfigurationApply](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| Envia o documento de configuração para o nó gerenciado e usa o Agente de Configuração para aplicar a configuração.| 
| [SendConfigurationApplyAsync](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| Envia o documento de configuração para o nó gerenciado e começa a usar o Agente de Configuração para aplicar a configuração. Use GetConfigurationResultOutput para recuperar a saída do resultado.| 
| [SendMetaConfigurationApply](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| Obtém as configurações de LCM que são usadas para controlar o Agente de Configuração.| 
| [StopConfiguration](msft-dsclocalconfigurationmanager-stopconfiguration.md)| Interrompe a configuração em andamento.| 
| [TestConfiguration](msft-dsclocalconfigurationmanager-testconfiguration.md)| Envia o documento de configuração para o nó gerenciado e verifica a configuração atual de acordo com o documento.| 



 

## Requisitos
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration



 

 





<!--HONumber=Jun16_HO3-->


