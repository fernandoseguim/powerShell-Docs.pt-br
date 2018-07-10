---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892392"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager

Habilita a depuração do recurso DSC.

## <a name="syntax"></a>Sintaxe

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a>Parâmetros

*BreakAll* \[in\] Define um ponto de interrupção em cada linha do script de recurso.

## <a name="return-value"></a>Retornar valor

Retorna zero em caso de êxito; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários

Esse é um método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Consulte também

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)