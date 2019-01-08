---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Chave do Registro de DSCAutomationHostEnabled
ms.openlocfilehash: 38e3189323c39a522b2ccad89f5cfcadf5e45616
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400125"
---
><span data-ttu-id="200a5-103">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="200a5-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="200a5-104">Chave do Registro de DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="200a5-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="200a5-105">O DSC usa a chave do Registro **DSCAutomationHostEnabled** em **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** para habilitar a configuração do computador na inicialização inicial.</span><span class="sxs-lookup"><span data-stu-id="200a5-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="200a5-106">O DSCAutomationHostEnabled dá suporte a três modos:</span><span class="sxs-lookup"><span data-stu-id="200a5-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="200a5-107">O valor de DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="200a5-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="200a5-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="200a5-108">Description</span></span>   |
|---|---|
<span data-ttu-id="200a5-109">0</span><span class="sxs-lookup"><span data-stu-id="200a5-109">0</span></span> | <span data-ttu-id="200a5-110">Desabilite a configuração do computador na inicialização.</span><span class="sxs-lookup"><span data-stu-id="200a5-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="200a5-111">1</span><span class="sxs-lookup"><span data-stu-id="200a5-111">1</span></span> | <span data-ttu-id="200a5-112">Habilite a configuração do computador na inicialização.</span><span class="sxs-lookup"><span data-stu-id="200a5-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="200a5-113">2</span><span class="sxs-lookup"><span data-stu-id="200a5-113">2</span></span> | <span data-ttu-id="200a5-114">Habilite a configuração do computador somente se o DSC estiver no estado atual ou pendente.</span><span class="sxs-lookup"><span data-stu-id="200a5-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="200a5-115">Este é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="200a5-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="200a5-116">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="200a5-116">See Also</span></span>

<span data-ttu-id="200a5-117">Para obter um exemplo de como usar esse recurso para executar as configurações na inicialização inicial, veja [Configurar uma máquina virtual na inicialização inicial usando a DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="200a5-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>