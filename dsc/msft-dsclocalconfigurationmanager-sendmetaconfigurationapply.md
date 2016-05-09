---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Obtém as configurações do Gerenciador de Configurações Local usadas para controlar o Agente de Configuração.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_sendmetaconfigurationapply'
MSHAttr: 'PreferredLib:/library'
title: 'Método SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager'
---

# Método SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager

Define as configurações do Gerenciador de Configurações Local usadas para controlar o Agente de Configuração.

Sintaxe
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

Parâmetros
----------

*ConfigurationData* \[in\]  
Dados do ambiente para a configuração.

*force* \[in\]  
**true** para forçar a configuração a parar.

## Retornar valor
------------

Retorna zero em caso de êxito; caso contrário, retorna um código de erro.

## Comentários

Esse é um método estático.

## Requisitos
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration


## Consulte também


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 





<!--HONumber=Apr16_HO2-->


