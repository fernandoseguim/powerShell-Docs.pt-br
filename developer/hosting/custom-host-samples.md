---
title: Exemplos de Host personalizado | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794137"
---
# <a name="custom-host-samples"></a><span data-ttu-id="244fc-102">Amostras de host personalizadas</span><span class="sxs-lookup"><span data-stu-id="244fc-102">Custom Host Samples</span></span>

<span data-ttu-id="244fc-103">Esta seção inclui o código de exemplo para a gravação de um host personalizado.</span><span class="sxs-lookup"><span data-stu-id="244fc-103">This section includes sample code for writing a custom host.</span></span> <span data-ttu-id="244fc-104">Você pode usar o Microsoft Visual Studio para criar um aplicativo de console e, em seguida, copie o código entre os tópicos nesta seção para seu aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="244fc-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="244fc-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="244fc-105">In This Section</span></span>

 <span data-ttu-id="244fc-106">[Exemplo de Host01](./host01-sample.md) Este exemplo mostra como implementar um aplicativo host que usa um host personalizado básico.</span><span class="sxs-lookup"><span data-stu-id="244fc-106">[Host01 Sample](./host01-sample.md) This sample shows how to implement a host application that uses a basic custom host.</span></span>

 <span data-ttu-id="244fc-107">[Exemplo de Host02](./host02-sample.md) Este exemplo mostra como escrever um aplicativo host que usa o tempo de execução do Windows PowerShell, juntamente com uma implementação de host personalizado.</span><span class="sxs-lookup"><span data-stu-id="244fc-107">[Host02 Sample](./host02-sample.md) This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="244fc-108">O aplicativo host define a cultura do host para alemão, executa o [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet e exibe os resultados que você veria usando pwrsh.exe e, em seguida, imprime a data e hora atuais em alemão.</span><span class="sxs-lookup"><span data-stu-id="244fc-108">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them using pwrsh.exe, and then prints out the current data and time in German.</span></span>

 <span data-ttu-id="244fc-109">[Exemplo de Host03](./host03-sample.md) Este exemplo mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, exibe os resultados no console.</span><span class="sxs-lookup"><span data-stu-id="244fc-109">[Host03 Sample](./host03-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

 <span data-ttu-id="244fc-110">[Exemplo de Host04](./host04-sample.md) Este exemplo mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, exibe os resultados no console.</span><span class="sxs-lookup"><span data-stu-id="244fc-110">[Host04 Sample](./host04-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="244fc-111">Esse aplicativo host também dá suporte a exibições de avisos que permitem ao usuário especificar várias opções.</span><span class="sxs-lookup"><span data-stu-id="244fc-111">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

 <span data-ttu-id="244fc-112">[Exemplo de Host05](./host05-sample.md) Este exemplo mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, exibe os resultados no console.</span><span class="sxs-lookup"><span data-stu-id="244fc-112">[Host05 Sample](./host05-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="244fc-113">Este aplicativo host também dá suporte a chamadas para computadores remotos usando o [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) e [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span><span class="sxs-lookup"><span data-stu-id="244fc-113">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span></span>

 <span data-ttu-id="244fc-114">[Exemplo de Host06](./host06-sample.md) Este exemplo mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, exibe os resultados no console.</span><span class="sxs-lookup"><span data-stu-id="244fc-114">[Host06 Sample](./host06-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="244fc-115">Além disso, este exemplo usa as APIs do Criador de Token para especificar a cor do texto inserido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="244fc-115">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="244fc-116">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="244fc-116">See Also</span></span>
