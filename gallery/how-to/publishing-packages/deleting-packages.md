---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Excluir pacotes
ms.openlocfilehash: ca5e68fcad52e4c7561d2c2b3858228652f22e0b
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003656"
---
# <a name="deleting-packages"></a><span data-ttu-id="ddcb1-103">Excluir pacotes</span><span class="sxs-lookup"><span data-stu-id="ddcb1-103">Deleting Packages</span></span>

<span data-ttu-id="ddcb1-104">A Galeria do PowerShell não dá suporte à exclusão permanente de pacotes porque isso interromperia qualquer usuário que dependesse da disponibilidade desses pacotes.</span><span class="sxs-lookup"><span data-stu-id="ddcb1-104">The PowerShell Gallery does not support permanent deletion of packages, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="ddcb1-105">Em vez disso, a Galeria de PowerShell dá suporte a uma maneira de "remover um pacote da lista", o que pode ser feito na página de gerenciamento dos pacotes no site.</span><span class="sxs-lookup"><span data-stu-id="ddcb1-105">Instead, the PowerShell Gallery supports a way to 'unlist' a package, which can be done in the package management page on the web site.</span></span>
<span data-ttu-id="ddcb1-106">Quando um pacote é removido da lista, ele não aparece mais na pesquisa e em nenhuma listagem de pacotes, tanto na Galeria do PowerShell quanto por meio dos comandos PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="ddcb1-106">When a package is unlisted, it no longer shows up in search and in any package listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="ddcb1-107">No entanto, ele permanece disponível para download, pela especificação da versão exata, o que permite que os scripts automatizados continuem funcionando.</span><span class="sxs-lookup"><span data-stu-id="ddcb1-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="ddcb1-108">Se você estiver em uma situação excepcional em que acredita que um de seus pacotes precise ser excluído, isso poderá ser feito manualmente pela equipe da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddcb1-108">If you run into an exceptional situation where you think one of your packages must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="ddcb1-109">Por exemplo, se houver um problema de violação de direitos autorais ou conteúdo potencialmente perigoso, isso poderá ser um motivo válido para excluí-lo.</span><span class="sxs-lookup"><span data-stu-id="ddcb1-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="ddcb1-110">Nesse caso, você deve enviar uma solicitação de suporte por meio da [Galeria do PowerShell](http://www.PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="ddcb1-110">You should submit a support request through [PowerShell Gallery](http://www.PowerShellGallery.com) in that case.</span></span>
