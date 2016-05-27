---
title:  Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---


# Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager

Habilita a depuração do recurso DSC.

Sintaxe
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

Parâmetros
----------

*BreakAll* \[in\]  
Define um ponto de interrupção em cada linha do script de recurso.

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


