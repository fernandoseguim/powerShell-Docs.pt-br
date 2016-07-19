---
title: "Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 919438862ca9786447b690d2db10e905da0a7c42
ms.openlocfilehash: 6f9c6a8851732574ac72bc4f3a3db1a73fbbecf2

---

# Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager

Usa o Agente de Configuração para aplicar a configuração pendente. 

Se não houver nenhuma configuração pendente, esse método reaplicará a configuração atual.


## Sintaxe
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## Parâmetros
----------

*force* \[in\]  
Se isso for **true**, a configuração atual é reaplicada, mesmo que haja uma configuração pendente.

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


