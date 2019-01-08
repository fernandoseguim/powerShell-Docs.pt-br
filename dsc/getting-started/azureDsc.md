---
ms.date: 03/15/2018
keywords: DSC,powershell,configuração,instalação
title: Usando a DSC no Microsoft Azure
ms.openlocfilehash: 54a317a415ff12c3d270897f414cba88716f0728
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400106"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="e0969-103">Usando a DSC no Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="e0969-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="e0969-104">A Configuração de Estado Desejado (DSC) tem suporte no Microsoft Azure por meio do [manipulador de extensões da Configuração de Estado Desejado do Azure](/azure/virtual-machines/extensions/dsc-overview) e da [DSC de Automação do Azure](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="e0969-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="e0969-105">Manipulador de extensões da Configuração de Estado Desejado do Azure</span><span class="sxs-lookup"><span data-stu-id="e0969-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="e0969-106">A extensão DSC do Azure permite que as VMs hospedadas no Microsoft Azure sejam gerenciadas com a DSC.</span><span class="sxs-lookup"><span data-stu-id="e0969-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span>
<span data-ttu-id="e0969-107">Para obter mais informações, consulte estes tópicos:</span><span class="sxs-lookup"><span data-stu-id="e0969-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="e0969-108">Manipulador de extensões da Configuração de Estado Desejado do Azure</span><span class="sxs-lookup"><span data-stu-id="e0969-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="e0969-109">Windows VMSS e Configuração de Estado Desejado com modelos do Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="e0969-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="e0969-110">Transmissão de credenciais para o manipulador de extensões da DSC do Azure</span><span class="sxs-lookup"><span data-stu-id="e0969-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="e0969-111">Histórico de extensões da Desired State Configuration do Azure</span><span class="sxs-lookup"><span data-stu-id="e0969-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="e0969-112">DSC de Automação do Azure</span><span class="sxs-lookup"><span data-stu-id="e0969-112">Azure Automation DSC</span></span>

<span data-ttu-id="e0969-113">O [serviço de Automação do Azure](https://azure.microsoft.com/en-us/services/automation/) permite que você gerencie configurações, recursos e nós gerenciados da DSC de dentro do Azure.</span><span class="sxs-lookup"><span data-stu-id="e0969-113">The [Azure Automation service](https://azure.microsoft.com/en-us/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="e0969-114">Para obter mais informações, consulte estes tópicos:</span><span class="sxs-lookup"><span data-stu-id="e0969-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="e0969-115">DSC de Automação do Azure</span><span class="sxs-lookup"><span data-stu-id="e0969-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="e0969-116">Introdução à DSC de Automação do Azure</span><span class="sxs-lookup"><span data-stu-id="e0969-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="e0969-117">Integração de computadores para o gerenciamento pelo DSC de Automação do Azure</span><span class="sxs-lookup"><span data-stu-id="e0969-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)