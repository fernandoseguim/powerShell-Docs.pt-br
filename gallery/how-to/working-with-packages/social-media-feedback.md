---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Fornecendo comentários por meio de mídia social ou do recurso Comentários
ms.openlocfilehash: a27a2fc7cf54835cb53b11382c20d1354345a5a3
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58054995"
---
# <a name="providing-feedback-via-social-media-or-comments"></a><span data-ttu-id="9abe6-103">Fornecendo comentários por meio de mídia social ou do recurso Comentários</span><span class="sxs-lookup"><span data-stu-id="9abe6-103">Providing Feedback via social media or comments</span></span>

<span data-ttu-id="9abe6-104">A Galeria do PowerShell dá suporte a duas abordagens para que os usuários forneçam comentários públicos sobre um pacote:</span><span class="sxs-lookup"><span data-stu-id="9abe6-104">The PowerShell Gallery supports two approaches for users to provide public feedback on a package:</span></span>

- <span data-ttu-id="9abe6-105">Use os links na borda esquerda para "compartilhar" um pacote nos sites de mídia social Facebook, LinkedIn ou Twitter;</span><span class="sxs-lookup"><span data-stu-id="9abe6-105">Use the links on the left edge to "share" a package in Facebook, LinkedIn, or Twitter social media sites;</span></span>
- <span data-ttu-id="9abe6-106">Use o recurso Comentário para enviar comentários sobre um pacote e para permitir que os autores detectem comentários sobre os pacotes que eles publicaram.</span><span class="sxs-lookup"><span data-stu-id="9abe6-106">Use the Comment feature to post comments on a package, and to allow Authors to watch for comments on packages they publish.</span></span>

## <a name="social-media-feedback"></a><span data-ttu-id="9abe6-107">Comentários em mídia social</span><span class="sxs-lookup"><span data-stu-id="9abe6-107">Social Media Feedback</span></span>

<span data-ttu-id="9abe6-108">No lado esquerdo da página de cada pacote da Galeria do PowerShell, há links para o LinkedIn, o Facebook e o Twitter.</span><span class="sxs-lookup"><span data-stu-id="9abe6-108">On the left side of the page for each package in the PowerShell Gallery there are links for Facebook, LinkedIn, and Twitter.</span></span>
<span data-ttu-id="9abe6-109">Clicar nesses links abrirá o site de mídia social e permitirá o compartilhamento rápido de um link para o pacote.</span><span class="sxs-lookup"><span data-stu-id="9abe6-109">Clicking on these links will open the social media site, and allow quickly sharing a link to the package.</span></span>

<span data-ttu-id="9abe6-110">Os usuários precisam fazer logon no site que escolheram para compartilhar o pacote da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9abe6-110">Users must log in to the site they have chosen in order to share the PowerShell Gallery package.</span></span>

<span data-ttu-id="9abe6-111">Recomenda-se fazer isso quando o usuário acha que um pacote é algo que ele recomendaria a outros usuários.</span><span class="sxs-lookup"><span data-stu-id="9abe6-111">Users are encouraged to do this if they find that a package is something they would recommend to others.</span></span>
<span data-ttu-id="9abe6-112">A Galeria do PowerShell verificará cada site de mídia social buscando "compartilhamentos" do pacote e exibirá quantas vezes o pacote foi compartilhado em cada um dos sites de mídia social.</span><span class="sxs-lookup"><span data-stu-id="9abe6-112">The PowerShell Gallery will check each social media site for "shares" of the package, and display how many times that package has been shared in each of the social media sites.</span></span>
<span data-ttu-id="9abe6-113">Como isso mostra apenas o número de vezes que algo foi compartilhado, será interpretado que os outros usuários "gostaram" do pacote.</span><span class="sxs-lookup"><span data-stu-id="9abe6-113">Since this shows only the count of times something has been shared, it will be interpreted other users as "liking" the package.</span></span>

## <a name="comments"></a><span data-ttu-id="9abe6-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="9abe6-114">Comments</span></span>

