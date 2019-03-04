---
title: Escrever ajuda para Cmdlets do PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857852"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="e8474-102">Escrevendo ajuda para Cmdlets do PowerShell</span><span class="sxs-lookup"><span data-stu-id="e8474-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="e8474-103">Cmdlets do PowerShell pode ser útil, mas a menos que seus tópicos da Ajuda explicar claramente que o cmdlet faz e como usá-lo, o cmdlet não pode ser usado ou, pior ainda, ela pode frustrar os usuários.</span><span class="sxs-lookup"><span data-stu-id="e8474-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span>
<span data-ttu-id="e8474-104">O formato de arquivo de Ajuda do cmdlet baseado em XML melhora a consistência, mas grande ajuda requer muito mais.</span><span class="sxs-lookup"><span data-stu-id="e8474-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="e8474-105">Se você nunca escreveu a Ajuda de cmdlet, examine as diretrizes a seguir.</span><span class="sxs-lookup"><span data-stu-id="e8474-105">If you have never written cmdlet Help, review the following guidelines.</span></span>
<span data-ttu-id="e8474-106">O esquema XML necessário para criar o tópico de Ajuda do cmdlet é descrito na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="e8474-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span>
<span data-ttu-id="e8474-107">Iniciar com [criando o arquivo de Ajuda do Cmdlet](./how-to-create-the-cmdlet-help-file.md).</span><span class="sxs-lookup"><span data-stu-id="e8474-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span>
<span data-ttu-id="e8474-108">Esse tópico inclui uma descrição de nós XML de nível superior.</span><span class="sxs-lookup"><span data-stu-id="e8474-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="e8474-109">Diretrizes de gravação para a Ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8474-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="e8474-110">Grave</span><span class="sxs-lookup"><span data-stu-id="e8474-110">Write well</span></span>
<span data-ttu-id="e8474-111">Nada substitui um tópico bem escrito.</span><span class="sxs-lookup"><span data-stu-id="e8474-111">Nothing replaces a well-written topic.</span></span>
<span data-ttu-id="e8474-112">Se você não for um escritor profissional, encontre um editor ou o gravador para ajudá-lo.</span><span class="sxs-lookup"><span data-stu-id="e8474-112">If you are not a professional writer, find a writer or editor to help you.</span></span>
<span data-ttu-id="e8474-113">Outra alternativa é copiar o texto de ajuda para o Microsoft Word e usar a gramática e ortografia verifica para melhorar o seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="e8474-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="e8474-114">Simplesmente escrever</span><span class="sxs-lookup"><span data-stu-id="e8474-114">Write simply</span></span>
<span data-ttu-id="e8474-115">Use frases e palavras simples.</span><span class="sxs-lookup"><span data-stu-id="e8474-115">Use simple words and phrases.</span></span>
<span data-ttu-id="e8474-116">Evite jargão.</span><span class="sxs-lookup"><span data-stu-id="e8474-116">Avoid jargon.</span></span>
<span data-ttu-id="e8474-117">Considere a possibilidade de que muitos leitores são equipados somente com um dicionário de idioma estrangeiro e seu tópico de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="e8474-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="e8474-118">Gravar de forma consistente</span><span class="sxs-lookup"><span data-stu-id="e8474-118">Write consistently</span></span>
<span data-ttu-id="e8474-119">A Ajuda para cmdlets relacionados devem ser semelhantes (por exemplo, get-x e set-x).</span><span class="sxs-lookup"><span data-stu-id="e8474-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span>
<span data-ttu-id="e8474-120">Usar as descrições padrão para os parâmetros padrão, como **Force** e **InputObject**.</span><span class="sxs-lookup"><span data-stu-id="e8474-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span>
<span data-ttu-id="e8474-121">(Copiá-los da Ajuda para os cmdlets de núcleo.) Use condições padrão.</span><span class="sxs-lookup"><span data-stu-id="e8474-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span>
<span data-ttu-id="e8474-122">Por exemplo, use "parâmetro", não "argument" e use "cmdlet" não "comando" ou "command-let".</span><span class="sxs-lookup"><span data-stu-id="e8474-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="e8474-123">Inicie a Sinopse com um verbo</span><span class="sxs-lookup"><span data-stu-id="e8474-123">Start the synopsis with a verb</span></span>
<span data-ttu-id="e8474-124">O campo Sinopse informa ao usuário que o cmdlet não, o que é ou como ele funciona.</span><span class="sxs-lookup"><span data-stu-id="e8474-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span>
<span data-ttu-id="e8474-125">Verbos de criar uma instrução baseado em tarefas que informam os usuários se esse cmdlet atende às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="e8474-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span>
<span data-ttu-id="e8474-126">Use verbos simples como "get", "criar" e "alterar".</span><span class="sxs-lookup"><span data-stu-id="e8474-126">Use simple verbs like "get", "create", and "change."</span></span>
<span data-ttu-id="e8474-127">Evite "set", que pode ser vagas e sofisticadas palavras como "modificar".</span><span class="sxs-lookup"><span data-stu-id="e8474-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="e8474-128">Concentre-se em objetos</span><span class="sxs-lookup"><span data-stu-id="e8474-128">Focus on objects</span></span>
<span data-ttu-id="e8474-129">A maioria "get" exibição de cmdlets algo, mas sua função principal é obter um objeto.</span><span class="sxs-lookup"><span data-stu-id="e8474-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span>
<span data-ttu-id="e8474-130">Sua ajuda nos concentrar no objeto, para que os usuários compreendam que a exibição padrão é uma das muitas e que eles podem usar os métodos e propriedades do objeto que você recuperou para eles de maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="e8474-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="e8474-131">Descrições detalhadas de gravação</span><span class="sxs-lookup"><span data-stu-id="e8474-131">Write detailed descriptions</span></span>
<span data-ttu-id="e8474-132">Liste brevemente tudo o que o cmdlet pode fazer na descrição detalhada.</span><span class="sxs-lookup"><span data-stu-id="e8474-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span>
<span data-ttu-id="e8474-133">Se a função principal é alterar uma propriedade, mas o cmdlet pode alterar todas as propriedades, liste isso na descrição detalhada.</span><span class="sxs-lookup"><span data-stu-id="e8474-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="e8474-134">Use uma sintaxe convencional</span><span class="sxs-lookup"><span data-stu-id="e8474-134">Use conventional syntax</span></span>
<span data-ttu-id="e8474-135">Use o formato Backus-Naur padrão que é comum para obter ajuda de linha de comando do UNIX e Windows.</span><span class="sxs-lookup"><span data-stu-id="e8474-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a><span data-ttu-id="e8474-136">Usar tipos do Microsoft .NET Framework para valores de parâmetro</span><span class="sxs-lookup"><span data-stu-id="e8474-136">Use Microsoft .NET Framework types for parameter values</span></span>
<span data-ttu-id="e8474-137">Os espaços reservados para valores de parâmetro (nas descrições de sintaxe e parâmetro) mostram os tipos do .NET Framework dos objetos que o parâmetro aceitará.</span><span class="sxs-lookup"><span data-stu-id="e8474-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span>
<span data-ttu-id="e8474-138">A equipe do PowerShell desenvolveu essa convenção para ajudar a ensinar os usuários sobre o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e8474-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="e8474-139">Descrições de parâmetro completa de gravação</span><span class="sxs-lookup"><span data-stu-id="e8474-139">Write complete parameter descriptions</span></span>
<span data-ttu-id="e8474-140">Descrições de parâmetro devem informar os usuários de duas coisas: qual o parâmetro faz (seu efeito) e o que eles devem digitar os valores de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e8474-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="e8474-141">Exemplos práticos de gravação</span><span class="sxs-lookup"><span data-stu-id="e8474-141">Write practical examples</span></span>
<span data-ttu-id="e8474-142">Os exemplos devem mostram como usar todos os parâmetros, mas o mais importante é mostrar como usar o cmdlet em tarefas do mundo real.</span><span class="sxs-lookup"><span data-stu-id="e8474-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span>
<span data-ttu-id="e8474-143">Começar com um exemplo simple e exemplos de cada vez mais complexos de gravação.</span><span class="sxs-lookup"><span data-stu-id="e8474-143">Start with a simple example and write increasingly complex examples.</span></span>
<span data-ttu-id="e8474-144">No exemplo final, mostram como usar o cmdlet em um pipeline.</span><span class="sxs-lookup"><span data-stu-id="e8474-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="e8474-145">Use o campo notas</span><span class="sxs-lookup"><span data-stu-id="e8474-145">Use the Notes field</span></span>
<span data-ttu-id="e8474-146">Use o campo notas para explicar conceitos que os usuários precisam entender o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e8474-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span>
<span data-ttu-id="e8474-147">Você também pode usar anotações para ajudar os usuários a evitar erros comuns.</span><span class="sxs-lookup"><span data-stu-id="e8474-147">You can also use notes to help users avoid common errors.</span></span>
<span data-ttu-id="e8474-148">Evite URLs conforme mudam.</span><span class="sxs-lookup"><span data-stu-id="e8474-148">Avoid URLs as they change.</span></span>
<span data-ttu-id="e8474-149">Em vez disso, forneça os termos de usuários a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="e8474-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="e8474-150">Teste a sua ajuda.</span><span class="sxs-lookup"><span data-stu-id="e8474-150">Test your Help</span></span>
<span data-ttu-id="e8474-151">Teste a Ajuda, exatamente como você testar seu código.</span><span class="sxs-lookup"><span data-stu-id="e8474-151">Test the Help just like you test your code.</span></span>
<span data-ttu-id="e8474-152">Tenho amigos e colegas ler seu conteúdo da Ajuda e fornecerem comentários.</span><span class="sxs-lookup"><span data-stu-id="e8474-152">Have friends and colleagues read your Help content and provide feedback.</span></span>
<span data-ttu-id="e8474-153">Você também pode solicitar comentários dos grupos de notícias.</span><span class="sxs-lookup"><span data-stu-id="e8474-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8474-154">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="e8474-154">See Also</span></span>

 [<span data-ttu-id="e8474-155">Como criar o arquivo de Ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8474-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="e8474-156">Como adicionar o nome do Cmdlet e a Sinopse a um tópico de ajuda</span><span class="sxs-lookup"><span data-stu-id="e8474-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e8474-157">Como adicionar a descrição detalhada para um tópico de Ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8474-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="e8474-158">Como adicionar uma sintaxe para um tópico de Ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8474-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e8474-159">Como adicionar parâmetros a um tópico de ajuda</span><span class="sxs-lookup"><span data-stu-id="e8474-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="e8474-160">Como adicionar tipos de entrada para um tópico de Ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8474-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e8474-161">Como adicionar valores de retorno para um tópico de Ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8474-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e8474-162">Como adicionar notas a um tópico de Ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8474-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e8474-163">Como adicionar exemplos para um tópico de ajuda</span><span class="sxs-lookup"><span data-stu-id="e8474-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e8474-164">Como adicionar Links relacionados a um tópico de ajuda</span><span class="sxs-lookup"><span data-stu-id="e8474-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e8474-165">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e8474-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)