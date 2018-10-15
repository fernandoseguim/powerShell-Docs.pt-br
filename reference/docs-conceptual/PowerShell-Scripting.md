---
ms.date: 08/27/2018
keywords: powershell, cmdlet
title: Scripts do PowerShell
ms.openlocfilehash: 8a152ab338d42f861b7ff38de44d68db14262abb
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851179"
---
# <a name="powershell"></a><span data-ttu-id="2e68f-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="2e68f-103">PowerShell</span></span>

<span data-ttu-id="2e68f-104">O PowerShell é um shell de linha de comando baseado em tarefas e linguagem de script desenvolvido no .NET.</span><span class="sxs-lookup"><span data-stu-id="2e68f-104">PowerShell is a task-based command-line shell and scripting language built on .NET.</span></span>
<span data-ttu-id="2e68f-105">O PowerShell ajuda os administradores do sistema e usuários avançados a automatizar rapidamente as tarefas que gerenciam processos e sistemas operacionais (Linux, macOS e Windows).</span><span class="sxs-lookup"><span data-stu-id="2e68f-105">PowerShell helps system administrators and power-users can rapidly automate tasks that manage operating systems (Linux, macOS, and Windows) and processes.</span></span>

<span data-ttu-id="2e68f-106">Os comandos do PowerShell permitem que você gerencie os computadores da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="2e68f-106">PowerShell commands let you manage computers from the command line.</span></span> <span data-ttu-id="2e68f-107">Os provedores do PowerShell permitem o acesso a repositórios de dados, como o Registro e o repositório de certificados, de forma tão fácil quanto acessar o sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="2e68f-107">PowerShell providers let you access data stores, such as the registry and certificate store, as easily as you access the file system.</span></span> <span data-ttu-id="2e68f-108">O PowerShell inclui um valioso analisador de expressões e uma linguagem de scripts totalmente desenvolvida.</span><span class="sxs-lookup"><span data-stu-id="2e68f-108">PowerShell includes a rich expression parser and a fully developed scripting language.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="2e68f-109">O PowerShell é um software livre</span><span class="sxs-lookup"><span data-stu-id="2e68f-109">PowerShell is open-source</span></span>

