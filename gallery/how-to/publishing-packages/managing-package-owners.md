---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Gerenciar proprietários de pacote
ms.openlocfilehash: 5cf26a7195ac446177cbb7f3a055e8e0a78569cc
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003658"
---
# <a name="managing-package-owners"></a><span data-ttu-id="95b55-103">Gerenciar proprietários de pacote</span><span class="sxs-lookup"><span data-stu-id="95b55-103">Managing package owners</span></span>

<span data-ttu-id="95b55-104">A propriedade de um pacote na Galeria do PowerShell é definida pelo usuário que publicou o pacote na galeria.</span><span class="sxs-lookup"><span data-stu-id="95b55-104">Ownership of a package in the PowerShell Gallery is defined by who published the package to the gallery.</span></span>
<span data-ttu-id="95b55-105">Às vezes, esses metadados precisam ser gerenciados além da publicação de pacote inicial, o que significa que os metadados de proprietário precisam ser mutáveis, enquanto o próprio pacote não é.</span><span class="sxs-lookup"><span data-stu-id="95b55-105">Sometimes this metadata needs to be managed beyond the initial package publishing, which means the owner metadata needs to be mutable while the package itself is not.</span></span>

<span data-ttu-id="95b55-106">Todos os proprietários de pacote são pares.</span><span class="sxs-lookup"><span data-stu-id="95b55-106">All package owners are peers.</span></span>
<span data-ttu-id="95b55-107">Isso significa que qualquer proprietário de pacote pode publicar uma nova versão de um pacote.</span><span class="sxs-lookup"><span data-stu-id="95b55-107">This means any package owner can publish a new version of an package.</span></span> <span data-ttu-id="95b55-108">Isso também significa que qualquer proprietário de pacote pode remover qualquer proprietário de pacote.</span><span class="sxs-lookup"><span data-stu-id="95b55-108">It also means that any package owner can remove any other package owner.</span></span>
<span data-ttu-id="95b55-109">Nenhum proprietário tem mais autoridade que outros proprietários.</span><span class="sxs-lookup"><span data-stu-id="95b55-109">No owner has more authority than other owners.</span></span>

## <a name="setting-a-packages-initial-owner"></a><span data-ttu-id="95b55-110">Configurar o proprietário inicial de um pacote</span><span class="sxs-lookup"><span data-stu-id="95b55-110">Setting a Package's Initial Owner</span></span>

<span data-ttu-id="95b55-111">Quando um novo pacote é publicado na Galeria do PowerShell, o proprietário inicial é definido pelo usuário que publicou o pacote.</span><span class="sxs-lookup"><span data-stu-id="95b55-111">When a new package is published to PowerShell Gallery, the initial owner is defined by the user that published the package.</span></span> <span data-ttu-id="95b55-112">Isso é determinado pela chave de API de quem foi usada no cmdlet Publish-Module.</span><span class="sxs-lookup"><span data-stu-id="95b55-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="95b55-113">Adicionando proprietários</span><span class="sxs-lookup"><span data-stu-id="95b55-113">Adding Owners</span></span>

<span data-ttu-id="95b55-114">Quando um pacote é publicado na Galeria do PowerShell, é fácil convidar outros usuários para se tornarem proprietários de pacote.</span><span class="sxs-lookup"><span data-stu-id="95b55-114">Once a package has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of a package.</span></span>

