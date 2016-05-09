---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Recupera a saída do Agente de Configuração relacionada a um trabalho específico.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_getconfigurationresultoutput'
MSHAttr: 'PreferredLib:/library'
title: 'Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager'
---

# Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager

Obtém a saída do Agente de Configuração associada a um trabalho específico.

Sintaxe
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

Parâmetros
----------

*jobId* \[in\]  
A ID do trabalho para o qual obter dados de saída.

*resumeOutputBookmark* \[in\]  
Especifica que a saída deve ser uma continuação de um indicador anterior.

*output* \[out\]  
A saída para o trabalho especificado.

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


