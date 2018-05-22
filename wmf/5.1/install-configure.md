---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,instalação
contributor: keithb
title: Instalar e configurar o WMF 5.1
ms.openlocfilehash: e5c7968744a442b4be9f1e43a45e91429a6d6165
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="install-and-configure-wmf-51"></a><span data-ttu-id="80a4d-103">Como instalar e configurar o WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="80a4d-103">Install and Configure WMF 5.1</span></span> #


## <a name="download-and-install-the-wmf-51-package"></a><span data-ttu-id="80a4d-104">Como baixar e instalar o pacote do WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="80a4d-104">Download and install the WMF 5.1 package</span></span>

<span data-ttu-id="80a4d-105">Baixe o pacote do WMF 5.1 de acordo com o seu sistema operacional e a sua arquitetura:</span><span class="sxs-lookup"><span data-stu-id="80a4d-105">Download the WMF 5.1 package for the operating system and architecture you wish to install it on:</span></span>

| <span data-ttu-id="80a4d-106">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="80a4d-106">Operating System</span></span>       | <span data-ttu-id="80a4d-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="80a4d-107">Prerequisites</span></span>           | <span data-ttu-id="80a4d-108">Links de pacote</span><span class="sxs-lookup"><span data-stu-id="80a4d-108">Package Links</span></span>                          |
|------------------------|-------------------------|----------------------------------------|
| <span data-ttu-id="80a4d-109">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="80a4d-109">Windows Server 2012 R2</span></span> |                         | <span data-ttu-id="80a4d-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="80a4d-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span> |
| <span data-ttu-id="80a4d-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="80a4d-111">Windows Server 2012</span></span>    |                         | <span data-ttu-id="80a4d-112">[W2K12-KB3191565-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="80a4d-112">[W2K12-KB3191565-x64.msu][]</span></span>            |
| <span data-ttu-id="80a4d-113">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="80a4d-113">Windows Server 2008 R2</span></span> | <span data-ttu-id="80a4d-114">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="80a4d-114">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="80a4d-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="80a4d-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span>    |
| <span data-ttu-id="80a4d-116">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="80a4d-116">Windows 8.1</span></span>            |                         | <span data-ttu-id="80a4d-117">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="80a4d-117">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span></br><span data-ttu-id="80a4d-118">**x86:** [Win8.1-KB3191564-x86.msu][]</span><span class="sxs-lookup"><span data-stu-id="80a4d-118">**x86:** [Win8.1-KB3191564-x86.msu][]</span></span> |
| <span data-ttu-id="80a4d-119">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="80a4d-119">Windows 7 SP1</span></span>          | <span data-ttu-id="80a4d-120">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="80a4d-120">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="80a4d-121">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="80a4d-121">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span></br><span data-ttu-id="80a4d-122">**x86:** [Win7-KB3191566-x86.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="80a4d-122">**x86:** [Win7-KB3191566-x86.ZIP][]</span></span> |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="80a4d-129">Como instalar o WMF 5.1 para Windows Server 2008 R2 e Windows 7</span><span class="sxs-lookup"><span data-stu-id="80a4d-129">Install WMF 5.1 for Windows Server 2008 R2 and Windows 7</span></span>

> <span data-ttu-id="80a4d-130">**Observação:** as instruções de instalação do Windows Server 2008 R2 e do Windows 7 foram alteradas e diferem das instruções dos outros pacotes.</span><span class="sxs-lookup"><span data-stu-id="80a4d-130">**Note:** Installation instructions for Windows Server 2008 R2 and Windows 7 have changed, and differ from the instructions for the other packages.</span></span> <span data-ttu-id="80a4d-131">Veja a seguir as instruções de instalação do Windows Server 2012 R2, do Windows Server 2012 e do Windows 8.1.</span><span class="sxs-lookup"><span data-stu-id="80a4d-131">Installation instructions for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1 are below.</span></span>

<span data-ttu-id="80a4d-132">**Instalação do WMF 5.1 em Windows Server 2008 R2 e Windows 7**</span><span class="sxs-lookup"><span data-stu-id="80a4d-132">**Installing WMF 5.1 on Windows Server 2008 R2 and Windows 7**</span></span>

1. <span data-ttu-id="80a4d-133">Navegue até a pasta em que você baixou o arquivo ZIP.</span><span class="sxs-lookup"><span data-stu-id="80a4d-133">Navigate to the folder into which you downloaded the ZIP file.</span></span>

2. <span data-ttu-id="80a4d-134">Clique com botão direito no arquivo ZIP e selecione "Extrair tudo…".</span><span class="sxs-lookup"><span data-stu-id="80a4d-134">Right-click on the ZIP file, and select "Extract All...".</span></span> <span data-ttu-id="80a4d-135">O Zip contém 2 arquivos: um MSU e o script Install-WMF5.1.PS1.</span><span class="sxs-lookup"><span data-stu-id="80a4d-135">The Zip contains 2 files: an MSU and the Install-WMF5.1.PS1 script file.</span></span>
<span data-ttu-id="80a4d-136">Depois que você descompactar o arquivo ZIP, poderá copiar todo o conteúdo em qualquer computador que execute Windows 7 ou Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="80a4d-136">Once you have unpacked the ZIP file, you can copy the contents to any machine running Windows 7 or Windows Server 2008 R2.</span></span>

3. <span data-ttu-id="80a4d-137">Depois de extrair o conteúdo do arquivo ZIP, abra o PowerShell como administrador e navegue até a pasta que inclui esse conteúdo.</span><span class="sxs-lookup"><span data-stu-id="80a4d-137">After extracting the ZIP file contents, open PowerShell as administrator, then navigate to the folder containing the contents of the ZIP file.</span></span>

4. <span data-ttu-id="80a4d-138">Execute o script Install-Wmf5.1.ps1 nessa pasta e siga as instruções.</span><span class="sxs-lookup"><span data-stu-id="80a4d-138">Run the Install-Wmf5.1.ps1 script in that folder, and follow the instructions.</span></span> <span data-ttu-id="80a4d-139">Esse script verificará os pré-requisitos no computador local e, caso eles sejam atendidos, instalará o WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="80a4d-139">This script will check the prerequisites on the local machine, and install WMF 5.1 if the prerequisites have been met.</span></span> <span data-ttu-id="80a4d-140">Os pré-requisitos estão listados a seguir.</span><span class="sxs-lookup"><span data-stu-id="80a4d-140">The prerequisites are listed below.</span></span>

<span data-ttu-id="80a4d-141">O Install-WMF5.1.ps1 usa os seguintes parâmetros para facilitar a automação e a instalação no Windows Server 2008 R2 e no Windows 7:</span><span class="sxs-lookup"><span data-stu-id="80a4d-141">Install-WMF5.1.ps1 takes the following parameters to ease automating the installation on Windows Server 2008 R2 and Windows 7:</span></span>

- <span data-ttu-id="80a4d-142">AcceptEula: quando este parâmetro é incluído, o EULA é aceito automaticamente e, portanto, não é exibido.</span><span class="sxs-lookup"><span data-stu-id="80a4d-142">AcceptEula: When this parameter is included, the EULA is automatically accepted and will not be displayed.</span></span>
- <span data-ttu-id="80a4d-143">AllowRestart: este parâmetro só pode ser usado se o AcceptEula for especificado.</span><span class="sxs-lookup"><span data-stu-id="80a4d-143">AllowRestart: This parameter can only be used if AcceptEula is specified.</span></span> <span data-ttu-id="80a4d-144">Se esse parâmetro for incluído e for necessário reiniciar após a instalação do WMF 5.1, o reinício ocorrerá automaticamente após a conclusão da instalação.</span><span class="sxs-lookup"><span data-stu-id="80a4d-144">If this parameter is included, and a restart is required after installing WMF 5.1, the restart will happen without prompting immediately after the installation is completed.</span></span>

<span data-ttu-id="80a4d-145">**Pré-requisitos do WMF 5.1 para Windows Server 2008 R2 SP1 e Windows 7 SP1**</span><span class="sxs-lookup"><span data-stu-id="80a4d-145">**WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1**</span></span>

<span data-ttu-id="80a4d-146">Os pré-requisitos para instalação do WMF 5.1 no Windows Server 2008 R2 SP1 ou no Windows 7 SP1 são:</span><span class="sxs-lookup"><span data-stu-id="80a4d-146">Installation of WMF 5.1 on either Windows Server 2008 R2 SP1 or Windows 7 SP1, requires the following:</span></span>
- <span data-ttu-id="80a4d-147">O service pack mais recente deve estar instalado.</span><span class="sxs-lookup"><span data-stu-id="80a4d-147">Latest service pack must be installed.</span></span>
- <span data-ttu-id="80a4d-148">O WMF 3.0 **não deve** estar instalado.</span><span class="sxs-lookup"><span data-stu-id="80a4d-148">WMF 3.0 **must not** be installed.</span></span> <span data-ttu-id="80a4d-149">Se você instalar o WMF 5.1 no lugar do WMF 3.0, ocorrerá a perda do PSModulePath, o que pode causar falhas em outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="80a4d-149">Installing WMF 5.1 over WMF 3.0 will result in the loss of the PSModulePath, which can cause other applications to fail.</span></span> <span data-ttu-id="80a4d-150">Antes de instalar o WMF 5.1, você deve desinstalar o WMF 3.0 ou salvar o PSModulePath e, depois, restaurá-lo manualmente após a conclusão da instalação do WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="80a4d-150">Before installing WMF 5.1, you must either un-install WMF 3.0, or save the PSModulePath and then restore it manually after WMF 5.1 installation is complete.</span></span>
- <span data-ttu-id="80a4d-151">O WMF 5.1 exige pelo menos [do .NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).</span><span class="sxs-lookup"><span data-stu-id="80a4d-151">WMF 5.1 requires at least [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).</span></span>
<span data-ttu-id="80a4d-152">Você pode instalar o Microsoft .NET Framework 4.5.2, seguindo as instruções no local fazer o download.</span><span class="sxs-lookup"><span data-stu-id="80a4d-152">You can install Microsoft .NET Framework 4.5.2 by following the instructions at the download location.</span></span>

<span data-ttu-id="80a4d-153">**Dependência do WinRM**</span><span class="sxs-lookup"><span data-stu-id="80a4d-153">**WinRM Dependency**</span></span>

<span data-ttu-id="80a4d-154">O DSC (Desired State Configuration) do Windows PowerShell depende do WinRM.</span><span class="sxs-lookup"><span data-stu-id="80a4d-154">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span>
<span data-ttu-id="80a4d-155">O WinRM não é habilitado por padrão no Windows Server 2008 R2 nem no Windows 7.</span><span class="sxs-lookup"><span data-stu-id="80a4d-155">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span>
<span data-ttu-id="80a4d-156">Execute o `Set-WSManQuickConfig`, em uma sessão com privilégios elevados do Windows PowerShell para habilitar o WinRM.</span><span class="sxs-lookup"><span data-stu-id="80a4d-156">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>


## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a><span data-ttu-id="80a4d-157">Como instalar o WMF 5.1 em Windows Server 2012 R2, Windows Server 2012 e Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="80a4d-157">Install WMF 5.1 for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1</span></span>
<span data-ttu-id="80a4d-158">**Como instalar usando o Windows Explorer (ou Explorador de Arquivos no Windows Server 2012 R2 ou no Windows 8.1)**</span><span class="sxs-lookup"><span data-stu-id="80a4d-158">**Install from Windows Explorer (or File Explorer in Windows Server 2012 R2 or Windows 8.1)**</span></span>

1. <span data-ttu-id="80a4d-159">Navegue até a pasta em que você baixou o arquivo MSU.</span><span class="sxs-lookup"><span data-stu-id="80a4d-159">Navigate to the folder into which you downloaded the MSU file.</span></span>
2. <span data-ttu-id="80a4d-160">Clique duas vezes no MSU para executá-lo.</span><span class="sxs-lookup"><span data-stu-id="80a4d-160">Double-click the MSU to run it.</span></span>

<span data-ttu-id="80a4d-161">**Como instalar usando o Prompt de Comando**</span><span class="sxs-lookup"><span data-stu-id="80a4d-161">**Installing from the Command Prompt**</span></span>

1. <span data-ttu-id="80a4d-162">Após baixar o pacote correto de acordo com a arquitetura do seu computador, abra uma janela do Prompt de Comando com direitos de usuário elevados (Executar como Administrador).</span><span class="sxs-lookup"><span data-stu-id="80a4d-162">After downloading the correct package for your computer's architecture, open a Command Prompt window with elevated user rights (Run as Administrator).</span></span> <span data-ttu-id="80a4d-163">Nas opções de instalação Server Core do Windows Server 2012 R2, do Windows Server 2012 ou do Windows Server 2008 R2 SP1 o Prompt de Comando é aberto por padrão com direitos de usuário elevados.</span><span class="sxs-lookup"><span data-stu-id="80a4d-163">On the Server Core installation options of Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1, Command Prompt opens with elevated user rights by default.</span></span>
2. <span data-ttu-id="80a4d-164">Altere os diretórios para a pasta em que você baixou ou copiou o pacote de instalação do WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="80a4d-164">Change directories to the folder into which you have downloaded or copied the WMF 5.1 installation package.</span></span>
3. <span data-ttu-id="80a4d-165">Execute um dos seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="80a4d-165">Run one of the following commands:</span></span>
   - <span data-ttu-id="80a4d-166">Em computadores com Windows Server 2012 R2 ou Windows 8.1 x64, execute o `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="80a4d-166">On computers that are running Windows Server 2012 R2 or Windows 8.1 x64, run `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="80a4d-167">Em computadores com Windows Server 2012, execute o `W2K12-KB3191565-x64.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="80a4d-167">On computers that are running Windows Server 2012, run `W2K12-KB3191565-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="80a4d-168">Em computadores com Windows 8.1 x86, execute o `Win8.1-KB3191564-x86.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="80a4d-168">On computers that are running Windows 8.1 x86, run `Win8.1-KB3191564-x86.msu /quiet`.</span></span>

> [!NOTE]
> <span data-ttu-id="80a4d-169">A instalação do WMF 5.1 exige uma reinicialização.</span><span class="sxs-lookup"><span data-stu-id="80a4d-169">Installing WMF 5.1 requires a reboot.</span></span> <span data-ttu-id="80a4d-170">O uso da opção `/quiet` reiniciará o sistema sem aviso.</span><span class="sxs-lookup"><span data-stu-id="80a4d-170">Using the `/quiet` option will reboot the system without warning.</span></span>
> <span data-ttu-id="80a4d-171">Use o opção `/norestart` para evitar a reinicialização.</span><span class="sxs-lookup"><span data-stu-id="80a4d-171">Use the `/norestart` option to avoid rebooting.</span></span> <span data-ttu-id="80a4d-172">No entanto, o WMF 5.1 será instalado apenas após a reinicialização.</span><span class="sxs-lookup"><span data-stu-id="80a4d-172">However, WMF 5.1 will not be installed until you have rebooted.</span></span>
