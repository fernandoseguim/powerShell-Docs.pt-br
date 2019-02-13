---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método StopConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676334"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método StopConfiguration da classe MSFT_DSCLocalConfigurationManager

Interrompe a alteração da configuração em andamento.

## <a name="syntax"></a>Sintaxe

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parâmetros

*force* \[in\] **true** para forçar a configuração a parar.

## <a name="return-value"></a>Retornar valor

Retorna zero em caso de êxito; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários

Esse é um método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Consulte também

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)