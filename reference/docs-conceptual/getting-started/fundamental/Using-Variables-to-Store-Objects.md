---
ms.date: 08/27/2018
keywords: powershell, cmdlet
title: Usando variáveis para armazenar objetos
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: d166ec58dc658c1b134030c9a9592249ee40d4f5
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320951"
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="7e234-103">Usando variáveis para armazenar objetos</span><span class="sxs-lookup"><span data-stu-id="7e234-103">Using variables to store objects</span></span>

<span data-ttu-id="7e234-104">O PowerShell funciona com objetos.</span><span class="sxs-lookup"><span data-stu-id="7e234-104">PowerShell works with objects.</span></span> <span data-ttu-id="7e234-105">O PowerShell permite que você crie objetos nomeados, conhecidos como variáveis.</span><span class="sxs-lookup"><span data-stu-id="7e234-105">PowerShell lets you create named objects known as variables.</span></span>
<span data-ttu-id="7e234-106">Nomes de variáveis podem incluir o caractere de sublinhado e a qualquer caractere alfanumérico.</span><span class="sxs-lookup"><span data-stu-id="7e234-106">Variable names can include the underscore character and any alphanumeric characters.</span></span> <span data-ttu-id="7e234-107">Quando usada no PowerShell, uma variável é sempre especificada usando o caractere \$ seguido pelo nome da variável.</span><span class="sxs-lookup"><span data-stu-id="7e234-107">When used in PowerShell, a variable is always specified using the \$ character followed by variable name.</span></span>

## <a name="creating-a-variable"></a><span data-ttu-id="7e234-108">Criar uma variável</span><span class="sxs-lookup"><span data-stu-id="7e234-108">Creating a variable</span></span>

<span data-ttu-id="7e234-109">Você pode criar uma variável digitando um nome de variável válido:</span><span class="sxs-lookup"><span data-stu-id="7e234-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="7e234-110">Este exemplo não retorna resultados porque `$loc` não tem um valor.</span><span class="sxs-lookup"><span data-stu-id="7e234-110">This example returns no result because `$loc` doesn't have a value.</span></span> <span data-ttu-id="7e234-111">Você pode criar uma variável e atribuir a ela um valor na mesma etapa.</span><span class="sxs-lookup"><span data-stu-id="7e234-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="7e234-112">O PowerShell só criará a variável se ela não existir.</span><span class="sxs-lookup"><span data-stu-id="7e234-112">PowerShell only creates the variable if it doesn't exist.</span></span>
<span data-ttu-id="7e234-113">Caso contrário, ele atribuirá o valor especificado à variável existente.</span><span class="sxs-lookup"><span data-stu-id="7e234-113">Otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="7e234-114">O exemplo a seguir armazena o local atual na variável `$loc`:</span><span class="sxs-lookup"><span data-stu-id="7e234-114">The following example stores the current location in the variable `$loc`:</span></span>

```powershell
$loc = Get-Location
```

<span data-ttu-id="7e234-115">O PowerShell não exibe qualquer saída quando você digita esse comando.</span><span class="sxs-lookup"><span data-stu-id="7e234-115">PowerShell displays no output when you type this command.</span></span> <span data-ttu-id="7e234-116">O PowerShell envia a saída de "Get-Location" para `$loc`.</span><span class="sxs-lookup"><span data-stu-id="7e234-116">PowerShell sends the output of 'Get-Location' to `$loc`.</span></span> <span data-ttu-id="7e234-117">No PowerShell, os dados que não estão atribuídos ou redirecionados são enviados para a tela.</span><span class="sxs-lookup"><span data-stu-id="7e234-117">In PowerShell, data that isn't assigned or redirected is sent to the screen.</span></span> <span data-ttu-id="7e234-118">A sua localização atual aparece ao digitar `$loc`:</span><span class="sxs-lookup"><span data-stu-id="7e234-118">Typing `$loc` shows your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="7e234-119">Use `Get-Member` para exibir informações sobre o conteúdo das variáveis.</span><span class="sxs-lookup"><span data-stu-id="7e234-119">You can use `Get-Member` to display information about the contents of variables.</span></span> <span data-ttu-id="7e234-120">`Get-Member` mostra que `$loc` é um objeto **PathInfo**, assim como a saída de `Get-Location`:</span><span class="sxs-lookup"><span data-stu-id="7e234-120">`Get-Member` shows you that `$loc` is a **PathInfo** object, just like the output from `Get-Location`:</span></span>

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a><span data-ttu-id="7e234-121">Manipular variáveis</span><span class="sxs-lookup"><span data-stu-id="7e234-121">Manipulating variables</span></span>

