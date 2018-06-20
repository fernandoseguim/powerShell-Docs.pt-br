---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Instalar o SDK do Windows PowerShell
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: 830b054c2cf2b49d935d3d96b79effa7131f6db2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953558"
---
# <a name="installing-the-windows-powershell-sdk"></a><span data-ttu-id="e4b36-103">Instalar o SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4b36-103">Installing the Windows PowerShell SDK</span></span>

<span data-ttu-id="e4b36-104">O tópico a seguir descreve como instalar o SDK do PowerShell em diferentes versões do Windows.</span><span class="sxs-lookup"><span data-stu-id="e4b36-104">The following topic describes how to install the PowerShell SDK on different versions of Windows.</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a><span data-ttu-id="e4b36-105">Instalando o SDK do Windows PowerShell 3.0 para Windows 8 e Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="e4b36-105">Installing Windows PowerShell 3.0 SDK for Windows 8 and Windows Server 2012</span></span>

<span data-ttu-id="e4b36-106">O Windows PowerShell 3.0 é instalado automaticamente com o Windows 8 e Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="e4b36-106">Windows PowerShell 3.0 is automatically installed with Windows 8 and Windows Server 2012.</span></span>
<span data-ttu-id="e4b36-107">Além disso, você pode baixar e instalar os assemblies de referência para o Windows PowerShell 3.0 como parte do SDK do Windows 8.</span><span class="sxs-lookup"><span data-stu-id="e4b36-107">In addition, you can download and install the reference assemblies for Windows PowerShell 3.0 as part of the Windows 8 SDK.</span></span>
<span data-ttu-id="e4b36-108">Esses assemblies permitem que você grave cmdlets, provedores e programas de host no Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="e4b36-108">These assemblies allow you to write cmdlets, providers, and host programs for Windows PowerShell 3.0.</span></span>
<span data-ttu-id="e4b36-109">Quando você instala o SDK do Windows para o Windows 8, os assemblies do Windows PowerShell são instalados automaticamente na pasta do assembly de referência, em \Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0.</span><span class="sxs-lookup"><span data-stu-id="e4b36-109">When you install the Windows SDK for Windows 8, the Windows PowerShell assemblies are automatically installed in the reference assembly folder, in \Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0.</span></span>
<span data-ttu-id="e4b36-110">Para obter mais informações, visite o [site de download do SDK do Windows 8](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4b36-110">For more information, see the [Windows 8 SDK download site](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).</span></span>
<span data-ttu-id="e4b36-111">Exemplos de código do Windows PowerShell também estão disponíveis no Centro de Desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="e4b36-111">Windows PowerShell code samples are also available on the Development Center.</span></span>
<span data-ttu-id="e4b36-112">Para obter mais informações, confira a página de exemplo de código de Área de Trabalho no [site do Centro de desenvolvimento](http://code.msdn.microsoft.com/windowsdesktop/).</span><span class="sxs-lookup"><span data-stu-id="e4b36-112">For more information, see the Desktop code sample page on the [Dev center site](http://code.msdn.microsoft.com/windowsdesktop/).</span></span>

<span data-ttu-id="e4b36-113">Além disso, o Windows PowerShell 3.0 é compatível com versões anteriores com o SDK do Windows PowerShell 2.0, que inclui diversos exemplos de código.</span><span class="sxs-lookup"><span data-stu-id="e4b36-113">In addition, Windows PowerShell 3.0 is backwards-compatible with the Windows PowerShell 2.0 SDK, which includes a number of code samples.</span></span>
<span data-ttu-id="e4b36-114">Para obter mais informações sobre como baixar o SDK do Windows PowerShell 2.0, consulte abaixo.</span><span class="sxs-lookup"><span data-stu-id="e4b36-114">For more information on how to download the Windows PowerShell 2.0 SDK, see below.</span></span>
<span data-ttu-id="e4b36-115">(Observe que, enquanto os exemplos de 2.0 código são compatíveis com o Windows 8 e Windows PowerShell 3.0, você não pode instalar o Windows PowerShell 2.0 em uma plataforma Windows 8).</span><span class="sxs-lookup"><span data-stu-id="e4b36-115">(Note that while the 2.0 code samples are compatible with Windows 8 and Windows PowerShell 3.0, you cannot install Windows PowerShell 2.0 on a Windows 8 platform.)</span></span>

##<a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a><span data-ttu-id="e4b36-116">Instalando o SDK do Windows PowerShell 3.0 no Windows 7 e Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="e4b36-116">Installing Windows PowerShell 3.0 SDK for Windows 7 and Windows Server 2008 R2</span></span>

<span data-ttu-id="e4b36-117">O Windows 7 e o Windows Server 2008 R2 têm o PowerShell 2.0 instalado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e4b36-117">Windows 7 and Windows Server 2008 R2 automatically have PowerShell 2.0 installed.</span></span>
<span data-ttu-id="e4b36-118">Além disso, você pode instalar o PowerShell 3.0 nesses sistemas.</span><span class="sxs-lookup"><span data-stu-id="e4b36-118">In addition, you can install PowerShell 3.0 on these systems.</span></span>
<span data-ttu-id="e4b36-119">(Para obter mais informações, veja [Installing Windows PowerShell](Installing-Windows-PowerShell.md) [Instalando o Windows PowerShell]).</span><span class="sxs-lookup"><span data-stu-id="e4b36-119">(For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).).</span></span>
<span data-ttu-id="e4b36-120">Conforme descrito acima, você também pode instalar o SDK do Windows 8 no Windows 7 e Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="e4b36-120">As described above, you can also install the Windows 8 SDK on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a><span data-ttu-id="e4b36-121">Instalando o SDK do Windows PowerShell 2.0 para Windows 7, Vista, XP, Server 2003 e Server 2008</span><span class="sxs-lookup"><span data-stu-id="e4b36-121">Installing Windows PowerShell 2.0 SDK for Windows 7, Vista, XP, Server 2003, and Server 2008</span></span>

<span data-ttu-id="e4b36-122">O SDK do Windows PowerShell 2.0 fornece os assemblies de referência necessários para gravar cmdlets, provedores e aplicativos de hospedagem, além de fornecer o código de exemplo em C# que poderá ser usado como ponto de partida quando você começar a gravar código.</span><span class="sxs-lookup"><span data-stu-id="e4b36-122">The Windows PowerShell 2.0 SDK provides the reference assemblies needed to write cmdlets, providers, and hosting applications, and it provides C# sample code that can be used as the starting point when you begin writing code.</span></span>

<span data-ttu-id="e4b36-123">Para instalar esse SDK, veja [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611) (SDK do Windows PowerShell 2.0).</span><span class="sxs-lookup"><span data-stu-id="e4b36-123">To install this SDK, see [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611).</span></span>

## <a name="reference-assemblies"></a><span data-ttu-id="e4b36-124">Assemblies de referência</span><span class="sxs-lookup"><span data-stu-id="e4b36-124">Reference assemblies</span></span>

<span data-ttu-id="e4b36-125">Assemblies de referência são instalados, por padrão, no seguinte local: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span><span class="sxs-lookup"><span data-stu-id="e4b36-125">Reference assemblies are installed in the following location by default: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span></span>

> <span data-ttu-id="e4b36-126">**Observação**: o código que é compilado nos assemblies do Windows PowerShell 2.0 não pode ser carregado em instalações do Windows PowerShell 1.0.</span><span class="sxs-lookup"><span data-stu-id="e4b36-126">**Note**: Code that is compiled against the Windows PowerShell 2.0 assemblies cannot be loaded into Windows PowerShell 1.0 installations.</span></span>
><span data-ttu-id="e4b36-127">No entanto, o código que é compilado em relação aos assemblies do Windows PowerShell 1.0 pode ser carregado em instalações do Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="e4b36-127">However, code that is compiled against the Windows PowerShell 1.0 assemblies can be loaded into Windows PowerShell 2.0 installations.</span></span>

## <a name="samples"></a><span data-ttu-id="e4b36-128">Amostras</span><span class="sxs-lookup"><span data-stu-id="e4b36-128">Samples</span></span>

<span data-ttu-id="e4b36-129">Exemplos de código são instalados, por padrão, no seguinte local: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="e4b36-129">Code samples are installed in the following location by default: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span></span>

<span data-ttu-id="e4b36-130">As seções a seguir fornecem uma breve descrição da ação de cada amostra.</span><span class="sxs-lookup"><span data-stu-id="e4b36-130">The following sections provide a brief description of what each sample does.</span></span>

## <a name="cmdlet-samples"></a><span data-ttu-id="e4b36-131">Amostras de cmdlet</span><span class="sxs-lookup"><span data-stu-id="e4b36-131">Cmdlet samples</span></span>
<span data-ttu-id="e4b36-132">**GetProcessSample01**</span><span class="sxs-lookup"><span data-stu-id="e4b36-132">**GetProcessSample01**</span></span>

<span data-ttu-id="e4b36-133">Mostra como gravar um cmdlet simples que coloca todos os processos no computador local.</span><span class="sxs-lookup"><span data-stu-id="e4b36-133">Shows how to write a simple cmdlet that gets all the processes on the local computer.</span></span>

<span data-ttu-id="e4b36-134">**GetProcessSample02**</span><span class="sxs-lookup"><span data-stu-id="e4b36-134">**GetProcessSample02**</span></span>

<span data-ttu-id="e4b36-135">Mostra como adicionar parâmetros ao cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e4b36-135">Shows how to add parameters to the cmdlet.</span></span>
<span data-ttu-id="e4b36-136">O cmdlet usa um ou mais nomes de processo e retorna os processos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="e4b36-136">The cmdlet takes one or more process names and returns the matching processes.</span></span>

<span data-ttu-id="e4b36-137">**GetProcessSample03**</span><span class="sxs-lookup"><span data-stu-id="e4b36-137">**GetProcessSample03**</span></span>

<span data-ttu-id="e4b36-138">Mostra como adicionar parâmetros que aceitam a entrada do pipeline.</span><span class="sxs-lookup"><span data-stu-id="e4b36-138">Shows how to add parameters that accept input from the pipeline.</span></span>

<span data-ttu-id="e4b36-139">**GetProcessSample04**</span><span class="sxs-lookup"><span data-stu-id="e4b36-139">**GetProcessSample04**</span></span>

<span data-ttu-id="e4b36-140">Mostra como tratar erros de não encerramento.</span><span class="sxs-lookup"><span data-stu-id="e4b36-140">Shows how to handle nonterminating errors.</span></span>

<span data-ttu-id="e4b36-141">**GetProcessSample05**</span><span class="sxs-lookup"><span data-stu-id="e4b36-141">**GetProcessSample05**</span></span>

<span data-ttu-id="e4b36-142">Mostra como exibir uma lista de processos especificados.</span><span class="sxs-lookup"><span data-stu-id="e4b36-142">Shows how to display a list of specified processes.</span></span>

<span data-ttu-id="e4b36-143">**SelectObject**</span><span class="sxs-lookup"><span data-stu-id="e4b36-143">**SelectObject**</span></span>

<span data-ttu-id="e4b36-144">Mostra como gravar um filtro para selecionar apenas determinados objetos.</span><span class="sxs-lookup"><span data-stu-id="e4b36-144">Shows how to write a filter to select only certain objects.</span></span>

<span data-ttu-id="e4b36-145">**SelectString**</span><span class="sxs-lookup"><span data-stu-id="e4b36-145">**SelectString**</span></span>

<span data-ttu-id="e4b36-146">Mostra como pesquisar padrões especificados em arquivos.</span><span class="sxs-lookup"><span data-stu-id="e4b36-146">Shows how to search files for specified patterns.</span></span>

<span data-ttu-id="e4b36-147">**StopProcessSample01**</span><span class="sxs-lookup"><span data-stu-id="e4b36-147">**StopProcessSample01**</span></span>

<span data-ttu-id="e4b36-148">Mostra como implementar um parâmetro *PassThru* e como solicitar comentários do usuário por chamadas para os métodos [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) e [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4b36-148">Shows how to implement a *PassThru* parameter, and how to request user feedback by calls to the [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) and [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx) methods.</span></span>
<span data-ttu-id="e4b36-149">Os usuários especificam o parâmetro *PassThru* quando querem forçar o cmdlet a retornar um objeto de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e4b36-149">Users specify the *PassThru* parameter when they want to force the cmdlet to return an object,</span></span>

<span data-ttu-id="e4b36-150">**StopProcessSample02**</span><span class="sxs-lookup"><span data-stu-id="e4b36-150">**StopProcessSample02**</span></span>

<span data-ttu-id="e4b36-151">Mostra como interromper um processo específico.</span><span class="sxs-lookup"><span data-stu-id="e4b36-151">Shows how to stop a specific process.</span></span>

<span data-ttu-id="e4b36-152">**StopProcessSample03**</span><span class="sxs-lookup"><span data-stu-id="e4b36-152">**StopProcessSample03**</span></span>

<span data-ttu-id="e4b36-153">Mostra como declarar aliases para parâmetros e como dar suporte a curingas.</span><span class="sxs-lookup"><span data-stu-id="e4b36-153">Shows how to declare aliases for parameters and how to support wildcards.</span></span>

<span data-ttu-id="e4b36-154">**StopProcessSample04**</span><span class="sxs-lookup"><span data-stu-id="e4b36-154">**StopProcessSample04**</span></span>

<span data-ttu-id="e4b36-155">Mostra como declarar conjuntos de parâmetros, o objeto que o cmdlet usa como entrada, e como especificar o parâmetro padrão definido a ser usado.</span><span class="sxs-lookup"><span data-stu-id="e4b36-155">Shows how to declare parameter sets, the object that the cmdlet takes as input, and how to specify the default parameter set to use.</span></span>

## <a name="remoting-samples"></a><span data-ttu-id="e4b36-156">Amostras de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="e4b36-156">Remoting samples</span></span>

<span data-ttu-id="e4b36-157">**RemoteRunspace01**</span><span class="sxs-lookup"><span data-stu-id="e4b36-157">**RemoteRunspace01**</span></span>

<span data-ttu-id="e4b36-158">Mostra como criar um runspace remoto que é usado para estabelecer uma conexão remota.</span><span class="sxs-lookup"><span data-stu-id="e4b36-158">Shows how to create a remote runspace that is used to establish a remote connection.</span></span>

<span data-ttu-id="e4b36-159">**RemoteRunspacePool01**</span><span class="sxs-lookup"><span data-stu-id="e4b36-159">**RemoteRunspacePool01**</span></span>

<span data-ttu-id="e4b36-160">Mostra como construir um pool de runspaces remotos e como executar vários comandos simultaneamente usando esse pool.</span><span class="sxs-lookup"><span data-stu-id="e4b36-160">Shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

<span data-ttu-id="e4b36-161">**Serialization01**</span><span class="sxs-lookup"><span data-stu-id="e4b36-161">**Serialization01**</span></span>

<span data-ttu-id="e4b36-162">Mostra como examinar uma classe existente do .NET e garantir que as informações das propriedades públicas selecionadas dessa classe são preservadas na serialização/desserialização.</span><span class="sxs-lookup"><span data-stu-id="e4b36-162">Shows how to look at an existing .NET class and make sure that information from selected public properties of this class is preserved across serialization/deserialization.</span></span>

<span data-ttu-id="e4b36-163">**Serialization02**</span><span class="sxs-lookup"><span data-stu-id="e4b36-163">**Serialization02**</span></span>

<span data-ttu-id="e4b36-164">Mostra como examinar uma classe existente do .NET e garantir que as informações da instância dessa classe são preservadas na serialização/desserialização quando as informações não estão disponíveis nas propriedades públicas da classe.</span><span class="sxs-lookup"><span data-stu-id="e4b36-164">Shows how to look at an existing .NET class and make sure that information from instance of this class is preserved across serialization/deserialization when the information is not available in public properties of the class.</span></span>

<span data-ttu-id="e4b36-165">**Serialization03**</span><span class="sxs-lookup"><span data-stu-id="e4b36-165">**Serialization03**</span></span>

<span data-ttu-id="e4b36-166">Mostra como examinar uma classe existente do .NET e garantir que as instâncias dessa classe e de classes derivadas são desserializadas (reidratadas) em objetos dinâmicos do .NET.</span><span class="sxs-lookup"><span data-stu-id="e4b36-166">Shows how to look at an existing .NET class and make sure that instances of this class and of derived classes are deserialized (rehydrated) into live .NET objects.</span></span>

## <a name="event-samples"></a><span data-ttu-id="e4b36-167">Amostras de eventos</span><span class="sxs-lookup"><span data-stu-id="e4b36-167">Event samples</span></span>

<span data-ttu-id="e4b36-168">**Event01**</span><span class="sxs-lookup"><span data-stu-id="e4b36-168">**Event01**</span></span>

<span data-ttu-id="e4b36-169">Mostra como criar um cmdlet de registro de eventos, fazendo a derivação de ObjectEventRegistrationBase.</span><span class="sxs-lookup"><span data-stu-id="e4b36-169">Shows how to create a cmdlet for event registration by deriving from ObjectEventRegistrationBase.</span></span>

<span data-ttu-id="e4b36-170">**Event02**</span><span class="sxs-lookup"><span data-stu-id="e4b36-170">**Event02**</span></span>

<span data-ttu-id="e4b36-171">Mostra como receber notificações de eventos do Windows PowerShell gerados em computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="e4b36-171">Shows how to shows how to receive notifications of Windows PowerShell events that are generated on remote computers.</span></span>
<span data-ttu-id="e4b36-172">Usa o evento PSEventReceived exposto por meio da classe [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4b36-172">It uses the PSEventReceived event exposed through the [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx) class.</span></span>

## <a name="hosting-application-samples"></a><span data-ttu-id="e4b36-173">Amostras de aplicativos de hospedagem</span><span class="sxs-lookup"><span data-stu-id="e4b36-173">Hosting application samples</span></span>

<span data-ttu-id="e4b36-174">**Runspace01**</span><span class="sxs-lookup"><span data-stu-id="e4b36-174">**Runspace01**</span></span>

<span data-ttu-id="e4b36-175">Mostra como usar a classe [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) para executar o cmdlet [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="e4b36-175">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet synchronously.</span></span>
<span data-ttu-id="e4b36-176">O cmdlet [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) retorna os objetos [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) de cada processo em execução no computador local.</span><span class="sxs-lookup"><span data-stu-id="e4b36-176">The [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer.</span></span>

<span data-ttu-id="e4b36-177">**Runspace02**</span><span class="sxs-lookup"><span data-stu-id="e4b36-177">**Runspace02**</span></span>

<span data-ttu-id="e4b36-178">Mostra como usar a classe [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) para executar os cmdlets [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) e [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="e4b36-178">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) and [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) cmdlets synchronously.</span></span>
<span data-ttu-id="e4b36-179">O cmdlet [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) retorna os objetos [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) de cada processo em execução no computador local e Sort-Object classifica os objetos com base em sua propriedade [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4b36-179">The [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer, and the Sort-Object sorts the objects based on their [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) property.</span></span>
<span data-ttu-id="e4b36-180">Os resultados desses comandos são exibidos com o uso de um controle [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4b36-180">The results of these commands is displayed by using a [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) control.</span></span>

<span data-ttu-id="e4b36-181">**Runspace03**</span><span class="sxs-lookup"><span data-stu-id="e4b36-181">**Runspace03**</span></span>

<span data-ttu-id="e4b36-182">Mostra como usar a classe [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) para executar um script de forma síncrona e como tratar erros de não encerramento.</span><span class="sxs-lookup"><span data-stu-id="e4b36-182">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run a script synchronously, and how to handle non-terminating errors.</span></span>
<span data-ttu-id="e4b36-183">O script recebe uma lista de nomes de processo e, em seguida, recupera tais processos.</span><span class="sxs-lookup"><span data-stu-id="e4b36-183">The script receives a list of process names and then retrieves those processes.</span></span>
<span data-ttu-id="e4b36-184">Os resultados do script, incluindo quaisquer erros de não encerramento gerados durante a execução do script, são exibidos em uma janela do console.</span><span class="sxs-lookup"><span data-stu-id="e4b36-184">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

<span data-ttu-id="e4b36-185">**Runspace04**</span><span class="sxs-lookup"><span data-stu-id="e4b36-185">**Runspace04**</span></span>

<span data-ttu-id="e4b36-186">Mostra como usar a classe [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) para executar comandos e como capturar erros de encerramento gerados durante a execução de comandos.</span><span class="sxs-lookup"><span data-stu-id="e4b36-186">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span>
<span data-ttu-id="e4b36-187">Dois comandos são executados e o último comando é passado um argumento de parâmetro que não é válido.</span><span class="sxs-lookup"><span data-stu-id="e4b36-187">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span>
<span data-ttu-id="e4b36-188">Como resultado, nenhum objeto é retornado e um erro de encerramento é gerado.</span><span class="sxs-lookup"><span data-stu-id="e4b36-188">As a result, no objects are returned and a terminating error is thrown.</span></span>

<span data-ttu-id="e4b36-189">**Runspace05**</span><span class="sxs-lookup"><span data-stu-id="e4b36-189">**Runspace05**</span></span>

<span data-ttu-id="e4b36-190">Mostra como adicionar um snap-in a um objeto [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) para que o cmdlet do snap-in esteja disponível quando o runspace for aberto.</span><span class="sxs-lookup"><span data-stu-id="e4b36-190">Shows how to add a snap-in to an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span>
<span data-ttu-id="e4b36-191">O snap-in fornece um cmdlet Get-Proc (definido pela [Amostra GetProcessSample01](https://technet.microsoft.com/library/ff602028.aspx)) que é executado de forma síncrona usando um objeto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4b36-191">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](https://technet.microsoft.com/library/ff602028.aspx)) that is run synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="e4b36-192">**Runspace06**</span><span class="sxs-lookup"><span data-stu-id="e4b36-192">**Runspace06**</span></span>

<span data-ttu-id="e4b36-193">Mostra como adicionar um módulo a um objeto [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) para que o módulo seja carregado quando o runspace for aberto.</span><span class="sxs-lookup"><span data-stu-id="e4b36-193">Shows how to add a module to an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object so that the module is loaded when the runspace is opened.</span></span>
<span data-ttu-id="e4b36-194">O módulo fornece um cmdlet Get-Proc (definido pelo [GetProcessSample02 exemplo](https://technet.microsoft.com/library/ff602027.aspx)) executado de forma síncrona com o uso de um objeto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4b36-194">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](https://technet.microsoft.com/library/ff602027.aspx)) that is run synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="e4b36-195">**Runspace07**</span><span class="sxs-lookup"><span data-stu-id="e4b36-195">**Runspace07**</span></span>

<span data-ttu-id="e4b36-196">Mostra como criar um runspace e usá-lo para executar dois cmdlets de forma síncrona usando um objeto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4b36-196">Shows how to create a runspace, and then use that runspace to run two cmdlets synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="e4b36-197">**Runspace08**</span><span class="sxs-lookup"><span data-stu-id="e4b36-197">**Runspace08**</span></span>

<span data-ttu-id="e4b36-198">Mostra como adicionar comandos e argumentos ao pipeline de um objeto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) e como executar os comandos de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="e4b36-198">Shows how to add commands and arguments to the pipeline of a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object and how to run the commands synchronously.</span></span>

<span data-ttu-id="e4b36-199">**Runspace09**</span><span class="sxs-lookup"><span data-stu-id="e4b36-199">**Runspace09**</span></span>

<span data-ttu-id="e4b36-200">Mostra como adicionar um script ao pipeline de um objeto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) e como executar o script de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="e4b36-200">Shows how to add a script to the pipeline of a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object and how to run the script asynchronously.</span></span>
<span data-ttu-id="e4b36-201">Eventos são usados para tratar a saída do script.</span><span class="sxs-lookup"><span data-stu-id="e4b36-201">Events are used to handle the output of the script.</span></span>

<span data-ttu-id="e4b36-202">**Runspace10**</span><span class="sxs-lookup"><span data-stu-id="e4b36-202">**Runspace10**</span></span>

<span data-ttu-id="e4b36-203">Mostra como criar um estado de sessão inicial padrão, como adicionar um cmdlet ao [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), como criar um runspace que usa o estado de sessão inicial e como executar o comando usando um objeto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4b36-203">Shows how to create a default initial session state, how to add a cmdlet to the [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), how to create a runspace that uses the initial session state, and how to run the command by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="e4b36-204">**Runspace11**</span><span class="sxs-lookup"><span data-stu-id="e4b36-204">**Runspace11**</span></span>

<span data-ttu-id="e4b36-205">Mostra como usar a classe [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) para criar um comando proxy que chama um cmdlet existente, mas restringe o conjunto de parâmetros disponíveis.</span><span class="sxs-lookup"><span data-stu-id="e4b36-205">Shows how to use the [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span>
<span data-ttu-id="e4b36-206">O comando de proxy é adicionado a um estado de sessão inicial que é usado para criar um espaço de execução restrito.</span><span class="sxs-lookup"><span data-stu-id="e4b36-206">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span>
<span data-ttu-id="e4b36-207">Isso significa que o usuário pode acessar a funcionalidade do cmdlet apenas por meio do comando proxy.</span><span class="sxs-lookup"><span data-stu-id="e4b36-207">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

<span data-ttu-id="e4b36-208">**PowerShell01**</span><span class="sxs-lookup"><span data-stu-id="e4b36-208">**PowerShell01**</span></span>

<span data-ttu-id="e4b36-209">Mostra como criar um runspace restrito usando um objeto [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4b36-209">Shows how to create a constrained runspace using an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object.</span></span>

<span data-ttu-id="e4b36-210">**PowerShell02**</span><span class="sxs-lookup"><span data-stu-id="e4b36-210">**PowerShell02**</span></span>

<span data-ttu-id="e4b36-211">Mostra como usar um pool de runspaces para executar vários comandos simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="e4b36-211">Shows how to use a runspace pool to run multiple commands concurrently.</span></span>

## <a name="host-samples"></a><span data-ttu-id="e4b36-212">Amostras de host</span><span class="sxs-lookup"><span data-stu-id="e4b36-212">Host samples</span></span>

<span data-ttu-id="e4b36-213">**Host01**</span><span class="sxs-lookup"><span data-stu-id="e4b36-213">**Host01**</span></span>

<span data-ttu-id="e4b36-214">Mostra como implementar um aplicativo host que usa um host personalizado.</span><span class="sxs-lookup"><span data-stu-id="e4b36-214">Shows how to implement a host application that uses a custom host.</span></span>
<span data-ttu-id="e4b36-215">Nesta amostra, é criado um runspace que usa o host personalizado e, em seguida, a API [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) é usada para executar um script que chama a “saída”.</span><span class="sxs-lookup"><span data-stu-id="e4b36-215">In this sample a runspace is created that uses the custom host, and then the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) API is used to run a script that calls "exit".</span></span>
<span data-ttu-id="e4b36-216">O aplicativo host analisa a saída do script e imprime os resultados.</span><span class="sxs-lookup"><span data-stu-id="e4b36-216">The host application then looks at the output of the script and prints out the results.</span></span>

<span data-ttu-id="e4b36-217">**Host02**</span><span class="sxs-lookup"><span data-stu-id="e4b36-217">**Host02**</span></span>

<span data-ttu-id="e4b36-218">Mostra como gravar um aplicativo host que usa o tempo de execução do Windows PowerShell, juntamente com uma implementação de host personalizado.</span><span class="sxs-lookup"><span data-stu-id="e4b36-218">Shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span>
<span data-ttu-id="e4b36-219">O aplicativo host define a cultura do host para alemão, executa o cmdlet [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324), exibe os resultados como seriam vistos com pwrsh.exe e imprime a data e hora atuais em alemão.</span><span class="sxs-lookup"><span data-stu-id="e4b36-219">The host application sets the host culture to German, runs the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet and displays the results as you would see them by using pwrsh.exe, and then prints out the current data and time in German.</span></span>

<span data-ttu-id="e4b36-220">**Host03**</span><span class="sxs-lookup"><span data-stu-id="e4b36-220">**Host03**</span></span>

<span data-ttu-id="e4b36-221">Mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e exibe os resultados para o console.</span><span class="sxs-lookup"><span data-stu-id="e4b36-221">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

<span data-ttu-id="e4b36-222">**Host04**</span><span class="sxs-lookup"><span data-stu-id="e4b36-222">**Host04**</span></span>

<span data-ttu-id="e4b36-223">Mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e exibe os resultados para o console.</span><span class="sxs-lookup"><span data-stu-id="e4b36-223">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="e4b36-224">Esse aplicativo host também dá suporte a exibições de avisos que permitem ao usuário especificar várias opções.</span><span class="sxs-lookup"><span data-stu-id="e4b36-224">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

<span data-ttu-id="e4b36-225">**Host05**</span><span class="sxs-lookup"><span data-stu-id="e4b36-225">**Host05**</span></span>

<span data-ttu-id="e4b36-226">Mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e exibe os resultados para o console.</span><span class="sxs-lookup"><span data-stu-id="e4b36-226">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="e4b36-227">Este aplicativo host também dá suporte a chamadas para computadores remotos com os cmdlets [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) e [Exit-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212).</span><span class="sxs-lookup"><span data-stu-id="e4b36-227">This host application also supports calls to remote computers by using the [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) and [Exit-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212) cmdlets.</span></span>

<span data-ttu-id="e4b36-228">**Host06**</span><span class="sxs-lookup"><span data-stu-id="e4b36-228">**Host06**</span></span>

<span data-ttu-id="e4b36-229">Mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e exibe os resultados para o console.</span><span class="sxs-lookup"><span data-stu-id="e4b36-229">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="e4b36-230">Além disso, este exemplo usa as APIs do Criador de Token para especificar a cor do texto inserido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="e4b36-230">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="provider-samples"></a><span data-ttu-id="e4b36-231">Amostras de provedor</span><span class="sxs-lookup"><span data-stu-id="e4b36-231">Provider samples</span></span>

<span data-ttu-id="e4b36-232">**AccessDBProviderSample01**</span><span class="sxs-lookup"><span data-stu-id="e4b36-232">**AccessDBProviderSample01**</span></span>

<span data-ttu-id="e4b36-233">Mostra como declarar uma classe de provedor que deriva diretamente da classe [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4b36-233">Shows how to declare a provider class that derives directly from the [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx) class.</span></span>
<span data-ttu-id="e4b36-234">Ele é incluído aqui apenas para fins de integridade.</span><span class="sxs-lookup"><span data-stu-id="e4b36-234">It is included here only for completeness.</span></span>

<span data-ttu-id="e4b36-235">**AccessDBProviderSample02**</span><span class="sxs-lookup"><span data-stu-id="e4b36-235">**AccessDBProviderSample02**</span></span>

<span data-ttu-id="e4b36-236">Mostra como substituir os métodos [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) e [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) para dar suporte a chamadas para os cmdlets New-PSDrive e Remove-PSDrive.</span><span class="sxs-lookup"><span data-stu-id="e4b36-236">Shows how to overwrite the [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) and [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) methods to support calls to the New-PSDrive and Remove-PSDrive cmdlets.</span></span>
<span data-ttu-id="e4b36-237">A classe de provedor nessa amostra deriva da classe [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4b36-237">The provider class in this sample derives from the [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx) class.</span></span>

<span data-ttu-id="e4b36-238">**AccessDBProviderSample03**</span><span class="sxs-lookup"><span data-stu-id="e4b36-238">**AccessDBProviderSample03**</span></span>

<span data-ttu-id="e4b36-239">Mostra como substituir os métodos [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) e [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) para dar suporte a chamadas para os cmdlets Get-Item e Set-Item.</span><span class="sxs-lookup"><span data-stu-id="e4b36-239">Shows how to overwrite the [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) and [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) methods to support calls to the Get-Item and Set-Item cmdlets.</span></span>
<span data-ttu-id="e4b36-240">A classe de provedor nessa amostra deriva da classe [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4b36-240">The provider class in this sample derives from the [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="e4b36-241">**AccessDBProviderSample04**</span><span class="sxs-lookup"><span data-stu-id="e4b36-241">**AccessDBProviderSample04**</span></span>

<span data-ttu-id="e4b36-242">Mostra como substituir os métodos de contêiner para dar suporte a chamadas para os cmdlets Copy-Item, Get-ChildItem, New-Item e Remove-Item.</span><span class="sxs-lookup"><span data-stu-id="e4b36-242">Shows how to overwrite container methods to support calls to the Copy-Item, Get-ChildItem, New-Item, and Remove-Item cmdlets.</span></span>
<span data-ttu-id="e4b36-243">Esses métodos devem ser implementados quando o armazenamento de dados contiver itens que são contêineres.</span><span class="sxs-lookup"><span data-stu-id="e4b36-243">These methods should be implemented when the data store contains items that are containers.</span></span>
<span data-ttu-id="e4b36-244">Um contêiner é um grupo de itens filho em um item pai comum.</span><span class="sxs-lookup"><span data-stu-id="e4b36-244">A container is a group of child items under a common parent item.</span></span>
<span data-ttu-id="e4b36-245">A classe de provedor nessa amostra deriva da classe [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4b36-245">The provider class in this sample derives from the [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="e4b36-246">**AccessDBProviderSample05**</span><span class="sxs-lookup"><span data-stu-id="e4b36-246">**AccessDBProviderSample05**</span></span>

<span data-ttu-id="e4b36-247">Mostra como substituir os métodos de contêiner para dar suporte a chamadas para os cmdlets Move-Item e Join-Path.</span><span class="sxs-lookup"><span data-stu-id="e4b36-247">Shows how to overwrite container methods to support calls to the Move-Item and Join-Path cmdlets.</span></span>
<span data-ttu-id="e4b36-248">Esses métodos deverão ser implementados quando o usuário precisar mover itens dentro de um contêiner e se o armazenamento de dados contiver contêineres aninhados.</span><span class="sxs-lookup"><span data-stu-id="e4b36-248">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span>
<span data-ttu-id="e4b36-249">A classe de provedor nessa amostra deriva da classe [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4b36-249">The provider class in this sample derives from the [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="e4b36-250">**AccessDBProviderSample06**</span><span class="sxs-lookup"><span data-stu-id="e4b36-250">**AccessDBProviderSample06**</span></span>

<span data-ttu-id="e4b36-251">Mostra como substituir os métodos de conteúdo para dar suporte a chamadas para os cmdlets Clear-Content, Get-Content e Set-Content.</span><span class="sxs-lookup"><span data-stu-id="e4b36-251">Shows how to overwrite content methods to support calls to the Clear-Content, Get-Content, and Set-Content cmdlets.</span></span>
<span data-ttu-id="e4b36-252">Esses métodos devem ser implementados quando o usuário precisa gerenciar o conteúdo dos itens no armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="e4b36-252">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span>
<span data-ttu-id="e4b36-253">A classe de provedor nessa amostra deriva da classe [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) e implementa a interface [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4b36-253">The provider class in this sample derives from the [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) class, and it implements the [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx) interface.</span></span>