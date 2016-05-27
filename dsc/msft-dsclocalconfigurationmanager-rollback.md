---
title: Método de reversão da classe MSFT_DSCLocalConfigurationManager 
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
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


 

 





<!--HONumber=May16_HO3-->


