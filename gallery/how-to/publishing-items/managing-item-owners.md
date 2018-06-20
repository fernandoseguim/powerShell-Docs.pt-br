---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Gerenciando proprietários do item
ms.openlocfilehash: 10d2a433253162847028e157b5bac47b23406469
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222098"
---
# <a name="managing-item-owners"></a><span data-ttu-id="8764d-103">Gerenciando proprietários do item</span><span class="sxs-lookup"><span data-stu-id="8764d-103">Managing item owners</span></span>

<span data-ttu-id="8764d-104">A propriedade de um item na Galeria do PowerShell é definida pelo usuário que publicou o item na galeria.</span><span class="sxs-lookup"><span data-stu-id="8764d-104">Ownership of an item in the PowerShell Gallery is defined by who published the item to the gallery.</span></span>
<span data-ttu-id="8764d-105">Às vezes, esses metadados precisam ser gerenciados além da publicação de item inicial, o que significa que os metadados de proprietário precisam ser mutáveis, enquanto o próprio item não é mutável.</span><span class="sxs-lookup"><span data-stu-id="8764d-105">Sometimes this metadata needs to be managed beyond the initial item publishing, which means the owner metadata needs to be mutable while the item itself is not.</span></span>

<span data-ttu-id="8764d-106">Todos os proprietários de item são pares.</span><span class="sxs-lookup"><span data-stu-id="8764d-106">All item owners are peers.</span></span>
<span data-ttu-id="8764d-107">Isso significa que qualquer proprietário do item pode publicar uma nova versão de um item.</span><span class="sxs-lookup"><span data-stu-id="8764d-107">This means any item owner can publish a new version of an item.</span></span> <span data-ttu-id="8764d-108">Isso também significa que qualquer proprietário do item pode remover qualquer proprietário do item.</span><span class="sxs-lookup"><span data-stu-id="8764d-108">It also means that any item owner can remove any other item owner.</span></span>
<span data-ttu-id="8764d-109">Nenhum proprietário tem mais autoridade que outros proprietários.</span><span class="sxs-lookup"><span data-stu-id="8764d-109">No owner has more authority than other owners.</span></span>

## <a name="setting-an-items-initial-owner"></a><span data-ttu-id="8764d-110">Configurando o proprietário inicial de um item</span><span class="sxs-lookup"><span data-stu-id="8764d-110">Setting an Item's Initial Owner</span></span>

<span data-ttu-id="8764d-111">Quando um novo item é publicado na Galeria do PowerShell, o proprietário inicial é definido pelo usuário que publicou o item.</span><span class="sxs-lookup"><span data-stu-id="8764d-111">When a new item is published to PowerShell Gallery, the initial owner is defined by the user that published the item.</span></span> <span data-ttu-id="8764d-112">Isso é determinado pela chave de API de quem foi usada no cmdlet Publish-Module.</span><span class="sxs-lookup"><span data-stu-id="8764d-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="8764d-113">Adicionando proprietários</span><span class="sxs-lookup"><span data-stu-id="8764d-113">Adding Owners</span></span>

<span data-ttu-id="8764d-114">Quando um item tiver sido publicado na Galeria do PowerShell, é fácil convidar outros usuários para se tornarem proprietários de um item.</span><span class="sxs-lookup"><span data-stu-id="8764d-114">Once an item has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of an item.</span></span>

