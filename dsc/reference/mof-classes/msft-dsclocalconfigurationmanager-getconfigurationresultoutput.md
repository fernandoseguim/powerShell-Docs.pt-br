---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675912"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager

Obtém a saída do Agente de Configuração associada a um trabalho específico.

## <a name="syntax"></a>Sintaxe

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a>Parâmetros

*jobId* \[in\] A ID do trabalho para o qual obter dados de saída.

*resumeOutputBookmark* \[in\] Especifica que a saída deve ser uma continuação de um indicador anterior.

*output* \[out\] A saída para o trabalho especificado.

## <a name="return-value"></a>Retornar valor

Retorna zero em caso de êxito; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários

Esse é um método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Consulte também

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)