---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Reverta a uma configuração anterior.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_rollback'
MSHAttr: 'PreferredLib:/library'
title: 'Método de reversão da classe MSFT_DSCLocalConfigurationManager'
---

# Método de reversão da classe MSFT_DSCLocalConfigurationManager

Reverte a configuração a uma versão anterior.

Sintaxe
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

Parâmetros
----------

*configurationNumber* \[in\]  
Especifica a configuração solicitada. 

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


