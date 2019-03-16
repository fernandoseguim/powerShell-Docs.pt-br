---
title: Exemplos de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: 0fa4a5f804586c51ae6a36121f9aab041b0989cc
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058038"
---
# <a name="cmdlet-samples"></a>Amostras de cmdlet

Esta seção descreve o código de exemplo que é fornecido no SDK do Windows PowerShell 2.0. Você pode copiar o código entre os tópicos nesta seção, ou abrir os arquivos de origem instalados com o SDK. O [Windows PowerShell 2.0 Software Development Kit (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560) fornece arquivos Leiame, arquivos de origem e arquivos de projeto do Visual Studio para cada amostra. Com o SDK instalado, você pode encontrar os exemplos sob o `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` pasta.

## <a name="in-this-section"></a>Nesta seção

[Exemplo GetProcessSample01](./getprocesssample01-sample.md) Este exemplo mostra como gravar um cmdlet que recupere os processos no computador local.

[GetProcessSample02 exemplo](./getprocesssample02-sample.md) Este exemplo mostra como gravar um cmdlet que recupere os processos no computador local. Ele fornece um parâmetro de nome que pode ser usado para especificar os processos a serem recuperados.

[Exemplo de GetProcessSample03](./getprocesssample03-sample.md) Este exemplo mostra como gravar um cmdlet que recupere os processos no computador local. Ele fornece um parâmetro de nome que pode aceitar um objeto do pipeline ou um valor de uma propriedade de um objeto cujo nome da propriedade é o mesmo que o nome do parâmetro.

[Exemplo de GetProcessSample04](./getprocesssample04-sample.md) Este exemplo mostra como gravar um cmdlet que recupere os processos no computador local. Se ocorrer um erro ao recuperar um processo, ele gera um erro sem encerramento.

[Exemplo de GetProcessSample05](./getprocesssample05-sample.md) Este exemplo mostra uma versão completa do cmdlet Get-Proc.

[Exemplo de StopProcessSample01](./stopprocesssample01-sample.md) Este exemplo mostra como gravar um cmdlet que solicita comentários do usuário antes de tentar interromper um processo e como implementar um `PassThru` parâmetro que indica que o usuário deseja o cmdlet para retornar um objeto.

[Exemplo de StopProcessSample02](./stopprocesssample02-sample.md) Este exemplo mostra como gravar um cmdlet que grava mensagens de aviso e de depuração, detalhada, ao parar processos no computador local.

[Exemplo de StopProcessSample03](./stopprocesssample03-sample.md) Este exemplo mostra como gravar um cmdlet cujos parâmetros têm aliases e que oferecem suporte a caracteres curinga.

[Exemplo de StopProcessSample04](./stopprocesssample04-sample.md) Este exemplo mostra como gravar um cmdlet que declara os conjuntos de parâmetros, especifica o parâmetro padrão definido e pode aceitar um objeto de entrada.

[Exemplo de Events01](./events01-sample.md) Este exemplo mostra como criar um cmdlet que permite ao usuário para se registrar para eventos gerados pelos [FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher). Com esse cmdlet os usuários podem, por exemplo, registrar uma ação a ser executada quando um arquivo é criado em um diretório específico. Neste exemplo deriva de [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) classe base.

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
