---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método de reversão da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893011"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método de reversão da classe MSFT_DSCLocalConfigurationManager

Reverte a configuração a uma versão anterior.

## <a name="syntax"></a>Sintaxe

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a>Parâmetros

*configurationNumber* \[in\] Especifica a configuração solicitada.

## <a name="return-value"></a>Retornar valor

Retorna zero em caso de êxito; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários

Esse é um método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Consulte também

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)