1. <span data-ttu-id="8764d-115">[Faça logon](https://powershellgallery.com/users/account/LogOn) na Galeria do PowerShell com a conta que é o proprietário atual de um item.</span><span class="sxs-lookup"><span data-stu-id="8764d-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of an item.</span></span>
2. <span data-ttu-id="8764d-116">Navegue até uma página de item usando a guia “Itens”, pesquisando ou clicando em seu nome de usuário e em [**Gerenciar Meus Itens**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="8764d-116">Navigate to an item page using the 'Items' tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="8764d-117">Quando estiver conectado como o proprietário de um item, você verá um link “Gerenciar proprietários” do lado esquerdo para clicar.</span><span class="sxs-lookup"><span data-stu-id="8764d-117">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="8764d-118">Insira o nome de usuário da pessoa a ser adicionada como um proprietário e clique em “Adicionar”.</span><span class="sxs-lookup"><span data-stu-id="8764d-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="8764d-119">Em seguida, é enviado um email para o novo coproprietário, como um convite para que ele se torne um proprietário de um item.</span><span class="sxs-lookup"><span data-stu-id="8764d-119">An email is then sent to the new co-owner, as an invitation to become an owner of an item.</span></span>
6. <span data-ttu-id="8764d-120">Depois que o usuário clicar no link, ele será um coproprietário completo com controle total sobre um item, incluindo a capacidade de remover outros usuários como proprietários.</span><span class="sxs-lookup"><span data-stu-id="8764d-120">Once that user clicks the link, they are a full co-owner with full control over an item, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="8764d-121">**OBSERVAÇÃO**: até que o novo proprietário confirme a propriedade, ele *não* será listado como um proprietário de um item.</span><span class="sxs-lookup"><span data-stu-id="8764d-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of an item.</span></span>
<span data-ttu-id="8764d-122">Ao exibir a página **Gerenciar Proprietários**, você verá uma entrada “aprovação pendente” nos proprietários atuais.</span><span class="sxs-lookup"><span data-stu-id="8764d-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="8764d-123">Esse convite pode ser removido, da mesma forma que outros proprietários podem ser removidos.</span><span class="sxs-lookup"><span data-stu-id="8764d-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="8764d-124">Esse processo de convites impede que os usuários adicionem outros usuários erroneamente como proprietários de seus itens.</span><span class="sxs-lookup"><span data-stu-id="8764d-124">This process of invitations prevents users from falsely adding other users as owners of their items.</span></span>

<span data-ttu-id="8764d-125">Observe que os metadados de “Autores” são meramente texto de forma livre; somente “Proprietários” são controlados.</span><span class="sxs-lookup"><span data-stu-id="8764d-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="8764d-126">Removendo proprietários</span><span class="sxs-lookup"><span data-stu-id="8764d-126">Removing Owners</span></span>

<span data-ttu-id="8764d-127">Quando um item tem vários proprietários e um deles precisa ser removido, o processo é simples:</span><span class="sxs-lookup"><span data-stu-id="8764d-127">When an item has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="8764d-128">[Faça logon](https://powershellgallery.com/users/account/LogOn) na Galeria do PowerShell com a conta que é o proprietário atual de um item;</span><span class="sxs-lookup"><span data-stu-id="8764d-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of an item;</span></span>
2. <span data-ttu-id="8764d-129">Navegue até uma página de item usando a guia Itens, pesquisando ou clicando em seu nome de usuário e em [**Gerenciar Meus Itens**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="8764d-129">Navigate to an item page using the Items tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="8764d-130">Quando estiver conectado como o proprietário de um item, você verá um link “Gerenciar proprietários” do lado esquerdo para clicar;</span><span class="sxs-lookup"><span data-stu-id="8764d-130">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="8764d-131">Clique no link “Remover” ao lado do proprietário a ser removido.</span><span class="sxs-lookup"><span data-stu-id="8764d-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-item-ownership"></a><span data-ttu-id="8764d-132">Transferindo a propriedade do item</span><span class="sxs-lookup"><span data-stu-id="8764d-132">Transferring Item Ownership</span></span>

<span data-ttu-id="8764d-133">Às vezes, recebemos solicitações de suporte para transferir a propriedade do item de um usuário para outro, mas quase sempre você pode fazer isso sozinho.</span><span class="sxs-lookup"><span data-stu-id="8764d-133">We sometimes get support requests to transfer item ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="8764d-134">Transferir a propriedade de um usuário para outro é simplesmente uma combinação dos dois recursos acima.</span><span class="sxs-lookup"><span data-stu-id="8764d-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="8764d-135">O proprietário atual convida o novo usuário para se tornar um coproprietário e o novo usuário aceita o convite;</span><span class="sxs-lookup"><span data-stu-id="8764d-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="8764d-136">O novo usuário remove o usuário antigo da lista de proprietários.</span><span class="sxs-lookup"><span data-stu-id="8764d-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="8764d-137">Essa solicitação chegou de diversas maneiras, mas o processo funciona da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="8764d-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="8764d-138">A propriedade do item muda de um desenvolvedor para outro</span><span class="sxs-lookup"><span data-stu-id="8764d-138">The item ownership is changing from one developer to another</span></span>
- <span data-ttu-id="8764d-139">O item foi publicado acidentalmente usando a conta errada</span><span class="sxs-lookup"><span data-stu-id="8764d-139">The item was accidentally published using the wrong account</span></span>


## <a name="orphaned-items"></a><span data-ttu-id="8764d-140">Itens órfãos</span><span class="sxs-lookup"><span data-stu-id="8764d-140">Orphaned Items</span></span>

<span data-ttu-id="8764d-141">Um último cenário ocorreu, mas não com muita frequência.</span><span class="sxs-lookup"><span data-stu-id="8764d-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="8764d-142">Alguns itens se tornaram órfãos e a única conta de proprietário do item não pode ser usada para adicionar novos proprietários.</span><span class="sxs-lookup"><span data-stu-id="8764d-142">Items have become orphans and the only item owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="8764d-143">Estes são alguns exemplos desse cenário:</span><span class="sxs-lookup"><span data-stu-id="8764d-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="8764d-144">A conta do proprietário é associada a um endereço de email que não existe mais, e o usuário esqueceu a senha</span><span class="sxs-lookup"><span data-stu-id="8764d-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="8764d-145">O proprietário registrado saiu da empresa que produz o item e não pode ser contatado para atualizar a propriedade do item</span><span class="sxs-lookup"><span data-stu-id="8764d-145">The registered owner has left the company that produces the item and cannot be reached to update the item ownership</span></span>
- <span data-ttu-id="8764d-146">Devido a um bug que afetou apenas alguns dos itens, de alguma forma, não há proprietário para o item na galeria</span><span class="sxs-lookup"><span data-stu-id="8764d-146">Due to a bug that has only affected a handful of items, the item is somehow ownerless on the gallery</span></span>

<span data-ttu-id="8764d-147">Os administradores da Galeria do PowerShell podem acessar o link “Gerenciar proprietários” de qualquer item.</span><span class="sxs-lookup"><span data-stu-id="8764d-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any item.</span></span>
<span data-ttu-id="8764d-148">Se você for o proprietário legítimo de um item e não conseguir acessar o proprietário atual para obter permissões de propriedade, use o link “Relatar abuso” na galeria para entrar em contato com os Administradores da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8764d-148">If you are the rightful owner of a item and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="8764d-149">Em seguida, vamos seguir um processo para verificar sua propriedade do item.</span><span class="sxs-lookup"><span data-stu-id="8764d-149">We will then follow a process to verify your ownership of the item.</span></span>
<span data-ttu-id="8764d-150">Se determinarmos que você deve ser o proprietário do item, nós mesmos usaremos o link “Gerenciar proprietários” do item e lhe enviaremos o convite para que você se torne um proprietário.</span><span class="sxs-lookup"><span data-stu-id="8764d-150">If we determine you should be an owner of the item, we will use the 'Manage Owners' link for the item ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="8764d-151">Podemos fazer isso apenas depois de verificar que você deve ser um proprietário e o processo para essa verificação varia de acordo com as circunstâncias.</span><span class="sxs-lookup"><span data-stu-id="8764d-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="8764d-152">Muitas vezes, usaremos a URL do Projeto do item para encontrar uma maneira de entrar em contato com o proprietário do projeto, mas também podemos usar o Twitter, email ou outros meios para entrar em contato com o proprietário do projeto.</span><span class="sxs-lookup"><span data-stu-id="8764d-152">Often times, we will use the item's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>