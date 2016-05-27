---
title:  Método GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---


# Método GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager

Obtém as configurações do Gerenciador de Configurações Local usadas para controlar o Agente de Configuração.

Sintaxe
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

Parâmetros
----------

*MetaConfiguration* \[out\]  
No retorno, contém uma instância incorporada da classe **MSFT_DSCMetaConfiguration** que define as configurações.

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


