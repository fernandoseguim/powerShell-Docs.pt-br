---
ms.date: 08/27/2018
keywords: powershell, cmdlet
title: Obtendo informações sobre comandos
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 7af83e3a0e776d96e580b442430357b4ea063a72
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400551"
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="42ada-103">Obtendo informações sobre comandos</span><span class="sxs-lookup"><span data-stu-id="42ada-103">Getting information about commands</span></span>

<span data-ttu-id="42ada-104">O `Get-Command` do PowerShell exibe os comandos disponíveis na sessão atual.</span><span class="sxs-lookup"><span data-stu-id="42ada-104">The PowerShell `Get-Command` displays commands that are available in your current session.</span></span>
<span data-ttu-id="42ada-105">Ao executar o cmdlet `Get-Command`, você verá algo semelhante à seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="42ada-105">When you run the `Get-Command` cmdlet, you see something similar to the following output:</span></span>

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

<span data-ttu-id="42ada-106">Esta saída se parece muito como a saída de Ajuda do **cmd.exe**: um resumo tabular de comandos internos.</span><span class="sxs-lookup"><span data-stu-id="42ada-106">This output looks a lot like the Help output of **cmd.exe**: a tabular summary of internal commands.</span></span> <span data-ttu-id="42ada-107">No trecho do resultado do comando `Get-Command` mostrado acima, todos os comandos mostrados têm um CommandType de Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="42ada-107">In the excerpt of the `Get-Command` command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="42ada-108">Um cmdlet é o tipo de comando intrínseco do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="42ada-108">A cmdlet is PowerShell's intrinsic command type.</span></span> <span data-ttu-id="42ada-109">Este tipo corresponde aproximadamente a comandos como `dir` e `cd` no **cmd.exe** ou aos comandos internos de shells de Unix, como bash.</span><span class="sxs-lookup"><span data-stu-id="42ada-109">This type corresponds roughly to commands like `dir` and `cd` in **cmd.exe** or the built-in commands of Unix shells like bash.</span></span>

<span data-ttu-id="42ada-110">O cmdlet `Get-Command` tem um parâmetro **Syntax** que retorna a sintaxe de cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="42ada-110">The `Get-Command` cmdlet has a **Syntax** parameter that returns syntax of each cmdlet.</span></span> <span data-ttu-id="42ada-111">O exemplo a seguir mostra como obter a sintaxe do cmdlet `Get-Help`:</span><span class="sxs-lookup"><span data-stu-id="42ada-111">The following example shows how to get the syntax of the `Get-Help` cmdlet:</span></span>

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a><span data-ttu-id="42ada-112">Exibir o comando disponível por tipo</span><span class="sxs-lookup"><span data-stu-id="42ada-112">Displaying available command by type</span></span>

<span data-ttu-id="42ada-113">O comando `Get-Command` lista somente os cmdlets na sessão atual.</span><span class="sxs-lookup"><span data-stu-id="42ada-113">The `Get-Command` command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="42ada-114">Na verdade, o PowerShell dá suporte a vários outros tipos de comandos:</span><span class="sxs-lookup"><span data-stu-id="42ada-114">PowerShell actually supports several other types of commands:</span></span>

- <span data-ttu-id="42ada-115">Aliases</span><span class="sxs-lookup"><span data-stu-id="42ada-115">Aliases</span></span>
- <span data-ttu-id="42ada-116">Funções</span><span class="sxs-lookup"><span data-stu-id="42ada-116">Functions</span></span>
- <span data-ttu-id="42ada-117">Scripts</span><span class="sxs-lookup"><span data-stu-id="42ada-117">Scripts</span></span>

<span data-ttu-id="42ada-118">Arquivos externos executáveis, ou arquivos que possuem um manipulador de tipo de arquivo registrado, também são classificados como comandos.</span><span class="sxs-lookup"><span data-stu-id="42ada-118">External executable files, or files that have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="42ada-119">Para obter todos os comandos na sessão, digite:</span><span class="sxs-lookup"><span data-stu-id="42ada-119">To get all commands in the session, type:</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="42ada-120">Essa lista inclui comandos externos em seu caminho de pesquisa, portanto pode conter milhares de itens.</span><span class="sxs-lookup"><span data-stu-id="42ada-120">This list includes external commands in your search path so it can contain thousands of items.</span></span>
<span data-ttu-id="42ada-121">É mais útil examinar um conjunto reduzido de comandos.</span><span class="sxs-lookup"><span data-stu-id="42ada-121">It is more useful to look at a reduced set of commands.</span></span>

> [!NOTE]
> <span data-ttu-id="42ada-122">O asterisco (\*) é usado para correspondência de curingas nos argumentos de comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="42ada-122">The asterisk (\*) is used for wildcard matching in PowerShell command arguments.</span></span> <span data-ttu-id="42ada-123">O \* corresponde a “um ou mais caracteres quaisquer”.</span><span class="sxs-lookup"><span data-stu-id="42ada-123">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="42ada-124">Você pode digitar `Get-Command a*` para encontrar todos os comandos que começam com a letra "a".</span><span class="sxs-lookup"><span data-stu-id="42ada-124">You can type `Get-Command a*` to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="42ada-125">Diferentemente da correspondência de curingas no **cmd.exe**, curingas do PowerShell também serão compatíveis com um ponto.</span><span class="sxs-lookup"><span data-stu-id="42ada-125">Unlike wildcard matching in **cmd.exe**, PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="42ada-126">Use o parâmetro **CommandType** de `Get-Command` para obter comandos nativos de outros tipos.</span><span class="sxs-lookup"><span data-stu-id="42ada-126">Use the **CommandType** parameter of `Get-Command` to get native commands of other types.</span></span>
<span data-ttu-id="42ada-127">.</span><span class="sxs-lookup"><span data-stu-id="42ada-127">cmdlet.</span></span>

<span data-ttu-id="42ada-128">Para obter os aliases de comando, que são os apelidos atribuídos a comandos, digite:</span><span class="sxs-lookup"><span data-stu-id="42ada-128">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```powershell
Get-Command -CommandType Alias
```

<span data-ttu-id="42ada-129">Para obter as funções na sessão atual, digite:</span><span class="sxs-lookup"><span data-stu-id="42ada-129">To get the functions in the current session, type:</span></span>

```powershell
Get-Command -CommandType Function
```

<span data-ttu-id="42ada-130">Para exibir os scripts no caminho de pesquisa do PowerShell, digite:</span><span class="sxs-lookup"><span data-stu-id="42ada-130">To display scripts in PowerShell's search path, type:</span></span>

```powershell
Get-Command -CommandType Script
```