---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Parando a configuração em andamento.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_stopconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'Método StopConfiguration da classe MSFT_DSCLocalConfigurationManager'
---

# Método StopConfiguration da classe MSFT_DSCLocalConfigurationManager

Interrompe a alteração da configuração em andamento.

Sintaxe
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

Parâmetros
----------

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


