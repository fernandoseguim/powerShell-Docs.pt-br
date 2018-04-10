---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Usando variáveis para armazenar objetos
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: e52f0a344d0ad13db42b34bed912d584c99b0e30
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="848dd-103">Usando variáveis para armazenar objetos</span><span class="sxs-lookup"><span data-stu-id="848dd-103">Using Variables to Store Objects</span></span>
<span data-ttu-id="848dd-104">O PowerShell funciona com objetos.</span><span class="sxs-lookup"><span data-stu-id="848dd-104">PowerShell works with objects.</span></span> <span data-ttu-id="848dd-105">O PowerShell permite criar variáveis, que são basicamente objetos nomeados, a fim de preservar a saída para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="848dd-105">PowerShell lets you create variables, essentially named objects, to preserve output for later use.</span></span> <span data-ttu-id="848dd-106">Se você está acostumado a trabalhar com variáveis em outros shells, lembre-se de que variáveis do PowerShell são objetos, não texto.</span><span class="sxs-lookup"><span data-stu-id="848dd-106">If you are used to working with variables in other shells remember that PowerShell variables are objects, not text.</span></span>

<span data-ttu-id="848dd-107">Variáveis sempre são especificadas com o caractere inicial $ e podem incluir qualquer caractere alfanumérico ou sublinhado em seus nomes.</span><span class="sxs-lookup"><span data-stu-id="848dd-107">Variables are always specified with the initial character $, and can include any alphanumeric characters or the underscore in their names.</span></span>

### <a name="creating-a-variable"></a><span data-ttu-id="848dd-108">Criando uma variável</span><span class="sxs-lookup"><span data-stu-id="848dd-108">Creating a Variable</span></span>
<span data-ttu-id="848dd-109">Você pode criar uma variável digitando um nome de variável válido:</span><span class="sxs-lookup"><span data-stu-id="848dd-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="848dd-110">Isso não retornará nenhum resultado porque **$loc** não tem um valor.</span><span class="sxs-lookup"><span data-stu-id="848dd-110">This returns no result because **$loc** does not have a value.</span></span> <span data-ttu-id="848dd-111">Você pode criar uma variável e atribuir a ela um valor na mesma etapa.</span><span class="sxs-lookup"><span data-stu-id="848dd-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="848dd-112">O PowerShell criará a variável somente se ela não existir; caso contrário, ele atribuirá o valor especificado para a variável existente.</span><span class="sxs-lookup"><span data-stu-id="848dd-112">PowerShell only creates the variable if it does not exist; otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="848dd-113">Para armazenar seu local atual na variável **$loc**, digite:</span><span class="sxs-lookup"><span data-stu-id="848dd-113">To store your current location in the variable **$loc**, type:</span></span>

```
$loc = Get-Location
```

<span data-ttu-id="848dd-114">Não há nenhuma saída exibida quando você digitar esse comando porque a saída é enviada para $loc.</span><span class="sxs-lookup"><span data-stu-id="848dd-114">There is no output displayed when you type this command because the output is sent to $loc.</span></span> <span data-ttu-id="848dd-115">No PowerShell, a saída exibida é um efeito colateral do fato de que os dados que não são direcionados sempre são enviados para a tela.</span><span class="sxs-lookup"><span data-stu-id="848dd-115">In PowerShell, displayed output is a side effect of the fact that data, which is not otherwise directed, always gets sent to the screen.</span></span> <span data-ttu-id="848dd-116">Digitar $loc mostrará o local atual:</span><span class="sxs-lookup"><span data-stu-id="848dd-116">Typing $loc will show your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="848dd-117">Você pode usar o **Get-Member** para exibir informações sobre o conteúdo de variáveis.</span><span class="sxs-lookup"><span data-stu-id="848dd-117">You can use **Get-Member** to display information about the contents of variables.</span></span> <span data-ttu-id="848dd-118">Direcionar $loc para Get-Member mostrará que ele é um objeto **PathInfo**, bem como a saída de Get-Location:</span><span class="sxs-lookup"><span data-stu-id="848dd-118">Piping $loc to Get-Member will show you that it is a **PathInfo** object, just like the output from Get-Location:</span></span>

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a><span data-ttu-id="848dd-119">Manipulação de variáveis</span><span class="sxs-lookup"><span data-stu-id="848dd-119">Manipulating Variables</span></span>
<span data-ttu-id="848dd-120">O PowerShell fornece vários comandos para manipular variáveis.</span><span class="sxs-lookup"><span data-stu-id="848dd-120">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="848dd-121">Você pode ver uma listagem completa em um formato legível digitando:</span><span class="sxs-lookup"><span data-stu-id="848dd-121">You can see a complete listing in a readable form by typing:</span></span>

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="848dd-122">Além de variáveis criadas na sessão atual do PowerShell, há diversas variáveis definidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="848dd-122">In addition to the variables you create in your current PowerShell session, there are several system-defined variables.</span></span> <span data-ttu-id="848dd-123">Você pode usar o cmdlet **Remove-Variable** para limpar todas as variáveis que não são controladas pelo PowerShell.</span><span class="sxs-lookup"><span data-stu-id="848dd-123">You can use the **Remove-Variable** cmdlet to clear out all of the variables which are not controlled by PowerShell.</span></span> <span data-ttu-id="848dd-124">Digite o seguinte comando a seguir para limpar todas as variáveis:</span><span class="sxs-lookup"><span data-stu-id="848dd-124">Type the following command to clear all variables:</span></span>

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="848dd-125">Isso produzirá o prompt de confirmação que você vê abaixo.</span><span class="sxs-lookup"><span data-stu-id="848dd-125">This will produce the confirmation prompt you see below.</span></span>

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

