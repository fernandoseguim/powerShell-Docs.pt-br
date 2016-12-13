---
title: "Método ResourceSet da classe MSFT_DSCLocalConfigurationManager"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: cbc499f293aad941d40fcb720ef53e832c3b1ea8
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método ResourceSet da classe MSFT_DSCLocalConfigurationManager

Chama diretamente o método **Set** de um recurso de DSC.

<a name="syntax"></a>Sintaxe
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a>Parâmetros
----------

*ResourceType* \[in\]  
O nome do recurso a chamar.

*ModuleName* \[in\]  
O nome do módulo que contém o recurso a chamar.

*resourceProperty* \[in\]  
Especifica o nome da propriedade de recurso e seu valor em uma tabela de hash como chave e valor, respectivamente. Use o cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) para descobrir as propriedades de recurso e seus tipos.

*RebootRequired* \[out\]  
No retorno, essa propriedade será definida como **true** se o nó de destino precisar ser reiniciado.

## <a name="return-value"></a>Retornar valor
------------

Retorna zero em caso de êxito; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários

Esse é um método estático.

## <a name="requirements"></a>Requisitos
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>Consulte também


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)

 

 



