---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Instalar o SDK do Windows PowerShell
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: fa876bac0c1afac24f93d11dd2e7ecfb1165cf5f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893531"
---
# <a name="installing-the-windows-powershell-sdk"></a><span data-ttu-id="30c35-103">Instalar o SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="30c35-103">Installing the Windows PowerShell SDK</span></span>

<span data-ttu-id="30c35-104">O tópico a seguir descreve como instalar o SDK do PowerShell em diferentes versões do Windows.</span><span class="sxs-lookup"><span data-stu-id="30c35-104">The following topic describes how to install the PowerShell SDK on different versions of Windows.</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a><span data-ttu-id="30c35-105">Instalando o SDK do Windows PowerShell 3.0 para Windows 8 e Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="30c35-105">Installing Windows PowerShell 3.0 SDK for Windows 8 and Windows Server 2012</span></span>

<span data-ttu-id="30c35-106">O Windows PowerShell 3.0 é instalado automaticamente com o Windows 8 e Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="30c35-106">Windows PowerShell 3.0 is automatically installed with Windows 8 and Windows Server 2012.</span></span>
<span data-ttu-id="30c35-107">Além disso, você pode baixar e instalar os assemblies de referência para o Windows PowerShell 3.0 como parte do SDK do Windows 8.</span><span class="sxs-lookup"><span data-stu-id="30c35-107">In addition, you can download and install the reference assemblies for Windows PowerShell 3.0 as part of the Windows 8 SDK.</span></span>
<span data-ttu-id="30c35-108">Esses assemblies permitem que você grave cmdlets, provedores e programas de host no Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="30c35-108">These assemblies allow you to write cmdlets, providers, and host programs for Windows PowerShell 3.0.</span></span>
<span data-ttu-id="30c35-109">Quando você instala o SDK do Windows para o Windows 8, os assemblies do Windows PowerShell são instalados automaticamente na pasta do assembly de referência, em `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.</span><span class="sxs-lookup"><span data-stu-id="30c35-109">When you install the Windows SDK for Windows 8, the Windows PowerShell assemblies are automatically installed in the reference assembly folder, in `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.</span></span>
<span data-ttu-id="30c35-110">Para obter mais informações, visite o [site de download do SDK do Windows 8](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).</span><span class="sxs-lookup"><span data-stu-id="30c35-110">For more information, see the [Windows 8 SDK download site](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).</span></span>
<span data-ttu-id="30c35-111">Exemplos de código do Windows PowerShell também estão disponíveis no Centro de Desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="30c35-111">Windows PowerShell code samples are also available on the Development Center.</span></span>
<span data-ttu-id="30c35-112">Para obter mais informações, confira a página de exemplo de código de Área de Trabalho no [site do Centro de desenvolvimento](https://code.msdn.microsoft.com:443/windowsdesktop/).</span><span class="sxs-lookup"><span data-stu-id="30c35-112">For more information, see the Desktop code sample page on the [Dev center site](https://code.msdn.microsoft.com:443/windowsdesktop/).</span></span>

<span data-ttu-id="30c35-113">Além disso, o Windows PowerShell 3.0 é compatível com versões anteriores com o SDK do Windows PowerShell 2.0, que inclui diversos exemplos de código.</span><span class="sxs-lookup"><span data-stu-id="30c35-113">In addition, Windows PowerShell 3.0 is backwards-compatible with the Windows PowerShell 2.0 SDK, which includes a number of code samples.</span></span>
<span data-ttu-id="30c35-114">Para obter mais informações sobre como baixar o SDK do Windows PowerShell 2.0, consulte abaixo.</span><span class="sxs-lookup"><span data-stu-id="30c35-114">For more information on how to download the Windows PowerShell 2.0 SDK, see below.</span></span>
<span data-ttu-id="30c35-115">(Observe que, enquanto os exemplos de 2.0 código são compatíveis com o Windows 8 e Windows PowerShell 3.0, você não pode instalar o Windows PowerShell 2.0 em uma plataforma Windows 8).</span><span class="sxs-lookup"><span data-stu-id="30c35-115">(Note that while the 2.0 code samples are compatible with Windows 8 and Windows PowerShell 3.0, you cannot install Windows PowerShell 2.0 on a Windows 8 platform.)</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a><span data-ttu-id="30c35-116">Instalando o SDK do Windows PowerShell 3.0 no Windows 7 e Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="30c35-116">Installing Windows PowerShell 3.0 SDK for Windows 7 and Windows Server 2008 R2</span></span>

<span data-ttu-id="30c35-117">O Windows 7 e o Windows Server 2008 R2 têm o PowerShell 2.0 instalado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="30c35-117">Windows 7 and Windows Server 2008 R2 automatically have PowerShell 2.0 installed.</span></span>
<span data-ttu-id="30c35-118">Além disso, você pode instalar o PowerShell 3.0 nesses sistemas.</span><span class="sxs-lookup"><span data-stu-id="30c35-118">In addition, you can install PowerShell 3.0 on these systems.</span></span>
<span data-ttu-id="30c35-119">(Para obter mais informações, veja [Installing Windows PowerShell](Installing-Windows-PowerShell.md) [Instalando o Windows PowerShell]).</span><span class="sxs-lookup"><span data-stu-id="30c35-119">(For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).).</span></span>
<span data-ttu-id="30c35-120">Conforme descrito acima, você também pode instalar o SDK do Windows 8 no Windows 7 e Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="30c35-120">As described above, you can also install the Windows 8 SDK on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a><span data-ttu-id="30c35-121">Instalando o SDK do Windows PowerShell 2.0 para Windows 7, Vista, XP, Server 2003 e Server 2008</span><span class="sxs-lookup"><span data-stu-id="30c35-121">Installing Windows PowerShell 2.0 SDK for Windows 7, Vista, XP, Server 2003, and Server 2008</span></span>

