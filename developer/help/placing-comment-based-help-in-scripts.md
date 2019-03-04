---
title: Colocando a Ajuda baseada em comentário em Scripts | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860762"
---
# <a name="placing-comment-based-help-in-scripts"></a>Colocar a ajuda baseada em comentários em scripts

Este tópico explica onde colocar a Ajuda baseada em comentário para um script para que o `Get-Help` cmdlet associa o tópico da Ajuda baseada em comentários com scripts e não todas as funções que podem ser no script.

## <a name="where-to-place-comment-based-help-for-a-script"></a>Onde colocar a Ajuda baseada em comentário para um Script

- No início do arquivo de script. Ajuda de script pode ser precedidas no script somente por linhas em branco e comentários.

- No final do arquivo de script.

  Se o primeiro item no corpo do script (após a Ajuda) é uma declaração de função, deve haver pelo menos duas linhas em branco entre o final do script de Ajuda e a declaração da função. Caso contrário, a Ajuda é interpretada como ajuda para a função, não a Ajuda para o script.

## <a name="examples-of-help-placement-in-a-script"></a>Exemplos de posicionamento de Ajuda em um Script

 Os exemplos a seguir mostram a cada uma das opções de posicionamento para ajuda baseada em comentário para um script.

### <a name="help-at-the-beginning-of-a-script"></a>Ajuda no início de um Script

 O exemplo a seguir mostra a baseada em comentário no início de um script.

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>Ajuda do final de um Script

 O exemplo a seguir mostra a baseada em comentários no final de um script.

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```