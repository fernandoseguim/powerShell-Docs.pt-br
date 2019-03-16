---
title: GetProc03 código de exemplo (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: 0cfb5c203c97a4d20e7fadf8183e608e9e31b881
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058242"
---
# <a name="getproc03-vbnet-sample-code"></a>Código de exemplo GetProc03 (VB.NET)

O código a seguir mostra a implementação de um `Get-Process` redirecionasse o cmdlet que aceite entrada. Essa implementação define uma `Name` parâmetro que aceita entrada do pipeline, recupera informações de processo do computador local com base em nomes fornecidos e, em seguida, usa o [System.Management.Automation.Cmdlet.WriteObject% 28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) método como o mecanismo de saída para enviar objetos ao pipeline.

## <a name="code-sample"></a>Exemplo de código

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->