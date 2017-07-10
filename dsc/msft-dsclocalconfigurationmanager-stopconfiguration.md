---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método StopConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: f0b550615b20f07f99c8ed7009805c45794bfe22
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Método StopConfiguration da classe MSFT_DSCLocalConfigurationManager

Interrompe a alteração da configuração em andamento.

<a id="syntax" class="xliff"></a>
Sintaxe
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a id="parameters" class="xliff"></a>
Parâmetros
----------

*force* \[in\]  
**true** para forçar a configuração a parar.

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


 

 



