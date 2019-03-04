---
title: Tutorial de GetProc | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862452"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="dccf0-102">Tutorial de GetProc</span><span class="sxs-lookup"><span data-stu-id="dccf0-102">GetProc Tutorial</span></span>

<span data-ttu-id="dccf0-103">Esta seção fornece um tutorial para criação de um cmdlet Get-Proc é muito semelhante do [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet fornecido pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dccf0-103">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="dccf0-104">Este tutorial fornece uma explicação do código e fragmentos de código que ilustram como os cmdlets são implementados.</span><span class="sxs-lookup"><span data-stu-id="dccf0-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="dccf0-105">Tópicos neste tutorial</span><span class="sxs-lookup"><span data-stu-id="dccf0-105">Topics in this Tutorial</span></span>

<span data-ttu-id="dccf0-106">Os tópicos neste tutorial são criados para serem lidos em sequência, com cada tópico com base no que foi discutido no tópico anterior.</span><span class="sxs-lookup"><span data-stu-id="dccf0-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="dccf0-107">[Criação de um Cmdlet sem parâmetros](./creating-a-cmdlet-without-parameters.md) esta seção descreve como criar um cmdlet que recupera informações do computador local sem o uso de parâmetros e, em seguida, grava as informações para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="dccf0-107">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="dccf0-108">[Adicionar parâmetros de entrada de linha de comando desse processo](./adding-parameters-that-process-command-line-input.md) esta seção descreve como adicionar um parâmetro para o cmdlet Get-Proc para que o cmdlet pode processar a entrada com base em objetos explícitos passados para o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dccf0-108">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="dccf0-109">A implementação descrita aqui recupera processos com base em seu nome e, em seguida, grava as informações para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="dccf0-109">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="dccf0-110">[Adicionando parâmetros de entrada do Pipeline esse processo](./adding-parameters-that-process-pipeline-input.md) esta seção descreve como adicionar um parâmetro para o cmdlet Get-Proc para que o cmdlet pode processar objetos passados para ele por meio do pipeline.</span><span class="sxs-lookup"><span data-stu-id="dccf0-110">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="dccf0-111">O cmdlet de implementação descrito aqui recupera processos com base em objetos passados para o cmdlet e, em seguida, grava as informações para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="dccf0-111">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="dccf0-112">[Adicionando o relatório de erros sem encerramento para o Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) esta seção descreve como adicionar relatórios a um cmdlet de erros sem encerramento.</span><span class="sxs-lookup"><span data-stu-id="dccf0-112">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="dccf0-113">A implementação descrita aqui detecta erros de não encerramento que ocorrem durante o processamento de entrada e grava um registro de erro no fluxo de erro.</span><span class="sxs-lookup"><span data-stu-id="dccf0-113">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="dccf0-114">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="dccf0-114">See Also</span></span>

[<span data-ttu-id="dccf0-115">Criação de um Cmdlet sem parâmetros</span><span class="sxs-lookup"><span data-stu-id="dccf0-115">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="dccf0-116">Adicionar parâmetros que processam a entrada de linha de comando</span><span class="sxs-lookup"><span data-stu-id="dccf0-116">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="dccf0-117">Adicionar parâmetros de entrada do Pipeline de processo</span><span class="sxs-lookup"><span data-stu-id="dccf0-117">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="dccf0-118">Adição do cmdlet de relatório de erros sem encerramento</span><span class="sxs-lookup"><span data-stu-id="dccf0-118">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="dccf0-119">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dccf0-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
