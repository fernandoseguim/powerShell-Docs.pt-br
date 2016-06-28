---
title: "Método ResourceTest da classe MSFT_DSCLocalConfigurationManager"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: c915ebd021ed20209bc491505d45cff2ac89f21d
ms.openlocfilehash: 4129c83dd0b72159cbf1d47c037b9d462ca45f0e

---


# Método ResourceTest da classe MSFT_DSCLocalConfigurationManager

Chama diretamente o método **Test** de um recurso de DSC.

Sintaxe
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

Parâmetros
----------

*ResourceType* \[in\]  
O nome do recurso a chamar.

*ModuleName* \[in\]  
O nome do módulo que contém o recurso a chamar.

*resourceProperty* \[in\]  
Especifica o nome da propriedade de recurso e seu valor em uma tabela de hash como chave e valor, respectivamente. Use o cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) para descobrir as propriedades de recurso e seus tipos.

*InDesiredState* \[out\]  
No retorno, essa propriedade será definida como **true** se o nó de destino estiver no estado desejado.

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


