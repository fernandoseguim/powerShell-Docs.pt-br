---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Visão Geral da Configuração de Estado Desejado do Windows PowerShell
ms.openlocfilehash: c9069d7c9ce9c614330e36a42233b00363660a4b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187469"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a><span data-ttu-id="8f4be-103">Visão Geral da Configuração de Estado Desejado do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8f4be-103">Windows PowerShell Desired State Configuration Overview</span></span>

> <span data-ttu-id="8f4be-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8f4be-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="8f4be-105">A DSC é uma plataforma de gerenciamento no PowerShell que permite que você gerencie sua infraestrutura de desenvolvimento e TI com configuração como código.</span><span class="sxs-lookup"><span data-stu-id="8f4be-105">DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code.</span></span>

- <span data-ttu-id="8f4be-106">Para obter uma visão geral dos benefícios comerciais de usar a DSC, confira [Visão Geral da Configuração do Estado Desejado para Tomadores de Decisão](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="8f4be-106">For an overview of the business benefits of using DSC, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>
- <span data-ttu-id="8f4be-107">Para obter uma visão geral dos benefícios de engenharia ao usar a DSC, confira [Visão Geral da Configuração do Estado Desejado para Engenheiros](DscForEngineers.md).</span><span class="sxs-lookup"><span data-stu-id="8f4be-107">For an overview of the engineering benefits of using DSC, see [Desired State Configuration Overview for Engineers](DscForEngineers.md).</span></span>
- <span data-ttu-id="8f4be-108">Para começar a usar a DSC rapidamente, veja [Início rápido da DSC](quickStart.md).</span><span class="sxs-lookup"><span data-stu-id="8f4be-108">To start using DSC quickly, see [DSC quick start](quickStart.md).</span></span>

## <a name="key-concepts"></a><span data-ttu-id="8f4be-109">Conceitos Principais</span><span class="sxs-lookup"><span data-stu-id="8f4be-109">Key Concepts</span></span>

<span data-ttu-id="8f4be-110">A DSC é uma plataforma declarativa usada para configuração, implantação e gerenciamento de sistemas.</span><span class="sxs-lookup"><span data-stu-id="8f4be-110">DSC is a declarative platform used for configuration, deployment, and management of systems.</span></span> <span data-ttu-id="8f4be-111">Consiste em três componentes principais:</span><span class="sxs-lookup"><span data-stu-id="8f4be-111">It consists of three primary components:</span></span>

- <span data-ttu-id="8f4be-112">[Configurações](configurations.md) são scripts declarativos do PowerShell que definem e configuram instâncias de recursos.</span><span class="sxs-lookup"><span data-stu-id="8f4be-112">[Configurations](configurations.md) are declarative PowerShell scripts which define and configure instances of resources.</span></span>
    <span data-ttu-id="8f4be-113">Após executar a configuração, a DSC (e os recursos que estão sendo chamados pela configuração) vai simplesmente “realizar”, garantindo que o sistema exista no estado disposto pela configuração.</span><span class="sxs-lookup"><span data-stu-id="8f4be-113">Upon running the configuration, DSC (and the resources being called by the configuration) will simply “make it so”, ensuring that the system exists in the state laid out by the configuration.</span></span>
    <span data-ttu-id="8f4be-114">As configurações da DSC também são idempotentes: o Gerenciador de Configurações Local (LCM) continuará garantindo que os computadores sejam configurados no estado declarado pela configuração.</span><span class="sxs-lookup"><span data-stu-id="8f4be-114">DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.</span></span>
- <span data-ttu-id="8f4be-115">Os [recursos](resources.md) são a parte de "realização" da DSC.</span><span class="sxs-lookup"><span data-stu-id="8f4be-115">[Resources](resources.md) are the "make it so" part of DSC.</span></span> <span data-ttu-id="8f4be-116">Eles contêm o código que definem e mantêm o destino de uma configuração no estado especificado.</span><span class="sxs-lookup"><span data-stu-id="8f4be-116">They contain the code that put and keep the target of a configuration in the specified state.</span></span>
    <span data-ttu-id="8f4be-117">Os recursos residem dentro de módulos do PowerShell e podem ser escritos para modelar algo tão genérico quanto um arquivo ou um processo do Windows ou tão específico quanto um servidor IIS ou em uma VM em execução no Azure.</span><span class="sxs-lookup"><span data-stu-id="8f4be-117">Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.</span></span>
- <span data-ttu-id="8f4be-118">O [Gerenciador de Configurações Local (LCM)](metaConfig.md) é o mecanismo pelo qual a DSC facilita a interação entre recursos e configurações.</span><span class="sxs-lookup"><span data-stu-id="8f4be-118">The [Local Configuration Manager (LCM)](metaConfig.md) is the engine by which DSC facilitates the interaction between resources and configurations.</span></span>
    <span data-ttu-id="8f4be-119">Regularmente, o LCM sonda o sistema usando o fluxo de controle implementado pelos recursos para garantir que o estado definido por uma Configuração seja mantido.</span><span class="sxs-lookup"><span data-stu-id="8f4be-119">The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained.</span></span>
    <span data-ttu-id="8f4be-120">Se o sistema estiver sem estado, o LCM faz chamadas para o código nos recursos para “realizar”, de acordo com a configuração.</span><span class="sxs-lookup"><span data-stu-id="8f4be-120">If the system is out of state, the LCM makes calls to the code in resources to “make it so” according to the configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f4be-121">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="8f4be-121">See Also</span></span>

- [<span data-ttu-id="8f4be-122">Configurações DSC</span><span class="sxs-lookup"><span data-stu-id="8f4be-122">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="8f4be-123">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="8f4be-123">DSC Resources</span></span>](resources.md)
- [<span data-ttu-id="8f4be-124">Configurando o Gerenciador de Configurações Local</span><span class="sxs-lookup"><span data-stu-id="8f4be-124">Configuring The Local Configuration Manager</span></span>](metaConfig.md)