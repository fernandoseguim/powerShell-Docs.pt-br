---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Obtendo informações sobre comandos
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 1426c171d74afc87751f7d31d46571b9c98fa47e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="8ae78-103">Obtendo informações sobre comandos</span><span class="sxs-lookup"><span data-stu-id="8ae78-103">Getting Information About Commands</span></span>
<span data-ttu-id="8ae78-104">O cmdlet **Get-Command** do Windows PowerShell obtém todos os comandos que estão disponíveis na sessão atual.</span><span class="sxs-lookup"><span data-stu-id="8ae78-104">The Windows PowerShell **Get-Command** cmdlet gets all commands that are available in your current session.</span></span> <span data-ttu-id="8ae78-105">Quando você digita **Get-Command** em um prompt do Windows PowerShell, uma saída semelhante à seguinte é exibida:</span><span class="sxs-lookup"><span data-stu-id="8ae78-105">When you type **Get-Command** at a Windows PowerShell prompt, you will see output similar to the following:</span></span>

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

<span data-ttu-id="8ae78-106">Esta saída se parece muito como a saída de Ajuda do Cmd.exe: um resumo tabular de comandos internos.</span><span class="sxs-lookup"><span data-stu-id="8ae78-106">This output looks a lot like the Help output of Cmd.exe: a tabular summary of internal commands.</span></span> <span data-ttu-id="8ae78-107">No trecho da saída do comando **Get-Command** mostrado acima, todos os comandos mostrados tem um CommandType do Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8ae78-107">In the excerpt of the **Get-Command** command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="8ae78-108">Um cmdlet é o tipo de comando intrínseco do Windows PowerShell; um tipo que corresponde aproximadamente aos comandos **dir** e **cd** de Cmd.exe e shells integrados do UNIX, como BASH.</span><span class="sxs-lookup"><span data-stu-id="8ae78-108">A cmdlet is Windows PowerShell's intrinsic command type - a type that corresponds roughly to the **dir** and **cd** commands of Cmd.exe and to built-ins in UNIX shells such as BASH.</span></span>

<span data-ttu-id="8ae78-109">Na saída do comando **Get-Command**, todas as definições terminam com reticências (...) para indicar que o PowerShell não consegue exibir todo o conteúdo no espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="8ae78-109">In the output of the **Get-Command** command, all the definitions end with ellipses (...) to indicate that PowerShell cannot display all the content in the available space.</span></span> <span data-ttu-id="8ae78-110">Quando o Windows PowerShell exibe a saída, ele formata o resultado como texto e o organiza para ajustar os dados corretamente na janela.</span><span class="sxs-lookup"><span data-stu-id="8ae78-110">When Windows PowerShell displays output, it formats the output as text and then arranges it to make the data fit cleanly into the window.</span></span> <span data-ttu-id="8ae78-111">Falaremos sobre isso mais tarde na seção sobre formatadores.</span><span class="sxs-lookup"><span data-stu-id="8ae78-111">We will talk about this later in the section on formatters.</span></span>

<span data-ttu-id="8ae78-112">O cmdlet **Get-Command** tem um parâmetro **Syntax** que obtém a sintaxe de cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8ae78-112">The **Get-Command** cmdlet has a **Syntax** parameter that gets the syntax of each cmdlet.</span></span> <span data-ttu-id="8ae78-113">Para obter a sintaxe do cmdlet Get-Help, use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="8ae78-113">To get the syntax of the Get-Help cmdlet, use the following command:</span></span>