<span data-ttu-id="2e68f-110">O código-fonte base do PowerShell agora está disponível no GitHub e está aberto para contribuições da comunidade.</span><span class="sxs-lookup"><span data-stu-id="2e68f-110">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="2e68f-111">Confira a [Fonte do PowerShell no GitHub](https://github.com/powershell/powershell).</span><span class="sxs-lookup"><span data-stu-id="2e68f-111">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="2e68f-112">Você pode começar com as partes de que precisa em [Obter PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span><span class="sxs-lookup"><span data-stu-id="2e68f-112">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="2e68f-113">Ou, talvez, com um tour rápido em [Guia de Introdução](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span><span class="sxs-lookup"><span data-stu-id="2e68f-113">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="2e68f-114">Metas de design do PowerShell</span><span class="sxs-lookup"><span data-stu-id="2e68f-114">PowerShell design goals</span></span>

<span data-ttu-id="2e68f-115">O PowerShell foi projetado para melhorar o ambiente de script e de linha de comando eliminando problemas antigos e adicionando novos recursos.</span><span class="sxs-lookup"><span data-stu-id="2e68f-115">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="2e68f-116">Detectabilidade</span><span class="sxs-lookup"><span data-stu-id="2e68f-116">Discoverability</span></span>

<span data-ttu-id="2e68f-117">O PowerShell facilita a descoberta dos seus recursos.</span><span class="sxs-lookup"><span data-stu-id="2e68f-117">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="2e68f-118">Por exemplo, para localizar uma lista de cmdlets que exibem e alteram os serviços do Windows, digite:</span><span class="sxs-lookup"><span data-stu-id="2e68f-118">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="2e68f-119">Depois de descobrir qual cmdlet realiza uma tarefa, você pode saber mais sobre ele usando o cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="2e68f-119">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span> <span data-ttu-id="2e68f-120">Por exemplo, para exibir a ajuda sobre o cmdlet `Get-Service`, digite:</span><span class="sxs-lookup"><span data-stu-id="2e68f-120">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```

<span data-ttu-id="2e68f-121">A maioria dos cmdlets retorna objetos que podem ser manipulados e renderizados como texto para exibição.</span><span class="sxs-lookup"><span data-stu-id="2e68f-121">Most cmdlets return objects that can be manipulated and then rendered as text for display.</span></span> <span data-ttu-id="2e68f-122">Para entender por completo a saída desse cmdlet, direcione a saída para o cmdlet `Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="2e68f-122">To fully understand the output of a cmdlet, pipe the output to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="2e68f-123">Por exemplo, o comando a seguir exibe informações sobre os membros da saída do objeto pelo cmdlet `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="2e68f-123">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="2e68f-124">Consistência</span><span class="sxs-lookup"><span data-stu-id="2e68f-124">Consistency</span></span>

<span data-ttu-id="2e68f-125">O gerenciamento de sistemas pode ser uma tarefa complexa.</span><span class="sxs-lookup"><span data-stu-id="2e68f-125">Managing systems can be a complex task.</span></span> <span data-ttu-id="2e68f-126">As ferramentas que têm uma interface consistente ajudam a controlar a complexidade inerente.</span><span class="sxs-lookup"><span data-stu-id="2e68f-126">Tools that have a consistent interface help to control the inherent complexity.</span></span> <span data-ttu-id="2e68f-127">Infelizmente, as ferramentas de linha de comando e objetos COM programáveis em script não são conhecidos por sua consistência.</span><span class="sxs-lookup"><span data-stu-id="2e68f-127">Unfortunately, command-line tools and scriptable COM objects aren't known for their consistency.</span></span>

<span data-ttu-id="2e68f-128">A consistência do PowerShell é um de seus principais ativos.</span><span class="sxs-lookup"><span data-stu-id="2e68f-128">The consistency of PowerShell is one of its primary assets.</span></span> <span data-ttu-id="2e68f-129">Por exemplo, se você aprender a usar o cmdlet `Sort-Object`, poderá usar esse conhecimento para classificar a saída de qualquer cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2e68f-129">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span> <span data-ttu-id="2e68f-130">Você não precisa apender as diferentes rotinas de classificação de cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2e68f-130">You don't have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="2e68f-131">Além disso, os desenvolvedores de cmdlet não precisam criar recursos de classificação para os seus cmdlets.</span><span class="sxs-lookup"><span data-stu-id="2e68f-131">Additionally, cmdlet developers don't have to design sorting features for their cmdlets.</span></span> <span data-ttu-id="2e68f-132">O PowerShell fornece uma estrutura com os recursos básicos que forçam a consistência.</span><span class="sxs-lookup"><span data-stu-id="2e68f-132">PowerShell provides a framework with the basic features that forces consistency.</span></span> <span data-ttu-id="2e68f-133">A estrutura elimina algumas opções que são deixadas para o desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="2e68f-133">The framework eliminates some choices that are left to the developer.</span></span> <span data-ttu-id="2e68f-134">Mas, em troca, ela torna o desenvolvimento de cmdlets muito mais simples.</span><span class="sxs-lookup"><span data-stu-id="2e68f-134">But, in return, it makes the development of cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="2e68f-135">Ambientes interativos e de scripts</span><span class="sxs-lookup"><span data-stu-id="2e68f-135">Interactive and scripting environments</span></span>

<span data-ttu-id="2e68f-136">O Prompt de Comando do Windows fornece um shell interativo com o acesso a ferramentas de linha de comando e scripts básicos.</span><span class="sxs-lookup"><span data-stu-id="2e68f-136">The Windows Command Prompt provides an interactive shell with access to command-line tools and basic scripting.</span></span> <span data-ttu-id="2e68f-137">O WSH (Windows Script Host) tem ferramentas de linha de comando programáveis por script e objetos de automação COM, mas não fornece um shell interativo.</span><span class="sxs-lookup"><span data-stu-id="2e68f-137">Windows Script Host (WSH) has scriptable command-line tools and COM automation objects, but doesn't provide an interactive shell.</span></span>

<span data-ttu-id="2e68f-138">O PowerShell combina um shell interativo e um ambiente de geração de script.</span><span class="sxs-lookup"><span data-stu-id="2e68f-138">PowerShell combines an interactive shell and a scripting environment.</span></span> <span data-ttu-id="2e68f-139">O PowerShell pode acessar as ferramentas de linha de comando, objetos COM e bibliotecas de classes do .NET.</span><span class="sxs-lookup"><span data-stu-id="2e68f-139">PowerShell can access command-line tools, COM objects, and .NET class libraries.</span></span> <span data-ttu-id="2e68f-140">Essa combinação de funcionalidades estende os recursos do usuário interativo, o produtor de script e o administrador do sistema.</span><span class="sxs-lookup"><span data-stu-id="2e68f-140">This combination of features extends the capabilities of the interactive user, the script writer, and the system administrator.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="2e68f-141">Orientação do objeto</span><span class="sxs-lookup"><span data-stu-id="2e68f-141">Object orientation</span></span>

<span data-ttu-id="2e68f-142">O PowerShell tem base no objeto, não no texto.</span><span class="sxs-lookup"><span data-stu-id="2e68f-142">PowerShell is based on object not text.</span></span> <span data-ttu-id="2e68f-143">A saída de um comando é um objeto.</span><span class="sxs-lookup"><span data-stu-id="2e68f-143">The output of a command is an object.</span></span> <span data-ttu-id="2e68f-144">Você pode enviar o objeto de saída, pelo pipeline, para outro comando como entrada.</span><span class="sxs-lookup"><span data-stu-id="2e68f-144">You can send the output object, through the pipeline, to another command as its input.</span></span>

<span data-ttu-id="2e68f-145">Esse pipeline fornece uma interface familiar para pessoas com experiência com outros shells.</span><span class="sxs-lookup"><span data-stu-id="2e68f-145">This pipeline provides a familiar interface for people experienced with other shells.</span></span> <span data-ttu-id="2e68f-146">O PowerShell expande esse conceito, enviando objetos em vez de texto.</span><span class="sxs-lookup"><span data-stu-id="2e68f-146">PowerShell extends this concept by sending objects rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="2e68f-147">Transição fácil para scripts</span><span class="sxs-lookup"><span data-stu-id="2e68f-147">Easy transition to scripting</span></span>

<span data-ttu-id="2e68f-148">A descoberta de comando do PowerShell facilita a transição de uma digitação interativa de comandos para a criação e execução de scripts.</span><span class="sxs-lookup"><span data-stu-id="2e68f-148">PowerShell's command discoverability makes it easy to transition from typing commands interactively to creating and running scripts.</span></span> <span data-ttu-id="2e68f-149">O histórico e as transcrições do PowerShell facilitam a cópia de comandos em um arquivo para uso como script.</span><span class="sxs-lookup"><span data-stu-id="2e68f-149">PowerShell transcripts and history make it easy to copy commands to a file for use as a script.</span></span>
