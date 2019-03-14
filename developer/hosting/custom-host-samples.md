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
# <a name="custom-host-samples"></a>Amostras de host personalizadas

Esta seção inclui o código de exemplo para a gravação de um host personalizado. Você pode usar o Microsoft Visual Studio para criar um aplicativo de console e, em seguida, copie o código entre os tópicos nesta seção para seu aplicativo host.

## <a name="in-this-section"></a>Nesta seção

 [Exemplo de Host01](./host01-sample.md) Este exemplo mostra como implementar um aplicativo host que usa um host personalizado básico.

 [Exemplo de Host02](./host02-sample.md) Este exemplo mostra como escrever um aplicativo host que usa o tempo de execução do Windows PowerShell, juntamente com uma implementação de host personalizado. O aplicativo host define a cultura do host para alemão, executa o [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet e exibe os resultados que você veria usando pwrsh.exe e, em seguida, imprime a data e hora atuais em alemão.

 [Exemplo de Host03](./host03-sample.md) Este exemplo mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, exibe os resultados no console.

 [Exemplo de Host04](./host04-sample.md) Este exemplo mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, exibe os resultados no console. Esse aplicativo host também dá suporte a exibições de avisos que permitem ao usuário especificar várias opções.

 [Exemplo de Host05](./host05-sample.md) Este exemplo mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, exibe os resultados no console. Este aplicativo host também dá suporte a chamadas para computadores remotos usando o [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) e [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets

 [Exemplo de Host06](./host06-sample.md) Este exemplo mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, exibe os resultados no console. Além disso, este exemplo usa as APIs do Criador de Token para especificar a cor do texto inserido pelo usuário.

## <a name="see-also"></a>Consulte Também
