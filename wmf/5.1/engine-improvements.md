---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
title: Melhorias do Mecanismo do PowerShell no WMF 5.1
ms.openlocfilehash: 6c8000ccfc59ab46de95dc4f67161e12a5a41199
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
#<a name="powershell-engine-improvements"></a><span data-ttu-id="b1c8d-103">Melhorias ao Mecanismo do PowerShell</span><span class="sxs-lookup"><span data-stu-id="b1c8d-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="b1c8d-104">As seguintes melhorias ao mecanismo principal do PowerShell foram implementadas no WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="b1c8d-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>


## <a name="performance"></a><span data-ttu-id="b1c8d-105">Desempenho</span><span class="sxs-lookup"><span data-stu-id="b1c8d-105">Performance</span></span> ##

<span data-ttu-id="b1c8d-106">O desempenho melhorou em algumas áreas importantes:</span><span class="sxs-lookup"><span data-stu-id="b1c8d-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="b1c8d-107">Inicialização</span><span class="sxs-lookup"><span data-stu-id="b1c8d-107">Startup</span></span>
- <span data-ttu-id="b1c8d-108">O pipelining para cmdlets como ForEach-Object e Where-Object é aproximadamente 50% mais rápido</span><span class="sxs-lookup"><span data-stu-id="b1c8d-108">Pipelining to cmdlets like ForEach-Object and Where-Object is approximately 50% faster</span></span> 

<span data-ttu-id="b1c8d-109">Alguns exemplos de melhorias (os resultados podem variar dependendo do hardware):</span><span class="sxs-lookup"><span data-stu-id="b1c8d-109">Some example improvements (your results may vary depending on your hardware):</span></span> 

| <span data-ttu-id="b1c8d-110">Cenário</span><span class="sxs-lookup"><span data-stu-id="b1c8d-110">Scenario</span></span> | <span data-ttu-id="b1c8d-111">Tempo de 5,0 (ms)</span><span class="sxs-lookup"><span data-stu-id="b1c8d-111">5.0 Time (ms)</span></span> | <span data-ttu-id="b1c8d-112">Tempo de 5,1 (ms)</span><span class="sxs-lookup"><span data-stu-id="b1c8d-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="b1c8d-113">900</span><span class="sxs-lookup"><span data-stu-id="b1c8d-113">900</span></span> | <span data-ttu-id="b1c8d-114">250</span><span class="sxs-lookup"><span data-stu-id="b1c8d-114">250</span></span> |
| <span data-ttu-id="b1c8d-115">Primeira execução do PowerShell: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="b1c8d-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="b1c8d-116">30000</span><span class="sxs-lookup"><span data-stu-id="b1c8d-116">30000</span></span> | <span data-ttu-id="b1c8d-117">13000</span><span class="sxs-lookup"><span data-stu-id="b1c8d-117">13000</span></span> |
| <span data-ttu-id="b1c8d-118">Built do cache de análise de comando: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="b1c8d-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="b1c8d-119">7000</span><span class="sxs-lookup"><span data-stu-id="b1c8d-119">7000</span></span> | <span data-ttu-id="b1c8d-120">520</span><span class="sxs-lookup"><span data-stu-id="b1c8d-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="b1c8d-121">1400</span><span class="sxs-lookup"><span data-stu-id="b1c8d-121">1400</span></span> | <span data-ttu-id="b1c8d-122">750</span><span class="sxs-lookup"><span data-stu-id="b1c8d-122">750</span></span> |
  
> <span data-ttu-id="b1c8d-123">Observação: uma alteração relacionada à inicialização pode afetar alguns cenários sem suporte.</span><span class="sxs-lookup"><span data-stu-id="b1c8d-123">Note One change related to startup might impact some unsupported scenarios.</span></span> 
> <span data-ttu-id="b1c8d-124">O PowerShell não lê mais os arquivos `$pshome\*.ps1xml` – esses arquivos foram convertidos para C# para evitar sobrecarga de arquivo e CPU do processamento dos arquivos XML.</span><span class="sxs-lookup"><span data-stu-id="b1c8d-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span> 
<span data-ttu-id="b1c8d-125">Os arquivos ainda existem para dar suporte à V2 lado a lado; portanto, se você alterar o conteúdo do arquivo, ele não terá qualquer efeito na V5, apenas na V2.</span><span class="sxs-lookup"><span data-stu-id="b1c8d-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span> 
<span data-ttu-id="b1c8d-126">Observe que alterar os conteúdos desses arquivos nunca foi um cenário com suporte.</span><span class="sxs-lookup"><span data-stu-id="b1c8d-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="b1c8d-127">Outra alteração visível é como o PowerShell armazena em cache os comandos exportados e outras informações para módulos instalados em um sistema.</span><span class="sxs-lookup"><span data-stu-id="b1c8d-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span> <span data-ttu-id="b1c8d-128">Antes, esse cache era armazenado no diretório `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span><span class="sxs-lookup"><span data-stu-id="b1c8d-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span> <span data-ttu-id="b1c8d-129">No WMF 5.1, o cache é um único arquivo `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="b1c8d-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="b1c8d-130">Veja [Cache de análise do módulo](scenarios-features.md#module-analysis-cache) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="b1c8d-130">See [Module Analysis Cache](scenarios-features.md#module-analysis-cache) for more details.</span></span>