<span data-ttu-id="30c35-122">O SDK do Windows PowerShell 2.0 fornece os assemblies de referência necessários para gravar cmdlets, provedores e aplicativos de hospedagem, além de fornecer o código de exemplo em C# que poderá ser usado como ponto de partida quando você começar a gravar código.</span><span class="sxs-lookup"><span data-stu-id="30c35-122">The Windows PowerShell 2.0 SDK provides the reference assemblies needed to write cmdlets, providers, and hosting applications, and it provides C# sample code that can be used as the starting point when you begin writing code.</span></span>

<span data-ttu-id="30c35-123">Para instalar esse SDK, veja [Windows PowerShell 2.0 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=2560) (SDK do Windows PowerShell 2.0).</span><span class="sxs-lookup"><span data-stu-id="30c35-123">To install this SDK, see [Windows PowerShell 2.0 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=2560).</span></span>

## <a name="reference-assemblies"></a><span data-ttu-id="30c35-124">Assemblies de referência</span><span class="sxs-lookup"><span data-stu-id="30c35-124">Reference assemblies</span></span>

<span data-ttu-id="30c35-125">Assemblies de referência são instalados, por padrão, no seguinte local: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span><span class="sxs-lookup"><span data-stu-id="30c35-125">Reference assemblies are installed in the following location by default: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span></span>

> [!NOTE] 
> <span data-ttu-id="30c35-126">O código que é compilado nos assemblies do Windows PowerShell 2.0 não pode ser carregado em instalações do Windows PowerShell 1.0.</span><span class="sxs-lookup"><span data-stu-id="30c35-126">Code that is compiled against the Windows PowerShell 2.0 assemblies cannot be loaded into Windows PowerShell 1.0 installations.</span></span>
> <span data-ttu-id="30c35-127">No entanto, o código que é compilado em relação aos assemblies do Windows PowerShell 1.0 pode ser carregado em instalações do Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="30c35-127">However, code that is compiled against the Windows PowerShell 1.0 assemblies can be loaded into Windows PowerShell 2.0 installations.</span></span>

## <a name="samples"></a><span data-ttu-id="30c35-128">Amostras</span><span class="sxs-lookup"><span data-stu-id="30c35-128">Samples</span></span>

<span data-ttu-id="30c35-129">Exemplos de código são instalados, por padrão, no seguinte local: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="30c35-129">Code samples are installed in the following location by default: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span></span>

<span data-ttu-id="30c35-130">As seções a seguir fornecem uma breve descrição da ação de cada amostra.</span><span class="sxs-lookup"><span data-stu-id="30c35-130">The following sections provide a brief description of what each sample does.</span></span>

## <a name="cmdlet-samples"></a><span data-ttu-id="30c35-131">Amostras de cmdlet</span><span class="sxs-lookup"><span data-stu-id="30c35-131">Cmdlet samples</span></span>

### <a name="getprocesssample01"></a><span data-ttu-id="30c35-132">GetProcessSample01</span><span class="sxs-lookup"><span data-stu-id="30c35-132">GetProcessSample01</span></span>

<span data-ttu-id="30c35-133">Mostra como gravar um cmdlet simples que coloca todos os processos no computador local.</span><span class="sxs-lookup"><span data-stu-id="30c35-133">Shows how to write a simple cmdlet that gets all the processes on the local computer.</span></span>

### <a name="getprocesssample02"></a><span data-ttu-id="30c35-134">GetProcessSample02</span><span class="sxs-lookup"><span data-stu-id="30c35-134">GetProcessSample02</span></span>

