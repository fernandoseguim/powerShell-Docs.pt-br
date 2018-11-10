---
ms.date: 09/11/2018
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Criando uma conta da Galeria do PowerShell
ms.openlocfilehash: e4cf73edb03267cff6bbcc0cf3b754225e45be9f
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003641"
---
# <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="fb11f-103">Criando uma conta da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb11f-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="fb11f-104">É necessário criar uma conta antes de publicar algo na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fb11f-104">You must create a PowerShell Gallery account before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="fb11f-105">As contas da Galeria do PowerShell precisam estar vinculadas a uma conta de logon habilitada por email.</span><span class="sxs-lookup"><span data-stu-id="fb11f-105">PowerShell Gallery accounts must be linked to an email-enabled login account.</span></span> <span data-ttu-id="fb11f-106">Essa conta pode ser uma do Azure Active Directory ou uma ID da Microsoft, como uma conta de email do outlook.com ou hotmail.com.</span><span class="sxs-lookup"><span data-stu-id="fb11f-106">This account can be an Azure Active Directory account or a Microsoft ID, like an email account from outlook.com or hotmail.com.</span></span>

<span data-ttu-id="fb11f-107">Para criar uma conta da Galeria do PowerShell, acesse [https://PowerShellGallery.com](https://PowerShellGallery.com) e clique em **Entrar**, conforme mostrado na imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="fb11f-107">To create a PowerShell Gallery account, go to [https://PowerShellGallery.com](https://PowerShellGallery.com) and click on **Sign in** as shown in the following image.</span></span>

![Registrar nova conta](../../Images/CreateAccount-Register.png)

<span data-ttu-id="fb11f-109">Para usar uma conta do Azure Active Directory, selecione **Conta corporativa ou de estudante** e entre com sua conta.</span><span class="sxs-lookup"><span data-stu-id="fb11f-109">To use an Azure Active Directory account, select **Work or School Account**, and sign in with your account.</span></span> <span data-ttu-id="fb11f-110">Para usar uma ID da Microsoft, escolha **Conta pessoal** e entre.</span><span class="sxs-lookup"><span data-stu-id="fb11f-110">To use a Microsoft ID, choose **Personal Account** and sign in.</span></span>

<span data-ttu-id="fb11f-111">Em seguida, será solicitado que você crie um nome de usuário para a Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fb11f-111">Next, you are prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="fb11f-112">Analise os Termos de Uso e a Política de Privacidade, insira um nome de usuário e, em seguida, clique em **Registrar**.</span><span class="sxs-lookup"><span data-stu-id="fb11f-112">Review the Terms of Use and Privacy Policy, enter a username, and then click **Register**.</span></span>

> [!NOTE]
> <span data-ttu-id="fb11f-113">Este nome de conta não poderá ser alterado após a criação.</span><span class="sxs-lookup"><span data-stu-id="fb11f-113">The account name cannot be changed once it is created.</span></span> <span data-ttu-id="fb11f-114">Para saber mais, confira [Gerenciar proprietários de pacotes](managing-package-owners.md).</span><span class="sxs-lookup"><span data-stu-id="fb11f-114">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="fb11f-115">Práticas recomendadas para contas da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="fb11f-115">Recommended practices for PowerShell Gallery accounts</span></span>

<span data-ttu-id="fb11f-116">É importante que a conta de email usada com sua conta da Galeria do PowerShell seja monitorada ativamente.</span><span class="sxs-lookup"><span data-stu-id="fb11f-116">It's important to actively monitor the email account used with your PowerShell Gallery account.</span></span> <span data-ttu-id="fb11f-117">Toda a comunicação com os proprietários de pacotes da Galeria do PowerShell será feita por esse endereço de email.</span><span class="sxs-lookup"><span data-stu-id="fb11f-117">All communication with owners of PowerShell Gallery packages is through this email address.</span></span> <span data-ttu-id="fb11f-118">Quando não for possível entrar em contato com um proprietário de pacote, a equipe de operações da Galeria do PowerShell poderá precisar excluir o pacote.</span><span class="sxs-lookup"><span data-stu-id="fb11f-118">If the PowerShell Gallery Operations team is unable to contact a package owner, we may be required to delete a package.</span></span>

<span data-ttu-id="fb11f-119">As organizações que publicam na Galeria do PowerShell geralmente criam uma conta externa exclusiva para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="fb11f-119">Organizations that publish to the PowerShell Gallery often create a unique external account for that purpose.</span></span> <span data-ttu-id="fb11f-120">É recomendável usar o encaminhamento de email para enviar as notificações para um endereço dentro da sua organização.</span><span class="sxs-lookup"><span data-stu-id="fb11f-120">We recommend you use email forwarding to forward notifications to an address within your organization.</span></span>

<span data-ttu-id="fb11f-121">Quando vários proprietários estão associados a um pacote, todas as notificações da Galeria do PowerShell são enviadas a todos os proprietários.</span><span class="sxs-lookup"><span data-stu-id="fb11f-121">When multiple owners are associated with a package, all PowerShell Gallery notifications are sent to all owners.</span></span> <span data-ttu-id="fb11f-122">Para saber mais, confira [Gerenciar proprietários de pacotes](managing-package-owners.md).</span><span class="sxs-lookup"><span data-stu-id="fb11f-122">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>
