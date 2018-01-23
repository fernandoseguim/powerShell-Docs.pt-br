---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Configurando um cliente de pull de DSC
ms.openlocfilehash: 98a67b8d27eeb445bb70f75253ca31e12207d5bd
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="cba3b-103">Configurando um cliente de pull de DSC</span><span class="sxs-lookup"><span data-stu-id="cba3b-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="cba3b-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="cba3b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="cba3b-105">Cada nó de destino deve ser instruído a usar o modo de pull e receber a URL ou local do arquivo em que possa contatar o servidor de pull para obter as configurações e recursos e para onde deve enviar os dados de relatório.</span><span class="sxs-lookup"><span data-stu-id="cba3b-105">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>


<span data-ttu-id="cba3b-106">Os tópicos a seguir explicam como configurar clientes de pull:</span><span class="sxs-lookup"><span data-stu-id="cba3b-106">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="cba3b-107">Configurando um cliente de pull usando nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="cba3b-107">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="cba3b-108">Configurando um cliente de pull usando uma ID de configuração</span><span class="sxs-lookup"><span data-stu-id="cba3b-108">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="cba3b-109">**Observação**: estes tópicos se aplicam ao PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="cba3b-109">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="cba3b-110">Para configurar um cliente de pull no PowerShell 4.0, consulte [Configurando um cliente de pull usando uma ID de configuração no PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="cba3b-110">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>

