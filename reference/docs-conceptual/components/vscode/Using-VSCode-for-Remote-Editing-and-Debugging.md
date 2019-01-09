---
title: Usando o Visual Studio Code para edição e depuração remotas
description: Usando o Visual Studio Code para edição e depuração remotas
ms.date: 08/06/2018
ms.openlocfilehash: bab1a629a7e9dafd5957cf93025abb18b8a4f326
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655567"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="aae74-103">Usando o Visual Studio Code para edição e depuração remotas</span><span class="sxs-lookup"><span data-stu-id="aae74-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="aae74-104">Para aqueles que estão familiarizados com o ISE, você deve se lembrar de que você pode executar `psedit file.ps1` do console integrado para abrir os arquivos - locais ou remotos - com o botão direito no ISE.</span><span class="sxs-lookup"><span data-stu-id="aae74-104">For those of you that were familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="aae74-105">Na verdade, esse recurso também está disponível na extensão do PowerShell para VSCode.</span><span class="sxs-lookup"><span data-stu-id="aae74-105">As it turns out, this feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="aae74-106">Este guia mostrará como fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="aae74-106">This guide will show you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="aae74-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="aae74-107">Prerequisites</span></span>

<span data-ttu-id="aae74-108">Este guia pressupõe que você tenha:</span><span class="sxs-lookup"><span data-stu-id="aae74-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="aae74-109">um recurso remoto (ex: uma VM, um contêiner) que você tenha acesso a</span><span class="sxs-lookup"><span data-stu-id="aae74-109">a remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="aae74-110">PowerShell em execução nele e o computador host</span><span class="sxs-lookup"><span data-stu-id="aae74-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="aae74-111">VSCode e a extensão do PowerShell para VSCode</span><span class="sxs-lookup"><span data-stu-id="aae74-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="aae74-112">Esse recurso funciona no Windows PowerShell e o PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="aae74-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="aae74-113">Esse recurso também funciona ao se conectar a um computador remoto via WinRM, PowerShell Direct ou SSH.</span><span class="sxs-lookup"><span data-stu-id="aae74-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="aae74-114">Se você quiser usar o SSH, mas estiver usando o Windows, confira a [versão Win32 do SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span><span class="sxs-lookup"><span data-stu-id="aae74-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

## <a name="lets-go"></a><span data-ttu-id="aae74-115">Vamos lá</span><span class="sxs-lookup"><span data-stu-id="aae74-115">Let's go</span></span>

<span data-ttu-id="aae74-116">Nesta seção, percorrerei remoto edição e depuração de meu MacBook Pro, para uma VM do Ubuntu em execução no Azure.</span><span class="sxs-lookup"><span data-stu-id="aae74-116">In this section, I'll walk through remote editing and debugging from my MacBook Pro, to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="aae74-117">Eu talvez não estejam usando o Windows, mas **o processo é idêntico**.</span><span class="sxs-lookup"><span data-stu-id="aae74-117">I might not be using Windows, but **the process is identical**.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="aae74-118">Edição com o Open EditorFile de arquivo local</span><span class="sxs-lookup"><span data-stu-id="aae74-118">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="aae74-119">Com a extensão do PowerShell para VSCode é iniciado e o Console integrado do PowerShell aberta, também podemos digitar `Open-EditorFile foo.ps1` ou `psedit foo.ps1` para abrir o arquivo de foo.ps1 local diretamente no editor.</span><span class="sxs-lookup"><span data-stu-id="aae74-119">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Abrir EditorFile foo.ps1 funciona localmente](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> <span data-ttu-id="aae74-121">foo.ps1 já deve existir.</span><span class="sxs-lookup"><span data-stu-id="aae74-121">foo.ps1 must already exist.</span></span>

<span data-ttu-id="aae74-122">A partir daí, podemos:</span><span class="sxs-lookup"><span data-stu-id="aae74-122">From there, we can:</span></span>

