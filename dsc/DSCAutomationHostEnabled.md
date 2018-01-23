---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Chave do Registro de DSCAutomationHostEnabled
ms.openlocfilehash: c58b7a8f2485ff02f09763749a3de8a75f882d19
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
><span data-ttu-id="da84f-103">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="da84f-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="da84f-104">Chave do Registro de DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="da84f-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="da84f-105">O DSC usa a chave do Registro **DSCAutomationHostEnabled** em **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** para habilitar a configuração do computador na inicialização inicial.</span><span class="sxs-lookup"><span data-stu-id="da84f-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="da84f-106">O DSCAutomationHostEnabled dá suporte a três modos:</span><span class="sxs-lookup"><span data-stu-id="da84f-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="da84f-107">O valor de DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="da84f-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="da84f-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="da84f-108">Description</span></span>   | 
|---|---| 
<span data-ttu-id="da84f-109">0</span><span class="sxs-lookup"><span data-stu-id="da84f-109">0</span></span> | <span data-ttu-id="da84f-110">Desabilite a configuração do computador na inicialização.</span><span class="sxs-lookup"><span data-stu-id="da84f-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="da84f-111">1</span><span class="sxs-lookup"><span data-stu-id="da84f-111">1</span></span> | <span data-ttu-id="da84f-112">Habilite a configuração do computador na inicialização.</span><span class="sxs-lookup"><span data-stu-id="da84f-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="da84f-113">2</span><span class="sxs-lookup"><span data-stu-id="da84f-113">2</span></span> | <span data-ttu-id="da84f-114">Habilite a configuração do computador somente se o DSC estiver no estado atual ou pendente.</span><span class="sxs-lookup"><span data-stu-id="da84f-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="da84f-115">Este é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="da84f-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="da84f-116">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="da84f-116">See Also</span></span>

<span data-ttu-id="da84f-117">Para obter um exemplo de como usar esse recurso para executar as configurações na inicialização inicial, veja [Configurar uma máquina virtual na inicialização inicial usando a DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="da84f-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>


