---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery
title: Removendo itens da lista
ms.openlocfilehash: 35dcd283ddace5aec62d692b0ede12ae0bada765
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="unlisting-items"></a><span data-ttu-id="2551e-103">Removendo itens da lista</span><span class="sxs-lookup"><span data-stu-id="2551e-103">Unlisting items</span></span>

<span data-ttu-id="2551e-104">**Por que a remoção de um item da Galeria do PowerShell não é exposta como uma opção?**</span><span class="sxs-lookup"><span data-stu-id="2551e-104">**Why is removing an item from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="2551e-105">A Galeria do PowerShell não dá suporte à exclusão permanente dos itens pelos usuários.</span><span class="sxs-lookup"><span data-stu-id="2551e-105">The PowerShell Gallery does not support users permanently deleting their items.</span></span>
<span data-ttu-id="2551e-106">Isso permite que outros usuários possam usar as dependências de seus itens sem se preocupar sobre possíveis interrupções no futuro.</span><span class="sxs-lookup"><span data-stu-id="2551e-106">This enables others to take dependencies on your items without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="2551e-107">Por exemplo, se o módulo do Pester depender do módulo do Azure e o módulo do Azure for removido da galeria, o usuário não poderá mais usar o módulo do Pester.</span><span class="sxs-lookup"><span data-stu-id="2551e-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="2551e-108">No entanto, em vez de remover um item, você poderá removê-lo da lista.</span><span class="sxs-lookup"><span data-stu-id="2551e-108">Instead of removing an item, however, you can unlist it instead.</span></span>

<span data-ttu-id="2551e-109">**Qual o resultado da remoção de um item da lista na Galeria do PowerShell?**</span><span class="sxs-lookup"><span data-stu-id="2551e-109">**What does unlisting an item on PowerShell Gallery do?**</span></span>

<span data-ttu-id="2551e-110">A remoção de um item da lista como um módulo ou script na Galeria do PowerShell o removerá da guia Itens. Além disso, os itens removidos da lista não serão detectáveis usando a barra de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2551e-110">Unlisting an item such as module or script on PowerShell Gallery will remove it from the Items tab. In addition, unlisted items will not be discoverable using the search bar.</span></span>
<span data-ttu-id="2551e-111">A única maneira de baixar um item removido da lista é especificar o nome exato e a versão do item.</span><span class="sxs-lookup"><span data-stu-id="2551e-111">The only way to download an unlisted item is to specify the exact name and version of the item.</span></span>
<span data-ttu-id="2551e-112">Por isso, a remoção de um item não interromperá outros módulos ou scripts que dependem dele.</span><span class="sxs-lookup"><span data-stu-id="2551e-112">Because of this, the unlisting of an item will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="2551e-113">Para remover o item da lista, visite a página de detalhes do item e selecione “Excluir Item”.</span><span class="sxs-lookup"><span data-stu-id="2551e-113">To unlist your item, visit the item details page and select 'Delete Item'.</span></span> <span data-ttu-id="2551e-114">Desmarque a caixa de seleção “Listado” e clique em Salvar.</span><span class="sxs-lookup"><span data-stu-id="2551e-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="2551e-115">**Como faço para remover um item?**</span><span class="sxs-lookup"><span data-stu-id="2551e-115">**How can I remove an item?**</span></span>

<span data-ttu-id="2551e-116">Se você tiver um cenário em que a exclusão do item é necessária, entre em contato com os Administradores da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2551e-116">If you experience a scenario where item deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="2551e-117">Os cenários de exclusão válidos são:</span><span class="sxs-lookup"><span data-stu-id="2551e-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="2551e-118">Problemas de violação de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="2551e-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="2551e-119">O item contém conteúdo potencialmente perigoso.</span><span class="sxs-lookup"><span data-stu-id="2551e-119">Item contains potentially harmful content.</span></span>
- <span data-ttu-id="2551e-120">O item contém dados confidenciais.</span><span class="sxs-lookup"><span data-stu-id="2551e-120">Item contains sensitive data.</span></span>

<span data-ttu-id="2551e-121">Para enviar uma Solicitação de Exclusão de Item aos Administradores da Galeria do PowerShell, visite a página de detalhes do item e selecione Entrar em Contato com o Suporte.</span><span class="sxs-lookup"><span data-stu-id="2551e-121">To submit a Delete Item Request to the PowerShell Gallery Administrators, visit your item's detail page and select Contact Support.</span></span>