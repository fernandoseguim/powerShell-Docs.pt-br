---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Obtém o histórico do status de configuração.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_getconfigurationstatus'
MSHAttr: 'PreferredLib:/library'
title: 'Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager'
---

# Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager

Obtém o histórico do status de configuração.

Sintaxe
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

Parâmetros
----------

*Todos* \[in\]  
**True** se esse método retornar informações sobre todos as configuração, será executado no computador, incluindo
o aplicativo de configuração e a verificação de consistência.

*configurationStatus* \[out\]  
No retorno, contém uma instância incorporada da classe **MSFT_DSCConfigurationStatus** que define as configurações.

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


