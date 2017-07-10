---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: faa113c442b80eea3ac474220b098b7d80ec50a8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager

Remove os arquivo de configuração.

<a id="syntax" class="xliff"></a>
Sintaxe
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a id="parameters" class="xliff"></a>
Parâmetros
----------

*Stage* \[in\]  
Especifica qual documento de configuração remover. Os seguintes valores são válidos:

|Valor |Descrição |
|:--- |:---|
|**1** | O documento de configuração **atual** (current.mof). |
|**2** | O documento de configuração **Pendente** (current.mof).  |
|**4** | O documento de configuração **Anterior** (current.mof). |

*Force* \[in\]  
**true** para forçar a remoção da configuração.

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


 

 



