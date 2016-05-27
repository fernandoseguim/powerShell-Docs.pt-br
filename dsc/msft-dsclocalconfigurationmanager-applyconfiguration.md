---
title: Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager 
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
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

 

 





<!--HONumber=May16_HO3-->


