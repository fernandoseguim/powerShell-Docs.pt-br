---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Obtém as configurações do Gerenciador de Configurações Local que são usadas para controlar o Agente de Configuração.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_getmetaconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'Método GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager'
---

# Método GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager

Obtém as configurações do Gerenciador de Configurações Local usadas para controlar o Agente de Configuração.

Sintaxe
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

Parâmetros
----------

*MetaConfiguration* \[out\]  
No retorno, contém uma instância incorporada da classe **MSFT_DSCMetaConfiguration** que define as configurações.

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


