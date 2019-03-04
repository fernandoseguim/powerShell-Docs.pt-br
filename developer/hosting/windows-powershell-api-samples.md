---
title: Exemplos de API do PowerShell do Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860772"
---
# <a name="windows-powershell-api-samples"></a><span data-ttu-id="1f6b1-102">Amostras de API do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f6b1-102">Windows PowerShell API Samples</span></span>

<span data-ttu-id="1f6b1-103">Esta seção inclui o código de exemplo que mostra como criar espaços de execução que restringem a funcionalidade e como executar assincronamente comandos por meio de um pool de Runspaces para fornecer os espaços de execução.</span><span class="sxs-lookup"><span data-stu-id="1f6b1-103">This section includes sample code that shows how to create runspaces that restrict functionality, and how to asynchronously run commands by using a runspace pool to supply the runspaces.</span></span> <span data-ttu-id="1f6b1-104">Você pode usar o Microsoft Visual Studio para criar um aplicativo de console e, em seguida, copie o código entre os tópicos nesta seção para seu aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="1f6b1-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1f6b1-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1f6b1-105">In This Section</span></span>

<span data-ttu-id="1f6b1-106">[Exemplo de PowerShell01](./windows-powershell01-sample.md) Este exemplo mostra como usar um [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto para limitar a funcionalidade de um espaço de execução.</span><span class="sxs-lookup"><span data-stu-id="1f6b1-106">[PowerShell01 Sample](./windows-powershell01-sample.md) This sample shows how to use an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to limit the functionality of a runspace.</span></span> <span data-ttu-id="1f6b1-107">A saída deste exemplo demonstra como restringir o modo de linguagem do runspace, como marcar um cmdlet como particulares, como adicionar e remover cmdlets e provedores, como adicionar um comando de proxy e muito mais.</span><span class="sxs-lookup"><span data-stu-id="1f6b1-107">The output of this sample demonstrates how to restrict the language mode of the runspace, how to mark a cmdlet as private, how to add and remove cmdlets and providers, how to add a proxy command, and more.</span></span>

<span data-ttu-id="1f6b1-108">[Exemplo de PowerShell02](./windows-powershell02-sample.md) Este exemplo mostra como executar comandos de forma assíncrona usando os espaços de execução de um pool de Runspaces.</span><span class="sxs-lookup"><span data-stu-id="1f6b1-108">[PowerShell02 Sample](./windows-powershell02-sample.md) This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="1f6b1-109">O exemplo gera uma lista de comandos e, em seguida, executa esses comandos, enquanto o mecanismo Windows PowerShell abre um espaço de execução do pool quando ele for necessário.</span><span class="sxs-lookup"><span data-stu-id="1f6b1-109">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>