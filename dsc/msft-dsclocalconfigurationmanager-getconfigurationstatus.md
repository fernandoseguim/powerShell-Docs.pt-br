---
title: "Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: c915ebd021ed20209bc491505d45cff2ac89f21d
ms.openlocfilehash: b430e98c7ec287c0efcf2c2e2736253797242904

---

# Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager

Obtém o histórico do status de configuração.

Sintaxe
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

Parâmetros
----------

*All* \[in\]  
**true** caso esse método deva retornar informações sobre todos as configurações executadas no computador, incluindo o aplicativo de configuração e a verificação de consistência.

*configurationStatus* \[out\]  
No retorno, contém uma instância incorporada da classe **MSFT_DSCConfigurationStatus** que define as configurações.

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


