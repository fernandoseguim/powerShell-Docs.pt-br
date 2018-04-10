---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Gerenciando o local atual
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: 8d529bf4a85553b95a9cab2739016859662486f2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="managing-current-location"></a><span data-ttu-id="6ad5e-103">Gerenciando o local atual</span><span class="sxs-lookup"><span data-stu-id="6ad5e-103">Managing Current Location</span></span>

<span data-ttu-id="6ad5e-104">Ao navegar em sistemas de pasta no Explorador de arquivos, você normalmente tem um local de trabalho específico, ou seja, a pasta aberta atual.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-104">When navigating folder systems in File Explorer, you usually have a specific working location - namely, the current open folder.</span></span> <span data-ttu-id="6ad5e-105">Itens na pasta atual podem ser manipulados facilmente clicando neles.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-105">Items in the current folder can be manipulated easily by clicking them.</span></span> <span data-ttu-id="6ad5e-106">Para interfaces de linha de comando como Cmd.exe, quando você estiver na mesma pasta que um arquivo específico, poderá acessá-lo especificando um nome relativamente curto, em vez de precisar especificar todo o caminho para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-106">For command-line interfaces such as Cmd.exe, when you are in the same folder as a particular file, you can access it by specifying a relatively short name, rather than needing to specify the entire path to the file.</span></span> <span data-ttu-id="6ad5e-107">O diretório atual é chamado no diretório de trabalho.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-107">The current directory is called the working directory.</span></span>

<span data-ttu-id="6ad5e-108">O Windows PowerShell usa o substantivo **Location** para referir-se ao diretório de trabalho e implementa uma família de cmdlets para examinar e manipular seu local.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-108">Windows PowerShell uses the noun **Location** to refer to the working directory, and implements a family of cmdlets to examine and manipulate your location.</span></span>

### <a name="getting-your-current-location-get-location"></a><span data-ttu-id="6ad5e-109">Obtendo seu local atual (Get-Location)</span><span class="sxs-lookup"><span data-stu-id="6ad5e-109">Getting Your Current Location (Get-Location)</span></span>

<span data-ttu-id="6ad5e-110">Para determinar o caminho do seu local de diretório atual, digite o comando **Get-Location**:</span><span class="sxs-lookup"><span data-stu-id="6ad5e-110">To determine the path of your current directory location, enter the **Get-Location** command:</span></span>

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="6ad5e-111">O cmdlet Get-Location é semelhante ao comando **pwd** no shell BASH.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-111">The Get-Location cmdlet is similar to the **pwd** command in the BASH shell.</span></span> <span data-ttu-id="6ad5e-112">O cmdlet Set-Location é semelhante ao comando **cd** do Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-112">The Set-Location cmdlet is similar to the **cd** command in Cmd.exe.</span></span>

### <a name="setting-your-current-location-set-location"></a><span data-ttu-id="6ad5e-113">Definindo seu local atual (Set-Location)</span><span class="sxs-lookup"><span data-stu-id="6ad5e-113">Setting Your Current Location (Set-Location)</span></span>

<span data-ttu-id="6ad5e-114">O comando **Get-Location** é usado com o comando **Set-Location**.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-114">The **Get-Location** command is used with the **Set-Location** command.</span></span> <span data-ttu-id="6ad5e-115">O comando **Set-Location** permite especificar seu local de diretório atual.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-115">The **Set-Location** command allows you to specify your current directory location.</span></span>

```powershell
Set-Location -Path C:\Windows
```

<span data-ttu-id="6ad5e-116">Depois de inserir o comando, você observará que não receberá nenhum feedback direto sobre o efeito do comando.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-116">After you enter the command, you will notice that you do not receive any direct feedback about the effect of the command.</span></span> <span data-ttu-id="6ad5e-117">A maioria dos comandos do Windows PowerShell que executam uma ação produzem pouca ou nenhuma saída porque a saída nem é sempre útil.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-117">Most Windows PowerShell commands that perform an action produce little or no output because the output is not always useful.</span></span> <span data-ttu-id="6ad5e-118">Para confirmar que uma alteração de diretório foi executada com êxito ao digitar o comando **Set-Location**, inclua o parâmetro **-PassThru** ao digitar o comando **Set-Location**:</span><span class="sxs-lookup"><span data-stu-id="6ad5e-118">To verify that a successful directory change has occurred when you enter the **Set-Location** command, include the **-PassThru** parameter when you enter the **Set-Location** command:</span></span>

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

<span data-ttu-id="6ad5e-119">O parâmetro **-PassThru** pode ser usado com muitos comandos Set no Windows PowerShell para retornar informações sobre o resultado em casos em que não há nenhuma saída padrão.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-119">The **-PassThru** parameter can be used with many Set commands in Windows PowerShell to return information about the result in cases in which there is no default output.</span></span>

