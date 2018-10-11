---
ms.date: 09/11/2018
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Criando uma conta da Galeria do PowerShell
ms.openlocfilehash: 08d18310d9e18b00bd9e22efcc552dfd29f8982c
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522814"
---
# <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="ec0e5-103">Criando uma conta da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec0e5-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="ec0e5-104">É necessário criar uma conta antes de publicar algo na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec0e5-104">You must create a PowerShell Gallery account before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="ec0e5-105">As contas da Galeria do PowerShell precisam estar vinculadas a uma conta de logon habilitada por email.</span><span class="sxs-lookup"><span data-stu-id="ec0e5-105">PowerShell Gallery accounts must be linked to an email-enabled login account.</span></span> <span data-ttu-id="ec0e5-106">Essa conta pode ser uma do Azure Active Directory ou uma ID da Microsoft, como uma conta de email do outlook.com ou hotmail.com.</span><span class="sxs-lookup"><span data-stu-id="ec0e5-106">This account can be an Azure Active Directory account or a Microsoft ID, like an email account from outlook.com or hotmail.com.</span></span>

<span data-ttu-id="ec0e5-107">Para criar uma conta da Galeria do PowerShell, acesse [https://PowerShellGallery.com](https://PowerShellGallery.com) e clique em **Entrar**, conforme mostrado na imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="ec0e5-107">To create a PowerShell Gallery account, go to [https://PowerShellGallery.com](https://PowerShellGallery.com) and click on **Sign in** as shown in the following image.</span></span>

![Registrar nova conta](../../Images/CreateAccount-Register.png)

<span data-ttu-id="ec0e5-109">Para usar uma conta do Azure Active Directory, selecione **Conta corporativa ou de estudante** e entre com sua conta.</span><span class="sxs-lookup"><span data-stu-id="ec0e5-109">To use an Azure Active Directory account, select **Work or School Account**, and sign in with your account.</span></span> <span data-ttu-id="ec0e5-110">Para usar uma ID da Microsoft, escolha **Conta pessoal** e entre.</span><span class="sxs-lookup"><span data-stu-id="ec0e5-110">To use a Microsoft ID, choose **Personal Account** and sign in.</span></span>

<span data-ttu-id="ec0e5-111">Em seguida, será solicitado que você crie um nome de usuário para a Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec0e5-111">Next, you are prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="ec0e5-112">Analise os Termos de Uso e a Política de Privacidade, insira um nome de usuário e, em seguida, clique em **Registrar**.</span><span class="sxs-lookup"><span data-stu-id="ec0e5-112">Review the Terms of Use and Privacy Policy, enter a username, and then click **Register**.</span></span>

> [!NOTE]
> <span data-ttu-id="ec0e5-113">Este nome de conta não poderá ser alterado após a criação.</span><span class="sxs-lookup"><span data-stu-id="ec0e5-113">The account name cannot be changed once it is created.</span></span> <span data-ttu-id="ec0e5-114">Para saber mais, confira [Gerenciar proprietários de itens](managing-item-owners.md).</span><span class="sxs-lookup"><span data-stu-id="ec0e5-114">For more information, see [Managing Item Owners](managing-item-owners.md).</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="ec0e5-115">Práticas recomendadas para contas da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec0e5-115">Recommended practices for PowerShell Gallery accounts</span></span>

<span data-ttu-id="ec0e5-116">É importante que a conta de email usada com sua conta da Galeria do PowerShell seja monitorada ativamente.</span><span class="sxs-lookup"><span data-stu-id="ec0e5-116">It's important to actively monitor the email account used with your PowerShell Gallery account.</span></span> <span data-ttu-id="ec0e5-117">Toda a comunicação com os proprietários de itens da Galeria do PowerShell será feita por meio desse endereço de email.</span><span class="sxs-lookup"><span data-stu-id="ec0e5-117">All communication with owners of PowerShell Gallery items is through this email address.</span></span> <span data-ttu-id="ec0e5-118">Quando não for possível entrar em contato com um proprietário de item, a equipe de operações da Galeria do PowerShell poderá precisar excluir o item.</span><span class="sxs-lookup"><span data-stu-id="ec0e5-118">If the PowerShell Gallery Operations team is unable to contact an item owner, we may be required to delete an item.</span></span>

<span data-ttu-id="ec0e5-119">As organizações que publicam na Galeria do PowerShell geralmente criam uma conta externa exclusiva para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="ec0e5-119">Organizations that publish to the PowerShell Gallery often create a unique external account for that purpose.</span></span> <span data-ttu-id="ec0e5-120">É recomendável usar o encaminhamento de email para enviar as notificações para um endereço dentro da sua organização.</span><span class="sxs-lookup"><span data-stu-id="ec0e5-120">We recommend you use email forwarding to forward notifications to an address within your organization.</span></span>

<span data-ttu-id="ec0e5-121">Quando vários proprietários estão associados a um item, todas as notificações da Galeria do PowerShell são enviadas a todos os proprietários.</span><span class="sxs-lookup"><span data-stu-id="ec0e5-121">When multiple owners are associated with an item, all PowerShell Gallery notifications are sent to all owners.</span></span> <span data-ttu-id="ec0e5-122">Para saber mais, confira [Gerenciar proprietários de itens](managing-item-owners.md).</span><span class="sxs-lookup"><span data-stu-id="ec0e5-122">For more information, see [Managing Item Owners](managing-item-owners.md).</span></span>
