---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método ResourceGet da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 30cbaa907d4dc3a921c9e5fe61ffddc5d61c2347
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método ResourceGet da classe MSFT_DSCLocalConfigurationManager

Chama diretamente o método **Get** de um recurso de DSC.

<a name="syntax"></a>Sintaxe
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a>Parâmetros
----------

*ResourceType* \[in\] O nome do recurso a chamar.

*ModuleName* \[in\] O nome do módulo que contém o recurso a chamar.

*resourceProperty* \[in\] Especifica o nome da propriedade do recurso e o respectivo valor em uma tabela de hash como chave e valor, respectivamente. Use o cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) para descobrir as propriedades de recurso e seus tipos.

*configurations* \[out\] No retorno, contém uma instância inserida das configurações.

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