<span data-ttu-id="6ad5e-120">Você pode especificar caminhos em relação ao seu local atual da mesma forma que faria na maioria dos shells de comando UNIX e Windows.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-120">You can specify paths relative to your current location in the same way as you would in most UNIX and Windows command shells.</span></span> <span data-ttu-id="6ad5e-121">Na notação padrão para caminhos relativos, um ponto (**.**) representa a pasta atual e um ponto duplo (**..**) representa o diretório pai do seu local atual.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-121">In standard notation for relative paths, a period (**.**)represents your current folder, and a doubled period (**..**) represents the parent directory of your current location.</span></span>

<span data-ttu-id="6ad5e-122">Por exemplo, se você está na pasta **C:\\Windows**, um ponto (**.**) representa **C:\\Windows** e um ponto duplo (**..**) representa **C:**.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-122">For example, if you are in the **C:\\Windows** folder, a period (**.**)represents **C:\\Windows** and double periods (**..**) represent **C:**.</span></span> <span data-ttu-id="6ad5e-123">Você pode alterar do seu local atual para a raiz da unidade C: digitando:</span><span class="sxs-lookup"><span data-stu-id="6ad5e-123">You can change from your current location to the root of the C: drive by typing:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

<span data-ttu-id="6ad5e-124">A mesma técnica funciona em unidades do Windows PowerShell que não são unidades de sistema de arquivos, como **HKLM:**.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-124">The same technique works on Windows PowerShell drives that are not file system drives, such as **HKLM:**.</span></span> <span data-ttu-id="6ad5e-125">Você pode definir o local na chave HKLM\\Software do Registro digitando:</span><span class="sxs-lookup"><span data-stu-id="6ad5e-125">You can set your location to the HKLM\\Software key in the registry by typing:</span></span>

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

<span data-ttu-id="6ad5e-126">Em seguida, você pode alterar o local do diretório para o diretório pai, que é a raiz da unidade HKLM: do Windows PowerShell, usando um caminho relativo:</span><span class="sxs-lookup"><span data-stu-id="6ad5e-126">You can then change the directory location to the parent directory, which is the root of the Windows PowerShell HKLM: drive, by using a relative path:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

<span data-ttu-id="6ad5e-127">Você pode digitar Set-Location ou usar qualquer um dos aliases internos do Windows PowerShell para Set-Location (cd, chdir, sl).</span><span class="sxs-lookup"><span data-stu-id="6ad5e-127">You can type Set-Location or use any of the built-in Windows PowerShell aliases for Set-Location (cd, chdir, sl).</span></span> <span data-ttu-id="6ad5e-128">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6ad5e-128">For example:</span></span>

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

### <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a><span data-ttu-id="6ad5e-129">Salvar e recuperar locais recentes (Push-Location e Pop-Location)</span><span class="sxs-lookup"><span data-stu-id="6ad5e-129">Saving and Recalling Recent Locations (Push-Location and Pop-Location)</span></span>

<span data-ttu-id="6ad5e-130">Ao alterar locais, é muito útil controlar onde você esteve para poder retornar ao local anterior.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-130">When changing locations, it is helpful to keep track of where you have been and to be able to return to your previous location.</span></span> <span data-ttu-id="6ad5e-131">O cmdlet do Windows PowerShell **Push-Location** cria um histórico ordenado (uma "pilha") de caminhos de diretório nos quais você esteve, para que seja possível percorrer novamente o histórico de caminhos de diretório usando o cmdlet complementar **Pop-Location**.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-131">The **Push-Location** cmdlet in Windows PowerShell creates a ordered history (a "stack") of directory paths where you have been, and you can step back through the history of directory paths by using the complementary **Pop-Location** cmdlet.</span></span>

<span data-ttu-id="6ad5e-132">Por exemplo, o Windows PowerShell inicia normalmente no diretório base do usuário.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-132">For example, Windows PowerShell typically starts in the user's home directory.</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="6ad5e-133">A palavra *pilha* tem um significado especial em muitas configurações de programação, incluindo o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-133">The word *stack* has a special meaning in many programming settings, including .NET Framework.</span></span> <span data-ttu-id="6ad5e-134">Como uma pilha física de itens, o último item que você coloca na pilha é o primeiro item que poderá obter dela.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-134">Like a physical stack of items, the last item you put onto the stack is the first item that you can pull off the stack.</span></span> <span data-ttu-id="6ad5e-135">Adicionar um item a uma pilha é geralmente conhecido como "enviar" o item para a pilha.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-135">Adding an item to a stack is colloquially known as "pushing" the item onto the stack.</span></span> <span data-ttu-id="6ad5e-136">Extrair um item na pilha coloquialmente é conhecido como "retirar" o item da pilha.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-136">Pulling an item off the stack is colloquially known as "popping" the item off the stack.</span></span>