1. <span data-ttu-id="95b55-115">[Faça logon](https://powershellgallery.com/users/account/LogOn) na Galeria do PowerShell com a conta que é o proprietário atual de um pacote.</span><span class="sxs-lookup"><span data-stu-id="95b55-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of a package.</span></span>
2. <span data-ttu-id="95b55-116">Navegue até uma página do pacote, usando a guia "Itens", pesquisando ou clicando em seu nome de usuário e em [**Gerenciar Meus Pacotes**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="95b55-116">Navigate to a package page using the 'Items' tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="95b55-117">Quando estiver conectado como o proprietário de um pacote, você verá um link "Gerenciar proprietários" do lado esquerdo para clicar.</span><span class="sxs-lookup"><span data-stu-id="95b55-117">When logged on as an package's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="95b55-118">Insira o nome de usuário da pessoa a ser adicionada como um proprietário e clique em “Adicionar”.</span><span class="sxs-lookup"><span data-stu-id="95b55-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="95b55-119">Em seguida, é enviado um email para o novo coproprietário, como um convite para que ele se torne um proprietário de pacote.</span><span class="sxs-lookup"><span data-stu-id="95b55-119">An email is then sent to the new co-owner, as an invitation to become an owner of a package.</span></span>
6. <span data-ttu-id="95b55-120">Depois que o usuário clicar no link, ele será um coproprietário completo com controle total sobre um pacote, incluindo a capacidade de remover outros usuários como proprietários.</span><span class="sxs-lookup"><span data-stu-id="95b55-120">Once that user clicks the link, they are a full co-owner with full control over a package, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="95b55-121">**OBSERVAÇÃO**: até que o novo proprietário confirme a propriedade, ele *não* será listado como um proprietário de pacote.</span><span class="sxs-lookup"><span data-stu-id="95b55-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of a package.</span></span>
<span data-ttu-id="95b55-122">Ao exibir a página **Gerenciar Proprietários**, você verá uma entrada “aprovação pendente” nos proprietários atuais.</span><span class="sxs-lookup"><span data-stu-id="95b55-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="95b55-123">Esse convite pode ser removido, da mesma forma que outros proprietários podem ser removidos.</span><span class="sxs-lookup"><span data-stu-id="95b55-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="95b55-124">Esse processo de convites impede que os usuários adicionem outros usuários erroneamente como proprietários de seus pacotes.</span><span class="sxs-lookup"><span data-stu-id="95b55-124">This process of invitations prevents users from falsely adding other users as owners of their packages.</span></span>

<span data-ttu-id="95b55-125">Observe que os metadados de “Autores” são meramente texto de forma livre; somente “Proprietários” são controlados.</span><span class="sxs-lookup"><span data-stu-id="95b55-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="95b55-126">Removendo proprietários</span><span class="sxs-lookup"><span data-stu-id="95b55-126">Removing Owners</span></span>

<span data-ttu-id="95b55-127">Quando um pacote tem vários proprietários e um deles precisa ser removido, o processo é simples:</span><span class="sxs-lookup"><span data-stu-id="95b55-127">When a package has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="95b55-128">[Faça logon](https://powershellgallery.com/users/account/LogOn) na Galeria do PowerShell com a conta que é o proprietário atual de um pacote;</span><span class="sxs-lookup"><span data-stu-id="95b55-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of a package;</span></span>
2. <span data-ttu-id="95b55-129">Navegue até uma página do pacote, usando a guia Pacotes, pesquisando ou clicando em seu nome de usuário e em [**Gerenciar Meus Pacotes**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="95b55-129">Navigate to a package page using the Packages tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="95b55-130">Quando estiver conectado como o proprietário de um pacote, você verá um link "Gerenciar proprietários" do lado esquerdo para clicar;</span><span class="sxs-lookup"><span data-stu-id="95b55-130">When logged on as a package's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="95b55-131">Clique no link “Remover” ao lado do proprietário a ser removido.</span><span class="sxs-lookup"><span data-stu-id="95b55-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-package-ownership"></a><span data-ttu-id="95b55-132">Transferir a propriedade do pacote</span><span class="sxs-lookup"><span data-stu-id="95b55-132">Transferring Package Ownership</span></span>

<span data-ttu-id="95b55-133">Às vezes, recebemos solicitações de suporte para transferir a propriedade do pacote de um usuário para outro, mas quase sempre você pode fazer isso sozinho.</span><span class="sxs-lookup"><span data-stu-id="95b55-133">We sometimes get support requests to transfer package ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="95b55-134">Transferir a propriedade de um usuário para outro é simplesmente uma combinação dos dois recursos acima.</span><span class="sxs-lookup"><span data-stu-id="95b55-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="95b55-135">O proprietário atual convida o novo usuário para se tornar um coproprietário e o novo usuário aceita o convite;</span><span class="sxs-lookup"><span data-stu-id="95b55-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="95b55-136">O novo usuário remove o usuário antigo da lista de proprietários.</span><span class="sxs-lookup"><span data-stu-id="95b55-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="95b55-137">Essa solicitação chegou de diversas maneiras, mas o processo funciona da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="95b55-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="95b55-138">A propriedade do pacote muda de um desenvolvedor para outro</span><span class="sxs-lookup"><span data-stu-id="95b55-138">The package ownership is changing from one developer to another</span></span>
- <span data-ttu-id="95b55-139">O pacote foi publicado acidentalmente usando a conta errada</span><span class="sxs-lookup"><span data-stu-id="95b55-139">The package was accidentally published using the wrong account</span></span>


## <a name="orphaned-packages"></a><span data-ttu-id="95b55-140">Pacotes órfãos</span><span class="sxs-lookup"><span data-stu-id="95b55-140">Orphaned Packages</span></span>

<span data-ttu-id="95b55-141">Um último cenário ocorreu, mas não com muita frequência.</span><span class="sxs-lookup"><span data-stu-id="95b55-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="95b55-142">Alguns pacotes se tornaram órfãos, e a única conta de proprietário do pacote não pode ser usada para adicionar novos proprietários.</span><span class="sxs-lookup"><span data-stu-id="95b55-142">Packages have become orphans and the only package owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="95b55-143">Estes são alguns exemplos desse cenário:</span><span class="sxs-lookup"><span data-stu-id="95b55-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="95b55-144">A conta do proprietário é associada a um endereço de email que não existe mais, e o usuário esqueceu a senha</span><span class="sxs-lookup"><span data-stu-id="95b55-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="95b55-145">O proprietário registrado saiu da empresa que produz o pacote, e não é possível entrar em contato com ele para que atualize a propriedade do pacote</span><span class="sxs-lookup"><span data-stu-id="95b55-145">The registered owner has left the company that produces the package and cannot be reached to update the package ownership</span></span>
- <span data-ttu-id="95b55-146">Devido a um bug que afetou apenas alguns dos pacotes, de alguma forma, não há proprietário para o pacote na galeria</span><span class="sxs-lookup"><span data-stu-id="95b55-146">Due to a bug that has only affected a handful of packages, the package is somehow ownerless on the gallery</span></span>

<span data-ttu-id="95b55-147">Os administradores da Galeria do PowerShell podem acessar o link "Gerenciar Proprietários" de qualquer pacote.</span><span class="sxs-lookup"><span data-stu-id="95b55-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any package.</span></span>
<span data-ttu-id="95b55-148">Se você for o proprietário legítimo de um pacote e não conseguir acessar o proprietário atual para obter permissões de propriedade, use o link "Relatar Abuso" na galeria para entrar em contato com os Administradores da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95b55-148">If you are the rightful owner of a package and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="95b55-149">Em seguida, vamos seguir um processo para verificar sua propriedade do pacote.</span><span class="sxs-lookup"><span data-stu-id="95b55-149">We will then follow a process to verify your ownership of the package.</span></span>
<span data-ttu-id="95b55-150">Se determinarmos que você deve ser o proprietário do pacote, nós mesmos usaremos o link "Gerenciar Proprietários" do pacote e enviaremos o convite para que você se torne um proprietário.</span><span class="sxs-lookup"><span data-stu-id="95b55-150">If we determine you should be an owner of the package, we will use the 'Manage Owners' link for the package ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="95b55-151">Podemos fazer isso apenas depois de verificar que você deve ser um proprietário e o processo para essa verificação varia de acordo com as circunstâncias.</span><span class="sxs-lookup"><span data-stu-id="95b55-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="95b55-152">Muitas vezes, usaremos a URL do Projeto do pacote para encontrar uma maneira de entrar em contato com o proprietário do projeto, mas também podemos usar o Twitter, email ou outros meios para entrar em contato com ele.</span><span class="sxs-lookup"><span data-stu-id="95b55-152">Often times, we will use the package's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>
