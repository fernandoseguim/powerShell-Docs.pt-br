---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: cedda61241df4965fe5db723f03e3497f046fa44
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a><span data-ttu-id="104ee-102">Extrair e analisar objetos estruturados fora da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="104ee-102">Extract and Parse Structured Objects out of String</span></span>
<span data-ttu-id="104ee-103">Isso também introduz algumas funcionalidades adicionais ao cmdlet ConvertFrom-String:</span><span class="sxs-lookup"><span data-stu-id="104ee-103">This also introduces some additional functionality for the ConvertFrom-String cmdlet:</span></span>

-   <span data-ttu-id="104ee-104">Por padrão, remove a propriedade de texto de extensão.</span><span class="sxs-lookup"><span data-stu-id="104ee-104">Removes the extent text property by default.</span></span> <span data-ttu-id="104ee-105">É possível incluí-la com o parâmetro -IncludeExtent.</span><span class="sxs-lookup"><span data-stu-id="104ee-105">You can include it with the -IncludeExtent parameter.</span></span>

-   <span data-ttu-id="104ee-106">Muitas correções de bug do algoritmo de aprendizado de acordo com os comentários da comunidade e do MVP.</span><span class="sxs-lookup"><span data-stu-id="104ee-106">Many learning algorithm bug fixes from MVP and community feedback.</span></span>

-   <span data-ttu-id="104ee-107">Um novo parâmetro -UpdateTemplate para salvar os resultados do algoritmo de aprendizado em um comentário no arquivo de modelo.</span><span class="sxs-lookup"><span data-stu-id="104ee-107">A new -UpdateTemplate parameter to save the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="104ee-108">Isso faz com que o processo de aprendizado (a etapa mais lenta) seja de custo único.</span><span class="sxs-lookup"><span data-stu-id="104ee-108">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="104ee-109">A execução de Convert-String com um modelo que contém o algoritmo de aprendizado codificado agora é quase instantânea.</span><span class="sxs-lookup"><span data-stu-id="104ee-109">Running Convert-String with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>


<a name="extract-and-parse-structured-objects-out-of-string-content"></a><span data-ttu-id="104ee-110">Extrair e analisar objetos estruturados fora do conteúdo da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="104ee-110">Extract and parse structured objects out of string content</span></span>
----------------------------------------------------------

