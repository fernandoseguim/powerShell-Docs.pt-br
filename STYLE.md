# <a name="style-guide-for-powershell-docs"></a><span data-ttu-id="8b2e5-101">Guia de estilo para o PowerShell-Docs</span><span class="sxs-lookup"><span data-stu-id="8b2e5-101">Style guide for PowerShell-Docs</span></span>


## <a name="titlesheadings"></a><span data-ttu-id="8b2e5-102">Títulos</span><span class="sxs-lookup"><span data-stu-id="8b2e5-102">Titles/Headings</span></span>

* <span data-ttu-id="8b2e5-103">Os títulos (prefixados por \#) devem ser seguidos por uma nova linha</span><span class="sxs-lookup"><span data-stu-id="8b2e5-103">Titles/headings (anything preprended by \#) should be followed with a newline</span></span>
* <span data-ttu-id="8b2e5-104">Somente a primeira letra de um título e os nomes próprios nesse título devem estar em letras maiúsculas</span><span class="sxs-lookup"><span data-stu-id="8b2e5-104">Only the first letter of a title and any proper nouns in that title should be capitalized</span></span>
* <span data-ttu-id="8b2e5-105">Somente um H1 por documento</span><span class="sxs-lookup"><span data-stu-id="8b2e5-105">Only 1 H1 per document</span></span>
* <span data-ttu-id="8b2e5-106">Ao editar o conteúdo de referência, os H2s são prescritos pelo platyPS e não devem ser adicionados ou removidos, uma vez que isso causará uma interrupção da compilação</span><span class="sxs-lookup"><span data-stu-id="8b2e5-106">When editing reference content, the H2s are prescribed by platyPS and should not be added or removed as it will cause a build break</span></span>
* <span data-ttu-id="8b2e5-107">Use somente os estilos de cabeçalho do \# (em vez de = ou cabeçalhos de estilo do \-)</span><span class="sxs-lookup"><span data-stu-id="8b2e5-107">Only use \# style headers (as opposed to = or \- style headers)</span></span>

### <a name="correct"></a><span data-ttu-id="8b2e5-108">Correto</span><span class="sxs-lookup"><span data-stu-id="8b2e5-108">Correct</span></span>

```
# Header 1

## Header 2

### Header 3

```

### <a name="incorrect"></a><span data-ttu-id="8b2e5-109">Incorreto</span><span class="sxs-lookup"><span data-stu-id="8b2e5-109">Incorrect</span></span>

```
Header 1
========

Header 2
--------

### Header 3
```

## <a name="syntax"></a><span data-ttu-id="8b2e5-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b2e5-110">Syntax</span></span>

* <span data-ttu-id="8b2e5-111">Ao falar sobre um cmdlet em um parágrafo, use \\` para realçar os nomes do cmdlet</span><span class="sxs-lookup"><span data-stu-id="8b2e5-111">When talking about a cmdlet in paragraph, use \\` to highlight cmdlet names</span></span>
  * <span data-ttu-id="8b2e5-112">Exemplo correto: Este Cmdlet `Write-Host` pode...</span><span class="sxs-lookup"><span data-stu-id="8b2e5-112">Correct Example: This `Write-Host` Cmdlet can ...</span></span>
  * <span data-ttu-id="8b2e5-113">Exemplo incorreto: Este Cmdlet **Write-Host** pode... e pipeline para que o Cmdlet out-file...</span><span class="sxs-lookup"><span data-stu-id="8b2e5-113">Incorrect Example: This **Write-Host** Cmdlet can ... and pipeline to out-file Cmdlet to ...</span></span>
* <span data-ttu-id="8b2e5-114">Ao escrever um artigo (em vez de um conteúdo de referência), a primeira instância de um nome de cmdlet deve ser um link para a documentação do cmdlet</span><span class="sxs-lookup"><span data-stu-id="8b2e5-114">When writing an article (as opposed to reference content), the first instance of a cmdlet name should be a link to the cmdlet documentation</span></span>
* <span data-ttu-id="8b2e5-115">Todos os blocos de sintaxe do PowerShell devem usar o &#96;&#96;&#96;powershell</span><span class="sxs-lookup"><span data-stu-id="8b2e5-115">All PowerShell syntax blocks should use &#96;&#96;&#96;powershell</span></span>
* <span data-ttu-id="8b2e5-116">Não inicie os comandos do PowerShell com "`PS C:\>`"</span><span class="sxs-lookup"><span data-stu-id="8b2e5-116">Do not start PowerShell commands with "`PS C:\>`"</span></span>
  * <span data-ttu-id="8b2e5-117">Exemplo correto:</span><span class="sxs-lookup"><span data-stu-id="8b2e5-117">Correct Example:</span></span>
  ```powershell
  Get-Process
  ```
  * <span data-ttu-id="8b2e5-118">Exemplo incorreto:</span><span class="sxs-lookup"><span data-stu-id="8b2e5-118">Incorrect Example:</span></span>
  ```powershell
  PS C:\> Get-Process
  ```
* <span data-ttu-id="8b2e5-119">A saída gerada pelos comandos do PowerShell deve ser comentada para impedir que ela receba realce de sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b2e5-119">Output emitted by PowerShell commands should be commented to prevent it from recieving syntax highlighting</span></span>
* <span data-ttu-id="8b2e5-120">Os nomes de propriedades e nomes de parâmetros devem estar em **negrito**</span><span class="sxs-lookup"><span data-stu-id="8b2e5-120">Property names and parameter names should be in **bold**</span></span>
* <span data-ttu-id="8b2e5-121">O cmdlets do PowerShell seguem a capitalização"[Pascal Case](https://en.wikipedia.org/wiki/PascalCase)".</span><span class="sxs-lookup"><span data-stu-id="8b2e5-121">PowerShell cmdlets are "[Pascal Cased](https://en.wikipedia.org/wiki/PascalCase)".</span></span> <span data-ttu-id="8b2e5-122">Os verbos são separados dos substantivos por um hífen.</span><span class="sxs-lookup"><span data-stu-id="8b2e5-122">Verbs are seperated from nouns by a hyphen.</span></span>

## <a name="lists"></a><span data-ttu-id="8b2e5-123">Listas</span><span class="sxs-lookup"><span data-stu-id="8b2e5-123">Lists</span></span>

* <span data-ttu-id="8b2e5-124">Não encerre os itens da lista com um ponto (a menos que eles tenham várias sentenças)</span><span class="sxs-lookup"><span data-stu-id="8b2e5-124">Do not end list items with a period (unless they contain multiple sentences)</span></span>
* <span data-ttu-id="8b2e5-125">Se sua lista contiver várias sentenças, considere usar um cabeçalho 3/4/5 (conforme aplicável) abaixo da ideia principal</span><span class="sxs-lookup"><span data-stu-id="8b2e5-125">If your list contains multiple sentences, consider using a header 3/4/5 (as applicable) underneath your primary idea</span></span>

## <a name="links"></a><span data-ttu-id="8b2e5-126">Links</span><span class="sxs-lookup"><span data-stu-id="8b2e5-126">Links</span></span>

* <span data-ttu-id="8b2e5-127">Os links são sempre marcados usando a sintaxe MarkDown `[friendlyname](url)`</span><span class="sxs-lookup"><span data-stu-id="8b2e5-127">Links are always marked up using MarkDown syntax `[friendlyname](url)`</span></span>
* <span data-ttu-id="8b2e5-128">Os links devem ter um nome amigável quando aplicável, preferencialmente o título da página vinculada</span><span class="sxs-lookup"><span data-stu-id="8b2e5-128">Links should have a a friendly name when applicable, most likely the title of the linked page</span></span>
  * <span data-ttu-id="8b2e5-129">**Exceção**: os links direcionados a sites que não sejam da Microsoft só devem ter uma URL</span><span class="sxs-lookup"><span data-stu-id="8b2e5-129">**Exception**: Links going towards non-Microsoft sites should only have a URL</span></span>
* <span data-ttu-id="8b2e5-130">Todos os itens da seção "links relacionados" na parte inferior devem ser hiperlinks.</span><span class="sxs-lookup"><span data-stu-id="8b2e5-130">All items in the "related links" section at the bottom should be hyperlinked.</span></span> 

## <a name="line-breaks"></a><span data-ttu-id="8b2e5-131">Quebras de linha</span><span class="sxs-lookup"><span data-stu-id="8b2e5-131">Line breaks</span></span>

* <span data-ttu-id="8b2e5-132">Inclua quebras de linha semânticas</span><span class="sxs-lookup"><span data-stu-id="8b2e5-132">You must include semantic line breaks</span></span>
* <span data-ttu-id="8b2e5-133">Limite as linhas a 100 caracteres (Item aberto: ferramentas para nos ajudar a validar isso)</span><span class="sxs-lookup"><span data-stu-id="8b2e5-133">You should limit lines to 100char (Open item: tooling to help us validate this)</span></span>
* <span data-ttu-id="8b2e5-134">Você PODE remover quebras de linhas adicionais para PS4+, NÃO para ps3 (precisa de validação)</span><span class="sxs-lookup"><span data-stu-id="8b2e5-134">You CAN remove additional line breaks for PS4+, NOT ps3 (needs validation)</span></span>
