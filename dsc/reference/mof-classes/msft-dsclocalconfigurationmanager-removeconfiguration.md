---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675532"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager

Remove os arquivo de configuração.

## <a name="syntax"></a>Sintaxe

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a>Parâmetros

*Stage* \[in\] Especifica qual documento de configuração deve ser removido. Os seguintes valores são válidos:

|Valor |Descrição |
|:--- |:---|
|**1** | O documento de configuração **atual** (current.mof). |
|**2** | O documento de configuração **Pendente** (current.mof).  |
|**4** | O documento de configuração **Anterior** (current.mof). |

*Force* \[in\] **true** para forçar a remoção da configuração.

## <a name="return-value"></a>Retornar valor

Retorna zero em caso de êxito; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários

Esse é um método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Consulte também

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)