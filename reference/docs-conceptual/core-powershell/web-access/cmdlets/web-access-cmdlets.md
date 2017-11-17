---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet
ms.date: 2016-12-12
title: cmdlets de acesso via Web
ms.technology: powershell
ms.openlocfilehash: daebe2fe2cbccaf8d3f41d265d23dc45d3bb99b6
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2017
---
# <a name="windows-powershell-web-access-cmdlets"></a><span data-ttu-id="debb5-103">Cmdlets do Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="debb5-103">Windows PowerShell Web Access Cmdlets</span></span>

<span data-ttu-id="debb5-104">Esta referência fornece descrições de cmdlet e a sintaxe para todos os cmdlets específicos do Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="debb5-104">This reference provides cmdlet descriptions and syntax for all Windows PowerShell® Web Access-specific cmdlets.</span></span> <span data-ttu-id="debb5-105">Ela lista os cmdlets em ordem alfabética com base no verbo no início do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="debb5-105">It lists the cmdlets in alphabetical order based on the verb at the beginning of the cmdlet.</span></span>

## <a name="add-pswaauthorizationruleadd-pswaauthorizationrulemd"></a>[<span data-ttu-id="debb5-106">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="debb5-106">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)

<span data-ttu-id="debb5-107">Adiciona uma nova regra de autorização ao conjunto de regras de autorização do Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="debb5-107">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="get-pswaauthorizationruleget-pswaauthorizationrulemd"></a>[<span data-ttu-id="debb5-108">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="debb5-108">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)

<span data-ttu-id="debb5-109">Retorna um conjunto de regras de autorização do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="debb5-109">Returns a set of the Windows PowerShell Web Access authorization rules.</span></span>

## <a name="install-pswawebapplicationinstall-pswawebapplicationmd"></a>[<span data-ttu-id="debb5-110">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="debb5-110">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)

<span data-ttu-id="debb5-111">Configura o aplicativo Web Windows PowerShell Web Access no IIS.</span><span class="sxs-lookup"><span data-stu-id="debb5-111">Configures the Windows PowerShell Web Access web application in IIS.</span></span>

## <a name="remove-pswaauthorizationruleremove-pswaauthorizationrulemd"></a>[<span data-ttu-id="debb5-112">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="debb5-112">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)

<span data-ttu-id="debb5-113">Remove uma regra de autorização especificada do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="debb5-113">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="test-pswaauthorizationruletest-pswaauthorizationrulemd"></a>[<span data-ttu-id="debb5-114">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="debb5-114">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)

<span data-ttu-id="debb5-115">Testa as regras de autorização para validar se uma determinada solicitação de acesso de usuário, de computador ou de ponto de extremidade está autorizada.</span><span class="sxs-lookup"><span data-stu-id="debb5-115">Tests authorization rules to validate that a particular user, computer, endpoint access request is authorized.</span></span>

## <a name="uninstall-pswawebapplicationuninstall-pswawebapplicationmd"></a>[<span data-ttu-id="debb5-116">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="debb5-116">Uninstall-PswaWebApplication</span></span>](uninstall-pswawebapplication.md)

<span data-ttu-id="debb5-117">Desinstala o aplicativo Web Windows PowerShell do IIS.</span><span class="sxs-lookup"><span data-stu-id="debb5-117">Uninstalls the Windows PowerShell web application from IIS.</span></span>

><span data-ttu-id="debb5-118">**Observação**:</span><span class="sxs-lookup"><span data-stu-id="debb5-118">**Note**:</span></span>
>
><span data-ttu-id="debb5-119">Para listar todos os cmdlets que estão disponíveis, use o:</span><span class="sxs-lookup"><span data-stu-id="debb5-119">To list all the cmdlets that are available, use the:</span></span>
>
> <span data-ttu-id="debb5-120">cmdlet `Get-Command –Module PowerShellWebAccess`.</span><span class="sxs-lookup"><span data-stu-id="debb5-120">`Get-Command –Module PowerShellWebAccess` cmdlet.</span></span>

<span data-ttu-id="debb5-121">Para saber mais informações ou para obter a sintaxe de qualquer um dos cmdlets, use:</span><span class="sxs-lookup"><span data-stu-id="debb5-121">For more information about, or for the syntax of, any of the cmdlets, use:</span></span>  
<span data-ttu-id="debb5-122">`Get-Help `*&lt;nome do cmdlet&gt;*</span><span class="sxs-lookup"><span data-stu-id="debb5-122">`Get-Help `*&lt;cmdlet name&gt;*</span></span>  
<span data-ttu-id="debb5-123">em que *&lt;nome do cmdlet&gt;* é o nome do cmdlet que você deseja pesquisar.</span><span class="sxs-lookup"><span data-stu-id="debb5-123">where *&lt;cmdlet name&gt;* is the name of the cmdlet that you want to research.</span></span>

<span data-ttu-id="debb5-124">Para obter mais informações, você pode executar qualquer um dos seguintes cmdlets:</span><span class="sxs-lookup"><span data-stu-id="debb5-124">For more detailed information, you can run any of the following cmdlets:</span></span>

- <span data-ttu-id="debb5-125">`Get-Help `*&lt;nome do cmdlet&gt;*` -Detailed`</span><span class="sxs-lookup"><span data-stu-id="debb5-125">`Get-Help `*&lt;cmdlet name&gt;*` -Detailed`</span></span>
- <span data-ttu-id="debb5-126">`Get-Help `*&lt;nome do cmdlet&gt;*` -Examples`</span><span class="sxs-lookup"><span data-stu-id="debb5-126">`Get-Help `*&lt;cmdlet name&gt;*` -Examples`</span></span>
- <span data-ttu-id="debb5-127">`Get-Help `*&lt;nome do cmdlet&gt;*` -Full`</span><span class="sxs-lookup"><span data-stu-id="debb5-127">`Get-Help `*&lt;cmdlet name&gt;*` -Full`</span></span>

### <a name="more-information"></a><span data-ttu-id="debb5-128">Mais Informações</span><span class="sxs-lookup"><span data-stu-id="debb5-128">More Information</span></span>

<span data-ttu-id="debb5-129">Para obter mais informações sobre o PowerShell Web Access, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="debb5-129">For more information about PowerShell Web Access, see the following:</span></span>

- [<span data-ttu-id="debb5-130">Instalar e usar o Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="debb5-130">Install and Use Windows PowerShell Web Access</span></span>](../install-and-use-windows-powershell-web-access.md)

