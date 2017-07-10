---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: febaf972a2a452eb9aaf3ec7fbc5e41f3f463a58
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager

Usa o Agente de Configuração para aplicar a configuração pendente. 

Se não houver nenhuma configuração pendente, esse método reaplicará a configuração atual.


<a id="syntax" class="xliff"></a>
## Sintaxe
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

<a id="parameters" class="xliff"></a>
## Parâmetros
----------

*force* \[in\]  
Se isso for **true**, a configuração atual é reaplicada, mesmo que haja uma configuração pendente.

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

 

 