<span data-ttu-id="848dd-126">Se você executar o cmdlet **Get-Variable**, verá as variáveis restantes do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="848dd-126">If you then run the **Get-Variable** cmdlet, you will see the remaining PowerShell variables.</span></span> <span data-ttu-id="848dd-127">Como também há uma variável de unidade do PowerShell, você também pode exibir todas as variáveis do PowerShell digitando:</span><span class="sxs-lookup"><span data-stu-id="848dd-127">Since there is also a variable PowerShell drive, you can also display all PowerShell variables by typing:</span></span>

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a><span data-ttu-id="848dd-128">Usando variáveis do Cmd.exe</span><span class="sxs-lookup"><span data-stu-id="848dd-128">Using Cmd.exe Variables</span></span>
<span data-ttu-id="848dd-129">Embora o PowerShell não seja o Cmd.exe, ele é executado em um ambiente de shell de comando e pode usar as mesmas variáveis disponíveis em qualquer ambiente no Windows.</span><span class="sxs-lookup"><span data-stu-id="848dd-129">Although PowerShell is not Cmd.exe, it runs in a command shell environment and can use the same variables available in any environment in Windows.</span></span> <span data-ttu-id="848dd-130">Essas variáveis são expostas por meio de uma unidade chamada **env**:.</span><span class="sxs-lookup"><span data-stu-id="848dd-130">These variables are exposed through a drive named **env**:.</span></span> <span data-ttu-id="848dd-131">Você pode exibir essas variáveis digitando:</span><span class="sxs-lookup"><span data-stu-id="848dd-131">You can view these variables by typing:</span></span>

```
Get-ChildItem env:
```

<span data-ttu-id="848dd-132">Embora os cmdlets de variável padrão não sejam projetados para trabalhar com variáveis **env:**, você ainda pode usá-las especificando o prefixo **env:**.</span><span class="sxs-lookup"><span data-stu-id="848dd-132">Although the standard variable cmdlets are not designed to work with **env:** variables, you can still use them by specifying the **env:** prefix.</span></span> <span data-ttu-id="848dd-133">Por exemplo, para ver a pasta raiz do sistema operacional, você pode usar a variável do shell de comando **%SystemRoot%** dentro do PowerShell digitando:</span><span class="sxs-lookup"><span data-stu-id="848dd-133">For example, to see the operating system root directory, you can use the command-shell **%SystemRoot%** variable from within PowerShell by typing:</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="848dd-134">Você também pode criar e modificar variáveis de ambiente do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="848dd-134">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="848dd-135">Variáveis de ambiente acessadas do Windows PowerShell estão em conformidade com as regras normais de variáveis de ambiente em outros lugares no Windows.</span><span class="sxs-lookup"><span data-stu-id="848dd-135">Environment variables accessed from Windows PowerShell conform to the normal rules for environment variables elsewhere in Windows.</span></span>