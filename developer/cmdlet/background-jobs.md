---
title: Trabalhos em segundo plano | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794698"
---
# <a name="background-jobs"></a><span data-ttu-id="74445-102">Trabalhos em segundo plano</span><span class="sxs-lookup"><span data-stu-id="74445-102">Background Jobs</span></span>

<span data-ttu-id="74445-103">Cmdlets pode executar sua ação internamente ou como um Windows PowerShell*trabalho em segundo plano*.</span><span class="sxs-lookup"><span data-stu-id="74445-103">Cmdlets can perform their action internally or as a Windows PowerShell*background job*.</span></span> <span data-ttu-id="74445-104">Quando um cmdlet é executado como um trabalho em segundo plano, o trabalho é feito de forma assíncrona em seu próprio thread separado do thread do pipeline que usa o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="74445-104">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="74445-105">Da perspectiva do usuário, quando um cmdlet é executado como um trabalho em segundo plano, o prompt de comando retorna imediatamente, mesmo se o trabalho leva um longo período de tempo para ser concluída e o usuário pode continuar sem interrupções enquanto o trabalho é executado.</span><span class="sxs-lookup"><span data-stu-id="74445-105">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="74445-106">Trabalhos em segundo plano, trabalhos filhos e o repositório de trabalho</span><span class="sxs-lookup"><span data-stu-id="74445-106">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="74445-107">O objeto de trabalho que é retornado pelos cmdlets que oferecem suporte a trabalhos em segundo plano define o trabalho.</span><span class="sxs-lookup"><span data-stu-id="74445-107">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="74445-108">(O [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet também retorna um objeto de trabalho.) O nome do trabalho, um identificador que é usado para especificar o trabalho, as informações de estado e os trabalhos filhos são incluídos nessa definição.</span><span class="sxs-lookup"><span data-stu-id="74445-108">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="74445-109">O trabalho não realiza o trabalho.</span><span class="sxs-lookup"><span data-stu-id="74445-109">The job does not perform any of the work.</span></span> <span data-ttu-id="74445-110">Cada trabalho em segundo plano tem pelo menos um trabalho filho, porque o trabalho filho executa o trabalho real.</span><span class="sxs-lookup"><span data-stu-id="74445-110">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="74445-111">Quando você executar um cmdlet, para que o trabalho é executado como um trabalho em segundo plano, o cmdlet deve adicionar o trabalho e os trabalhos filho para um repositório comum, conhecido como o *repositório de trabalho*.</span><span class="sxs-lookup"><span data-stu-id="74445-111">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="74445-112">Para obter mais informações sobre como os trabalhos em segundo plano são tratados na linha de comando, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="74445-112">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="74445-113">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="74445-113">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="74445-114">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="74445-114">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="74445-115">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="74445-115">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="74445-116">Escrevendo um Cmdlet que é executado como um trabalho em segundo plano</span><span class="sxs-lookup"><span data-stu-id="74445-116">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="74445-117">Para gravar um cmdlet que pode ser executado como um trabalho em segundo plano, você deve concluir as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="74445-117">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="74445-118">Definir um `asJob` Troque o parâmetro para que o usuário pode decidir se deseja executar o cmdlet como um trabalho em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="74445-118">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="74445-119">Criar um objeto que deriva de [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) classe.</span><span class="sxs-lookup"><span data-stu-id="74445-119">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="74445-120">Esse objeto pode ser um objeto de trabalho personalizado ou um objeto de trabalho fornecida pelo Windows PowerShell, tal como uma [pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) objeto.</span><span class="sxs-lookup"><span data-stu-id="74445-120">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="74445-121">Em um método de processamento de registro, adicione um `if` instrução que detecta se o cmdlet deve ser executado como um trabalho em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="74445-121">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="74445-122">Para objetos de trabalho personalizado, implemente a classe de trabalho.</span><span class="sxs-lookup"><span data-stu-id="74445-122">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="74445-123">Retorne os objetos apropriados, dependendo se o cmdlet é executado como um trabalho em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="74445-123">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="74445-124">Para obter um exemplo de código, consulte [como suporte a trabalhos](./how-to-support-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="74445-124">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="74445-125">APIs de relacionados ao trabalho em segundo plano</span><span class="sxs-lookup"><span data-stu-id="74445-125">Background Job-Related APIs</span></span>

<span data-ttu-id="74445-126">As seguintes APIs são fornecidas pelo Windows PowerShell para gerenciar trabalhos em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="74445-126">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="74445-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) deriva objetos de trabalho personalizado.</span><span class="sxs-lookup"><span data-stu-id="74445-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="74445-128">Esta é uma classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="74445-128">This is an abstract class.</span></span>

<span data-ttu-id="74445-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) gerencia e fornece informações sobre os trabalhos em segundo plano ativo atual.</span><span class="sxs-lookup"><span data-stu-id="74445-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="74445-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) define o estado do trabalho em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="74445-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="74445-131">Os estados incluem iniciado, em execução e parado.</span><span class="sxs-lookup"><span data-stu-id="74445-131">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="74445-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) fornece informações sobre o estado de um trabalho em segundo plano e, se o estado da última alteração foi causado por um erro, o motivo pelo qual o trabalho entrou no seu estado atual.</span><span class="sxs-lookup"><span data-stu-id="74445-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="74445-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) fornece os argumentos para um evento que é gerado quando um trabalho de plano de fundo muda de estado.</span><span class="sxs-lookup"><span data-stu-id="74445-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="74445-134">Cmdlets de trabalho do PowerShell do Windows</span><span class="sxs-lookup"><span data-stu-id="74445-134">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="74445-135">Os cmdlets a seguir são fornecidos pelo Windows PowerShell para gerenciar trabalhos em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="74445-135">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="74445-136">Get-Job</span><span class="sxs-lookup"><span data-stu-id="74445-136">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="74445-137">Obtém trabalhos em segundo plano do Windows PowerShell que estão em execução na sessão atual.</span><span class="sxs-lookup"><span data-stu-id="74445-137">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="74445-138">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="74445-138">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="74445-139">Obtém os resultados dos trabalhos de plano de fundo do Windows PowerShell na sessão atual.</span><span class="sxs-lookup"><span data-stu-id="74445-139">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="74445-140">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="74445-140">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="74445-141">Exclui um trabalho em plano de fundo do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="74445-141">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="74445-142">Start-Job</span><span class="sxs-lookup"><span data-stu-id="74445-142">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="74445-143">Inicia um trabalho em segundo plano do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="74445-143">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="74445-144">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="74445-144">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="74445-145">Interrompe um trabalho em plano de fundo do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="74445-145">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="74445-146">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="74445-146">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="74445-147">Suprime o prompt de comando até que um ou todos os trabalhos em segundo plano do Windows PowerShell executados na sessão sejam concluídos.</span><span class="sxs-lookup"><span data-stu-id="74445-147">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="74445-148">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="74445-148">See Also</span></span>

<span data-ttu-id="74445-149">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="74445-149">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
