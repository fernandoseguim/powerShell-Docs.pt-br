---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método ResourceSet da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2712b7ff0a19e643c1f343d436c084f8970c9dd4
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892093"
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método ResourceSet da classe MSFT_DSCLocalConfigurationManager

Chama diretamente o método **Set** de um recurso de DSC.

## <a name="syntax"></a>Sintaxe

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a>Parâmetros

*ResourceType* \[in\] O nome do recurso a chamar.

*ModuleName* \[in\] O nome do módulo que contém o recurso a chamar.

*resourceProperty* \[in\] Especifica o nome da propriedade do recurso e o respectivo valor em uma tabela de hash como chave e valor, respectivamente. Use o cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) para descobrir as propriedades de recurso e seus tipos.

*RebootRequired* \[out\] No retorno, essa propriedade será definida como **true**, se for necessário reiniciar o nó de destino.

## <a name="return-value"></a>Retornar valor

Retorna zero em caso de êxito; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários

Esse é um método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Consulte também

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)