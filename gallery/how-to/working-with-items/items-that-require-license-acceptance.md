---
ms.date: 06/12/2017
contributor: Farehar
ms.topic: conceptual
keywords: galeria, powershell, psgallery
title: Exigir a aceitação da licença
ms.openlocfilehash: 76f16e848e1cd660e062bf8569fb914b32f14934
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="require-license-acceptance"></a>Exigir a aceitação da licença

O texto Exigir a Aceitação da Licença aparece na página de detalhes do item para módulos que exigem a aceitação da licença. A licença para o módulo pode ser exibida clicando no link 'Exibir Licença.txt'.

![Exigir a Aceitação da Licença](../../Images/RequireLicenseAcceptance.png)

Usuários receberão uma solicitação para aceitar a licença ao instalar, salvar ou atualizar o módulo por meio do PowerShellGet ou ao implantar a Automação do Azure.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Exigir a aceitação da licença ao implantar na Automação do Azure

Se o módulo que está sendo implantado na Automação do Azure exigir a aceitação da licença, a interface do usuário do portal exibirá um aviso de isenção informando que "Esse módulo exige a aceitação da licença. Ao clicar em OK, você aceita os termos da licença."

![A implantação na Automação do Azure exige a aceitação da licença](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Mais detalhes

[Exigir a aceitação da licença no PowerShellGet](../../concepts/module-license-acceptance.md)
[Site da Automação do Azure](/azure/automation)