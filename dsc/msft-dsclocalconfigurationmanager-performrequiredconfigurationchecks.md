---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método PerformRequiredConfigurationChecks da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 26110b3920104da7343b8d55cf63440c12accbbc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Método PerformRequiredConfigurationChecks da classe MSFT_DSCLocalConfigurationManager

Inicia uma verificação de consistência usando o Agendador de Tarefas.

<a id="syntax" class="xliff"></a>
Sintaxe
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a id="parameters" class="xliff"></a>
Parâmetros
----------

*Flags* \[in\]  
Um bitmask que especifica o tipo de verificação de consistência a ser executada. Os seguintes valores são válidos e podem ser combinados usando um operação **OR** bit a bit:

|Valor |Descrição |
|:--- |:---|
|**1** | Uma verificação de consistência normal. |
|**2** | Uma continuação de uma verificação de consistência após uma reinicialização. Esse valor não deve ser combinado com outros valores. |
|**4** | A configuração deve ser extraída do servidor de pull especificado na metaconfiguração do nó. Esse valor deve sempre ser combinado com **1**, para um valor de **5**. |
|**8** | Envie status para o servidor de relatório. |

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


 

 



