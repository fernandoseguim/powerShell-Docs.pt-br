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
ms.openlocfilehash: 27c8e2c7525aba38e69e50b2b7fd3b18b8e54989
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794392"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="a8aa9-102">Tutorial de StopProc</span><span class="sxs-lookup"><span data-stu-id="a8aa9-102">StopProc Tutorial</span></span>

<span data-ttu-id="a8aa9-103">Esta seção fornece um tutorial para criar o cmdlet Stop-Proc, que é muito semelhante para o [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet fornecido pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a8aa9-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="a8aa9-104">Este tutorial fornece uma explicação do código e fragmentos de código que ilustram como os cmdlets são implementados.</span><span class="sxs-lookup"><span data-stu-id="a8aa9-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="a8aa9-105">Tópicos neste tutorial</span><span class="sxs-lookup"><span data-stu-id="a8aa9-105">Topics in this Tutorial</span></span>

<span data-ttu-id="a8aa9-106">Os tópicos neste tutorial são criados para serem lidos em sequência, com cada tópico com base no que foi discutido no tópico anterior.</span><span class="sxs-lookup"><span data-stu-id="a8aa9-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="a8aa9-107">[Criação de um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md) esta seção descreve como criar um cmdlet que dá suporte a modificações no sistema, como interromper um processo em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="a8aa9-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="a8aa9-108">[Adicionar mensagens de usuário para o Cmdlet](./adding-user-messages-to-your-cmdlet.md) esta seção descreve como adicionar a capacidade de gravar mensagens de usuário, mensagens de depuração, as mensagens de aviso e informações de progresso do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a8aa9-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="a8aa9-109">[Adicionar Aliases, expansão de curinga e ajudar a parâmetros de Cmdlet](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) esta seção descreve como criar um cmdlet que dá suporte a aliases de parâmetro, ajuda e expansão de curinga.</span><span class="sxs-lookup"><span data-stu-id="a8aa9-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="a8aa9-110">[Adicionando conjuntos de parâmetros aos Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) esta seção descreve como adicionar conjuntos de parâmetros para um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a8aa9-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="a8aa9-111">Conjuntos de parâmetros permitem que o cmdlet operar variam de acordo com quais parâmetros são especificados pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="a8aa9-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8aa9-112">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="a8aa9-112">See Also</span></span>

[<span data-ttu-id="a8aa9-113">Criação de um Cmdlet que modifica o sistema</span><span class="sxs-lookup"><span data-stu-id="a8aa9-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="a8aa9-114">Adicionar mensagens de usuário para o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a8aa9-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="a8aa9-115">Adicionar Aliases, expansão de curinga e ajudar a parâmetros de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a8aa9-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="a8aa9-116">Adicionando o parâmetro define como os Cmdlets</span><span class="sxs-lookup"><span data-stu-id="a8aa9-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="a8aa9-117">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a8aa9-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
