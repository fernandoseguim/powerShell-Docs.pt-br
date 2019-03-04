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
# <a name="windows-powershell-api-samples"></a>Amostras de API do Windows PowerShell

Esta seção inclui o código de exemplo que mostra como criar espaços de execução que restringem a funcionalidade e como executar assincronamente comandos por meio de um pool de Runspaces para fornecer os espaços de execução. Você pode usar o Microsoft Visual Studio para criar um aplicativo de console e, em seguida, copie o código entre os tópicos nesta seção para seu aplicativo host.

## <a name="in-this-section"></a>Nesta seção

[Exemplo de PowerShell01](./windows-powershell01-sample.md) Este exemplo mostra como usar um [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto para limitar a funcionalidade de um espaço de execução. A saída deste exemplo demonstra como restringir o modo de linguagem do runspace, como marcar um cmdlet como particulares, como adicionar e remover cmdlets e provedores, como adicionar um comando de proxy e muito mais.

[Exemplo de PowerShell02](./windows-powershell02-sample.md) Este exemplo mostra como executar comandos de forma assíncrona usando os espaços de execução de um pool de Runspaces. O exemplo gera uma lista de comandos e, em seguida, executa esses comandos, enquanto o mecanismo Windows PowerShell abre um espaço de execução do pool quando ele for necessário.