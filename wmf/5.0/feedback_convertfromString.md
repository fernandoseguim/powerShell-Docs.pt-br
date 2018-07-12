---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: fcf2adf67f36edb534df3e2a849459fb20e1c2de
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892336"
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a><span data-ttu-id="77f57-102">Extrair e analisar objetos estruturados fora da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="77f57-102">Extract and Parse Structured Objects out of String</span></span>

<span data-ttu-id="77f57-103">Isso também introduz algumas funcionalidades adicionais ao cmdlet `ConvertFrom-String`:</span><span class="sxs-lookup"><span data-stu-id="77f57-103">This also introduces some additional functionality for the `ConvertFrom-String` cmdlet:</span></span>

- <span data-ttu-id="77f57-104">Por padrão, remove a propriedade de texto de extensão.</span><span class="sxs-lookup"><span data-stu-id="77f57-104">Removes the extent text property by default.</span></span> <span data-ttu-id="77f57-105">É possível incluí-la com o parâmetro -IncludeExtent.</span><span class="sxs-lookup"><span data-stu-id="77f57-105">You can include it with the -IncludeExtent parameter.</span></span>

- <span data-ttu-id="77f57-106">Muitas correções de bug do algoritmo de aprendizado de acordo com os comentários da comunidade e do MVP.</span><span class="sxs-lookup"><span data-stu-id="77f57-106">Many learning algorithm bug fixes from MVP and community feedback.</span></span>

- <span data-ttu-id="77f57-107">Um novo parâmetro -UpdateTemplate para salvar os resultados do algoritmo de aprendizado em um comentário no arquivo de modelo.</span><span class="sxs-lookup"><span data-stu-id="77f57-107">A new -UpdateTemplate parameter to save the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="77f57-108">Isso faz com que o processo de aprendizado (a etapa mais lenta) seja de custo único.</span><span class="sxs-lookup"><span data-stu-id="77f57-108">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="77f57-109">A execução de Convert-String com um modelo que contém o algoritmo de aprendizado codificado agora é quase instantânea.</span><span class="sxs-lookup"><span data-stu-id="77f57-109">Running Convert-String with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

## <a name="extract-and-parse-structured-objects-out-of-string-content"></a><span data-ttu-id="77f57-110">Extrair e analisar objetos estruturados fora do conteúdo da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="77f57-110">Extract and parse structured objects out of string content</span></span>

<span data-ttu-id="77f57-111">Em colaboração com o [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), um novo cmdlet `ConvertFrom-String` foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="77f57-111">In collaboration with [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), a new `ConvertFrom-String` cmdlet has been added.</span></span>

<span data-ttu-id="77f57-112">Esse cmdlet dá suporte a dois modos: análise delimitada básica e análise orientada por exemplo gerada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="77f57-112">This cmdlet supports two modes: basic delimited parsing, and auto generated example-driven parsing.</span></span>

<span data-ttu-id="77f57-113">A análise delimitada, por padrão, divide a entrada no espaço em branco e atribui nomes de propriedade aos grupos resultantes.</span><span class="sxs-lookup"><span data-stu-id="77f57-113">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span> <span data-ttu-id="77f57-114">É possível personalizar o delimitador:</span><span class="sxs-lookup"><span data-stu-id="77f57-114">You can customize the delimiter:</span></span>

```powershell
"Hello World" | ConvertFrom-String | Format-Table -Auto
```

```output
P1     P2
--     --
Hello  World
```

<span data-ttu-id="77f57-115">O cmdlet também dá suporte à análise orientada por exemplo gerada automaticamente com base no trabalho de pesquisa [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) no [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).</span><span class="sxs-lookup"><span data-stu-id="77f57-115">The cmdlet also supports auto-generated example-driven parsing based on the [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) research work in [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).</span></span>

<span data-ttu-id="77f57-116">Para começar, considere um catálogo de endereços baseado em texto:</span><span class="sxs-lookup"><span data-stu-id="77f57-116">To get started, consider a text-based address book:</span></span>

```
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
```

<span data-ttu-id="77f57-117">Faça uma cópia de alguns exemplos em um arquivo, que você usará como o modelo:</span><span class="sxs-lookup"><span data-stu-id="77f57-117">Copy a few examples into a file, which you will use as your template:</span></span>

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA
```

<span data-ttu-id="77f57-118">Coloque chaves em torno dos dados que deseja extrair, nomeando-os.</span><span class="sxs-lookup"><span data-stu-id="77f57-118">Put curly braces around data that you want to extract, giving it a name as you do so.</span></span> <span data-ttu-id="77f57-119">Como a propriedade **Name** (e suas outras propriedades associadas) pode aparecer várias vezes, use um asterisco (\*) para indicar que isso resultará em vários registros (em vez de extrair várias propriedades em um registro):</span><span class="sxs-lookup"><span data-stu-id="77f57-119">Because the **Name** property (and its associated other properties) can appear multiple times, use an asterisk (\*) to indicate that this results in multiple records (rather than extracting a bunch of properties into one record):</span></span>

```
    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}
```

<span data-ttu-id="77f57-120">Desse conjunto de exemplos, `ConvertFrom-String` agora pode extrair automaticamente a saída com base no objeto de arquivos de entrada com uma estrutura semelhante.</span><span class="sxs-lookup"><span data-stu-id="77f57-120">From this set of examples, `ConvertFrom-String` can now automatically extract object-based output from input files with similar structure.</span></span>

```powershell
Get-Content .\addresses.output.txt | ConvertFrom-String -TemplateFile .\addresses.template.txt | Format-Table -Auto
```

```output
ExtentText                     Name               City     State
----------                     ----               ----     -----
Ana Trujillo...                Ana Trujillo       Redmond  WA
Antonio Moreno...              Antonio Moreno     Renton   WA
Thomas Hardy...                Thomas Hardy       Seattle  WA
Christina Berglund...          Christina Berglund Redmond  WA
Hanna Moos...                  Hanna Moos         Puyallup WA
```

<span data-ttu-id="77f57-121">A fim de realizar a manipulação de dados adicional no texto extraído, a propriedade **ExtentText** captura o texto não processado do qual o registro foi extraído.</span><span class="sxs-lookup"><span data-stu-id="77f57-121">To do additional data manipulation on extracted text, the **ExtentText** property captures the raw text from which the record was extracted.</span></span> <span data-ttu-id="77f57-122">Para fornecer comentários sobre este recurso ou compartilhar conteúdo para o qual você está com dificuldades para escrever exemplos, envie um email para <psdmfb@microsoft.com>.</span><span class="sxs-lookup"><span data-stu-id="77f57-122">To provide feedback on this feature, or to share content for which you are having difficulty writing examples, please email <psdmfb@microsoft.com>.</span></span>