---
ms.date: 2017-08-09
keywords: powershell, cmdlet, baixar, instalar, configurar, windows 10, windows 8.1, windows 8.0, windows 7
title: Instalar o Windows PowerShell
ms.openlocfilehash: ec8f09087a5c5f2e7ea6237faa01ea3f447ad1f3
ms.sourcegitcommit: 755d7bc0740573d73613cedcf79981ca3dc81c5e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="installing-windows-powershell"></a><span data-ttu-id="3176d-103">Instalar o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3176d-103">Installing Windows PowerShell</span></span>

<span data-ttu-id="3176d-104">O PowerShell vem instalado por padrão em todos os Windows, começando com o Windows 7 SP1 e Windows Server 2008 R2 SP1.</span><span class="sxs-lookup"><span data-stu-id="3176d-104">PowerShell comes installed by default in every Windows, starting with Windows 7 SP1 and Windows Server 2008 R2 SP1.</span></span>

<span data-ttu-id="3176d-105">Os usuários do Windows, Linux e macOS que gostariam de instalar **PowerShell 6** (beta), em seus computadores, precisam:</span><span class="sxs-lookup"><span data-stu-id="3176d-105">Linux, macOS, and Windows users that would like to install **PowerShell 6** (beta), in their machines, need to:</span></span>

