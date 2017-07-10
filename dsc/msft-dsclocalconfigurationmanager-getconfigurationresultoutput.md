---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 09862fd3c19e1e517c9bf5df878113ba3f10d8a6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager

Obtém a saída do Agente de Configuração associada a um trabalho específico.

<a id="syntax" class="xliff"></a>
Sintaxe
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a id="parameters" class="xliff"></a>
Parâmetros
----------

*jobId* \[in\]  
A ID do trabalho para o qual obter dados de saída.

*resumeOutputBookmark* \[in\]  
Especifica que a saída deve ser uma continuação de um indicador anterior.

*output* \[out\]  
A saída para o trabalho especificado.

<a id="return-value" class="xliff"></a>
## Retornar valor
------------

Retorna zero em caso de êxito; caso contrário, retorna um código de erro.

<a id="remarks" class="xliff"></a>
## Comentários

Esse é um método estático.

<a id="requirements" class="xliff"></a>
## Requisitos
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration


<a id="see-also" class="xliff"></a>
## Consulte também


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)

 

 



