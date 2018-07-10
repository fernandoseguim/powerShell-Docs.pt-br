---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método GetConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ae31ac30c152c96707b764ddaf00c924806afcfc
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892535"
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método GetConfiguration da classe MSFT_DSCLocalConfigurationManager

Envia o documento de configuração para o nó gerenciado e usa o método **Get** do Agente de Configuração para aplicar a configuração.

## <a name="syntax"></a>Sintaxe

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a>Parâmetros

*configurationData* \[in\] Especifica os dados de configuração para envio.

*configurations* \[out\] No retorno, contém uma instância inserida das configurações.

## <a name="return-value"></a>Retornar valor

Retorna zero em caso de êxito; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários

Esse é um método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Consulte também

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)