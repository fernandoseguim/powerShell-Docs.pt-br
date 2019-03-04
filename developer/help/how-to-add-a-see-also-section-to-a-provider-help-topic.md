---
title: Como adicionar um, consulte também seção um tópico de Ajuda do provedor | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858342"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="4562e-102">Como adicionar uma seção “veja também” a um tópico de ajuda do provedor</span><span class="sxs-lookup"><span data-stu-id="4562e-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="4562e-103">Esta seção explica como popular o **Consulte também** seção de um tópico de Ajuda do provedor.</span><span class="sxs-lookup"><span data-stu-id="4562e-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="4562e-104">O **Consulte também** seção consiste em uma lista de tópicos relacionados ao provedor ou pode ajudar o usuário a entender melhor e usar o provedor.</span><span class="sxs-lookup"><span data-stu-id="4562e-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="4562e-105">A lista de tópicos pode incluir a Ajuda do cmdlet, Ajuda do provedor e tópicos de Ajuda no Windows PowerShell ("sobre").</span><span class="sxs-lookup"><span data-stu-id="4562e-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="4562e-106">Ele também pode incluir referências a livros, papel e tópicos online, incluindo uma versão online do tópico da Ajuda de provedor atual.</span><span class="sxs-lookup"><span data-stu-id="4562e-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="4562e-107">Ao fazer referência a tópicos online, forneça o URI ou um termo de pesquisa em texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="4562e-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="4562e-108">O `Get-Help` cmdlet não vincular ou redirecionar para qualquer um dos tópicos na lista.</span><span class="sxs-lookup"><span data-stu-id="4562e-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="4562e-109">Além disso, o `Online` parâmetro do `Get-Help` cmdlet não funciona com a Ajuda do provedor.</span><span class="sxs-lookup"><span data-stu-id="4562e-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="4562e-110">A seção Consulte também é criada a partir de `RelatedLinks` elemento e as marcas que ele contém.</span><span class="sxs-lookup"><span data-stu-id="4562e-110">The See Also section is created from the `RelatedLinks` element and the tags that it contains.</span></span> <span data-ttu-id="4562e-111">O XML a seguir mostra como adicionar as marcas.</span><span class="sxs-lookup"><span data-stu-id="4562e-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="4562e-112">Para adicionar tópicos "Consulte também"</span><span class="sxs-lookup"><span data-stu-id="4562e-112">To Add "SEE ALSO" Topics</span></span>

1. <span data-ttu-id="4562e-113">No *AssemblyName*help.xml. dll do arquivo, dentro de `providerHelp` elemento, adicionar um `RelatedLinks` elemento.</span><span class="sxs-lookup"><span data-stu-id="4562e-113">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="4562e-114">O `RelatedLinks` elemento deve ser o último elemento no `providerHelp` elemento.</span><span class="sxs-lookup"><span data-stu-id="4562e-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="4562e-115">Apenas um `RelatedLinks` elemento é permitido em cada tópico de Ajuda do provedor.</span><span class="sxs-lookup"><span data-stu-id="4562e-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="4562e-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4562e-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. <span data-ttu-id="4562e-117">Para cada tópico na **Consulte também** seção, dentro de `RelatedLinks` elemento, adicionar um `navigationLink` elemento.</span><span class="sxs-lookup"><span data-stu-id="4562e-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="4562e-118">Em seguida, dentro de cada `navigationLink` elemento, adicione uma `linkText` e um elemento `uri` elemento.</span><span class="sxs-lookup"><span data-stu-id="4562e-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="4562e-119">Se você não estiver usando o `uri` elemento, você pode adicioná-lo como um elemento vazio (\<uri / >).</span><span class="sxs-lookup"><span data-stu-id="4562e-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="4562e-120">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4562e-120">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. <span data-ttu-id="4562e-121">Digite o nome do tópico entre o `linkText` marcas.</span><span class="sxs-lookup"><span data-stu-id="4562e-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="4562e-122">Se você estiver fornecendo um URI, digite-a entre o `uri` marcas.</span><span class="sxs-lookup"><span data-stu-id="4562e-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="4562e-123">Para indicar a versão online do tópico de ajuda de provedor atual, entre o `linkText` marcas, tipo de "versão Online:" em vez do nome do tópico.</span><span class="sxs-lookup"><span data-stu-id="4562e-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="4562e-124">Normalmente, a "versão Online:" link é o primeiro tópico na lista de tópico Consulte também.</span><span class="sxs-lookup"><span data-stu-id="4562e-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="4562e-125">O exemplo a seguir incluem três tópicos Consulte também.</span><span class="sxs-lookup"><span data-stu-id="4562e-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="4562e-126">O primeiro consulte a versão online do tópico atual.</span><span class="sxs-lookup"><span data-stu-id="4562e-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="4562e-127">O segundo refere-se a um tópico de ajuda de cmdlet do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4562e-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="4562e-128">O terceiro refere-se para outro tópico on-line.</span><span class="sxs-lookup"><span data-stu-id="4562e-128">The third refers to another online topic.</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```