<span data-ttu-id="9abe6-115">A Galeria do PowerShell usa o serviço LiveFyre para permitir que os usuários comentem sobre os pacotes.</span><span class="sxs-lookup"><span data-stu-id="9abe6-115">The PowerShell Gallery uses the LiveFyre service to allow users to comment on packages.</span></span>
<span data-ttu-id="9abe6-116">Os usuários que têm recomendações ou comentários podem usar esse recurso para fornecer comentários que ficam visíveis para qualquer pessoa que visitar a página do pacote.</span><span class="sxs-lookup"><span data-stu-id="9abe6-116">Users who have recommendations or feedback can use this feature to provide feedback that is visible to anyone who visits the package page.</span></span>
<span data-ttu-id="9abe6-117">Os proprietários do pacote podem Seguir este comentário e ser notificados quando alguém postar um comentário.</span><span class="sxs-lookup"><span data-stu-id="9abe6-117">Package owners can Follow this feedback, and be notified when someone posts a comment.</span></span>

<span data-ttu-id="9abe6-118">O sistema de Comentário é baseado no LiveFyre, que é um serviço separado que não é gerenciado pela Microsoft e requer o uso de logon exclusivo.</span><span class="sxs-lookup"><span data-stu-id="9abe6-118">The Comment system is based on LiveFyre, which is a separate service that is not managed by Microsoft, and requires unique login to use.</span></span>
<span data-ttu-id="9abe6-119">Na primeira vez que desejar deixar um comentário ou seguir os comentários em um de seus pacotes, será solicitado que você crie uma conta do LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="9abe6-119">The first time you choose to leave a comment or follow comments on one of your packages, you will be prompted to create a LiveFyre account.</span></span>

<span data-ttu-id="9abe6-120">Se você tiver criado uma conta do LiveFyre e feito logon, você poderá criar um comentário que forneça comentários sobre o pacote e, em seguida, clicar em "Postar comentário..." O comentário não ficará visível imediatamente.</span><span class="sxs-lookup"><span data-stu-id="9abe6-120">If you have created a LiveFyre account and logged in, you can craft a comment that provides feedback on the package, then click on "Post comment..." The comment will not be visible immediately.</span></span>
<span data-ttu-id="9abe6-121">Os comentários de pacotes da galeria são moderados pelos administradores da Galeria do PowerShell e todas as postagens são examinadas pelos moderadores antes de serem publicadas e ficarem visíveis para outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="9abe6-121">Comments for gallery packages are moderated by the PowerShell Gallery administrators, and all posts are reviewed by the moderators before being published and visible to others.</span></span>
<span data-ttu-id="9abe6-122">Nosso objetivo ao moderar os comentários é garantir que eles se alinhem a um comportamento público consistente com os [Termos de uso](https://www.powershellgallery.com/policies/Terms) da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9abe6-122">Our purpose in moderating the comments is to ensure that they align with public behavior consistent with the PowerShell Gallery [Terms of Use](https://www.powershellgallery.com/policies/Terms).</span></span>

<span data-ttu-id="9abe6-123">Os proprietários de pacote são incentivados a Seguir os comentários postados no LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="9abe6-123">Package owners are encouraged to Follow comments that are posted to LiveFyre.</span></span>
<span data-ttu-id="9abe6-124">É necessária uma conta do LiveFyre e é recomendável usar o mesmo endereço de email usado para publicar o pacote no LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="9abe6-124">A LiveFyre account is required, and it is recommended to use the same email address you use for publishing your package in LiveFyre.</span></span>
<span data-ttu-id="9abe6-125">Para Seguir comentários, faça logon no LiveFyre e navegue para qualquer pacote em que você esteja listado como Proprietário.</span><span class="sxs-lookup"><span data-stu-id="9abe6-125">To Follow comments, log into LiveFyre, and navigate to any package where you are listed as an Owner.</span></span>
<span data-ttu-id="9abe6-126">Abaixo da caixa Comentário na parte inferior de cada pacote, será exibido "+Seguir".</span><span class="sxs-lookup"><span data-stu-id="9abe6-126">Below the Comment box at the bottom of each package you will see "+Follow".</span></span>
<span data-ttu-id="9abe6-127">Depois de clicar nisso, o LiveFyre enviará um email para o endereço de email registrado sempre que novos comentários forem feitos no pacote.</span><span class="sxs-lookup"><span data-stu-id="9abe6-127">Once you click on this, LiveFyre will send an email to the registered email address any time new comments made on the package.</span></span>
