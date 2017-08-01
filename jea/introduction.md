---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "introdução"
ms.technology: powershell
ms.openlocfilehash: 71264d1001228249d9f2bb0f72473e9761170bf0
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: pt-BR
---
# <a name="introduction"></a><span data-ttu-id="3128d-103">Introdução</span><span class="sxs-lookup"><span data-stu-id="3128d-103">Introduction</span></span>

##  <a name="motivation"></a><span data-ttu-id="3128d-104">**Motivação**</span><span class="sxs-lookup"><span data-stu-id="3128d-104">**Motivation**</span></span>  
<span data-ttu-id="3128d-105">Quando você concede acesso privilegiado aos sistemas a alguém, está oferecendo seu limite de confiança para essa pessoa.</span><span class="sxs-lookup"><span data-stu-id="3128d-105">When you grant someone privileged access to your systems, you extend your trust boundary to that person.</span></span>
<span data-ttu-id="3128d-106">Esse é um risco, pois os administradores são uma superfície de ataque.</span><span class="sxs-lookup"><span data-stu-id="3128d-106">This is a risk -- administrators are an attack surface.</span></span>
<span data-ttu-id="3128d-107">Ataques internos e roubo de credenciais são reais e comuns.</span><span class="sxs-lookup"><span data-stu-id="3128d-107">Insider attacks and stolen credentials are both real and common.</span></span>

##  <a name="not-a-new-problem"></a><span data-ttu-id="3128d-108">**Não é um novo problema**</span><span class="sxs-lookup"><span data-stu-id="3128d-108">**Not a new problem**</span></span>  
<span data-ttu-id="3128d-109">Você provavelmente conhece muito bem o princípio de privilégio mínimo e pode usar alguma forma de RBAC (controle de acesso baseado em função) com aplicativos que o fornecem.</span><span class="sxs-lookup"><span data-stu-id="3128d-109">You are probably very familiar with the principle of least privilege, and you might use some form of role-based access control (RBAC) with applications that provide it.</span></span>
<span data-ttu-id="3128d-110">No entanto, a eficiência e a gerenciabilidade dessas soluções geralmente são limitadas por seu escopo amplo e imprecisão.</span><span class="sxs-lookup"><span data-stu-id="3128d-110">However, the effectiveness and manageability of these solutions are often limited by their broad scope and imprecision.</span></span>
<span data-ttu-id="3128d-111">Além disso, existem lacunas na cobertura do RBAC.</span><span class="sxs-lookup"><span data-stu-id="3128d-111">Furthermore, there are gaps in RBAC coverage.</span></span>
<span data-ttu-id="3128d-112">Por exemplo, no Windows, o acesso privilegiado é basicamente um comutador binário, o que força você a conceder permissões desnecessárias ao adicionar usuários ao grupo Administradores.</span><span class="sxs-lookup"><span data-stu-id="3128d-112">For example, in Windows, privileged access is largely a binary switch, forcing you to give unnecessary permissions when adding users to the Administrators group.</span></span>

##  <a name="just-enough-administration-jea"></a><span data-ttu-id="3128d-113">**JEA (Administração Suficiente)**</span><span class="sxs-lookup"><span data-stu-id="3128d-113">**Just Enough Administration (JEA)**</span></span> 
<span data-ttu-id="3128d-114">Fornece uma plataforma de RBAC (controle de acesso baseado em função) por meio da Comunicação Remota do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3128d-114">Provides a role-based access control (RBAC) platform through PowerShell Remoting.</span></span>
<span data-ttu-id="3128d-115">*Ele permite que usuários específicos executem tarefas administrativas específicas nos servidores sem conceder direitos de administrador.*</span><span class="sxs-lookup"><span data-stu-id="3128d-115">*It allows specific users to perform specific administrative tasks on servers without giving them administrator rights.*</span></span>
<span data-ttu-id="3128d-116">Isso permite que você preencha as lacunas entre suas soluções existentes de RBAC e simplifica o gerenciamento dessas configurações.</span><span class="sxs-lookup"><span data-stu-id="3128d-116">This allows you to fill in the gaps between your existing RBAC solutions, and simplifies management of those settings.</span></span>

