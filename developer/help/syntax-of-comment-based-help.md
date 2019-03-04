---
title: Sintaxe de ajuda baseados em comentário | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855542"
---
# <a name="syntax-of-comment-based-help"></a>Sintaxe de ajuda baseada em comentários

Esta seção descreve a sintaxe de ajuda baseados em comentário.

## <a name="syntax-diagram"></a>Diagrama de sintaxe

 A sintaxe para a Ajuda baseada em comentário é da seguinte maneira:

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a>Descrição da sintaxe

 A Ajuda baseada em comentário é escrita como uma série de comentários. Você pode digitar um símbolo de comentário (#) antes de cada linha de comentários, ou você pode usar o "\<#" e "#>" símbolos para criar um bloco de comentário. Todas as linhas dentro do bloco de comentário são interpretadas como comentários.

 Cada seção de ajuda baseados em comentário é definida por uma palavra-chave e cada palavra-chave é precedido por um ponto (.). As palavras-chave podem aparecer em qualquer ordem. Os nomes de palavra-chave não diferenciam maiusculas de minúsculas.

 Um bloco de comentário deve conter pelo menos uma palavra-chave de Ajuda. Algumas das palavras-chave, como no exemplo, podem aparecer várias vezes no mesmo bloco de comentário. O conteúdo da Ajuda para cada palavra-chave começa na linha após a palavra-chave e pode abranger várias linhas.

 Todas as linhas em um tópico de ajuda baseados em comentário devem ser contíguas. Se um tópico de ajuda baseados em comentário segue um comentário que não faz parte do tópico da Ajuda, deve haver pelo menos uma linha em branco entre a última linha de comentário não ajuda e o início da Ajuda baseada em comentário.

 Por exemplo, o seguinte tópico da Ajuda baseada em comentário contém o. Palavra-chave de descrição e seu valor, que é uma descrição de uma função ou script.

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```