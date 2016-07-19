---
title: "Método TestConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: c915ebd021ed20209bc491505d45cff2ac89f21d
ms.openlocfilehash: 0777467d37e2f5588f9c0ef368148e3bea963a5b

---


# Método TestConfiguration da classe MSFT_DSCLocalConfigurationManager

Envia o documento de configuração para o nó gerenciado e verifica a configuração atual de acordo com o documento.

Sintaxe
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

Parâmetros
----------

*configurationData* \[in\]  
Dados de ambiente de configuration.

*InDesiredState* \[out\]  
No retorno, especifica se o nó gerenciado está no estado especificado pelo documento de configuração.

*ResourcesInDesiredState* \[out\]  
No retorno, contém uma instância incorporada da classe **MSFT_ResourceInDesiredState** que especifica os recursos que estão no estado desejado.

*ResourcesNotInDesiredState* \[out\]  
No retorno, contém uma instância incorporada da classe **MSFT_ResourceNotInDesiredState** que especifica os recursos que não estão no estado desejado.

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


