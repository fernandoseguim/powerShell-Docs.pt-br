---
title:  Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager

Obtém a saída do Agente de Configuração associada a um trabalho específico.

Sintaxe
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

Parâmetros
----------

*jobId* \[in\]  
A ID do trabalho para o qual obter dados de saída.

*resumeOutputBookmark* \[in\]  
Especifica que a saída deve ser uma continuação de um indicador anterior.

*output* \[out\]  
A saída para o trabalho especificado.

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


