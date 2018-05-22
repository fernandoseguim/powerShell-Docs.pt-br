---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método de reversão da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d2f9b7025d611912e119800408e25fcb66bc0228
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método de reversão da classe MSFT_DSCLocalConfigurationManager

Reverte a configuração a uma versão anterior.

<a name="syntax"></a>Sintaxe
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a>Parâmetros
----------

*configurationNumber* \[in\] Especifica a configuração solicitada.

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