<span data-ttu-id="30c35-135">Mostra como adicionar parâmetros ao cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30c35-135">Shows how to add parameters to the cmdlet.</span></span>
<span data-ttu-id="30c35-136">O cmdlet usa um ou mais nomes de processo e retorna os processos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="30c35-136">The cmdlet takes one or more process names and returns the matching processes.</span></span>

### <a name="getprocesssample03"></a><span data-ttu-id="30c35-137">GetProcessSample03</span><span class="sxs-lookup"><span data-stu-id="30c35-137">GetProcessSample03</span></span>

<span data-ttu-id="30c35-138">Mostra como adicionar parâmetros que aceitam a entrada do pipeline.</span><span class="sxs-lookup"><span data-stu-id="30c35-138">Shows how to add parameters that accept input from the pipeline.</span></span>

### <a name="getprocesssample04"></a><span data-ttu-id="30c35-139">GetProcessSample04</span><span class="sxs-lookup"><span data-stu-id="30c35-139">GetProcessSample04</span></span>

<span data-ttu-id="30c35-140">Mostra como tratar erros de não encerramento.</span><span class="sxs-lookup"><span data-stu-id="30c35-140">Shows how to handle nonterminating errors.</span></span>

### <a name="getprocesssample05"></a><span data-ttu-id="30c35-141">GetProcessSample05</span><span class="sxs-lookup"><span data-stu-id="30c35-141">GetProcessSample05</span></span>

<span data-ttu-id="30c35-142">Mostra como exibir uma lista de processos especificados.</span><span class="sxs-lookup"><span data-stu-id="30c35-142">Shows how to display a list of specified processes.</span></span>

### <a name="selectobject"></a><span data-ttu-id="30c35-143">SelectObject</span><span class="sxs-lookup"><span data-stu-id="30c35-143">SelectObject</span></span>

<span data-ttu-id="30c35-144">Mostra como gravar um filtro para selecionar apenas determinados objetos.</span><span class="sxs-lookup"><span data-stu-id="30c35-144">Shows how to write a filter to select only certain objects.</span></span>

### <a name="selectstring"></a><span data-ttu-id="30c35-145">SelectString</span><span class="sxs-lookup"><span data-stu-id="30c35-145">SelectString</span></span>

<span data-ttu-id="30c35-146">Mostra como pesquisar padrões especificados em arquivos.</span><span class="sxs-lookup"><span data-stu-id="30c35-146">Shows how to search files for specified patterns.</span></span>

### <a name="stopprocesssample01"></a><span data-ttu-id="30c35-147">StopProcessSample01</span><span class="sxs-lookup"><span data-stu-id="30c35-147">StopProcessSample01</span></span>

<span data-ttu-id="30c35-148">Mostra como implementar um parâmetro *PassThru* e como solicitar comentários do usuário por chamadas para os métodos [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) e [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue).</span><span class="sxs-lookup"><span data-stu-id="30c35-148">Shows how to implement a *PassThru* parameter, and how to request user feedback by calls to the [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) and [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) methods.</span></span>
<span data-ttu-id="30c35-149">Os usuários especificam o parâmetro *PassThru* quando querem forçar o cmdlet a retornar um objeto de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="30c35-149">Users specify the *PassThru* parameter when they want to force the cmdlet to return an object,</span></span>

### <a name="stopprocesssample02"></a><span data-ttu-id="30c35-150">StopProcessSample02</span><span class="sxs-lookup"><span data-stu-id="30c35-150">StopProcessSample02</span></span>

<span data-ttu-id="30c35-151">Mostra como interromper um processo específico.</span><span class="sxs-lookup"><span data-stu-id="30c35-151">Shows how to stop a specific process.</span></span>

### <a name="stopprocesssample03"></a><span data-ttu-id="30c35-152">StopProcessSample03</span><span class="sxs-lookup"><span data-stu-id="30c35-152">StopProcessSample03</span></span>

<span data-ttu-id="30c35-153">Mostra como declarar aliases para parâmetros e como dar suporte a curingas.</span><span class="sxs-lookup"><span data-stu-id="30c35-153">Shows how to declare aliases for parameters and how to support wildcards.</span></span>

### <a name="stopprocesssample04"></a><span data-ttu-id="30c35-154">StopProcessSample04</span><span class="sxs-lookup"><span data-stu-id="30c35-154">StopProcessSample04</span></span>

<span data-ttu-id="30c35-155">Mostra como declarar conjuntos de parâmetros, o objeto que o cmdlet usa como entrada, e como especificar o parâmetro padrão definido a ser usado.</span><span class="sxs-lookup"><span data-stu-id="30c35-155">Shows how to declare parameter sets, the object that the cmdlet takes as input, and how to specify the default parameter set to use.</span></span>

