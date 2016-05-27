---
title: Método SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager 
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Método SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager

Define as configurações do Gerenciador de Configurações Local usadas para controlar o Agente de Configuração.

Sintaxe
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

Parâmetros
----------

*ConfigurationData* \[in\]  
Dados do ambiente para a configuração.

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


 

 





<!--HONumber=May16_HO3-->