<span data-ttu-id="6ad5e-137">Para enviar o local atual para a pilha e depois movê-lo para a pasta Configurações Locais, digite:</span><span class="sxs-lookup"><span data-stu-id="6ad5e-137">To push the current location onto the stack, and then move to the Local Settings folder, type:</span></span>

```powershell
Push-Location -Path "Local Settings"
```

<span data-ttu-id="6ad5e-138">Em seguida, você pode enviar o local de configurações para a pilha e movê-lo para a pasta Temp digitando:</span><span class="sxs-lookup"><span data-stu-id="6ad5e-138">You can then push the Local Settings location onto the stack and and move to the Temp folder by typing:</span></span>

```powershell
Push-Location -Path Temp
```

<span data-ttu-id="6ad5e-139">É possível confirmar a alteração dos diretórios digitando o comando **Get-Location**:</span><span class="sxs-lookup"><span data-stu-id="6ad5e-139">You can verify that you changed directories by entering the **Get-Location** command:</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

<span data-ttu-id="6ad5e-140">Você poderá então retornar para o último diretório visitado digitando o comando **Pop-Location** e verificar a mudança digitando o comando **Get-Location**:</span><span class="sxs-lookup"><span data-stu-id="6ad5e-140">You can then pop back into the most recently visited directory by entering the **Pop-Location** command, and verify the change by entering the **Get-Location** command:</span></span>

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

<span data-ttu-id="6ad5e-141">Assim como no cmdlet **Set-Location**, você pode incluir o parâmetro **-PassThru** ao inserir o cmdlet **Pop-Location** para exibir o diretório inserido:</span><span class="sxs-lookup"><span data-stu-id="6ad5e-141">Just as with the **Set-Location** cmdlet, you can include the **-PassThru** parameter when you enter the **Pop-Location** cmdlet to display the directory that you entered:</span></span>

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

<span data-ttu-id="6ad5e-142">Você também pode usar os cmdlets Location com caminhos de rede.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-142">You can also use the Location cmdlets with network paths.</span></span> <span data-ttu-id="6ad5e-143">Se você tiver um servidor denominado FS01 com um compartilhamento chamado Public, poderá alterar seu local digitando</span><span class="sxs-lookup"><span data-stu-id="6ad5e-143">If you have a server named FS01 with an share named Public, you can change your location by typing</span></span>

```powershell
Set-Location \\FS01\Public
```

<span data-ttu-id="6ad5e-144">ou</span><span class="sxs-lookup"><span data-stu-id="6ad5e-144">or</span></span>

```powershell
Push-Location \\FS01\Public
```

<span data-ttu-id="6ad5e-145">Você pode usar os comandos **Push-Location** e **Set-Location** para alterar o local de qualquer unidade disponível.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-145">You can use the **Push-Location** and **Set-Location** commands to change the location to any available drive.</span></span> <span data-ttu-id="6ad5e-146">Por exemplo, se você tiver uma unidade de CD-ROM local com a letra da unidade D contendo um CD de dados, será possível alterar o local da unidade de CD digitando o comando **Set-Location D:**.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-146">For example, if you have a local CD-ROM drive with drive letter D that contains a data CD, you can change the location to the CD drive by entering the **Set-Location D:** command.</span></span>

<span data-ttu-id="6ad5e-147">Se a unidade estiver vazia, você receberá a seguinte mensagem de erro:</span><span class="sxs-lookup"><span data-stu-id="6ad5e-147">If the drive is empty, you will get the following error message:</span></span>

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

<span data-ttu-id="6ad5e-148">Ao usar uma interface de linha de comando, não é conveniente usar o Explorador de Arquivos para examinar os discos físicos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-148">When you are using a command-line interface, it is not convenient to use File Explorer to examine the available physical drives.</span></span> <span data-ttu-id="6ad5e-149">Além disso, o Explorador de Arquivos não mostra todas as unidades do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-149">Also, File Explorer would not show you the all of the Windows PowerShell drives.</span></span> <span data-ttu-id="6ad5e-150">O Windows PowerShell oferece um conjunto de comandos para manipular as unidades do Windows PowerShell, o qual abordaremos em seguida.</span><span class="sxs-lookup"><span data-stu-id="6ad5e-150">Windows PowerShell provides a set of commands for manipulating Windows PowerShell drives, and we will talk about these next.</span></span>