## <a name="remoting-samples"></a><span data-ttu-id="30c35-156">Amostras de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="30c35-156">Remoting samples</span></span>

### <a name="remoterunspace01"></a><span data-ttu-id="30c35-157">RemoteRunspace01</span><span class="sxs-lookup"><span data-stu-id="30c35-157">RemoteRunspace01</span></span>

<span data-ttu-id="30c35-158">Mostra como criar um runspace remoto que é usado para estabelecer uma conexão remota.</span><span class="sxs-lookup"><span data-stu-id="30c35-158">Shows how to create a remote runspace that is used to establish a remote connection.</span></span>

### <a name="remoterunspacepool01"></a><span data-ttu-id="30c35-159">RemoteRunspacePool01</span><span class="sxs-lookup"><span data-stu-id="30c35-159">RemoteRunspacePool01</span></span>

<span data-ttu-id="30c35-160">Mostra como construir um pool de runspaces remotos e como executar vários comandos simultaneamente usando esse pool.</span><span class="sxs-lookup"><span data-stu-id="30c35-160">Shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

### <a name="serialization01"></a><span data-ttu-id="30c35-161">Serialization01</span><span class="sxs-lookup"><span data-stu-id="30c35-161">Serialization01</span></span>

<span data-ttu-id="30c35-162">Mostra como examinar uma classe existente do .NET e garantir que as informações das propriedades públicas selecionadas dessa classe são preservadas na serialização/desserialização.</span><span class="sxs-lookup"><span data-stu-id="30c35-162">Shows how to look at an existing .NET class and make sure that information from selected public properties of this class is preserved across serialization/deserialization.</span></span>

### <a name="serialization02"></a><span data-ttu-id="30c35-163">Serialization02</span><span class="sxs-lookup"><span data-stu-id="30c35-163">Serialization02</span></span>

<span data-ttu-id="30c35-164">Mostra como examinar uma classe existente do .NET e garantir que as informações da instância dessa classe são preservadas na serialização/desserialização quando as informações não estão disponíveis nas propriedades públicas da classe.</span><span class="sxs-lookup"><span data-stu-id="30c35-164">Shows how to look at an existing .NET class and make sure that information from instance of this class is preserved across serialization/deserialization when the information is not available in public properties of the class.</span></span>

### <a name="serialization03"></a><span data-ttu-id="30c35-165">Serialization03</span><span class="sxs-lookup"><span data-stu-id="30c35-165">Serialization03</span></span>

<span data-ttu-id="30c35-166">Mostra como examinar uma classe existente do .NET e garantir que as instâncias dessa classe e de classes derivadas são desserializadas (reidratadas) em objetos dinâmicos do .NET.</span><span class="sxs-lookup"><span data-stu-id="30c35-166">Shows how to look at an existing .NET class and make sure that instances of this class and of derived classes are deserialized (rehydrated) into live .NET objects.</span></span>

## <a name="event-samples"></a><span data-ttu-id="30c35-167">Amostras de eventos</span><span class="sxs-lookup"><span data-stu-id="30c35-167">Event samples</span></span>

### <a name="event01"></a><span data-ttu-id="30c35-168">Event01</span><span class="sxs-lookup"><span data-stu-id="30c35-168">Event01</span></span>

<span data-ttu-id="30c35-169">Mostra como criar um cmdlet de registro de eventos, fazendo a derivação de ObjectEventRegistrationBase.</span><span class="sxs-lookup"><span data-stu-id="30c35-169">Shows how to create a cmdlet for event registration by deriving from ObjectEventRegistrationBase.</span></span>

### <a name="event02"></a><span data-ttu-id="30c35-170">Event02</span><span class="sxs-lookup"><span data-stu-id="30c35-170">Event02</span></span>

<span data-ttu-id="30c35-171">Mostra como receber notificações de eventos do Windows PowerShell gerados em computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="30c35-171">Shows how to shows how to receive notifications of Windows PowerShell events that are generated on remote computers.</span></span>
<span data-ttu-id="30c35-172">Usa o evento PSEventReceived exposto por meio da classe [Runspace](/dotnet/api/system.management.automation.runspaces.runspace).</span><span class="sxs-lookup"><span data-stu-id="30c35-172">It uses the PSEventReceived event exposed through the [Runspace](/dotnet/api/system.management.automation.runspaces.runspace) class.</span></span>

## <a name="hosting-application-samples"></a><span data-ttu-id="30c35-173">Amostras de aplicativos de hospedagem</span><span class="sxs-lookup"><span data-stu-id="30c35-173">Hosting application samples</span></span>

