---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Envia o documento de configuração para o nó gerenciado e usa o Agente de Configuração para aplicar a configuração usando o método Get.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_getconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'Método GetConfiguration da classe MSFT_DSCLocalConfigurationManager'
---

# Método GetConfiguration da classe MSFT_DSCLocalConfigurationManager

Envia o documento de configuração para o nó gerenciado e usa o método **Get** do Agente de Configuração para aplicar a configuração.

Sintaxe
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

Parâmetros
----------

*configurationData* \[in\]  
Especifica os dados de configuração para envio.

*configurações* \[out\]  
No retorno, contém uma instância incorporada das configurações.

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


