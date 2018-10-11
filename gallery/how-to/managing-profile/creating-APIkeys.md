---
ms.date: 09/10/2018
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Gerenciar chaves de API
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523122"
---
# <a name="managing-api-keys"></a><span data-ttu-id="55f12-103">Gerenciar chaves de API</span><span class="sxs-lookup"><span data-stu-id="55f12-103">Managing API keys</span></span>

<span data-ttu-id="55f12-104">A Galeria do PowerShell dá suporte à criação de várias chaves de API compatíveis com uma série de requisitos de publicação.</span><span class="sxs-lookup"><span data-stu-id="55f12-104">The PowerShell Gallery supports creating multiple API keys to support a range of publishing requirements.</span></span> <span data-ttu-id="55f12-105">Uma chave de API pode ser aplicada a um ou mais pacotes, permite privilégios específicos e tem uma data de validade.</span><span class="sxs-lookup"><span data-stu-id="55f12-105">An API key can apply to one or more packages, grants specific privileges, and has an expiration date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="55f12-106">Os usuários que publicaram na Galeria do PowerShell antes da introdução das chaves de API com escopo terão uma "chave de API de acesso completo".</span><span class="sxs-lookup"><span data-stu-id="55f12-106">Users who published to the PowerShell Gallery prior to the introduction of scoped API keys will have a "Full access API key".</span></span> <span data-ttu-id="55f12-107">As chaves de acesso completo não têm as melhorias de segurança incorporadas às chaves de API com escopo.</span><span class="sxs-lookup"><span data-stu-id="55f12-107">The full access keys do not have the security improvements built into scoped API keys.</span></span> <span data-ttu-id="55f12-108">As chaves de acesso completo nunca perdem a validade e são aplicadas a tudo o que pertence ao usuário.</span><span class="sxs-lookup"><span data-stu-id="55f12-108">The full access keys never expires and apply to everything owned by the user.</span></span> <span data-ttu-id="55f12-109">Se essa chave for excluída, não poderá ser recriada.</span><span class="sxs-lookup"><span data-stu-id="55f12-109">If you delete this key, it cannot be recreated.</span></span>

<span data-ttu-id="55f12-110">A imagem a seguir mostra as opções disponíveis ao criar uma chave de API com escopo.</span><span class="sxs-lookup"><span data-stu-id="55f12-110">The following image shows the options available when creating a scoped API key.</span></span>

![Criar chaves de API](../../Images/PSGallery_KeyScoped.png)

<span data-ttu-id="55f12-112">Neste exemplo, criamos uma chave de API com o nome **AzureRMDataFactory**.</span><span class="sxs-lookup"><span data-stu-id="55f12-112">In this example, we created an API key named **AzureRMDataFactory**.</span></span> <span data-ttu-id="55f12-113">Esse valor de chave pode ser usado para efetuar push de pacotes com nomes que começam com "AzureRM.DataFactory" e é válido por 365 dias.</span><span class="sxs-lookup"><span data-stu-id="55f12-113">This key value can be used to push packages with names that begin with 'AzureRM.DataFactory' and is valid for 365 days.</span></span> <span data-ttu-id="55f12-114">Trata-se de um cenário normal quando equipes diferentes trabalham em pacotes distintos dentro da mesma organização.</span><span class="sxs-lookup"><span data-stu-id="55f12-114">This is a typical scenario when different teams within the same organization work on different packages.</span></span> <span data-ttu-id="55f12-115">Os membros da equipe têm uma chave que concede privilégios para o pacote específico em que estão trabalhando.</span><span class="sxs-lookup"><span data-stu-id="55f12-115">The members of the team have a key that grants them privileges for the specific package they work on.</span></span>
<span data-ttu-id="55f12-116">O valor de expiração impede o uso de chaves obsoletas ou esquecidas.</span><span class="sxs-lookup"><span data-stu-id="55f12-116">The expiration value prevents the use of stale or forgotten keys.</span></span>

## <a name="using-glob-patterns"></a><span data-ttu-id="55f12-117">Usar padrões glob</span><span class="sxs-lookup"><span data-stu-id="55f12-117">Using glob patterns</span></span>