### <a name="runspace01"></a><span data-ttu-id="30c35-174">Runspace01</span><span class="sxs-lookup"><span data-stu-id="30c35-174">Runspace01</span></span>

<span data-ttu-id="30c35-175">Mostra como usar a classe [PowerShell](/dotnet/api/system.management.automation.powershell) para executar o cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="30c35-175">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously.</span></span>
<span data-ttu-id="30c35-176">O cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) retorna os objetos [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) de cada processo em execução no computador local.</span><span class="sxs-lookup"><span data-stu-id="30c35-176">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer.</span></span>

### <a name="runspace02"></a><span data-ttu-id="30c35-177">Runspace02</span><span class="sxs-lookup"><span data-stu-id="30c35-177">Runspace02</span></span>

<span data-ttu-id="30c35-178">Mostra como usar a classe [PowerShell](/dotnet/api/system.management.automation.powershell) para executar os cmdlets [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) e [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="30c35-178">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span>
<span data-ttu-id="30c35-179">O cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) retorna os objetos [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) de cada processo em execução no computador local e `Sort-Object` classifica os objetos com base em sua propriedade [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx).</span><span class="sxs-lookup"><span data-stu-id="30c35-179">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) property.</span></span>
<span data-ttu-id="30c35-180">Os resultados desses comandos são exibidos com o uso de um controle [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx).</span><span class="sxs-lookup"><span data-stu-id="30c35-180">The results of these commands is displayed by using a [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) control.</span></span>

### <a name="runspace03"></a><span data-ttu-id="30c35-181">Runspace03</span><span class="sxs-lookup"><span data-stu-id="30c35-181">Runspace03</span></span>

<span data-ttu-id="30c35-182">Mostra como usar a classe [PowerShell](/dotnet/api/system.management.automation.powershell) para executar um script de forma síncrona e como tratar erros de não encerramento.</span><span class="sxs-lookup"><span data-stu-id="30c35-182">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run a script synchronously, and how to handle non-terminating errors.</span></span>
<span data-ttu-id="30c35-183">O script recebe uma lista de nomes de processo e, em seguida, recupera tais processos.</span><span class="sxs-lookup"><span data-stu-id="30c35-183">The script receives a list of process names and then retrieves those processes.</span></span>
<span data-ttu-id="30c35-184">Os resultados do script, incluindo quaisquer erros de não encerramento gerados durante a execução do script, são exibidos em uma janela do console.</span><span class="sxs-lookup"><span data-stu-id="30c35-184">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

### <a name="runspace04"></a><span data-ttu-id="30c35-185">Runspace04</span><span class="sxs-lookup"><span data-stu-id="30c35-185">Runspace04</span></span>

<span data-ttu-id="30c35-186">Mostra como usar a classe [PowerShell](/dotnet/api/system.management.automation.powershell) para executar comandos e como capturar erros de encerramento gerados durante a execução de comandos.</span><span class="sxs-lookup"><span data-stu-id="30c35-186">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span>
<span data-ttu-id="30c35-187">Dois comandos são executados e o último comando é passado um argumento de parâmetro que não é válido.</span><span class="sxs-lookup"><span data-stu-id="30c35-187">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span>
<span data-ttu-id="30c35-188">Como resultado, nenhum objeto é retornado e um erro de encerramento é gerado.</span><span class="sxs-lookup"><span data-stu-id="30c35-188">As a result, no objects are returned and a terminating error is thrown.</span></span>

### <a name="runspace05"></a><span data-ttu-id="30c35-189">Runspace05</span><span class="sxs-lookup"><span data-stu-id="30c35-189">Runspace05</span></span>

