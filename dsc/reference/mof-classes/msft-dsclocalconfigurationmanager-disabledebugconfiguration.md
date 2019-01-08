---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método DisableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ec5a401de4cb93f302f8572c0408e3f32d8876ad
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047040"
---
# <a name="disabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método DisableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager

Desabilita a depuração do recurso DSC.

## <a name="syntax"></a>Sintaxe

```mof
uint32 DisableDebugConfiguration();
```

## <a name="parameters"></a>Parâmetros

Esse método não tem parâmetros.

## <a name="return-value"></a>Retornar valor

Retorna zero em caso de êxito; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários

Esse é um método estático.

## <a name="requirements"></a>Requisitos

MOF** DscCore.mof

namespace {0} Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Consulte também

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)