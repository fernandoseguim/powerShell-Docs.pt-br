---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery
title: Excluindo itens
ms.openlocfilehash: f82d80a35f51227c4671bd2b15a7d1c16f0ba0a8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="deleting-items"></a><span data-ttu-id="ac7b5-103">Excluindo itens</span><span class="sxs-lookup"><span data-stu-id="ac7b5-103">Deleting items</span></span>

<span data-ttu-id="ac7b5-104">A Galeria do PowerShell não dá suporte à exclusão permanente de itens, porque isso interromperia qualquer usuário que dependesse da disponibilidade desses itens.</span><span class="sxs-lookup"><span data-stu-id="ac7b5-104">The PowerShell Gallery does not support permanent deletion of items, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="ac7b5-105">Em vez disso, a Galeria de PowerShell dá suporte a uma maneira de “remover um item da lista”, que pode ser feito na página de gerenciamento dos itens no site.</span><span class="sxs-lookup"><span data-stu-id="ac7b5-105">Instead, the PowerShell Gallery supports a way to 'unlist' an item, which can be done in the item management page on the web site.</span></span>
<span data-ttu-id="ac7b5-106">Quando um item é removido da lista, ele não aparece mais na pesquisa e em nenhuma listagem de itens, tanto na Galeria do PowerShell quanto por meio dos comandos PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="ac7b5-106">When an item is unlisted, it no longer shows up in search and in any item listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="ac7b5-107">No entanto, ele permanece disponível para download, pela especificação da versão exata, o que permite que os scripts automatizados continuem funcionando.</span><span class="sxs-lookup"><span data-stu-id="ac7b5-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="ac7b5-108">Se você estiver em uma situação excepcional em que acredita que um de seus itens precise ser excluído, isso poderá ser feito manualmente pela equipe da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ac7b5-108">If you run into an exceptional situation where you think one of your items must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="ac7b5-109">Por exemplo, se houver um problema de violação de direitos autorais ou conteúdo potencialmente perigoso, isso poderá ser um motivo válido para excluí-lo.</span><span class="sxs-lookup"><span data-stu-id="ac7b5-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="ac7b5-110">Nesse caso, você deve enviar uma solicitação de suporte por meio da [Galeria do PowerShell] (http://www.PowerShellGallery.com)).</span><span class="sxs-lookup"><span data-stu-id="ac7b5-110">You should submit a support request through [PowerShell Gallery] (http://www.PowerShellGallery.com) in that case.</span></span>