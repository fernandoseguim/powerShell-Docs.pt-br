---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Implantar na Automação do Azure
ms.openlocfilehash: ced67809387a85e089259edf6b091d68e58ba6a7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="49605-103">Implantar na Automação do Azure</span><span class="sxs-lookup"><span data-stu-id="49605-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="49605-104">O botão Implantar na Automação do Azure na página de detalhes do item implantará o item da Galeria do PowerShell para a Automação do Azure.</span><span class="sxs-lookup"><span data-stu-id="49605-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Botão Implantar na Automação do Azure](../../Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="49605-106">Quando acionado, ele redirecionará você para o Portal de Gerenciamento do Azure, em que você entra usando as credenciais de sua conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="49605-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="49605-107">Se o item incluir dependências, todas as dependências serão implantadas também na Automação do Azure.</span><span class="sxs-lookup"><span data-stu-id="49605-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="49605-108">Se o mesmo item com a mesma versão já existir na sua conta de Automação, implantá-lo novamente por meio da Galeria do PowerShell substituirá o item na conta de Automação.</span><span class="sxs-lookup"><span data-stu-id="49605-108">If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="49605-109">Se você implantar um módulo, ele será exibido na seção Módulos da Automação do Azure.</span><span class="sxs-lookup"><span data-stu-id="49605-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="49605-110">Se você implantar um script, ele será exibido na seção Runbooks da Automação do Azure.</span><span class="sxs-lookup"><span data-stu-id="49605-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="49605-111">O botão Implantar na Automação do Azure pode ser desabilitado adicionando a marca AzureAutomationNotSupported aos metadados do item.</span><span class="sxs-lookup"><span data-stu-id="49605-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="49605-112">Exigir a aceitação da licença ao implantar na Automação do Azure</span><span class="sxs-lookup"><span data-stu-id="49605-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="49605-113">Se o módulo que está sendo implantado na Automação do Azure exigir a aceitação da licença, a interface do usuário do portal exibirá um aviso de isenção informando que "Esse módulo exige a aceitação da licença.</span><span class="sxs-lookup"><span data-stu-id="49605-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="49605-114">Ao clicar em OK, você aceita os termos da licença."</span><span class="sxs-lookup"><span data-stu-id="49605-114">By clicking OK, you are accepting license terms.'</span></span>

![A implantação na Automação do Azure exige a aceitação da licença](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="49605-116">Mais detalhes</span><span class="sxs-lookup"><span data-stu-id="49605-116">More details</span></span>

- [<span data-ttu-id="49605-117">Exigir a aceitação da licença no PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="49605-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="49605-118">Exigir a aceitação da licença na Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="49605-118">Require License Acceptance in PowerShell Gallery</span></span>](items-that-require-license-acceptance.md)
- [<span data-ttu-id="49605-119">Site da Automação do Azure</span><span class="sxs-lookup"><span data-stu-id="49605-119">Azure Automation website</span></span>](http://azure.microsoft.com/services/automation/)