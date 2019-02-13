---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método ResourceTest da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e7645b0c6b93b96cb01f72c1c92d468f7642ea13
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675830"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método ResourceTest da classe MSFT_DSCLocalConfigurationManager

Chama diretamente o método **Test** de um recurso de DSC.

## <a name="syntax"></a>Sintaxe

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a>Parâmetros

*ResourceType* \[in\] O nome do recurso a chamar.

*ModuleName* \[in\] O nome do módulo que contém o recurso a chamar.

*resourceProperty* \[in\] Especifica o nome da propriedade do recurso e o respectivo valor em uma tabela de hash como chave e valor, respectivamente. Use o cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) para descobrir as propriedades de recurso e seus tipos.

*InDesiredState* \[out\] No retorno, essa propriedade será definida como **true** se o nó de destino estiver no estado desejado.

## <a name="return-value"></a>Retornar valor

Retorna zero em caso de êxito; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários

Esse é um método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Consulte também

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)