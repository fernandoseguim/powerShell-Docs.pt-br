---
title: Exemplos de código GetProc04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 67081528ebe14fbb082091c1b9500de82069b48f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054638"
---
# <a name="getproc04-code-samples"></a>Exemplos de código GetProc04

Aqui estão exemplos de código para o cmdlet de exemplo GetProc04. Esse é o `Get-Process` cmdlet de exemplo descrito em [adicionando sem encerramento relatório de erros para o Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md). Isso `Get-Process` cmdlet chamadas a [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método sempre que uma exceção de operação inválida é lançada durante a recuperação de informações do processo.

> [!NOTE]
> Você pode baixar o C# arquivo de origem (getprov04.cs) para esse cmdlet Get-Proc usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components. Para obter instruções de download, consulte [como instalar o Windows PowerShell e o Download do SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Os arquivos de origem baixado estão disponíveis na  **\<amostras do PowerShell >** directory.

Para o código de exemplo completo, consulte os tópicos a seguir.

|Language|Tópico|
|--------------|-----------|
|C#|[GetProc04 (C#) código de exemplo](./getproc04-csharp-sample-code.md)|
|VB.NET|[GetProc04 código de exemplo (VB.NET)](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a>Consulte Também

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)