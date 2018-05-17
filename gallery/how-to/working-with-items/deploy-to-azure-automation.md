---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery
title: Implantar na Automação do Azure
ms.openlocfilehash: 1efdc289228d3a6962302d12ccf44143ce63a806
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="deploy-to-azure-automation"></a>Implantar na Automação do Azure

O botão Implantar na Automação do Azure na página de detalhes do item implantará o item da Galeria do PowerShell para a Automação do Azure.

![Botão Implantar na Automação do Azure](../../Images/DeployToAzureAutomationButton.png)

Quando acionado, ele redirecionará você para o Portal de Gerenciamento do Azure, em que você entra usando as credenciais de sua conta do Azure.
Se o item incluir dependências, todas as dependências serão implantadas também na Automação do Azure.

> [!WARNING]
> Se o mesmo item com a mesma versão já existir na sua conta de Automação, implantá-lo novamente por meio da Galeria do PowerShell substituirá o item na conta de Automação.

Se você implantar um módulo, ele será exibido na seção Módulos da Automação do Azure.  Se você implantar um script, ele será exibido na seção Runbooks da Automação do Azure.

O botão Implantar na Automação do Azure pode ser desabilitado adicionando a marca AzureAutomationNotSupported aos metadados do item.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Exigir a aceitação da licença ao implantar na Automação do Azure

Se o módulo que está sendo implantado na Automação do Azure exigir a aceitação da licença, a interface do usuário do portal exibirá um aviso de isenção informando que "Esse módulo exige a aceitação da licença. Ao clicar em OK, você aceita os termos da licença."

![A implantação na Automação do Azure exige a aceitação da licença](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Mais detalhes

- [Exigir a aceitação da licença no PowerShellGet](../../concepts/module-license-acceptance.md)
- [Exigir a aceitação da licença na Galeria do PowerShell](items-that-require-license-acceptance.md)
- [Site da Automação do Azure](http://azure.microsoft.com/services/automation/)
