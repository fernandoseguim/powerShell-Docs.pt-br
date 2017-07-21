---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 91f48fb43d7fb099e34ce5d3b3b632e3cb119d64
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a name="deploy-to-azure-automation"></a><span data-ttu-id="30493-103">Implantar na Automação do Azure</span><span class="sxs-lookup"><span data-stu-id="30493-103">Deploy to Azure Automation</span></span>
===========================

<span data-ttu-id="30493-104">O botão Implantar na Automação do Azure na página de detalhes do item implantará o item da Galeria do PowerShell para a Automação do Azure.</span><span class="sxs-lookup"><span data-stu-id="30493-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Botão Implantar na Automação do Azure](Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="30493-106">Quando acionado, ele redirecionará você para o Portal de Gerenciamento do Azure, em que você entra usando as credenciais de sua conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="30493-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="30493-107">Se o item incluir dependências, todas as dependências serão implantadas também na Automação do Azure.</span><span class="sxs-lookup"><span data-stu-id="30493-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

<span data-ttu-id="30493-108">AVISO: se o mesmo item e a versão já existirem na sua conta de Automação, implantá-lo novamente da Galeria PowerShell substituirá o item na sua conta de Automação.</span><span class="sxs-lookup"><span data-stu-id="30493-108">WARNING:  If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="30493-109">Se você implantar um módulo, ele será exibido na seção Módulos da Automação do Azure.</span><span class="sxs-lookup"><span data-stu-id="30493-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="30493-110">Se você implantar um script, ele será exibido na seção Runbooks da Automação do Azure.</span><span class="sxs-lookup"><span data-stu-id="30493-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="30493-111">O botão Implantar na Automação do Azure pode ser desabilitado adicionando a marca AzureAutomationNotSupported aos metadados do item.</span><span class="sxs-lookup"><span data-stu-id="30493-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

<span data-ttu-id="30493-112">Para saber mais sobre a Automação do Azure, consulte o site da Automação do Azure [Site da Automação do Azure](http://azure.microsoft.com/en-us/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="30493-112">To learn more about Azure Automation, see the Azure Automation website [Azure Automation website](http://azure.microsoft.com/en-us/services/automation/).</span></span>

