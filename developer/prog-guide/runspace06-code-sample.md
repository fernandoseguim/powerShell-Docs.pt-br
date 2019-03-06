---
title: Exemplo de código RunSpace06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: d0330f082262b68486a582ed95c7a520be1e184c
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429526"
---
# <a name="runspace06-code-sample"></a>Exemplo de código RunSpace06

Aqui está o código-fonte para o exemplo Runspace06 descrito [Configurando um Runspace usando um Snap-in do PowerShell do Windows](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83). Este aplicativo de exemplo cria um espaço de execução com base em um snap-in do Windows PowerShell, que é usado para executar um pipeline com um único comando. Para fazer isso, o aplicativo cria as informações de configuração do espaço de execução, cria um espaço de execução, cria um pipeline com um único comando e, em seguida, executa o pipeline.

> [!NOTE]
> Você pode baixar o C# arquivo de origem (runspace06.cs) usando o Windows Software Development Kit do Windows Vista e o Microsoft .NET Framework 3.0 Runtime Components. Para obter instruções de download, consulte [como instalar o Windows PowerShell e o Download do SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Os arquivos de origem baixado estão disponíveis na  **\<amostras do PowerShell >** directory.

## <a name="code-sample"></a>Exemplo de código

[!code-csharp[Runspace06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a>Consulte Também

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)