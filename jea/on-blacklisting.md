---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: sobre a lista de bloqueios
ms.technology: powershell
ms.openlocfilehash: e823cc0b130500fb7ea60e65acf27f90ad3f3802
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: pt-BR
---
### <a name="on-blacklisting"></a><span data-ttu-id="b868c-103">Sobre lista de bloqueios</span><span class="sxs-lookup"><span data-stu-id="b868c-103">On Blacklisting</span></span>
<span data-ttu-id="b868c-104">Depois de explorar o JEA, você pode estar se perguntando se é possível colocar comandos na lista de bloqueios.</span><span class="sxs-lookup"><span data-stu-id="b868c-104">After playing around with JEA, you may be wondering if it is possible to blacklist commands.</span></span>
<span data-ttu-id="b868c-105">Essa é uma solicitação compreensível, mas ela não está planejada para JEA pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="b868c-105">This is an understandable request, but it is not currently planned for JEA for the following reasons:</span></span>

1.  <span data-ttu-id="b868c-106">Criamos o JEA para limitar os operadores somente às ações que eles precisam realizar.</span><span class="sxs-lookup"><span data-stu-id="b868c-106">We designed JEA to limit operators to only the actions they need to do.</span></span>
<span data-ttu-id="b868c-107">Uma lista de bloqueios é o oposto.</span><span class="sxs-lookup"><span data-stu-id="b868c-107">A blacklist is the opposite.</span></span>

2.  <span data-ttu-id="b868c-108">Os autores de comando do PowerShell não projetaram comandos dele tendo o JEA em mente.</span><span class="sxs-lookup"><span data-stu-id="b868c-108">PowerShell command authors did not design PowerShell commands with the JEA in mind.</span></span>
<span data-ttu-id="b868c-109">Em uma instalação nova do Windows Server 2016, há cerca de 1520 comandos disponíveis imediatamente.</span><span class="sxs-lookup"><span data-stu-id="b868c-109">On a fresh install of Windows Server 2016, there are about 1520 commands immediately available.</span></span>
<span data-ttu-id="b868c-110">Os modelos de ameaças para esses comandos não incluem a possibilidade de que um usuário poderia executar comandos como uma conta com mais privilégios.</span><span class="sxs-lookup"><span data-stu-id="b868c-110">The threat models for these commands did not include the possibility that a user would be running commands as a more privileged account.</span></span>
<span data-ttu-id="b868c-111">Por exemplo, determinados comandos permitem realizar injeção de código por design (por exemplo, Add-Type e Invoke-Command no módulo do núcleo do PowerShell).</span><span class="sxs-lookup"><span data-stu-id="b868c-111">For example, certain commands allow for code injection by design (e.g. Add-Type and Invoke-Command in the core PowerShell module).</span></span>
<span data-ttu-id="b868c-112">O JEA pode avisá-lo quando você expõe os comandos específicos que conhecemos, mas não reavaliamos todos os outros comandos no Windows com base no novo modelo de ameaça.</span><span class="sxs-lookup"><span data-stu-id="b868c-112">JEA can warn you when you expose the specific commands we know about, but we have not re-assessed every other command in Windows based on the new threat model.</span></span>
<span data-ttu-id="b868c-113">Você deve compreender as capacidades dos comandos que são expostos por meio do JEA.</span><span class="sxs-lookup"><span data-stu-id="b868c-113">You must understand the capabilities of the commands you exposing through JEA.</span></span>  

3.  <span data-ttu-id="b868c-114">Além disso, mesmo que o JEA bloqueie todos os comandos com vulnerabilidades de injeção de código, não há nenhuma garantia de que um usuário mal-intencionado não poderá executar uma ação na lista de bloqueios com outro comando relacionado.</span><span class="sxs-lookup"><span data-stu-id="b868c-114">Furthermore, even if JEA blocked all commands with code-injection vulnerabilities, there is no guarantee that a malicious user would not be able to carry out a blacklisted action with another related command.</span></span>
<span data-ttu-id="b868c-115">A menos que você compreenda todos os comandos que estiver expondo, é impossível assegurar que uma determinada ação não será possível.</span><span class="sxs-lookup"><span data-stu-id="b868c-115">Unless you understand all of the commands that you are exposing, it is impossible for you to guarantee that a certain action is not possible.</span></span>
<span data-ttu-id="b868c-116">Cabe a você entender os comandos que você está expondo, seja usando uma lista de permissões ou uma lista de bloqueios.</span><span class="sxs-lookup"><span data-stu-id="b868c-116">The burden is on you to understand what commands you are exposing, whether they are using a whitelist or a blacklist.</span></span>
<span data-ttu-id="b868c-117">O número de comandos que uma lista de bloqueios poderia expor é impossível de gerenciar, portanto o JEA é implementado usando listas de permissões.</span><span class="sxs-lookup"><span data-stu-id="b868c-117">The number of commands a blacklist would expose is unmanageable, so JEA is implemented using whitelists instead.</span></span>

