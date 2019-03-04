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
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="4ee56-102">Sintaxe de ajuda baseada em comentários</span><span class="sxs-lookup"><span data-stu-id="4ee56-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="4ee56-103">Esta seção descreve a sintaxe de ajuda baseados em comentário.</span><span class="sxs-lookup"><span data-stu-id="4ee56-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="4ee56-104">Diagrama de sintaxe</span><span class="sxs-lookup"><span data-stu-id="4ee56-104">Syntax Diagram</span></span>

 <span data-ttu-id="4ee56-105">A sintaxe para a Ajuda baseada em comentário é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="4ee56-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="4ee56-106">Descrição da sintaxe</span><span class="sxs-lookup"><span data-stu-id="4ee56-106">Syntax Description</span></span>

 <span data-ttu-id="4ee56-107">A Ajuda baseada em comentário é escrita como uma série de comentários.</span><span class="sxs-lookup"><span data-stu-id="4ee56-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="4ee56-108">Você pode digitar um símbolo de comentário (#) antes de cada linha de comentários, ou você pode usar o "\<#" e "#>" símbolos para criar um bloco de comentário.</span><span class="sxs-lookup"><span data-stu-id="4ee56-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="4ee56-109">Todas as linhas dentro do bloco de comentário são interpretadas como comentários.</span><span class="sxs-lookup"><span data-stu-id="4ee56-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="4ee56-110">Cada seção de ajuda baseados em comentário é definida por uma palavra-chave e cada palavra-chave é precedido por um ponto (.).</span><span class="sxs-lookup"><span data-stu-id="4ee56-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="4ee56-111">As palavras-chave podem aparecer em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="4ee56-111">The keywords can appear in any order.</span></span> <span data-ttu-id="4ee56-112">Os nomes de palavra-chave não diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="4ee56-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="4ee56-113">Um bloco de comentário deve conter pelo menos uma palavra-chave de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="4ee56-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="4ee56-114">Algumas das palavras-chave, como no exemplo, podem aparecer várias vezes no mesmo bloco de comentário.</span><span class="sxs-lookup"><span data-stu-id="4ee56-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="4ee56-115">O conteúdo da Ajuda para cada palavra-chave começa na linha após a palavra-chave e pode abranger várias linhas.</span><span class="sxs-lookup"><span data-stu-id="4ee56-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="4ee56-116">Todas as linhas em um tópico de ajuda baseados em comentário devem ser contíguas.</span><span class="sxs-lookup"><span data-stu-id="4ee56-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="4ee56-117">Se um tópico de ajuda baseados em comentário segue um comentário que não faz parte do tópico da Ajuda, deve haver pelo menos uma linha em branco entre a última linha de comentário não ajuda e o início da Ajuda baseada em comentário.</span><span class="sxs-lookup"><span data-stu-id="4ee56-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="4ee56-118">Por exemplo, o seguinte tópico da Ajuda baseada em comentário contém o. Palavra-chave de descrição e seu valor, que é uma descrição de uma função ou script.</span><span class="sxs-lookup"><span data-stu-id="4ee56-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```