<span data-ttu-id="30c35-190">Mostra como adicionar um snap-in a um objeto [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) para que o cmdlet do snap-in esteja disponível quando o runspace for aberto.</span><span class="sxs-lookup"><span data-stu-id="30c35-190">Shows how to add a snap-in to an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span>
<span data-ttu-id="30c35-191">O snap-in fornece um cmdlet Get-Proc (definido pela [Amostra GetProcessSample01](https://technet.microsoft.com/library/ff602028.aspx)) que é executado de forma síncrona usando um objeto [PowerShell](/dotnet/api/system.management.automation.powershell).</span><span class="sxs-lookup"><span data-stu-id="30c35-191">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](https://technet.microsoft.com/library/ff602028.aspx)) that is run synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace06"></a><span data-ttu-id="30c35-192">Runspace06</span><span class="sxs-lookup"><span data-stu-id="30c35-192">Runspace06</span></span>

<span data-ttu-id="30c35-193">Mostra como adicionar um módulo a um objeto [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) para que o módulo seja carregado quando o runspace for aberto.</span><span class="sxs-lookup"><span data-stu-id="30c35-193">Shows how to add a module to an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object so that the module is loaded when the runspace is opened.</span></span>
<span data-ttu-id="30c35-194">O módulo fornece um cmdlet Get-Proc (definido pelo [GetProcessSample02 exemplo](https://technet.microsoft.com/library/ff602027.aspx)) executado de forma síncrona com o uso de um objeto [PowerShell](/dotnet/api/system.management.automation.powershell).</span><span class="sxs-lookup"><span data-stu-id="30c35-194">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](https://technet.microsoft.com/library/ff602027.aspx)) that is run synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace07"></a><span data-ttu-id="30c35-195">Runspace07</span><span class="sxs-lookup"><span data-stu-id="30c35-195">Runspace07</span></span>

<span data-ttu-id="30c35-196">Mostra como criar um runspace e usá-lo para executar dois cmdlets de forma síncrona usando um objeto [PowerShell](/dotnet/api/system.management.automation.powershell).</span><span class="sxs-lookup"><span data-stu-id="30c35-196">Shows how to create a runspace, and then use that runspace to run two cmdlets synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace08"></a><span data-ttu-id="30c35-197">Runspace08</span><span class="sxs-lookup"><span data-stu-id="30c35-197">Runspace08</span></span>

<span data-ttu-id="30c35-198">Mostra como adicionar comandos e argumentos ao pipeline de um objeto [PowerShell](/dotnet/api/system.management.automation.powershell) e como executar os comandos de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="30c35-198">Shows how to add commands and arguments to the pipeline of a [PowerShell](/dotnet/api/system.management.automation.powershell) object and how to run the commands synchronously.</span></span>

### <a name="runspace09"></a><span data-ttu-id="30c35-199">Runspace09</span><span class="sxs-lookup"><span data-stu-id="30c35-199">Runspace09</span></span>

<span data-ttu-id="30c35-200">Mostra como adicionar um script ao pipeline de um objeto [PowerShell](/dotnet/api/system.management.automation.powershell) e como executar o script de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="30c35-200">Shows how to add a script to the pipeline of a [PowerShell](/dotnet/api/system.management.automation.powershell) object and how to run the script asynchronously.</span></span>
<span data-ttu-id="30c35-201">Eventos são usados para tratar a saída do script.</span><span class="sxs-lookup"><span data-stu-id="30c35-201">Events are used to handle the output of the script.</span></span>

### <a name="runspace10"></a><span data-ttu-id="30c35-202">Runspace10</span><span class="sxs-lookup"><span data-stu-id="30c35-202">Runspace10</span></span>

<span data-ttu-id="30c35-203">Mostra como criar um estado de sessão inicial padrão, como adicionar um cmdlet ao [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), como criar um runspace que usa o estado de sessão inicial e como executar o comando usando um objeto [PowerShell](/dotnet/api/system.management.automation.powershell).</span><span class="sxs-lookup"><span data-stu-id="30c35-203">Shows how to create a default initial session state, how to add a cmdlet to the [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), how to create a runspace that uses the initial session state, and how to run the command by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace11"></a><span data-ttu-id="30c35-204">Runspace11</span><span class="sxs-lookup"><span data-stu-id="30c35-204">Runspace11</span></span>

<span data-ttu-id="30c35-205">Mostra como usar a classe [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) para criar um comando proxy que chama um cmdlet existente, mas restringe o conjunto de parâmetros disponíveis.</span><span class="sxs-lookup"><span data-stu-id="30c35-205">Shows how to use the [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span>
<span data-ttu-id="30c35-206">O comando de proxy é adicionado a um estado de sessão inicial que é usado para criar um espaço de execução restrito.</span><span class="sxs-lookup"><span data-stu-id="30c35-206">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span>
<span data-ttu-id="30c35-207">Isso significa que o usuário pode acessar a funcionalidade do cmdlet apenas por meio do comando proxy.</span><span class="sxs-lookup"><span data-stu-id="30c35-207">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

### <a name="powershell01"></a><span data-ttu-id="30c35-208">PowerShell01</span><span class="sxs-lookup"><span data-stu-id="30c35-208">PowerShell01</span></span>

<span data-ttu-id="30c35-209">Mostra como criar um runspace restrito usando um objeto [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate).</span><span class="sxs-lookup"><span data-stu-id="30c35-209">Shows how to create a constrained runspace using an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object.</span></span>

### <a name="powershell02"></a><span data-ttu-id="30c35-210">PowerShell02</span><span class="sxs-lookup"><span data-stu-id="30c35-210">PowerShell02</span></span>

<span data-ttu-id="30c35-211">Mostra como usar um pool de runspaces para executar vários comandos simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="30c35-211">Shows how to use a runspace pool to run multiple commands concurrently.</span></span>

## <a name="host-samples"></a><span data-ttu-id="30c35-212">Amostras de host</span><span class="sxs-lookup"><span data-stu-id="30c35-212">Host samples</span></span>

### <a name="host01"></a><span data-ttu-id="30c35-213">Host01</span><span class="sxs-lookup"><span data-stu-id="30c35-213">Host01</span></span>

<span data-ttu-id="30c35-214">Mostra como implementar um aplicativo host que usa um host personalizado.</span><span class="sxs-lookup"><span data-stu-id="30c35-214">Shows how to implement a host application that uses a custom host.</span></span>
<span data-ttu-id="30c35-215">Nesta amostra, é criado um runspace que usa o host personalizado e, em seguida, a API [PowerShell](/dotnet/api/system.management.automation.powershell) é usada para executar um script que chama a “saída”.</span><span class="sxs-lookup"><span data-stu-id="30c35-215">In this sample a runspace is created that uses the custom host, and then the [PowerShell](/dotnet/api/system.management.automation.powershell) API is used to run a script that calls "exit".</span></span>
<span data-ttu-id="30c35-216">O aplicativo host analisa a saída do script e imprime os resultados.</span><span class="sxs-lookup"><span data-stu-id="30c35-216">The host application then looks at the output of the script and prints out the results.</span></span>

### <a name="host02"></a><span data-ttu-id="30c35-217">Host02</span><span class="sxs-lookup"><span data-stu-id="30c35-217">Host02</span></span>

<span data-ttu-id="30c35-218">Mostra como gravar um aplicativo host que usa o tempo de execução do Windows PowerShell, juntamente com uma implementação de host personalizado.</span><span class="sxs-lookup"><span data-stu-id="30c35-218">Shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span>
<span data-ttu-id="30c35-219">O aplicativo host define a cultura do host para alemão, executa o cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process), exibe os resultados como seriam vistos com pwrsh.exe e imprime a data e hora atuais em alemão.</span><span class="sxs-lookup"><span data-stu-id="30c35-219">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them by using pwrsh.exe, and then prints out the current data and time in German.</span></span>

### <a name="host03"></a><span data-ttu-id="30c35-220">Host03</span><span class="sxs-lookup"><span data-stu-id="30c35-220">Host03</span></span>

<span data-ttu-id="30c35-221">Mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e exibe os resultados para o console.</span><span class="sxs-lookup"><span data-stu-id="30c35-221">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

### <a name="host04"></a><span data-ttu-id="30c35-222">Host04</span><span class="sxs-lookup"><span data-stu-id="30c35-222">Host04</span></span>

<span data-ttu-id="30c35-223">Mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e exibe os resultados para o console.</span><span class="sxs-lookup"><span data-stu-id="30c35-223">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="30c35-224">Esse aplicativo host também dá suporte a exibições de avisos que permitem ao usuário especificar várias opções.</span><span class="sxs-lookup"><span data-stu-id="30c35-224">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

### <a name="host05"></a><span data-ttu-id="30c35-225">Host05</span><span class="sxs-lookup"><span data-stu-id="30c35-225">Host05</span></span>

<span data-ttu-id="30c35-226">Mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e exibe os resultados para o console.</span><span class="sxs-lookup"><span data-stu-id="30c35-226">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="30c35-227">Este aplicativo host também dá suporte a chamadas para computadores remotos com os cmdlets [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) e [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession).</span><span class="sxs-lookup"><span data-stu-id="30c35-227">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets.</span></span>

### <a name="host06"></a><span data-ttu-id="30c35-228">Host06</span><span class="sxs-lookup"><span data-stu-id="30c35-228">Host06</span></span>

<span data-ttu-id="30c35-229">Mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e exibe os resultados para o console.</span><span class="sxs-lookup"><span data-stu-id="30c35-229">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="30c35-230">Além disso, este exemplo usa as APIs do Criador de Token para especificar a cor do texto inserido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="30c35-230">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="provider-samples"></a><span data-ttu-id="30c35-231">Amostras de provedor</span><span class="sxs-lookup"><span data-stu-id="30c35-231">Provider samples</span></span>

### <a name="accessdbprovidersample01"></a><span data-ttu-id="30c35-232">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="30c35-232">AccessDBProviderSample01</span></span>

<span data-ttu-id="30c35-233">Mostra como declarar uma classe de provedor que deriva diretamente da classe [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider).</span><span class="sxs-lookup"><span data-stu-id="30c35-233">Shows how to declare a provider class that derives directly from the [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) class.</span></span>
<span data-ttu-id="30c35-234">Ele é incluído aqui apenas para fins de integridade.</span><span class="sxs-lookup"><span data-stu-id="30c35-234">It is included here only for completeness.</span></span>

### <a name="accessdbprovidersample02"></a><span data-ttu-id="30c35-235">AccessDBProviderSample02</span><span class="sxs-lookup"><span data-stu-id="30c35-235">AccessDBProviderSample02</span></span>

<span data-ttu-id="30c35-236">Mostra como substituir os métodos [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) e [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) para dar suporte a chamadas para os cmdlets `New-PSDrive` e `Remove-PSDrive`.</span><span class="sxs-lookup"><span data-stu-id="30c35-236">Shows how to overwrite the [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) and [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) methods to support calls to the `New-PSDrive` and `Remove-PSDrive` cmdlets.</span></span>
<span data-ttu-id="30c35-237">A classe de provedor nessa amostra deriva da classe [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider).</span><span class="sxs-lookup"><span data-stu-id="30c35-237">The provider class in this sample derives from the [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) class.</span></span>

### <a name="accessdbprovidersample03"></a><span data-ttu-id="30c35-238">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="30c35-238">AccessDBProviderSample03</span></span>

<span data-ttu-id="30c35-239">Mostra como substituir os métodos [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) e [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) para dar suporte a chamadas para os cmdlets `Get-Item` e `Set-Item`.</span><span class="sxs-lookup"><span data-stu-id="30c35-239">Shows how to overwrite the [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) and [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span>
<span data-ttu-id="30c35-240">A classe de provedor nessa amostra deriva da classe [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider).</span><span class="sxs-lookup"><span data-stu-id="30c35-240">The provider class in this sample derives from the [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample04"></a><span data-ttu-id="30c35-241">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="30c35-241">AccessDBProviderSample04</span></span>

<span data-ttu-id="30c35-242">Mostra como substituir os métodos de contêiner para dar suporte a chamadas para os cmdlets `Copy-Item`, `Get-ChildItem`, `New-Item` e `Remove-Item`.</span><span class="sxs-lookup"><span data-stu-id="30c35-242">Shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span>
<span data-ttu-id="30c35-243">Esses métodos devem ser implementados quando o armazenamento de dados contiver itens que são contêineres.</span><span class="sxs-lookup"><span data-stu-id="30c35-243">These methods should be implemented when the data store contains items that are containers.</span></span>
<span data-ttu-id="30c35-244">Um contêiner é um grupo de itens filho em um item pai comum.</span><span class="sxs-lookup"><span data-stu-id="30c35-244">A container is a group of child items under a common parent item.</span></span>
<span data-ttu-id="30c35-245">A classe de provedor nessa amostra deriva da classe [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider).</span><span class="sxs-lookup"><span data-stu-id="30c35-245">The provider class in this sample derives from the [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample05"></a><span data-ttu-id="30c35-246">AccessDBProviderSample05</span><span class="sxs-lookup"><span data-stu-id="30c35-246">AccessDBProviderSample05</span></span>

<span data-ttu-id="30c35-247">Mostra como substituir os métodos de contêiner para dar suporte a chamadas para os cmdlets `Move-Item` e `Join-Path`.</span><span class="sxs-lookup"><span data-stu-id="30c35-247">Shows how to overwrite container methods to support calls to the `Move-Item` and `Join-Path` cmdlets.</span></span>
<span data-ttu-id="30c35-248">Esses métodos deverão ser implementados quando o usuário precisar mover itens dentro de um contêiner e se o armazenamento de dados contiver contêineres aninhados.</span><span class="sxs-lookup"><span data-stu-id="30c35-248">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span>
<span data-ttu-id="30c35-249">A classe de provedor nessa amostra deriva da classe [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider).</span><span class="sxs-lookup"><span data-stu-id="30c35-249">The provider class in this sample derives from the [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample06"></a><span data-ttu-id="30c35-250">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="30c35-250">AccessDBProviderSample06</span></span>

<span data-ttu-id="30c35-251">Mostra como substituir os métodos de conteúdo para dar suporte a chamadas para os cmdlets `Clear-Content`, `Get-Content` e `Set-Content`.</span><span class="sxs-lookup"><span data-stu-id="30c35-251">Shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span>
<span data-ttu-id="30c35-252">Esses métodos devem ser implementados quando o usuário precisa gerenciar o conteúdo dos itens no armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="30c35-252">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span>
<span data-ttu-id="30c35-253">A classe de provedor nessa amostra deriva da classe [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) e implementa a interface [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider).</span><span class="sxs-lookup"><span data-stu-id="30c35-253">The provider class in this sample derives from the [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) class, and it implements the [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interface.</span></span>