<span data-ttu-id="104ee-111">Em colaboração com o [Microsoft Research](http://research.microsoft.com/), um novo cmdlet **ConvertFrom-String** foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="104ee-111">In collaboration with [Microsoft Research](http://research.microsoft.com/), a new **ConvertFrom-String** cmdlet has been added.</span></span>

<span data-ttu-id="104ee-112">Esse cmdlet dá suporte a dois modos: análise delimitada básica e análise orientada por exemplo gerada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="104ee-112">This cmdlet supports two modes: basic delimited parsing, and auto generated example-driven parsing.</span></span>

<span data-ttu-id="104ee-113">A análise delimitada, por padrão, divide a entrada no espaço em branco e atribui nomes de propriedade aos grupos resultantes.</span><span class="sxs-lookup"><span data-stu-id="104ee-113">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span> <span data-ttu-id="104ee-114">É possível personalizar o delimitador:</span><span class="sxs-lookup"><span data-stu-id="104ee-114">You can customize the delimiter:</span></span>

> <span data-ttu-id="104ee-115">1 \[C:\\temp\] &gt;&gt; "Hello World" | ConvertFrom-String | Format-Table -Auto</span><span class="sxs-lookup"><span data-stu-id="104ee-115">1 \[C:\\temp\] &gt;&gt; "Hello World" | ConvertFrom-String | Format-Table -Auto</span></span>

<span data-ttu-id="104ee-116">P1    P2</span><span class="sxs-lookup"><span data-stu-id="104ee-116">P1    P2</span></span>
--    --

<span data-ttu-id="104ee-117">O cmdlet também dá suporte à análise orientada por exemplo gerada automaticamente com base no trabalho de pesquisa [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) no [Microsoft Research](http://research.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="104ee-117">The cmdlet also supports auto-generated example-driven parsing based on the [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) research work in [Microsoft Research](http://research.microsoft.com).</span></span>

<span data-ttu-id="104ee-118">Para começar, considere um catálogo de endereços baseado em texto:</span><span class="sxs-lookup"><span data-stu-id="104ee-118">To get started, consider a text-based address book:</span></span>

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

    Thomas Hardy

    Seattle, WA

    Christina Berglund

    Redmond, WA

    Hanna Moos

    Puyallup, WA

<span data-ttu-id="104ee-119">Faça uma cópia de alguns exemplos em um arquivo, que você usará como o modelo:</span><span class="sxs-lookup"><span data-stu-id="104ee-119">Copy a few examples into a file, which you will use as your template:</span></span>

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA



<span data-ttu-id="104ee-120">Coloque chaves em torno dos dados que deseja extrair, nomeando-os.</span><span class="sxs-lookup"><span data-stu-id="104ee-120">Put curly braces around data that you want to extract, giving it a name as you do so.</span></span> <span data-ttu-id="104ee-121">Como a propriedade **Name** (e suas outras propriedades associadas) pode aparecer várias vezes, use um asterisco (\*) para indicar que isso resultará em vários registros (em vez de extrair várias propriedades em um registro):</span><span class="sxs-lookup"><span data-stu-id="104ee-121">Because the **Name** property (and its associated other properties) can appear multiple times, use an asterisk (\*) to indicate that this results in multiple records (rather than extracting a bunch of properties into one record):</span></span>

    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}

<span data-ttu-id="104ee-122">Desse conjunto de exemplos, **ConvertFrom-String** agora pode extrair automaticamente a saída com base no objeto de arquivos de entrada com uma estrutura semelhante.</span><span class="sxs-lookup"><span data-stu-id="104ee-122">From this set of examples, **ConvertFrom-String** can now automatically extract object-based output from input files with similar structure.</span></span>

> <span data-ttu-id="104ee-123">2 \[C:\\temp\]</span><span class="sxs-lookup"><span data-stu-id="104ee-123">2 \[C:\\temp\]</span></span>
>
> <span data-ttu-id="104ee-124">&gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto</span><span class="sxs-lookup"><span data-stu-id="104ee-124">&gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto</span></span>
>
> <span data-ttu-id="104ee-125">ExtentText                     Name               City     State</span><span class="sxs-lookup"><span data-stu-id="104ee-125">ExtentText                     Name               City     State</span></span>
> ----------                     ----               ----     -----
> <span data-ttu-id="104ee-126">Ana Trujillo...                Ana Trujillo       Redmond  WA Antonio Moreno...              Antonio Moreno     Renton   WA Thomas Hardy...                Thomas Hardy       Seattle  WA Christina Berglund...          Christina Berglund Redmond  WA Hanna Moos...                  Hanna Moos         Puyallup WA</span><span class="sxs-lookup"><span data-stu-id="104ee-126">Ana Trujillo...                Ana Trujillo       Redmond  WA Antonio Moreno...              Antonio Moreno     Renton   WA Thomas Hardy...                Thomas Hardy       Seattle  WA Christina Berglund...          Christina Berglund Redmond  WA Hanna Moos...                  Hanna Moos         Puyallup WA</span></span>

<span data-ttu-id="104ee-127">A fim de realizar a manipulação de dados adicional no texto extraído, a propriedade **ExtentText** captura o texto não processado do qual o registro foi extraído.</span><span class="sxs-lookup"><span data-stu-id="104ee-127">To do additional data manipulation on extracted text, the **ExtentText** property captures the raw text from which the record was extracted.</span></span> <span data-ttu-id="104ee-128">Para fornecer comentários sobre este recurso ou compartilhar conteúdo para o qual você está com dificuldades para escrever exemplos, envie um email para <psdmfb@microsoft.com>.</span><span class="sxs-lookup"><span data-stu-id="104ee-128">To provide feedback on this feature, or to share content for which you are having difficulty writing examples, please email <psdmfb@microsoft.com>.</span></span>