---
ms.date: 2017-10-16
author: eslesar;mgreenegit
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Aplicando configurações"
ms.openlocfilehash: f9f8889439e43d540b50b68ef13e8e088b8cadd3
ms.sourcegitcommit: 9a5da3f739b1eebb81ede58bd4fc8037bad87224
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2017
---
# <a name="enacting-configurations"></a>Aplicando configurações

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Há duas maneiras de aplicar configurações da Configuração de Estado Desejado (DSC) do PowerShell: modo de push e modo de pull.

## <a name="push-mode"></a>Modo de push

![Modo de push](images/pushModel.png "Como funciona o modo de push")

O modo de push se refere a um usuário aplicando ativamente uma configuração a um nó de destino chamando o cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx).

Depois de criar e compilar uma configuração, você pode aplicá-la no modo de push chamando o cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), definindo o parâmetro -Path do cmdlet para o caminho em que se encontra o MOF de configuração.
Por exemplo, se o MOF da configuração estiver localizado em `C:\DSC\Configurations\localhost.mof`, você o aplicaria no computador local com o seguinte comando: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __Observação__: por padrão, a DSC executa uma configuração como um trabalho em segundo plano. Para executar a configuração interativamente, chame o [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) com o parâmetro __-Wait__.

## <a name="pull-mode"></a>Modo de pull

![Modo de pull](images/pullModel.png "Como funciona o modo de pull")

No modo de pull, os clientes de pull são configurados para obter suas configurações de estado desejado de um serviço de pull remoto.
Da mesma forma, o serviço de pull foi configurado para hospedar o serviço de DSC e recebeu as configurações e os recursos necessários para os clientes de pull.
Cada um dos clientes de pull tem um evento agendado que executa uma verificação periódica de conformidade na configuração do nó.
Quando o evento é disparado pela primeira vez, o LCM (Gerenciador de Configurações Local) no cliente de pull faz uma solicitação ao serviço de pull para obter a configuração especificada no LCM.
Se essa configuração existir no serviço de pull e passar nas verificações iniciais de validação, ela será baixada para o cliente de pull, no qual será executada pelo LCM.

O LCM verifica se o cliente está em conformidade com a configuração em intervalos regulares, especificados pela propriedade **ConfigurationModeFrequencyMins** do LCM.
O LCM verifica configurações atualizadas no serviço de pull em intervalos regulares, especificados pela propriedade **RefreshModeFrequency** do LCM.
Para saber mais sobre como configurar o LCM, veja [Configurando o Gerenciador de Configurações Local](metaConfig.md).

A solução recomendada para hospedar um Serviço de Pull é o serviço de nuvem do DSC, [Automação do Azure](https://azure.microsoft.com/en-us/services/automation/).
Essa solução hospedada fornece gerenciamento gráfico, relatórios e administração centralizada.

Para saber mais sobre a configuração de um Serviço de Pull no Windows Server, confira [Configuração de um servidor de pull da Web de DSC](pullServer.md).
Entenda, no entanto, que essa implementação tem recursos limitados e exige alguma integração "por conta própria".

Os tópicos a seguir explicam o serviço de pull e os clientes:

- [Visão geral do DSC de Automação do Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [Configurando um servidor de pull da Web e SMB](pullServerSMB.md)
- [Configurando um cliente de pull](pullClientConfigID.md)
