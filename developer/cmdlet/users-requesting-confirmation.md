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
ms.openlocfilehash: e4abbb14b31406b845d9b6af6b6372338fb0d926
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856232"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="b4898-102">Usuários que solicitam confirmação</span><span class="sxs-lookup"><span data-stu-id="b4898-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="b4898-103">Quando você especifica um valor de `true` para o `SupportsShouldProcess` parâmetro da declaração de atributo do Cmdlet, em que os usuários podem especificar o `Confirm` parâmetro no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="b4898-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="b4898-104">No ambiente padrão, os usuários podem especificar o `Confirm` parâmetro ou `"-Confirm:$true` para que a confirmação é solicitada quando o [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método é chamado.</span><span class="sxs-lookup"><span data-stu-id="b4898-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="b4898-105">Isso ignora [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) solicitações de confirmação, mesmo para operações de alto impacto.</span><span class="sxs-lookup"><span data-stu-id="b4898-105">This bypasses [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="b4898-106">Se `Confirm` não for especificado, o [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamada solicita confirmação se a `$ConfirmPreference` variável de preferência é igual ou maior que o `ConfirmImpact` configuração das cmdlet ou provedor.</span><span class="sxs-lookup"><span data-stu-id="b4898-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="b4898-107">A configuração padrão de `$ConfirmPreference` é alta.</span><span class="sxs-lookup"><span data-stu-id="b4898-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="b4898-108">Portanto, no ambiente padrão, somente cmdlets e provedores que especificam uma ação de alto impacto solicitam confirmação.</span><span class="sxs-lookup"><span data-stu-id="b4898-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="b4898-109">Se `Confirm` for false ou se `"-Confirm:$false` for especificado, o [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamada solicita a confirmação do usuário e o `$ConfirmPreference` variável do shell é ignorado.</span><span class="sxs-lookup"><span data-stu-id="b4898-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4898-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4898-110">Remarks</span></span>

- <span data-ttu-id="b4898-111">Para cmdlets e provedores que especificam `SupportsShouldProcess`, mas não `ConfirmImpact`, essas ações são tratadas como ações de "impacto médio", e eles não solicitar por padrão.</span><span class="sxs-lookup"><span data-stu-id="b4898-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="b4898-112">Seu nível de impacto é menor que a configuração padrão da `$ConfirmPreference` variável de preferência.</span><span class="sxs-lookup"><span data-stu-id="b4898-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="b4898-113">Se o usuário especificar o `Verbose` parâmetro, eles serão notificados sobre a operação, mesmo se eles não for solicitada uma confirmação.</span><span class="sxs-lookup"><span data-stu-id="b4898-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4898-114">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="b4898-114">See Also</span></span>

<span data-ttu-id="b4898-115">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="b4898-115">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