<span data-ttu-id="55f12-118">Caso você trabalhe com vários pacotes, poderá usar padrões glob para combinar vários pacotes em um grupo.</span><span class="sxs-lookup"><span data-stu-id="55f12-118">If you work on multiple packages, you can use globbing patterns to match multiple packages as a group.</span></span> <span data-ttu-id="55f12-119">As permissões de chave de API se aplicam a todos os novos pacotes que correspondem ao padrão glob.</span><span class="sxs-lookup"><span data-stu-id="55f12-119">API key permissions apply to all new packages matching the glob pattern.</span></span> <span data-ttu-id="55f12-120">Por exemplo, o exemplo anterior usa um valor **Padrão Glob** de "AzureRM.DataFactory\*".</span><span class="sxs-lookup"><span data-stu-id="55f12-120">For example, the previous example uses a **Glob Pattern** value of 'AzureRM.DataFactory\*'.</span></span> <span data-ttu-id="55f12-121">É possível efetuar push de um pacote chamado "AzureRm.DataFactoryV2.Netcore" usando essa chave, pois o pacote corresponde ao padrão glob.</span><span class="sxs-lookup"><span data-stu-id="55f12-121">You can push a package named 'AzureRm.DataFactoryV2.Netcore' using this key since the package matches the glob pattern.</span></span>

## <a name="create-api-keys-securely"></a><span data-ttu-id="55f12-122">Criar chaves de API com segurança</span><span class="sxs-lookup"><span data-stu-id="55f12-122">Create API keys securely</span></span>

<span data-ttu-id="55f12-123">Por questões de segurança, um valor de chave recém-criado nunca é exibido na tela e só fica disponível com o botão Copiar, conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="55f12-123">For security, a newly created key value is never shown on the screen and is only available with the Copy button, as shown below.</span></span>

