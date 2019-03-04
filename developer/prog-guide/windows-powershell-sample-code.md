---
title: Código de exemplo do PowerShell do Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1106829a-8ddc-454e-bbdd-ade15d4bffb4
caps.latest.revision: 7
ms.openlocfilehash: 264e9f7538e13b48d899e87541239250eb88f14e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863352"
---
# <a name="windows-powershell-sample-code"></a>Código de exemplo do Windows PowerShell

Exemplos de Windows PowerShell® estão disponíveis por meio do SDK do Windows. Esta seção contém o código de exemplo que está contido nas amostras do SDK do Windows.

> [!NOTE]
> Quando o SDK do Windows é instalado, uma **exemplos** diretório é criado no qual todos os exemplos do Windows PowerShell são disponibilizados. É um diretório de instalação típica **C:\Program Files\Microsoft SDKs\Windows\v6.0**. Inicie o Windows PowerShell e digite **"cd Samples\SysMgmt\PowerShell"** para localizar o diretório de exemplos do Windows PowerShell. Neste documento, o diretório de exemplos do Windows PowerShell é conhecido como  **\<amostras do PowerShell >**.

## <a name="sample-code-listing"></a>Listagem de código de exemplo

|Código de exemplo|Descrição|
|-----------------|-----------------|
|[Exemplo de código AccessDbProviderSample01](./accessdbprovidersample01-code-sample.md)|Esse é o provedor descrito em [criando um provedor básico do Windows PowerShell](./creating-a-basic-windows-powershell-provider.md).|
|[Exemplo de código AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md)|Esse é o provedor descrito em [criando um provedor de unidade do Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).|
|[Exemplo de código AccessDbProviderSample03](./accessdbprovidersample03-code-sample.md)|Esse é o provedor descrito em [criando um provedor de Item do Windows PowerShell](./creating-a-windows-powershell-item-provider.md).|
|[Exemplo de código AccessDbProviderSample04](./accessdbprovidersample04-code-sample.md)|Esse é o provedor descrito em [criando um provedor de contêiner do Windows PowerShell](./creating-a-windows-powershell-container-provider.md).|
|[Exemplo de código AccessDbProviderSample05](./accessdbprovidersample05-code-sample.md)|Esse é o provedor descrito em [criando um provedor de navegação do Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md).|
|[Exemplo de código AccessDbProviderSample06](./accessdbprovidersample06-code-sample.md)|Esse é o provedor descrito em [criando um provedor de conteúdo do Windows PowerShell](./creating-a-windows-powershell-content-provider.md).|
|[Exemplos de código GetProc01](./getproc01-code-samples.md)|Isso é básica `Get-Process` cmdlet de exemplo descrito em [criando seu primeiro Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md).|
|[Exemplos de código GetProc02](./getproc02-code-samples.md)|Esse é o `Get-Process` cmdlet de exemplo descrito em [adicionando parâmetros essa entrada de linha de comando de processo](../cmdlet/adding-parameters-that-process-command-line-input.md).|
|[Exemplos de código GetProc03](./getproc03-code-samples.md)|Esse é o `Get-Process` cmdlet de exemplo descrito em [adicionando parâmetros de entrada do Pipeline esse processo](../cmdlet/adding-parameters-that-process-pipeline-input.md).|
|[Exemplos de código GetProc04](./getproc04-code-samples.md)|Esse é o `Get-Process` cmdlet de exemplo descrito em [adicionando sem encerramento relatório de erros para o Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).|
|[Exemplos de código GetProc05](./getproc05-code-samples.md)|Isso `Get-Process` cmdlet é semelhante ao cmdlet descrito [adicionando sem encerramento relatório de erros para o Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).|
|[Exemplos de código StopProc01](./stopproc01-code-samples.md)|Esse é o `Stop-Process` cmdlet de exemplo descrito em [criando um Cmdlet que modifica o sistema](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md).|
|[Exemplos de código StopProcessSample04](./stopprocesssample04-code-samples.md)|Esse é o `Stop-Process` cmdlet de exemplo descrito em [adicionando conjuntos de parâmetros para um Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).|
|[Exemplos de código Runspace01](./runspace01-code-samples.md)|Esses são os exemplos de código para o espaço de execução descrito na [criação de um Console do aplicativo que é executado um comando especificado](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).|
|[Exemplos de código Runspace02](./runspace02-code-samples.md)|Este exemplo usa o [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) classe para executar o `Get-Process` cmdlet sincronicamente.|
|[Exemplos de código RunSpace03](./runspace03-code-samples.md)|Esses são os exemplos de código para o espaço de execução descrito na [criando um Console do aplicativo que é executado em um Script especificado](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).|
|[Exemplos de código RunSpace04](./runspace04-code-samples.md)|Este é um exemplo de código para um runspace que usa o [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) classe para executar um script que gera um erro de encerramento.|
|[Exemplo de código RunSpace05](./runspace05-code-sample.md)|Isso é o código-fonte para o exemplo Runspace05 descrito [Configurando um RunspaceConfiguration do Runspace usando](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).|
|[Exemplo de código RunSpace06](./runspace06-code-sample.md)|Isso é o código-fonte para o exemplo Runspace06 descrito [Configurando um Runspace usando um Snap-in do PowerShell do Windows](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).|
|[Exemplo de código RunSpace07](./runspace07-code-sample.md)|Isso é o código-fonte para o exemplo Runspace07 descrito [criando um aplicativo que adiciona comandos do Console a um Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).|
|[Exemplo de código RunSpace08](./runspace08-code-sample.md)|Isso é o código-fonte para o exemplo Runspace08 descrito [criando um aplicativo que adiciona parâmetros do Console a um comando](http://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).|
|[Exemplo de código RunSpace09](./runspace09-code-sample.md)|Isso é o código-fonte para o exemplo Runspace09 descrito [criação de um Console do aplicativo que invoca um Pipeline de forma assíncrona](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).|
|[Exemplo de código RunSpace10](./runspace10-code-sample.md)|Isso é o código-fonte para o exemplo Runspace10, que adiciona um cmdlet para [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) e, em seguida, usa as informações de configuração modificado para criar o espaço de execução.|

## <a name="see-also"></a>Consulte Também

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)