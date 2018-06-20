---
ms.date: 10/16/2017
keywords: DSC,powershell,configuração,instalação
title: Aplicando configurações
ms.openlocfilehash: 3d938d14a4da645bbea7ba30ab41e0af72c4b94e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188457"
---
# <a name="enacting-configurations"></a><span data-ttu-id="e64ff-103">Aplicando configurações</span><span class="sxs-lookup"><span data-stu-id="e64ff-103">Enacting configurations</span></span>

><span data-ttu-id="e64ff-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e64ff-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e64ff-105">Há duas maneiras de aplicar configurações da Configuração de Estado Desejado (DSC) do PowerShell: modo de push e modo de pull.</span><span class="sxs-lookup"><span data-stu-id="e64ff-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="e64ff-106">Modo de push</span><span class="sxs-lookup"><span data-stu-id="e64ff-106">Push mode</span></span>

<span data-ttu-id="e64ff-107">![Modo de push](images/pushModel.png "Como funciona o modo de push")</span><span class="sxs-lookup"><span data-stu-id="e64ff-107">![Push mode](images/pushModel.png "How push mode works")</span></span>

<span data-ttu-id="e64ff-108">O modo de push se refere a um usuário aplicando ativamente uma configuração a um nó de destino chamando o cmdlet [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx).</span><span class="sxs-lookup"><span data-stu-id="e64ff-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet.</span></span>

<span data-ttu-id="e64ff-109">Depois de criar e compilar uma configuração, você pode aplicá-la no modo de push chamando o cmdlet [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx), definindo o parâmetro -Path do cmdlet para o caminho em que se encontra o MOF de configuração.</span><span class="sxs-lookup"><span data-stu-id="e64ff-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span>
<span data-ttu-id="e64ff-110">Por exemplo, se o MOF da configuração estiver localizado em `C:\DSC\Configurations\localhost.mof`, você o aplicaria no computador local com o seguinte comando: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="e64ff-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="e64ff-111">__Observação__: por padrão, a DSC executa uma configuração como um trabalho em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="e64ff-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="e64ff-112">Para executar a configuração interativamente, chame o [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) com o parâmetro __-Wait__.</span><span class="sxs-lookup"><span data-stu-id="e64ff-112">To run the configuration interactively, call the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) with the __-Wait__ parameter.</span></span>

## <a name="pull-mode"></a><span data-ttu-id="e64ff-113">Modo de pull</span><span class="sxs-lookup"><span data-stu-id="e64ff-113">Pull mode</span></span>

<span data-ttu-id="e64ff-114">![Modo de pull](images/pullModel.png "Como funciona o modo de pull")</span><span class="sxs-lookup"><span data-stu-id="e64ff-114">![Pull Mode](images/pullModel.png "How pull mode works")</span></span>

<span data-ttu-id="e64ff-115">No modo de pull, os clientes de pull são configurados para obter suas configurações de estado desejado de um serviço de pull remoto.</span><span class="sxs-lookup"><span data-stu-id="e64ff-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull service.</span></span>
<span data-ttu-id="e64ff-116">Da mesma forma, o serviço de pull foi configurado para hospedar o serviço de DSC e recebeu as configurações e os recursos necessários para os clientes de pull.</span><span class="sxs-lookup"><span data-stu-id="e64ff-116">Likewise, the pull service has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span>
<span data-ttu-id="e64ff-117">Cada um dos clientes de pull tem um evento agendado que executa uma verificação periódica de conformidade na configuração do nó.</span><span class="sxs-lookup"><span data-stu-id="e64ff-117">Each of the pull clients has a scheduled event that performs a periodic compliance check on the configuration of the node.</span></span>
<span data-ttu-id="e64ff-118">Quando o evento é disparado pela primeira vez, o LCM (Gerenciador de Configurações Local) no cliente de pull faz uma solicitação ao serviço de pull para obter a configuração especificada no LCM.</span><span class="sxs-lookup"><span data-stu-id="e64ff-118">When the event is triggered the first time, the Local Configuration Manager (LCM) on the pull client makes a request to the pull service to get the configuration specified in the LCM.</span></span>
<span data-ttu-id="e64ff-119">Se essa configuração existir no serviço de pull e passar nas verificações iniciais de validação, ela será baixada para o cliente de pull, no qual será executada pelo LCM.</span><span class="sxs-lookup"><span data-stu-id="e64ff-119">If that configuration exists on the pull service, and it passes initial validation checks, the configuration is downloaded to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="e64ff-120">O LCM verifica se o cliente está em conformidade com a configuração em intervalos regulares, especificados pela propriedade **ConfigurationModeFrequencyMins** do LCM.</span><span class="sxs-lookup"><span data-stu-id="e64ff-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span>
<span data-ttu-id="e64ff-121">O LCM verifica configurações atualizadas no serviço de pull em intervalos regulares, especificados pela propriedade **RefreshModeFrequency** do LCM.</span><span class="sxs-lookup"><span data-stu-id="e64ff-121">The LCM checks for updated configurations on the pull service at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span>
<span data-ttu-id="e64ff-122">Para saber mais sobre como configurar o LCM, veja [Configurando o Gerenciador de Configurações Local](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="e64ff-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

<span data-ttu-id="e64ff-123">A solução recomendada para hospedar um Serviço de Pull é o serviço de nuvem do DSC, [Automação do Azure](https://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="e64ff-123">The recommended solution for hosting a Pull Service, is the DSC cloud service, [Azure Automation](https://azure.microsoft.com/services/automation/).</span></span>
<span data-ttu-id="e64ff-124">Essa solução hospedada fornece gerenciamento gráfico, relatórios e administração centralizada.</span><span class="sxs-lookup"><span data-stu-id="e64ff-124">This is hosted solution provides graphical management, reporting, and centralized administration.</span></span>

<span data-ttu-id="e64ff-125">Para saber mais sobre a configuração de um Serviço de Pull no Windows Server, confira [Configuração de um servidor de pull da Web de DSC](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="e64ff-125">For more information on setting up a Pull Service on Windows Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>
<span data-ttu-id="e64ff-126">Entenda, no entanto, que essa implementação tem recursos limitados e exige alguma integração "por conta própria".</span><span class="sxs-lookup"><span data-stu-id="e64ff-126">Understand however, that this implementation has limited features and does require some "do it yourself" integration.</span></span>

<span data-ttu-id="e64ff-127">Os tópicos a seguir explicam o serviço de pull e os clientes:</span><span class="sxs-lookup"><span data-stu-id="e64ff-127">The following topics explain pull service and clients:</span></span>

- [<span data-ttu-id="e64ff-128">Visão geral do DSC de Automação do Azure</span><span class="sxs-lookup"><span data-stu-id="e64ff-128">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="e64ff-129">Configurando um servidor de pull da Web e SMB</span><span class="sxs-lookup"><span data-stu-id="e64ff-129">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="e64ff-130">Configurando um cliente de pull</span><span class="sxs-lookup"><span data-stu-id="e64ff-130">Configuring a pull client</span></span>](pullClientConfigID.md)