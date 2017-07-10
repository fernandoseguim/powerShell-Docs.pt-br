---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método de reversão da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: b8597e3eb7872d9894863fb02d927c9f475da44c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="rollback-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Método de reversão da classe MSFT_DSCLocalConfigurationManager

Reverte a configuração a uma versão anterior.

<a id="syntax" class="xliff"></a>
Sintaxe
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a id="parameters" class="xliff"></a>
Parâmetros
----------

*configurationNumber* \[in\]  
Especifica a configuração solicitada. 

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


 

 



