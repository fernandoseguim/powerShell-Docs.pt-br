---
title: Usuários que solicitam confirmação | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059551"
---
# <a name="users-requesting-confirmation"></a>Usuários que solicitam confirmação

Quando você especifica um valor de `true` para o `SupportsShouldProcess` parâmetro da declaração de atributo do Cmdlet, em que os usuários podem especificar o `Confirm` parâmetro no prompt de comando.

No ambiente padrão, os usuários podem especificar o `Confirm` parâmetro ou `"-Confirm:$true` para que a confirmação é solicitada quando o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método é chamado. Isso ignora [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) solicitações de confirmação, mesmo para operações de alto impacto.

Se `Confirm` não for especificado, o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamada solicita confirmação se a `$ConfirmPreference` variável de preferência é igual ou maior que o `ConfirmImpact` configuração das cmdlet ou provedor. A configuração padrão de `$ConfirmPreference` é alta. Portanto, no ambiente padrão, somente cmdlets e provedores que especificam uma ação de alto impacto solicitam confirmação.

Se `Confirm` for false ou se `"-Confirm:$false` for especificado, o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamada solicita a confirmação do usuário e o `$ConfirmPreference` variável do shell é ignorado.

## <a name="remarks"></a>Comentários

- Para cmdlets e provedores que especificam `SupportsShouldProcess`, mas não `ConfirmImpact`, essas ações são tratadas como ações de "impacto médio", e eles não solicitar por padrão. Seu nível de impacto é menor que a configuração padrão da `$ConfirmPreference` variável de preferência.

- Se o usuário especificar o `Verbose` parâmetro, eles serão notificados sobre a operação, mesmo se eles não for solicitada uma confirmação.

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
