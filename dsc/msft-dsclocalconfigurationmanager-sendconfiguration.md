---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método SendConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b4d4c901268344ba67d77e4dc982042bfc2abd78
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método SendConfiguration da classe MSFT_DSCLocalConfigurationManager

Envia o documento de configuração para o nó gerenciado e o salva como alteração pendente.

<a name="syntax"></a>Sintaxe
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a>Parâmetros
----------

*ConfigurationData* \[in\] Dados de ambiente da configuração.

*force* \[in\] **true** para forçar a configuração a parar.

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