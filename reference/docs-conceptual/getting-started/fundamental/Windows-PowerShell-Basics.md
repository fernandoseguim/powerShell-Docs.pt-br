---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: "Noções básicas do Windows PowerShell"
ms.assetid: 6b3cbbc8-060c-4877-b00b-7300dbbe4e28
ms.openlocfilehash: f8a520f1fbe97737c7d0c2acab0129f88b5ed425
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
# <a name="windows-powershell-basics"></a><span data-ttu-id="59032-103">Noções básicas do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="59032-103">Windows PowerShell Basics</span></span>
<span data-ttu-id="59032-104">Interfaces do usuário gráficas usam alguns conceitos básicos que são conhecidos para a maioria dos usuários do computador.</span><span class="sxs-lookup"><span data-stu-id="59032-104">Graphical user interfaces use some basic concepts that are well known to most computer users.</span></span> <span data-ttu-id="59032-105">Os usuários contam com a familiaridade dessas interfaces para realizar tarefas.</span><span class="sxs-lookup"><span data-stu-id="59032-105">Users rely on the familiarity of those interfaces to accomplish tasks.</span></span> <span data-ttu-id="59032-106">Os sistemas operacionais apresentam aos usuários uma representação gráfica dos itens que podem ser explorados, geralmente com menus suspensos para acesso a funcionalidades específicas e menus de contexto para acesso a funcionalidades específicas de contexto.</span><span class="sxs-lookup"><span data-stu-id="59032-106">Operating systems present users with a graphical representation of items that can be browsed, usually with drop-down menus for accessing specific functionality and context menus for accessing context-specific functionality.</span></span>

<span data-ttu-id="59032-107">Uma CLI (Interface de Linha de Comando), como o Windows PowerShell, deve usar uma abordagem diferente para expor informações, pois não apresenta menus ou sistemas gráficos para ajudar o usuário.</span><span class="sxs-lookup"><span data-stu-id="59032-107">A command-line interface (CLI), such as Windows PowerShell, must use a different approach to expose information, because it does not have menus or graphical systems to help the user.</span></span> <span data-ttu-id="59032-108">Você precisa saber os nomes de comando para poder usá-los.</span><span class="sxs-lookup"><span data-stu-id="59032-108">You need to know command names before you can use them.</span></span> <span data-ttu-id="59032-109">Embora seja possível digitar comandos complexos que são equivalentes aos recursos em um ambiente de GUI, você deve se familiarizar com os comandos mais frequentemente usados e os parâmetros de comando.</span><span class="sxs-lookup"><span data-stu-id="59032-109">Although you can type complex commands that are equivalent to the features in a GUI environment, you must become familiar with commonly-used commands and command parameters.</span></span>

<span data-ttu-id="59032-110">A maioria das CLIs não tem padrões que podem ajudar o usuário a aprender a interface.</span><span class="sxs-lookup"><span data-stu-id="59032-110">Most CLIs do not have patterns that can help the user to learn the interface.</span></span> <span data-ttu-id="59032-111">Como as CLIs foram os primeiros shells de sistema operacional, muitos nomes de comandos e parâmetros foram selecionados arbitrariamente.</span><span class="sxs-lookup"><span data-stu-id="59032-111">Because CLIs were the first operating system shells, many command names and parameter names were selected arbitrarily.</span></span> <span data-ttu-id="59032-112">Nomes de comando concisos geralmente eram escolhidos em vez de nomes claros.</span><span class="sxs-lookup"><span data-stu-id="59032-112">Terse command names were generally chosen over clear ones.</span></span> <span data-ttu-id="59032-113">Embora os sistemas de ajuda e padrões de design de comando estejam integrados à maioria das CLIs, eles em geral foram projetados para compatibilidade com os comandos mais antigos, portanto o conjunto de comandos ainda é modelado por decisões tomadas décadas atrás.</span><span class="sxs-lookup"><span data-stu-id="59032-113">Although help systems and command design standards are integrated into most CLIs, they have been generally designed for compatibility with the earliest commands, so the command set is still shaped by decisions made decades ago.</span></span>

<span data-ttu-id="59032-114">O Windows PowerShell foi projetado para aproveitar o conhecimento histórico de um usuário de CLIs.</span><span class="sxs-lookup"><span data-stu-id="59032-114">Windows PowerShell was designed to take advantage of a user's historic knowledge of CLIs.</span></span> <span data-ttu-id="59032-115">Neste capítulo, abordaremos algumas ferramentas e conceitos básicos que você pode usar para aprender a usar o Windows PowerShell rapidamente.</span><span class="sxs-lookup"><span data-stu-id="59032-115">In this chapter, we will talk about some basic tools and concepts that you can use to learn Windows PowerShell quickly.</span></span> <span data-ttu-id="59032-116">Elas incluem:</span><span class="sxs-lookup"><span data-stu-id="59032-116">They include:</span></span>

-   <span data-ttu-id="59032-117">Uso de Get-Command</span><span class="sxs-lookup"><span data-stu-id="59032-117">Using Get-Command</span></span>

-   <span data-ttu-id="59032-118">Usar comandos de Cmd.exe e de UNIX</span><span class="sxs-lookup"><span data-stu-id="59032-118">Using Cmd.exe and UNIX commands</span></span>

-   <span data-ttu-id="59032-119">Usar comandos externos</span><span class="sxs-lookup"><span data-stu-id="59032-119">Using External Commands</span></span>

-   <span data-ttu-id="59032-120">Uso de Tab-Completion</span><span class="sxs-lookup"><span data-stu-id="59032-120">Using Tab-Completion</span></span>

-   <span data-ttu-id="59032-121">Uso de Get-Help</span><span class="sxs-lookup"><span data-stu-id="59032-121">Using Get-Help</span></span>