<span data-ttu-id="7e234-122">O PowerShell fornece vários comandos para manipular variáveis.</span><span class="sxs-lookup"><span data-stu-id="7e234-122">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="7e234-123">Você pode ver uma listagem completa em um formato legível digitando:</span><span class="sxs-lookup"><span data-stu-id="7e234-123">You can see a complete listing in a readable form by typing:</span></span>

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="7e234-124">O PowerShell também cria diversas variáveis definidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="7e234-124">PowerShell also creates several system-defined variables.</span></span> <span data-ttu-id="7e234-125">Você pode usar o cmdlet `Remove-Variable` para remover as variáveis que não são controladas pelo PowerShell da sessão atual.</span><span class="sxs-lookup"><span data-stu-id="7e234-125">You can use the `Remove-Variable` cmdlet to remove variables, which are not controlled by PowerShell, from the current session.</span></span> <span data-ttu-id="7e234-126">Digite o seguinte comando a seguir para limpar todas as variáveis:</span><span class="sxs-lookup"><span data-stu-id="7e234-126">Type the following command to clear all variables:</span></span>

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="7e234-127">Após a execução do comando anterior, o cmdlet `Get-Variable` mostra as variáveis de sistema do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7e234-127">After running the previous command, the `Get-Variable` cmdlet shows the PowerShell system variables.</span></span>

<span data-ttu-id="7e234-128">O PowerShell também cria uma unidade de variável.</span><span class="sxs-lookup"><span data-stu-id="7e234-128">PowerShell also creates a variable drive.</span></span> <span data-ttu-id="7e234-129">Use o exemplo a seguir para exibir todas as variáveis do PowerShell usando a unidade de variável:</span><span class="sxs-lookup"><span data-stu-id="7e234-129">Use the following example to display all PowerShell variables using the variable drive:</span></span>

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a><span data-ttu-id="7e234-130">Usar variáveis do cmd.exe</span><span class="sxs-lookup"><span data-stu-id="7e234-130">Using cmd.exe variables</span></span>

<span data-ttu-id="7e234-131">O PowerShell pode usar as mesmas variáveis de ambiente disponíveis a qualquer processo do Windows, incluindo **cmd.exe**.</span><span class="sxs-lookup"><span data-stu-id="7e234-131">PowerShell can use the same environment variables available to any Windows process, including **cmd.exe**.</span></span> <span data-ttu-id="7e234-132">Essas variáveis são expostas por meio de uma unidade chamada `env:`.</span><span class="sxs-lookup"><span data-stu-id="7e234-132">These variables are exposed through a drive named `env:`.</span></span> <span data-ttu-id="7e234-133">Exiba essas variáveis digitando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="7e234-133">You can view these variables by typing the following command:</span></span>

```powershell
Get-ChildItem env:
```

<span data-ttu-id="7e234-134">Os cmdlets `*-Variable` padrão não são projetados para funcionar com variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="7e234-134">The standard `*-Variable` cmdlets aren't designed to work with environment variables.</span></span> <span data-ttu-id="7e234-135">Variáveis de ambiente são acessadas usando o prefixo de unidade `env:`.</span><span class="sxs-lookup"><span data-stu-id="7e234-135">Environment variables are accessed using the `env:` drive prefix.</span></span> <span data-ttu-id="7e234-136">Por exemplo, a variável **% SystemRoot %** no **cmd.exe** contém nome do diretório raiz do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="7e234-136">For example, the **%SystemRoot%** variable in **cmd.exe** contains the operating system's root directory name.</span></span> <span data-ttu-id="7e234-137">No PowerShell, use `$env:SystemRoot` para acessar o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="7e234-137">In PowerShell, you use `$env:SystemRoot` to access the same value.</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="7e234-138">Você também pode criar e modificar variáveis de ambiente do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7e234-138">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="7e234-139">As variáveis de ambiente do PowerShell seguem as mesmas regras para variáveis de ambiente usadas em outro lugar no sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="7e234-139">Environment variables in PowerShell follow the same rules for environment variables used elsewhere in the operating system.</span></span> <span data-ttu-id="7e234-140">O exemplo a seguir cria uma nova variável de ambiente:</span><span class="sxs-lookup"><span data-stu-id="7e234-140">The following example creates a new environment variable:</span></span>

```powershell
$env:LIB_PATH='/usr/local/lib'
```

<span data-ttu-id="7e234-141">Embora não seja necessário, é comum usar letras maiúsculas nos nomes de variáveis de ambientes.</span><span class="sxs-lookup"><span data-stu-id="7e234-141">Though not required, is it common for environment variable names to use all uppercase letters.</span></span>
