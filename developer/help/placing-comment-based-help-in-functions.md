---
title: Colocando a Ajuda baseada em comentário em funções | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857942"
---
# <a name="placing-comment-based-help-in-functions"></a>Colocar a ajuda baseada em comentários em funções

Este tópico explica onde colocar a Ajuda baseada em comentário para uma função, de modo que o `Get-Help` cmdlet associa o tópico da Ajuda baseada em comentários com a função correta.

## <a name="where-to-place-comment-based-help-for-a-function"></a>Onde colocar a Ajuda baseada em comentário para uma função

- No início do corpo da função.

- No final do corpo da função.

- Antes do `Function` palavra-chave. Quando a função está em um script ou módulo de script, não pode haver mais de uma linha em branco entre a última linha a Ajuda baseada em comentários e o `Function` palavra-chave. Caso contrário, `Get-Help` associa a ajuda com o script, não com a função.

## <a name="examples-of-help-placement-in-a-function"></a>Exemplos de posicionamento de Ajuda em uma função

 Os exemplos a seguir mostram a cada uma das opções de posicionamento de três para ajuda baseada em comentário para uma função.

### <a name="help-at-the-beginning-of-a-function-body"></a>Ajuda no início do corpo da função

 O exemplo a seguir mostra a baseada em comentário no início do corpo da função.

```powershell

function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}

```

### <a name="help-at-the-end-of-a-function-body"></a>Ajuda do final do corpo de uma função

 O exemplo a seguir mostra a baseada em comentários no final do corpo da função.

```powershell

function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}

```

### <a name="help-before-the-function-keyword"></a>Ajuda antes da palavra-chave de função

 Os exemplos a seguir mostra a baseada em comentário na linha antes da palavra-chave de função.

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```