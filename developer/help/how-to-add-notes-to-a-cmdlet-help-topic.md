---
title: Como adicionar anotações a um tópico de ajuda | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862262"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="69175-102">Como adicionar notas a um tópico de ajuda do cmdlet</span><span class="sxs-lookup"><span data-stu-id="69175-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="69175-103">Esta seção descreve como adicionar uma seção de notas a um tópico de ajuda Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="69175-103">This section describes how to add a Notes section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="69175-104">A seção Observações é usada para explicar os detalhes que não se encaixam facilmente em outras seções estruturadas, como uma explicação mais detalhada de um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="69175-104">The Notes section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="69175-105">Esse conteúdo pode incluir comentários em como o cmdlet funciona com um provedor específico, alguns usos exclusivos, embora importantes, do cmdlet ou maneiras de evitar possíveis condições de erro.</span><span class="sxs-lookup"><span data-stu-id="69175-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="69175-106">Não há nenhum limite para o número de observações que você pode adicionar uma seção de anotações.</span><span class="sxs-lookup"><span data-stu-id="69175-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="69175-107">Para cada nota, adicione um par de \<maml:alert > marcas para o \<maml:alertset > nó.</span><span class="sxs-lookup"><span data-stu-id="69175-107">For each note, add a pair of \<maml:alert> tags to the \<maml:alertset> node.</span></span> <span data-ttu-id="69175-108">O conteúdo de cada nota é adicionado em um conjunto de \<MAML: para > marcas.</span><span class="sxs-lookup"><span data-stu-id="69175-108">The content of each note is added within a set of \<maml:para> tags.</span></span> <span data-ttu-id="69175-109">Espaço em branco de uso \<MAML: para > marcas para espaçamento.</span><span class="sxs-lookup"><span data-stu-id="69175-109">Use blank \<maml:para> tags for spacing.</span></span>

<span data-ttu-id="69175-110">O XML a seguir mostra um \<maml:alertset > nó com duas anotações.</span><span class="sxs-lookup"><span data-stu-id="69175-110">The following XML shows an \<maml:alertset> node with two notes.</span></span> <span data-ttu-id="69175-111">Observe que cada Observação tem um recurso opcional \<MAML: Title > marca (títulos podem ser usados para agrupar qualquer conjunto de \<maml:alert > marcas), e se cada Observação tem uma linha em branco após o conteúdo para espaçamento.</span><span class="sxs-lookup"><span data-stu-id="69175-111">Notice that each note has an optional \<maml:title> tag (titles can be used to group any set of \<maml:alert> tags), and that each note has a blank line following the content for spacing.</span></span>

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```