<span data-ttu-id="aae74-123">Adicionar pontos de interrupção a medianiz ![adicionando o ponto de interrupção para da medianiz](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span><span class="sxs-lookup"><span data-stu-id="aae74-123">add breakpoints to the gutter ![adding breakpoint to gutter](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span></span>

<span data-ttu-id="aae74-124">e pressione F5 para depurar o script do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aae74-124">and hit F5 to debug the PowerShell script.</span></span>
<span data-ttu-id="aae74-125">![o script do PowerShell local de depuração](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span><span class="sxs-lookup"><span data-stu-id="aae74-125">![debugging the PowerShell local script](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span></span>

<span data-ttu-id="aae74-126">Durante a depuração, você pode interagir com o console de depuração, confira as variáveis no escopo à esquerda, e todos os outro padrão as ferramentas de depuração.</span><span class="sxs-lookup"><span data-stu-id="aae74-126">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="aae74-127">Edição com o Open EditorFile de arquivo remoto</span><span class="sxs-lookup"><span data-stu-id="aae74-127">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="aae74-128">Agora, vejamos arquivo remoto, edição e depuração.</span><span class="sxs-lookup"><span data-stu-id="aae74-128">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="aae74-129">As etapas são praticamente as mesmas, há apenas uma coisa que precisamos fazer primeiro – insira nossa sessão do PowerShell para o servidor remoto.</span><span class="sxs-lookup"><span data-stu-id="aae74-129">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="aae74-130">Há um cmdlet para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="aae74-130">There's a cmdlet for to do so.</span></span> <span data-ttu-id="aae74-131">Ele é chamado `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="aae74-131">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="aae74-132">A explicação menos potente e para baixo do cmdlet é:</span><span class="sxs-lookup"><span data-stu-id="aae74-132">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="aae74-133">`Enter-PSSession -ComputerName foo` inicia uma sessão por meio do WinRM</span><span class="sxs-lookup"><span data-stu-id="aae74-133">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="aae74-134">`Enter-PSSession -ContainerId foo` e `Enter-PSSession -VmId foo` iniciar uma sessão por meio do PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="aae74-134">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="aae74-135">`Enter-PSSession -HostName foo` inicia uma sessão por meio do SSH</span><span class="sxs-lookup"><span data-stu-id="aae74-135">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="aae74-136">Para obter mais informações sobre `Enter-PSSession`, confira os documentos [aqui](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="aae74-136">For more info on `Enter-PSSession`, check out the docs [here](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span></span>

<span data-ttu-id="aae74-137">Usarei SSH para a comunicação remota, pois vou do macOS para uma VM do Ubuntu no Azure.</span><span class="sxs-lookup"><span data-stu-id="aae74-137">I'll be using SSH for remoting since I'm going from macOS to an Ubuntu VM in Azure.</span></span>

<span data-ttu-id="aae74-138">Primeiro, no Console integrado, vamos executar nosso Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="aae74-138">First, in the Integrated Console, let's run our Enter-PSSession.</span></span> <span data-ttu-id="aae74-139">Você saberá que você está na sessão porque `[something]` serão exibidos à esquerda do prompt de.</span><span class="sxs-lookup"><span data-stu-id="aae74-139">You'll know that you're in the session because `[something]` will show up to the left of your prompt.</span></span>

![A chamada para Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

<span data-ttu-id="aae74-141">A partir daí, podemos fazer as etapas exatas como se podemos estava editando um script local.</span><span class="sxs-lookup"><span data-stu-id="aae74-141">From there, we can do the exact steps as if we were editing a local script.</span></span>

1. <span data-ttu-id="aae74-142">Execute `Open-EditorFile test.ps1` ou `psedit test.ps1` para abrir o controle remoto `test.ps1` arquivo ![EditorFile com a abrir o arquivo ps1](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span><span class="sxs-lookup"><span data-stu-id="aae74-142">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file ![Open-EditorFile the test.ps1 file](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span></span>
2. <span data-ttu-id="aae74-143">Editar os arquivo/definir pontos de interrupção</span><span class="sxs-lookup"><span data-stu-id="aae74-143">Edit the file/set breakpoints</span></span> ![Editar e defina pontos de interrupção](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. <span data-ttu-id="aae74-145">Iniciar a depuração (F5) o arquivo remoto</span><span class="sxs-lookup"><span data-stu-id="aae74-145">Start debugging (F5) the remote file</span></span>

![depurando o arquivo remoto](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

<span data-ttu-id="aae74-147">Isso é tudo para ele!</span><span class="sxs-lookup"><span data-stu-id="aae74-147">That's all there's to it!</span></span> <span data-ttu-id="aae74-148">Esperamos que este guia ajudou a esclarecer os alguma dúvida sobre a depuração remota e edição do PowerShell no VSCode.</span><span class="sxs-lookup"><span data-stu-id="aae74-148">We hope that this guide helped clear up any questions about remote debugging and editing PowerShell in VSCode.</span></span>

<span data-ttu-id="aae74-149">Se você tiver problemas, fique à vontade para problemas em aberto [no repositório GitHub](http://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="aae74-149">If you have any problems, feel free to open issues [on the GitHub repo](http://github.com/powershell/vscode-powershell).</span></span>
