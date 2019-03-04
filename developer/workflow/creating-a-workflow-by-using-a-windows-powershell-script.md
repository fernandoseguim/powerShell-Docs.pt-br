---
title: Criando um fluxo de trabalho usando um Script do Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853042"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>Criar um fluxo de trabalho pelo uso de um script do Windows PowerShell

Você pode criar um fluxo de trabalho, escrevendo um script do Windows PowerShell. Para criar um fluxo de trabalho, use a palavra-chave de fluxo de trabalho seguida por um nome para o fluxo de trabalho antes do corpo do script. Por exemplo:

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

Você pode encontrar o fluxo de trabalho da mesma maneira que faria com qualquer outro comando do Windows PowerShell.

## <a name="implementing-parallel-and-sequence"></a>Implementando Parallel e Sequence

[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) dá suporte à execução de atividades em paralelo. Para implementar essa funcionalidade em um script do Windows PowerShell, use o `parallel` palavra-chave na frente de um bloco de script. Você também pode usar o `foreach -parallel` construção para iterar por meio de uma coleção de objetos em paralelo. Para executar um grupo de atividades em ordem sequencial dentro de um bloco paralelo, coloque o grupo de atividades em um bloco de script e preceder o bloco com a palavra-chave de sequência.

## <a name="joining-computers-to-a-domain"></a>Ingressando computadores em um domínio

O script a seguir cria um fluxo de trabalho que verifica o status de domínio de um grupo de computadores especificados pelo usuário, une-as em um domínio, se eles não estão associados e, em seguida, verifica o status novamente. Esta é uma versão de script do fluxo de trabalho XAML explicado [criando um fluxo de trabalho com atividades do Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md).

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
 }

```