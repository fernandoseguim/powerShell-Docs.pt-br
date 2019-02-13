---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método SendConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675537"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método SendConfiguration da classe MSFT_DSCLocalConfigurationManager

Envia o documento de configuração para o nó gerenciado e o salva como alteração pendente.

## <a name="syntax"></a>Sintaxe

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a>Parâmetros

*ConfigurationData* \[in\] Dados de ambiente da configuração.

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