<span data-ttu-id="8ae78-114">**Get-Command Get-Help -Syntax**</span><span class="sxs-lookup"><span data-stu-id="8ae78-114">**Get-Command Get-Help -Syntax**</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### <a name="displaying-available-command-types"></a><span data-ttu-id="8ae78-115">Exibindo tipos de comando disponíveis</span><span class="sxs-lookup"><span data-stu-id="8ae78-115">Displaying Available Command Types</span></span>
<span data-ttu-id="8ae78-116">O comando **Get-Command** não lista todos os comandos disponíveis no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ae78-116">The **Get-Command** command does not list every command that is available in Windows PowerShell.</span></span> <span data-ttu-id="8ae78-117">Em vez disso, o comando **Get-Command** lista somente os cmdlets da sessão atual.</span><span class="sxs-lookup"><span data-stu-id="8ae78-117">Instead, the **Get-Command** command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="8ae78-118">Na verdade, o Windows PowerShell oferece suporte a vários outros tipos de comandos.</span><span class="sxs-lookup"><span data-stu-id="8ae78-118">Windows PowerShell actually supports several other types of commands.</span></span> <span data-ttu-id="8ae78-119">Aliases, funções e scripts também são comandos do Windows PowerShell, embora eles não sejam discutidos em detalhes no Guia do Usuário do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ae78-119">Aliases, functions, and scripts are also Windows PowerShell commands, although they are not discussed in detail in the Windows PowerShell User's Guide.</span></span> <span data-ttu-id="8ae78-120">Arquivos externos executáveis ou que possuem um manipulador do tipo de arquivo registrado também são classificados como comandos.</span><span class="sxs-lookup"><span data-stu-id="8ae78-120">External files that are executable, or have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="8ae78-121">Para obter todos os comandos na sessão, digite:</span><span class="sxs-lookup"><span data-stu-id="8ae78-121">To get all commands in the session, type:</span></span>

```
Get-Command *
```

<span data-ttu-id="8ae78-122">Como essa lista inclui arquivos externos em seu caminho de pesquisa, ela pode conter milhares de itens.</span><span class="sxs-lookup"><span data-stu-id="8ae78-122">Because this list includes external files in your search path, it may contain thousands of items.</span></span> <span data-ttu-id="8ae78-123">É mais útil examinar um conjunto reduzido de comandos.</span><span class="sxs-lookup"><span data-stu-id="8ae78-123">It is more useful to look at a reduced set of commands.</span></span>

<span data-ttu-id="8ae78-124">Para obter comandos nativos de outros tipos, use o parâmetro **CommandType** do cmdlet **Get-Command**.</span><span class="sxs-lookup"><span data-stu-id="8ae78-124">To get native commands of other types, use the **CommandType** parameter of the **Get-Command** cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="8ae78-125">O asterisco (\*) é usado para correspondência de curingas nos argumentos de comando do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ae78-125">The asterisk (\*) is used for wildcard matching in Windows PowerShell command arguments.</span></span> <span data-ttu-id="8ae78-126">O \* corresponde a “um ou mais caracteres quaisquer”.</span><span class="sxs-lookup"><span data-stu-id="8ae78-126">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="8ae78-127">Você pode digitar **Get-Command a\&#42;** para encontrar todos os comandos que começam com a letra "a".</span><span class="sxs-lookup"><span data-stu-id="8ae78-127">You can type **Get-Command a\&#42;** to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="8ae78-128">Diferentemente da correspondência de curingas no Cmd.exe, curingas do Windows PowerShell também serão compatíveis com um ponto.</span><span class="sxs-lookup"><span data-stu-id="8ae78-128">Unlike wildcard matching in Cmd.exe, Windows PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="8ae78-129">Para obter os aliases de comando, que são os apelidos atribuídos a comandos, digite:</span><span class="sxs-lookup"><span data-stu-id="8ae78-129">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```
Get-Command -CommandType Alias
```

<span data-ttu-id="8ae78-130">Para obter as funções na sessão atual, digite:</span><span class="sxs-lookup"><span data-stu-id="8ae78-130">To get the functions in the current session, type:</span></span>

```
Get-Command -CommandType Function
```

<span data-ttu-id="8ae78-131">Para exibir os scripts no caminho de pesquisa do Windows PowerShell, digite:</span><span class="sxs-lookup"><span data-stu-id="8ae78-131">To display scripts in Windows PowerShell's search path, type:</span></span>

```
Get-Command -CommandType Script
```