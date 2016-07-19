---
title: "Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 919438862ca9786447b690d2db10e905da0a7c42
ms.openlocfilehash: f74e9941180c00a1aae1bd1d7b48fa4de0c8790d

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
 

 






<!--HONumber=Jun16_HO4-->


