---
title: Tutorial de StopProc | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a142aeb6-9c11-44a0-b34f-1f9470fa347b
caps.latest.revision: 5
ms.openlocfilehash: 6e1c8a4709988adfa59bda14eb3af52b0a79f1df
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856352"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="9661a-102">Tutorial de StopProc</span><span class="sxs-lookup"><span data-stu-id="9661a-102">StopProc Tutorial</span></span>

<span data-ttu-id="9661a-103">Esta seção fornece um tutorial para criar o cmdlet Stop-Proc, que é muito semelhante para o [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet fornecido pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9661a-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="9661a-104">Este tutorial fornece uma explicação do código e fragmentos de código que ilustram como os cmdlets são implementados.</span><span class="sxs-lookup"><span data-stu-id="9661a-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>
<span data-ttu-id="9661a-105">Esta seção fornece um tutorial para criar o cmdlet Stop-Proc, que é muito semelhante para o [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet fornecido pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9661a-105">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="9661a-106">Este tutorial fornece uma explicação do código e fragmentos de código que ilustram como os cmdlets são implementados.</span><span class="sxs-lookup"><span data-stu-id="9661a-106">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="9661a-107">Tópicos neste tutorial</span><span class="sxs-lookup"><span data-stu-id="9661a-107">Topics in this Tutorial</span></span>

<span data-ttu-id="9661a-108">Os tópicos neste tutorial são criados para serem lidos em sequência, com cada tópico com base no que foi discutido no tópico anterior.</span><span class="sxs-lookup"><span data-stu-id="9661a-108">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="9661a-109">[Criação de um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md) esta seção descreve como criar um cmdlet que dá suporte a modificações no sistema, como interromper um processo em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="9661a-109">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="9661a-110">[Adicionar mensagens de usuário para o Cmdlet](./adding-user-messages-to-your-cmdlet.md) esta seção descreve como adicionar a capacidade de gravar mensagens de usuário, mensagens de depuração, as mensagens de aviso e informações de progresso do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9661a-110">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="9661a-111">[Adicionar Aliases, expansão de curinga e ajudar a parâmetros de Cmdlet](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) esta seção descreve como criar um cmdlet que dá suporte a aliases de parâmetro, ajuda e expansão de curinga.</span><span class="sxs-lookup"><span data-stu-id="9661a-111">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="9661a-112">[Adicionando conjuntos de parâmetros aos Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) esta seção descreve como adicionar conjuntos de parâmetros para um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9661a-112">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="9661a-113">Conjuntos de parâmetros permitem que o cmdlet operar variam de acordo com quais parâmetros são especificados pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="9661a-113">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="9661a-114">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="9661a-114">See Also</span></span>

[<span data-ttu-id="9661a-115">Criação de um Cmdlet que modifica o sistema</span><span class="sxs-lookup"><span data-stu-id="9661a-115">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="9661a-116">Adicionar mensagens de usuário para o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9661a-116">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="9661a-117">Adicionar Aliases, expansão de curinga e ajudar a parâmetros de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9661a-117">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="9661a-118">Adicionando o parâmetro define como os Cmdlets</span><span class="sxs-lookup"><span data-stu-id="9661a-118">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="9661a-119">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9661a-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
