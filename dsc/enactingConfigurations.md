---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Aplicando configurações"
ms.openlocfilehash: db82788650186eb82f67b30b24cd45b719bbe314
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="enacting-configurations"></a><span data-ttu-id="72ac4-103">Aplicando configurações</span><span class="sxs-lookup"><span data-stu-id="72ac4-103">Enacting configurations</span></span>

><span data-ttu-id="72ac4-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="72ac4-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="72ac4-105">Há duas maneiras de aplicar configurações da Configuração de Estado Desejado (DSC) do PowerShell: modo de push e modo de pull.</span><span class="sxs-lookup"><span data-stu-id="72ac4-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="72ac4-106">Modo de push</span><span class="sxs-lookup"><span data-stu-id="72ac4-106">Push mode</span></span>

<span data-ttu-id="72ac4-107">![Modo de push](images/Push.png "Como funciona o modo de push")</span><span class="sxs-lookup"><span data-stu-id="72ac4-107">![Push mode](images/Push.png "How push mode works")</span></span>

<span data-ttu-id="72ac4-108">O modo de push se refere a um usuário aplicando ativamente uma configuração a um nó de destino chamando o cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx).</span><span class="sxs-lookup"><span data-stu-id="72ac4-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span>

<span data-ttu-id="72ac4-109">Depois de criar e compilar uma configuração, você pode aplicá-la no modo de push chamando o cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), definindo o parâmetro -Path do cmdlet para o caminho em que se encontra o MOF de configuração.</span><span class="sxs-lookup"><span data-stu-id="72ac4-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span> <span data-ttu-id="72ac4-110">Por exemplo, se o MOF da configuração estiver localizado em `C:\DSC\Configurations\localhost.mof`, você o aplicaria no computador local com o seguinte comando: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="72ac4-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="72ac4-111">__Observação__: por padrão, a DSC executa uma configuração como um trabalho em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="72ac4-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="72ac4-112">Para executar a configuração interativamente, chame o [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) com o parâmetro __-Wait__.</span><span class="sxs-lookup"><span data-stu-id="72ac4-112">To run the configuration interactively, call the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) with the __-Wait__ parameter.</span></span>


## <a name="pull-mode"></a><span data-ttu-id="72ac4-113">Modo de pull</span><span class="sxs-lookup"><span data-stu-id="72ac4-113">Pull mode</span></span>

<span data-ttu-id="72ac4-114">![Modo de pull](images/Pull.png "Como funciona o modo de pull")</span><span class="sxs-lookup"><span data-stu-id="72ac4-114">![Pull Mode](images/Pull.png "How pull mode works")</span></span>

<span data-ttu-id="72ac4-115">No modo de pull, os clientes de pull são configurados para obter suas configurações de estado desejado de um servidor remoto de pull.</span><span class="sxs-lookup"><span data-stu-id="72ac4-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull server.</span></span> <span data-ttu-id="72ac4-116">Da mesma forma, o servidor de pull foi configurado para hospedar o serviço de DSC e recebeu as configurações e os recursos necessários para os clientes de pull.</span><span class="sxs-lookup"><span data-stu-id="72ac4-116">Likewise, the pull server has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span> <span data-ttu-id="72ac4-117">Cada um dos clientes de pull tem uma tarefa agendada que executa uma verificação periódica de conformidade na configuração do nó.</span><span class="sxs-lookup"><span data-stu-id="72ac4-117">Each one of the pull clients has a scheduled task that performs a periodic compliance check on the configuration of the node.</span></span> <span data-ttu-id="72ac4-118">Quando o evento é disparado na primeira vez, faz com que o Gerenciador de Configurações Local (LCM) no cliente de pull faça uma solicitação ao servidor de pull para especificar a configuração no LCM.</span><span class="sxs-lookup"><span data-stu-id="72ac4-118">When the event is triggered the first time, it the Local Configuration Manager (LCM) on the pull client makes a request to the pull server to get the configuration specified in the LCM.</span></span> <span data-ttu-id="72ac4-119">Se essa configuração existir no servidor de pull e passar nas verificações iniciais de validação, ela será transmitida para o cliente pull, no qual será executada pelo LCM.</span><span class="sxs-lookup"><span data-stu-id="72ac4-119">If that configuration exists on the pull server, and it passes initial validation checks, the configuration is transmitted to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="72ac4-120">O LCM verifica se o cliente está em conformidade com a configuração em intervalos regulares, especificados pela propriedade **ConfigurationModeFrequencyMins** do LCM.</span><span class="sxs-lookup"><span data-stu-id="72ac4-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="72ac4-121">O LCM verifica configurações atualizadas no servidor de pull em intervalos regulares, especificados pela propriedade **RefreshModeFrequency** do LCM.</span><span class="sxs-lookup"><span data-stu-id="72ac4-121">The LCM checks for updated configurations on the pull server at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span> <span data-ttu-id="72ac4-122">Para saber mais sobre como configurar o LCM, veja [Configurando o Gerenciador de Configurações Local](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="72ac4-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

<span data-ttu-id="72ac4-123">Para saber mais sobre a configuração de um Servidor de Pull de DSC, veja [Configurando um servidor de pull da Web de DSC](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="72ac4-123">For more information on setting up a DSC Pull Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>

<span data-ttu-id="72ac4-124">Se preferir tirar proveito de um serviço online para hospedar a funcionalidade de Servidor de Pull, consulte o serviço de [DSC de Automação do Azure](https://azure.microsoft.com/en-us/documentation/articles/automation-dsc-overview/).</span><span class="sxs-lookup"><span data-stu-id="72ac4-124">If you would prefer to take advantage of an online service to host Pull Server functionality, see the [Azure Automation DSC](https://azure.microsoft.com/en-us/documentation/articles/automation-dsc-overview/) service.</span></span>

<span data-ttu-id="72ac4-125">Os tópicos a seguir explicam como configurar clientes e servidores de pull:</span><span class="sxs-lookup"><span data-stu-id="72ac4-125">The following topics explain how to set up pull servers and clients:</span></span>

- [<span data-ttu-id="72ac4-126">Configurando um servidor de pull da Web</span><span class="sxs-lookup"><span data-stu-id="72ac4-126">Setting up a web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="72ac4-127">Configurando um servidor de pull da Web e SMB</span><span class="sxs-lookup"><span data-stu-id="72ac4-127">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="72ac4-128">Configurando um cliente de pull</span><span class="sxs-lookup"><span data-stu-id="72ac4-128">Configuring a pull client</span></span>](pullClientConfigID.md)

