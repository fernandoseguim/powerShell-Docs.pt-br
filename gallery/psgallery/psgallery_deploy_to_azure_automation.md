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
<a name="deploy-to-azure-automation"></a>Implantar na Automação do Azure
===========================

O botão Implantar na Automação do Azure na página de detalhes do item implantará o item da Galeria do PowerShell para a Automação do Azure.

![Botão Implantar na Automação do Azure](Images/DeployToAzureAutomationButton.png)

Quando acionado, ele redirecionará você para o Portal de Gerenciamento do Azure, em que você entra usando as credenciais de sua conta do Azure.
Se o item incluir dependências, todas as dependências serão implantadas também na Automação do Azure.

AVISO: se o mesmo item e a versão já existirem na sua conta de Automação, implantá-lo novamente da Galeria PowerShell substituirá o item na sua conta de Automação.

Se você implantar um módulo, ele será exibido na seção Módulos da Automação do Azure.  Se você implantar um script, ele será exibido na seção Runbooks da Automação do Azure.

O botão Implantar na Automação do Azure pode ser desabilitado adicionando a marca AzureAutomationNotSupported aos metadados do item.

Para saber mais sobre a Automação do Azure, consulte o site da Automação do Azure [Site da Automação do Azure](http://azure.microsoft.com/en-us/services/automation/).