1. <span data-ttu-id="3176d-106">Obter o PowerShell para o sistema operacional e a versão específicos, por meio do [GitHub](https://github.com/powershell/powershell#get-powershell)</span><span class="sxs-lookup"><span data-stu-id="3176d-106">Get PowerShell for the specific OS and version, from [GitHub](https://github.com/powershell/powershell#get-powershell)</span></span>
1. <span data-ttu-id="3176d-107">Siga as instruções de instalação</span><span class="sxs-lookup"><span data-stu-id="3176d-107">Follow the installation instructions</span></span>
  - [<span data-ttu-id="3176d-108">Linux</span><span class="sxs-lookup"><span data-stu-id="3176d-108">Linux</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md)
  - [<span data-ttu-id="3176d-109">macOS</span><span class="sxs-lookup"><span data-stu-id="3176d-109">macOS</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/macos.md)
  - [<span data-ttu-id="3176d-110">Windows</span><span class="sxs-lookup"><span data-stu-id="3176d-110">Windows</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi)

<span data-ttu-id="3176d-111">O PowerShell 6 também está disponível para o Docker; consulte as instruções [Instalação do Docker](https://github.com/PowerShell/PowerShell/tree/master/docker).</span><span class="sxs-lookup"><span data-stu-id="3176d-111">PowerShell 6 is also available for Docker; see [Docker installation](https://github.com/PowerShell/PowerShell/tree/master/docker) instructions.</span></span>

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a><span data-ttu-id="3176d-112">Localizando o PowerShell no Windows 7, 8.0, 8.1 e 10</span><span class="sxs-lookup"><span data-stu-id="3176d-112">Finding PowerShell in Windows 10, 8.1, 8.0, and 7</span></span>

<span data-ttu-id="3176d-113">Às vezes, localizar o console do PowerShell ou o ISE (Ambiente de Script Integrado) no Windows pode ser difícil, já que sua localização muda de uma versão do Windows para a outra.</span><span class="sxs-lookup"><span data-stu-id="3176d-113">Sometimes locating PowerShell console or ISE (Integrated Scripting Environment) in Windows can be difficult, as it's location moves from one version of Windows to the next.</span></span>

<span data-ttu-id="3176d-114">As tabelas a seguir devem ajudar você a localizar PowerShell na sua versão do Windows.</span><span class="sxs-lookup"><span data-stu-id="3176d-114">The following tables should help you find PowerShell in your Windows version.</span></span>
<span data-ttu-id="3176d-115">Todas as versões listadas aqui são a versão original, conforme lançada, sem atualizações.</span><span class="sxs-lookup"><span data-stu-id="3176d-115">All versions listed here are the original version, as released, with no updates.</span></span>

### <a name="for-console"></a><span data-ttu-id="3176d-116">Para o Console</span><span class="sxs-lookup"><span data-stu-id="3176d-116">For Console</span></span>

<span data-ttu-id="3176d-117">Versão</span><span class="sxs-lookup"><span data-stu-id="3176d-117">Version</span></span> | <span data-ttu-id="3176d-118">Local</span><span class="sxs-lookup"><span data-stu-id="3176d-118">Location</span></span>
-- | --
<span data-ttu-id="3176d-119">Windows 10</span><span class="sxs-lookup"><span data-stu-id="3176d-119">Windows 10</span></span> | <span data-ttu-id="3176d-120">Clique no ícone do Windows no canto inferior esquerdo e comece digitando PowerShell</span><span class="sxs-lookup"><span data-stu-id="3176d-120">Click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="3176d-121">Windows 8.1, 8.0</span><span class="sxs-lookup"><span data-stu-id="3176d-121">Windows 8.1, 8.0</span></span> | <span data-ttu-id="3176d-122">Na tela inicial, comece a digitar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3176d-122">On the start screen, start typing PowerShell.</span></span><br/><span data-ttu-id="3176d-123">Se estiver na área de trabalho, clique no ícone do Windows canto inferior esquerdo, comece digitando PowerShell</span><span class="sxs-lookup"><span data-stu-id="3176d-123">If on desktop, click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="3176d-124">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="3176d-124">Windows 7 SP1</span></span> | <span data-ttu-id="3176d-125">Clique no ícone do Windows no canto inferior esquerdo e, na caixa de pesquisa, comece digitando PowerShell</span><span class="sxs-lookup"><span data-stu-id="3176d-125">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

### <a name="for-ise"></a><span data-ttu-id="3176d-126">Para o ISE</span><span class="sxs-lookup"><span data-stu-id="3176d-126">For ISE</span></span>

<span data-ttu-id="3176d-127">Versão</span><span class="sxs-lookup"><span data-stu-id="3176d-127">Version</span></span> | <span data-ttu-id="3176d-128">Local</span><span class="sxs-lookup"><span data-stu-id="3176d-128">Location</span></span>
-- | --
<span data-ttu-id="3176d-129">Windows 10</span><span class="sxs-lookup"><span data-stu-id="3176d-129">Windows 10</span></span> | <span data-ttu-id="3176d-130">Clique no ícone do Windows no canto inferior esquerdo e comece digitando ISE</span><span class="sxs-lookup"><span data-stu-id="3176d-130">Click left lower corner Windows icon, start typing ISE</span></span>
<span data-ttu-id="3176d-131">Windows 8.1, 8.0</span><span class="sxs-lookup"><span data-stu-id="3176d-131">Windows 8.1, 8.0</span></span> | <span data-ttu-id="3176d-132">Na tela inicial, clique em **ISE do PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="3176d-132">On the start screen, type **PowerShell ISE**.</span></span><br/><span data-ttu-id="3176d-133">Se estiver na área de trabalho, clique no ícone do Windows canto inferior esquerdo, comece digitando **ISE do PowerShell**</span><span class="sxs-lookup"><span data-stu-id="3176d-133">If on desktop, click left lower corner Windows icon, type **PowerShell ISE**</span></span>
<span data-ttu-id="3176d-134">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="3176d-134">Windows 7 SP1</span></span> | <span data-ttu-id="3176d-135">Clique no ícone do Windows no canto inferior esquerdo e, na caixa de pesquisa, comece digitando PowerShell</span><span class="sxs-lookup"><span data-stu-id="3176d-135">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

## <a name="finding-powershell-in-windows-server-versions"></a><span data-ttu-id="3176d-136">Localizando o PowerShell em versões do Windows Server</span><span class="sxs-lookup"><span data-stu-id="3176d-136">Finding PowerShell in Windows Server versions</span></span>

<span data-ttu-id="3176d-137">Começando com o Windows Server 2008 R2, o sistema operacional Windows pode ser instalado sem a interface gráfica do usuário (GUI).</span><span class="sxs-lookup"><span data-stu-id="3176d-137">Starting with Windows Server 2008 R2, Windows operating system can be installed without the graphical user interface (GUI).</span></span>
<span data-ttu-id="3176d-138">Edições do Windows Server sem a GUI são nomeadas **Core** e edições com a GUI são nomeadas **Desktop**.</span><span class="sxs-lookup"><span data-stu-id="3176d-138">Editions of Windows Server without GUI are named **Core** editions, and editions with the GUI are named **Desktop**.</span></span>

### <a name="windows-server-core-editions"></a><span data-ttu-id="3176d-139">Edições do Windows Server Core</span><span class="sxs-lookup"><span data-stu-id="3176d-139">Windows Server Core editions</span></span>

<span data-ttu-id="3176d-140">Em todas as edições Core, ao fazer logon no servidor, você obtém uma janela de prompt de comando do Windows.</span><span class="sxs-lookup"><span data-stu-id="3176d-140">In all Core editions, when you log to the server you get a Windows command prompt window.</span></span>

<span data-ttu-id="3176d-141">Digite `powershell` e pressione **ENTER** para iniciar o PowerShell na sessão de prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="3176d-141">Type `powershell` and press **ENTER** to start PowerShell inside the command prompt session.</span></span> <span data-ttu-id="3176d-142">Digite `exit` para encerrar a sessão do PowerShell e retornar ao prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="3176d-142">Type `exit` to terminate the PowerShell session and return to command prompt.</span></span>

### <a name="windows-server-desktop-editions"></a><span data-ttu-id="3176d-143">Edições do Windows Server Desktop</span><span class="sxs-lookup"><span data-stu-id="3176d-143">Windows Server Desktop editions</span></span>

<span data-ttu-id="3176d-144">Em todas as edições de área de trabalho, clique no ícone do Windows canto inferior esquerdo, comece digitando PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3176d-144">In all desktop editions, click the left lower corner Windows icon, start typing PowerShell.</span></span>
<span data-ttu-id="3176d-145">Você obtém as opções de ISE e de console.</span><span class="sxs-lookup"><span data-stu-id="3176d-145">You get both console and ISE options.</span></span>

<span data-ttu-id="3176d-146">A única exceção à regra acima é o ISE do Windows Server 2008 R2 SP1; nesse caso, clique no ícone do Windows canto inferior esquerdo, digite ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3176d-146">The only exception to the above rule is the ISE in Windows Server 2008 R2 SP1; in this case, click the left lower corner Windows icon, type PowerShell ISE.</span></span>

## <a name="how-to-check-the-version-of-powershell"></a><span data-ttu-id="3176d-147">Como verificar a versão do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3176d-147">How to check the version of PowerShell</span></span>

<span data-ttu-id="3176d-148">Para descobrir qual versão do PowerShell você instalou, inicie o console do Windows PowerShell (ou o ISE), digite `$PSVersionTable` e pressione **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="3176d-148">To find which version of PowerShell you have installed, start a PowerShell console (or the ISE) and type `$PSVersionTable` and press **ENTER**.</span></span>

## <a name="upgrading-existing-windows-powershell"></a><span data-ttu-id="3176d-149">Atualizando um Windows PowerShell existente</span><span class="sxs-lookup"><span data-stu-id="3176d-149">Upgrading existing Windows PowerShell</span></span>

<span data-ttu-id="3176d-150">O pacote de instalação para o PowerShell vem dentro de um instalador WMF.</span><span class="sxs-lookup"><span data-stu-id="3176d-150">The installation package for PowerShell comes inside a WMF installer.</span></span>
<span data-ttu-id="3176d-151">A versão do instalador WMF corresponde à versão do PowerShell; Não há nenhum instalador autônomo para o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3176d-151">The version of the WMF installer matches the version of PowerShell; there's no stand alone installer for Windows PowerShell.</span></span>

<span data-ttu-id="3176d-152">Se você precisa atualizar a versão existente do PowerShell, no Windows, use a tabela a seguir para localizar o instalador para a versão do PowerShell para a qual você deseja atualizar.</span><span class="sxs-lookup"><span data-stu-id="3176d-152">If you need to update your existing version of PowerShell, in Windows, use the following table to locate the installer for the version of PowerShell you want to update to.</span></span>

<span data-ttu-id="3176d-153">Windows</span><span class="sxs-lookup"><span data-stu-id="3176d-153">Windows</span></span> | <span data-ttu-id="3176d-154">PS 3.0</span><span class="sxs-lookup"><span data-stu-id="3176d-154">PS 3.0</span></span> | <span data-ttu-id="3176d-155">PS 4.0</span><span class="sxs-lookup"><span data-stu-id="3176d-155">PS 4.0</span></span> | <span data-ttu-id="3176d-156">PS 5.0</span><span class="sxs-lookup"><span data-stu-id="3176d-156">PS 5.0</span></span> | <span data-ttu-id="3176d-157">PS 5.1</span><span class="sxs-lookup"><span data-stu-id="3176d-157">PS 5.1</span></span> |
--|--|--|--|--|
<span data-ttu-id="3176d-158">Windows 10 (consulte a Observação 1)</span><span class="sxs-lookup"><span data-stu-id="3176d-158">Windows 10 (see Note1)</span></span><br/><span data-ttu-id="3176d-159">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="3176d-159">Windows Server 2016</span></span> | - | - | - | <span data-ttu-id="3176d-160">instalado</span><span class="sxs-lookup"><span data-stu-id="3176d-160">installed</span></span>
<span data-ttu-id="3176d-161">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="3176d-161">Windows 8.1</span></span><br/><span data-ttu-id="3176d-162">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="3176d-162">Windows Server 2012 R2</span></span> | - | <span data-ttu-id="3176d-163">instalado</span><span class="sxs-lookup"><span data-stu-id="3176d-163">installed</span></span> | [<span data-ttu-id="3176d-164">Windows Management Framework 5.0</span><span class="sxs-lookup"><span data-stu-id="3176d-164">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="3176d-165">Windows Management Framework 5.1</span><span class="sxs-lookup"><span data-stu-id="3176d-165">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="3176d-166">Windows 8</span><span class="sxs-lookup"><span data-stu-id="3176d-166">Windows 8</span></span><br/><span data-ttu-id="3176d-167">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="3176d-167">Windows Server 2012</span></span> | <span data-ttu-id="3176d-168">instalado</span><span class="sxs-lookup"><span data-stu-id="3176d-168">installed</span></span> | [<span data-ttu-id="3176d-169">Windows Management Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="3176d-169">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="3176d-170">Windows Management Framework 5.0</span><span class="sxs-lookup"><span data-stu-id="3176d-170">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="3176d-171">Windows Management Framework 5.1</span><span class="sxs-lookup"><span data-stu-id="3176d-171">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="3176d-172">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="3176d-172">Windows 7 SP1</span></span><br/><span data-ttu-id="3176d-173">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="3176d-173">Windows Server 2008 R2 SP1</span></span> | [<span data-ttu-id="3176d-174">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="3176d-174">WMF 3.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [<span data-ttu-id="3176d-175">Windows Management Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="3176d-175">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="3176d-176">Windows Management Framework 5.0</span><span class="sxs-lookup"><span data-stu-id="3176d-176">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="3176d-177">Windows Management Framework 5.1</span><span class="sxs-lookup"><span data-stu-id="3176d-177">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> <span data-ttu-id="3176d-178">**Observação 1**:</span><span class="sxs-lookup"><span data-stu-id="3176d-178">**Note 1**:</span></span>
  >>
  >> <span data-ttu-id="3176d-179">Na versão inicial do Windows 10, com as atualizações automáticas ativadas, o PowerShell é atualizado da versão 5.0 para a 5.1.</span><span class="sxs-lookup"><span data-stu-id="3176d-179">On the initial release of Windows 10, with automatic updates enabled, PowerShell gets updated from version 5.0 to 5.1.</span></span>
  >>
  >> <span data-ttu-id="3176d-180">Se a versão original do Windows 10 não for atualizada por meio de atualizações do Windows, a versão do PowerShell será a 5.0.</span><span class="sxs-lookup"><span data-stu-id="3176d-180">If the original version of Windows 10 is not updated through Windows Updates, the version of PowerShell is 5.0.</span></span>

## <a name="need-azure-powershell"></a><span data-ttu-id="3176d-181">O Azure PowerShell é necessário</span><span class="sxs-lookup"><span data-stu-id="3176d-181">Need Azure PowerShell</span></span>

<span data-ttu-id="3176d-182">Se você estiver procurando o **Azure PowerShell**, você poderá começar com a [Visão geral do Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure).</span><span class="sxs-lookup"><span data-stu-id="3176d-182">If you're looking for **Azure PowerShell**, you could start with [Overview of Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure).</span></span>

<span data-ttu-id="3176d-183">Caso contrário, talvez seja necessário [instalar e configurar o Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)</span><span class="sxs-lookup"><span data-stu-id="3176d-183">Otherwise, what you might need is [Install and configure Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)</span></span>

## <a name="see-also"></a><span data-ttu-id="3176d-184">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="3176d-184">See Also</span></span>

- [<span data-ttu-id="3176d-185">Requisitos do Sistema do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3176d-185">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)
- [<span data-ttu-id="3176d-186">Iniciando o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3176d-186">Starting Windows PowerShell</span></span>](Starting-Windows-PowerShell.md)
