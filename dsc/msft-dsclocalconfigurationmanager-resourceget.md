---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método ResourceGet da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1b74adf2327af2e0f9416f1d00eac4e3b75e9013
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893198"
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método ResourceGet da classe MSFT_DSCLocalConfigurationManager

Chama diretamente o método **Get** de um recurso de DSC.

## <a name="syntax"></a>Sintaxe

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a>Parâmetros

*ResourceType* \[in\] O nome do recurso a chamar.

*ModuleName* \[in\] O nome do módulo que contém o recurso a chamar.

*resourceProperty* \[in\] Especifica o nome da propriedade do recurso e o respectivo valor em uma tabela de hash como chave e valor, respectivamente. Use o cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) para descobrir as propriedades de recurso e seus tipos.

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