---
title: Exemplos de Runspace | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c92a6d3d-8d34-4a76-bdc3-dea923d9858e
caps.latest.revision: 17
ms.openlocfilehash: e24d40746da91f60aaf2af655ddcadc88ab6a4db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857332"
---
# <a name="runspace-samples"></a>Amostras de runspace

Esta seção inclui o código de exemplo que mostra como usar tipos diferentes de espaços de execução para executar comandos de forma síncrona e assíncrona. Você pode usar o Microsoft Visual Studio para criar um aplicativo de console e, em seguida, copie o código entre os tópicos nesta seção para seu aplicativo host.

## <a name="in-this-section"></a>Nesta seção

> [!NOTE]
> Para obter exemplos de aplicativos de host que criam interfaces de host personalizado, consulte [amostras de Host personalizado](./custom-host-samples.md).

 [Exemplo Runspace01](./runspace01-sample.md) Este exemplo mostra como usar o [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe a ser executada a [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet forma síncrona e exibir sua saída em um console do janela.

 [Exemplo de Runspace02](./runspace02-sample.md) Este exemplo mostra como usar o [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe a ser executada a [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) e [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets de forma síncrona. Os resultados desses comandos é exibida usando um [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) controle.

 [Exemplo de Runspace03](./runspace03-sample.md) Este exemplo mostra como usar o [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe para executar um script de forma síncrona e como tratar erros de não finalização. O script recebe uma lista de nomes de processo e, em seguida, recupera tais processos. Os resultados do script, incluindo quaisquer erros de não encerramento gerados durante a execução do script, são exibidos em uma janela do console.

 [Exemplo Runspace04](./runspace04-sample.md) Este exemplo mostra como usar o [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe para executar comandos e como capturar erros de encerramento gerados durante a execução de comandos. Dois comandos são executados e o último comando é passado um argumento de parâmetro que não é válido. Como resultado, nenhum objeto é retornado e um erro de encerramento é lançado.

 [Exemplo de Runspace05](./runspace05-sample.md) Este exemplo mostra como adicionar um snap-in para um [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) do objeto para que o cmdlet do snap-in está disponível quando o runspace for aberto. O snap-in fornece um cmdlet Get-Proc (definido pelos [exemplo GetProcessSample01](../cmdlet/getprocesssample01-sample.md)) que é executado de forma síncrona usando um [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.

 [Exemplo de Runspace06](./runspace06-sample.md) Este exemplo mostra como adicionar um módulo a um [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) do objeto para que o módulo seja carregado quando o runspace for aberto. O módulo fornece um cmdlet Get-Proc (definido pelos [GetProcessSample02 exemplo](../cmdlet/getprocesssample02-sample.md)) que é executado de forma síncrona usando um [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.

 [Exemplo de Runspace07](./runspace07-sample.md) Este exemplo mostra como criar um runspace e, em seguida, usá-lo para executar dois cmdlets de forma síncrona usando um [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.

 [Exemplo de Runspace08](./runspace08-sample.md) Este exemplo mostra como adicionar comandos e argumentos ao pipeline de uma [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto e como executar os comandos de forma síncrona.

 [Exemplo de Runspace09](./runspace09-sample.md) Este exemplo mostra como adicionar um script para o pipeline de uma [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto e como executar o script de forma assíncrona. Eventos são usados para tratar a saída do script.

 [Exemplo de Runspace10](./runspace10-sample.md) Este exemplo mostra como criar um estado de sessão inicial padrão, como adicionar um cmdlet para o [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), como criar um runspace que usa o estado de sessão inicial e como executar o comando usando um [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.

 [Exemplo de Runspace11](./runspace11-sample.md) isso mostra como usar o [System.Management.Automation.Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand) classe para criar um comando de proxy que chama um cmdlet existente, mas restringe o conjunto de parâmetros disponíveis. O comando de proxy é adicionado a um estado de sessão inicial que é usado para criar um espaço de execução restrito. Isso significa que o usuário pode acessar a funcionalidade do cmdlet apenas por meio do comando proxy.

## <a name="see-also"></a>Consulte Também
