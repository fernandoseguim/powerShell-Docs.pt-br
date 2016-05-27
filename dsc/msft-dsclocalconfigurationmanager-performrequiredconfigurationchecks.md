---
title: Método PerformRequiredConfigurationChecks da classe MSFT_DSCLocalConfigurationManager 
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---


# Método PerformRequiredConfigurationChecks da classe MSFT_DSCLocalConfigurationManager

Inicia uma verificação de consistência usando o Agendador de Tarefas.

Sintaxe
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

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


