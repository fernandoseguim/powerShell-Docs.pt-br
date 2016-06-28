---
title: "Método SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: c915ebd021ed20209bc491505d45cff2ac89f21d
ms.openlocfilehash: a81b41f66883b3cf0931905d24c8ff92ef55b6c7

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


 

 






<!--HONumber=Jun16_HO4-->


