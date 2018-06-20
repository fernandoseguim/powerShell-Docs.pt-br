---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ebf2b65f152c622ccf42e12545b0048a0b96d963
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219769"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager

Obtém as configurações do Gerenciador de Configurações Local usadas para controlar o Agente de Configuração.

<a name="syntax"></a>Sintaxe
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a>Parâmetros
----------

*MetaConfiguration* \[out\] No retorno, contém uma instância inserida da classe **MSFT_DSCMetaConfiguration** que define as configurações.

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