---
ms.date: 2017-06-12T00:00:00.000Z
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Aplicando configurações"
ms.openlocfilehash: db3a999f3e413ebb88e79f5ec04a7449db543030
ms.sourcegitcommit: 46feddbc753523f464f139b5d272794620072fc8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/02/2017
---
# <a name="enacting-configurations"></a>Aplicando configurações

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Há duas maneiras de aplicar configurações da Configuração de Estado Desejado (DSC) do PowerShell: modo de push e modo de pull.

## <a name="push-mode"></a>Modo de push

![Modo de push](images/Push.png "Como funciona o modo de push")

O modo de push se refere a um usuário aplicando ativamente uma configuração a um nó de destino chamando o cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx).

Depois de criar e compilar uma configuração, você pode aplicá-la no modo de push chamando o cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), definindo o parâmetro -Path do cmdlet para o caminho em que se encontra o MOF de configuração. Por exemplo, se o MOF da configuração estiver localizado em `C:\DSC\Configurations\localhost.mof`, você o aplicaria no computador local com o seguinte comando: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __Observação__: por padrão, a DSC executa uma configuração como um trabalho em segundo plano. Para executar a configuração interativamente, chame o [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) com o parâmetro __-Wait__.


## <a name="pull-mode"></a>Modo de pull

![Modo de pull](images/Pull.png "Como funciona o modo de pull")

No modo de pull, os clientes de pull são configurados para obter suas configurações de estado desejado de um servidor remoto de pull. Da mesma forma, o servidor de pull foi configurado para hospedar o serviço de DSC e recebeu as configurações e os recursos necessários para os clientes de pull. Cada um dos clientes de pull tem uma tarefa agendada que executa uma verificação periódica de conformidade na configuração do nó. Quando o evento é disparado pela primeira vez, o LCM (Gerenciador de Configurações Local) no cliente de pull faz uma solicitação ao servidor de pull para obter a configuração especificada no LCM. Se essa configuração existir no servidor de pull e passar nas verificações iniciais de validação, ela será transmitida para o cliente pull, no qual será executada pelo LCM.

O LCM verifica se o cliente está em conformidade com a configuração em intervalos regulares, especificados pela propriedade **ConfigurationModeFrequencyMins** do LCM. O LCM verifica configurações atualizadas no servidor de pull em intervalos regulares, especificados pela propriedade **RefreshModeFrequency** do LCM. Para saber mais sobre como configurar o LCM, veja [Configurando o Gerenciador de Configurações Local](metaConfig.md).

Para saber mais sobre a configuração de um Servidor de Pull de DSC, veja [Configurando um servidor de pull da Web de DSC](pullServer.md).

Se preferir tirar proveito de um serviço online para hospedar a funcionalidade de Servidor de Pull, consulte o serviço de [DSC de Automação do Azure](https://azure.microsoft.com/en-us/documentation/articles/automation-dsc-overview/).

Os tópicos a seguir explicam como configurar clientes e servidores de pull:

- [Configurando um servidor de pull da Web](pullServer.md)
- [Configurando um servidor de pull da Web e SMB](pullServerSMB.md)
- [Configurando um cliente de pull](pullClientConfigID.md)

