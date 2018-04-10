---
ms.date: 03/15/2018
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Usando a DSC no Microsoft Azure
ms.openlocfilehash: 5b0d577e1fecdeac38c2c5f8e955a2d23b1eb707
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="using-dsc-on-microsoft-azure"></a>Usando a DSC no Microsoft Azure

A Configuração de Estado Desejado (DSC) tem suporte no Microsoft Azure por meio do [manipulador de extensões da Configuração de Estado Desejado do Azure](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) e da [DSC de Automação do Azure](/azure/automation/automation-dsc-overview).

## <a name="azure-desired-state-configuration-extension-handler"></a>Manipulador de extensões da Configuração de Estado Desejado do Azure

A extensão DSC do Azure permite que as VMs hospedadas no Microsoft Azure sejam gerenciadas com a DSC.
Para obter mais informações, consulte estes tópicos:

- [Manipulador de extensões da Configuração de Estado Desejado do Azure](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview)
- [Windows VMSS e Configuração de Estado Desejado com modelos do Azure Resource Manager](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-template)
- [Transmissão de credenciais para o manipulador de extensões da DSC do Azure](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-credentials)
- [Histórico de extensões da Desired State Configuration do Azure](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a>DSC de Automação do Azure

O [serviço de Automação do Azure](https://azure.microsoft.com/services/automation/) permite que você gerencie configurações, recursos e nós gerenciados da DSC de dentro do Azure. Para obter mais informações, consulte estes tópicos:

- [DSC de Automação do Azure](/azure/automation/automation-dsc-overview)
- [Introdução à DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started)
- [Integração de computadores para o gerenciamento pelo DSC de Automação do Azure](/azure/automation/automation-dsc-onboarding)