---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método StopConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046992"
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

MOF** DscCore.mof

namespace {0} Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Consulte também

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)