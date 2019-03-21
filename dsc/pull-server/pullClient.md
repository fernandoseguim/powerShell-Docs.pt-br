---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Configurando um cliente de pull de DSC
ms.openlocfilehash: 54c68ac26e5388260e252ce01418170e26ddecde
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58054247"
---
# <a name="setting-up-a-dsc-pull-client"></a>Configurando um cliente de pull de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> O Servidor de Recepção (Recurso do Windows *Serviço DSC*) é um componente compatível com o Windows Server, no entanto, não há planos de oferecer novos recursos ou funcionalidades. É recomendável começar a fazer a transição dos clientes gerenciados para o [DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started) (inclui recursos além do Servidor de Recepção no Windows Server) ou para uma das soluções da comunidade listadas [aqui](pullserver.md#community-solutions-for-pull-service).

Cada nó de destino deve ser instruído a usar o modo de pull e receber a URL ou local do arquivo em que possa contatar o servidor de pull para obter as configurações e recursos e para onde deve enviar os dados de relatório.

Os tópicos a seguir explicam como configurar clientes de pull:

* [Configurando um cliente de pull usando nomes de configuração](pullClientConfigNames.md)
* [Configurando um cliente de pull usando uma ID de configuração](pullClientConfigID.md)

> [!NOTE]
> Estes tópicos se aplicam ao PowerShell 5.0. Para configurar um cliente de pull no PowerShell 4.0, consulte [Configurando um cliente de pull usando uma ID de configuração no PowerShell 4.0](pullClientConfigID4.md).