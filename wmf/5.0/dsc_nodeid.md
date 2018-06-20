---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 6c036c2d8f97e559d20dd3ac40133fa06f5dab08
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188278"
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="be6f7-102">Separação de IDs de nó e de configuração</span><span class="sxs-lookup"><span data-stu-id="be6f7-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="be6f7-103">Visão geral</span><span class="sxs-lookup"><span data-stu-id="be6f7-103">Overview</span></span>

<span data-ttu-id="be6f7-104">Para proporcionar uma experiência mais flexível e simplificada ao usar o DSC no modo Pull, adicionamos uma série de recursos nesta versão.</span><span class="sxs-lookup"><span data-stu-id="be6f7-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="be6f7-105">Esses recursos destinam-se a permitir que você tenha a flexibilidade de configurar e implantar configurações em vários nós com facilidade, ao mesmo tempo que acompanha as informações de status e relatório de cada nó individualmente.</span><span class="sxs-lookup"><span data-stu-id="be6f7-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span>
<span data-ttu-id="be6f7-106">Esses recursos são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="be6f7-106">These features are as follows:</span></span>

* <span data-ttu-id="be6f7-107">Um nome de configuração que identifica a configuração de um computador.</span><span class="sxs-lookup"><span data-stu-id="be6f7-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="be6f7-108">Esse nome pode ser compartilhado por vários nós de destino</span><span class="sxs-lookup"><span data-stu-id="be6f7-108">This name can be shared by multiple target nodes</span></span>
* <span data-ttu-id="be6f7-109">Uma ID de agente que identifica exclusivamente um único nó</span><span class="sxs-lookup"><span data-stu-id="be6f7-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="be6f7-110">Uma etapa de registro que ocorre apenas na primeira vez em que um nó de destino se conecta a um servidor de recepção</span><span class="sxs-lookup"><span data-stu-id="be6f7-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="be6f7-111">**Observação:** esses recursos e funcionalidades foram adicionados e não substituem os conceitos e recursos existentes de pull.</span><span class="sxs-lookup"><span data-stu-id="be6f7-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="be6f7-112">É possível usar esses novos recursos ou os antigos com o novo servidor de recepção fornecido nesta versão.</span><span class="sxs-lookup"><span data-stu-id="be6f7-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="be6f7-113">Para obter mais informações, veja [Configurando um cliente de pull usando nomes de configuração](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span><span class="sxs-lookup"><span data-stu-id="be6f7-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>