![Obter um novo valor de chave de API](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> <span data-ttu-id="55f12-125">Só é possível copiar o valor da chave de API imediatamente após criá-lo ou atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="55f12-125">You can only copy the API key value immediately after creating or refreshing it.</span></span> <span data-ttu-id="55f12-126">Esse valor não será exibido e não ficará acessível novamente após a atualização da página.</span><span class="sxs-lookup"><span data-stu-id="55f12-126">It will not be displayed, and will not be accessible again after the page is refreshed.</span></span> <span data-ttu-id="55f12-127">Se você perder o valor da chave, será necessário regenerá-lo e copiar a chave depois disso.</span><span class="sxs-lookup"><span data-stu-id="55f12-127">If you lose the key value, you must use Regenerate, and copy the key after it is regenerated.</span></span>

## <a name="key-permissions-and-expiration"></a><span data-ttu-id="55f12-128">Expiração e permissões de chave</span><span class="sxs-lookup"><span data-stu-id="55f12-128">Key permissions and expiration</span></span>

<span data-ttu-id="55f12-129">As chaves de API com escopo podem atribuir qualquer uma das seguintes permissões:</span><span class="sxs-lookup"><span data-stu-id="55f12-129">Scoped API keys can assign any of the following permissions:</span></span>

- <span data-ttu-id="55f12-130">Efetuar push de novos pacotes</span><span class="sxs-lookup"><span data-stu-id="55f12-130">Push new packages</span></span>
- <span data-ttu-id="55f12-131">Efetuar push de pacotes novos ou de atualização</span><span class="sxs-lookup"><span data-stu-id="55f12-131">Push new or update packages</span></span>
- <span data-ttu-id="55f12-132">Remover pacotes da lista</span><span class="sxs-lookup"><span data-stu-id="55f12-132">Unlist packages</span></span>

<span data-ttu-id="55f12-133">Toda nova chave tem uma expiração.</span><span class="sxs-lookup"><span data-stu-id="55f12-133">Every new key has an expiration.</span></span> <span data-ttu-id="55f12-134">O valor de expiração é medido em dias.</span><span class="sxs-lookup"><span data-stu-id="55f12-134">The expiration value is measured in days.</span></span> <span data-ttu-id="55f12-135">Os valores possíveis para expiração são:</span><span class="sxs-lookup"><span data-stu-id="55f12-135">The possible values for expiration are:</span></span>

- <span data-ttu-id="55f12-136">Um dia</span><span class="sxs-lookup"><span data-stu-id="55f12-136">1 day</span></span>
- <span data-ttu-id="55f12-137">90 dias</span><span class="sxs-lookup"><span data-stu-id="55f12-137">90 days</span></span>
- <span data-ttu-id="55f12-138">180 dias</span><span class="sxs-lookup"><span data-stu-id="55f12-138">180 days</span></span>
- <span data-ttu-id="55f12-139">270 dias</span><span class="sxs-lookup"><span data-stu-id="55f12-139">270 days</span></span>
- <span data-ttu-id="55f12-140">365 dias (padrão)</span><span class="sxs-lookup"><span data-stu-id="55f12-140">365 days (default)</span></span>

<span data-ttu-id="55f12-141">Essas configurações não podem ser alteradas após a criação da chave.</span><span class="sxs-lookup"><span data-stu-id="55f12-141">These settings cannot be changed once the key is created.</span></span> <span data-ttu-id="55f12-142">Não é possível criar uma nova chave que não expira.</span><span class="sxs-lookup"><span data-stu-id="55f12-142">You cannot create a new key that never expires.</span></span>

## <a name="editing-and-deleting-existing-api-keys"></a><span data-ttu-id="55f12-143">Editar e excluir chaves de API existentes</span><span class="sxs-lookup"><span data-stu-id="55f12-143">Editing and deleting existing API keys</span></span>

<span data-ttu-id="55f12-144">É possível alterar algumas configurações de uma chave existente.</span><span class="sxs-lookup"><span data-stu-id="55f12-144">You can change some settings of an existing key.</span></span> <span data-ttu-id="55f12-145">Conforme mencionado anteriormente, não é possível modificar o escopo de segurança de uma chave de API existente ou alterar a expiração.</span><span class="sxs-lookup"><span data-stu-id="55f12-145">As previously noted, you cannot modify the security scope for an existing API key or change the expiration.</span></span> <span data-ttu-id="55f12-146">As opções que podem ser alteradas são mostradas na captura de tela a seguir:</span><span class="sxs-lookup"><span data-stu-id="55f12-146">The changeable options are shown in the following screenshot:</span></span>

![Obter um novo valor de chave de API](../../Images/PSGallery_EditAPIKey.png)

<span data-ttu-id="55f12-148">Para alterar os pacotes controlados por uma chave, escolha pacotes individuais na lista ou altere o padrão glob.</span><span class="sxs-lookup"><span data-stu-id="55f12-148">To change the packages controlled by a key, you can choose individual packages from the list or change the glob pattern.</span></span>

<span data-ttu-id="55f12-149">Ao clicar em **Regenerar**, um novo valor de chave é criado.</span><span class="sxs-lookup"><span data-stu-id="55f12-149">Clicking **Regenerate** creates a new key value.</span></span> <span data-ttu-id="55f12-150">Do mesmo modo que a chave foi inicialmente criada, é necessário **Copiar** o valor de chave imediatamente após a atualização.</span><span class="sxs-lookup"><span data-stu-id="55f12-150">Just like when you initially created the key, you must **Copy** the key value immediately after updating it.</span></span> <span data-ttu-id="55f12-151">A opção **Copiar** não estará mais disponível depois que você sair da página.</span><span class="sxs-lookup"><span data-stu-id="55f12-151">The **Copy** option is not available once you leave this page.</span></span>

<span data-ttu-id="55f12-152">Clicar em **Excluir** mostra uma mensagem de confirmação.</span><span class="sxs-lookup"><span data-stu-id="55f12-152">Clicking **Delete** displays a confirmation message.</span></span> <span data-ttu-id="55f12-153">Depois de excluída, uma chave não pode mais ser usada.</span><span class="sxs-lookup"><span data-stu-id="55f12-153">Once a key is deleted, it will be unusable.</span></span>

## <a name="key-expiration"></a><span data-ttu-id="55f12-154">Expiração da chave</span><span class="sxs-lookup"><span data-stu-id="55f12-154">Key expiration</span></span>

<span data-ttu-id="55f12-155">Dez dias antes da expiração, a Galeria do PowerShell envia um aviso para o email do titular da conta da chave de API.</span><span class="sxs-lookup"><span data-stu-id="55f12-155">Ten days before the expiration, the PowerShell Gallery sends a warning email the account holder of the API key.</span></span> <span data-ttu-id="55f12-156">Após a expiração, a chave não pode mais ser usada.</span><span class="sxs-lookup"><span data-stu-id="55f12-156">After expiration, the key is unusable.</span></span> <span data-ttu-id="55f12-157">Uma mensagem de aviso é exibida na parte superior da página de gerenciamento de chaves de API, mostrando quais delas não são mais válidas.</span><span class="sxs-lookup"><span data-stu-id="55f12-157">A warning message is displayed at the top of the API key management page showing which keys are no longer valid.</span></span> <span data-ttu-id="55f12-158">É possível gerar um novo valor de chave.</span><span class="sxs-lookup"><span data-stu-id="55f12-158">You can generate a new key value.</span></span>
