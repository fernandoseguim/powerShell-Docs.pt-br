---
title: Escrevendo um fluxo de trabalho do Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 4f0be193fb5b5c753d040a48e5f49235ece11708
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857402"
---
# <a name="writing-a-windows-powershell-workflow"></a>Escrevendo um Fluxo de Trabalho do Windows PowerShell

Você pode criar um fluxo de trabalho XAML, adicionando atividades expostas por assemblies do Windows PowerShell para o designer de fluxo de trabalho no Visual Studio. Os seguintes assemblies do Windows PowerShell expõem as atividades de fluxo de trabalho.

> [!IMPORTANT]
> Um fluxo de trabalho XAML deve ser empacotado como um módulo, se você quiser fornecer ajuda para o fluxo de trabalho. Para obter informações sobre os módulos, consulte [escrevendo um módulo do Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities)

- [Microsoft.Powershell.Core.Activities](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [Microsoft.Powershell.Diagnostics.Activities](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [Microsoft.Powershell.Security.Activities](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [Microsoft.Powershell.Utility.Activities](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  Os tópicos a seguir descrevem como criar um fluxo de trabalho usando atividades do Windows PowerShell.

- [Adicionando atividades do Windows PowerShell para a caixa de ferramentas do Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [Criando um fluxo de trabalho com atividades do Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md)

- [Criando um fluxo de trabalho usando um Script do Windows PowerShell](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [Importando e chamar um fluxo de trabalho do Windows PowerShell](./importing-and-invoking-a-windows-powershell-workflow.md)

- [Criando uma atividade de fluxo de trabalho de um Cmdlet do Windows PowerShell](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)