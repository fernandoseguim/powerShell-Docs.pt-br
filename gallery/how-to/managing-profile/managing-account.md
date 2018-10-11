---
ms.date: 09/05/2018
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Configurações de conta da Galeria do PowerShell
ms.openlocfilehash: dd7b8b3a99b5b7fbfec5d7f82b81dd6d5cfb906c
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523121"
---
# <a name="powershell-gallery-account-settings"></a><span data-ttu-id="e4c11-103">Configurações de conta da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4c11-103">PowerShell Gallery Account Settings</span></span>

<span data-ttu-id="e4c11-104">A conta da Galeria do PowerShell é um nome publicamente visível vinculado a uma identidade.</span><span class="sxs-lookup"><span data-stu-id="e4c11-104">Your PowerShell Gallery account is a publicly visible name that is linked to an identity.</span></span> <span data-ttu-id="e4c11-105">Essa identidade é uma ID da Microsoft, como `user@hotmail.com` ou `user@outlook.com`, ou uma conta do AAD (Azure Active Directory).</span><span class="sxs-lookup"><span data-stu-id="e4c11-105">That identity is either a Microsoft ID, like `user@hotmail.com` or `user@outlook.com`, or an Azure Active Directory (AAD) account.</span></span>

<span data-ttu-id="e4c11-106">A Galeria do PowerShell oferece as seguintes configurações de conta:</span><span class="sxs-lookup"><span data-stu-id="e4c11-106">The PowerShell Gallery provides the following account settings:</span></span>

- <span data-ttu-id="e4c11-107">A conta de email associada à sua conta da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4c11-107">The email account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="e4c11-108">Opções para notificações por email enviadas da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4c11-108">Options for email notifications sent from the PowerShell Gallery</span></span>
- <span data-ttu-id="e4c11-109">A conta de usuário associada à sua conta da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4c11-109">The user account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="e4c11-110">A imagem associada à sua conta da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4c11-110">The picture associated with your PowerShell Gallery account</span></span>

## <a name="email-address"></a><span data-ttu-id="e4c11-111">Endereço de email</span><span class="sxs-lookup"><span data-stu-id="e4c11-111">Email address</span></span>

<span data-ttu-id="e4c11-112">O endereço de email é o destino para receber notificações de Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e4c11-112">The email address is the destination for PowerShell Gallery notifications.</span></span> <span data-ttu-id="e4c11-113">Ele não precisa corresponder à conta de logon.</span><span class="sxs-lookup"><span data-stu-id="e4c11-113">It does not have to match the login account.</span></span> <span data-ttu-id="e4c11-114">É possível usar qualquer conta de email a que você tem acesso.</span><span class="sxs-lookup"><span data-stu-id="e4c11-114">You may use any email account you have access to.</span></span> <span data-ttu-id="e4c11-115">Seu endereço de email nunca é diretamente fornecido pela Galeria do PowerShell para outros usuários.</span><span class="sxs-lookup"><span data-stu-id="e4c11-115">Your email address is never directly provided by the PowerShell Gallery to other users.</span></span>

![Alterar o endereço de email](../../Images/PSGallery_AcccountEmailAddress.png)

<span data-ttu-id="e4c11-117">A Galeria do PowerShell envia uma mensagem de verificação quando um novo endereço de email é inserido.</span><span class="sxs-lookup"><span data-stu-id="e4c11-117">When you enter a new email address, the PowerShell Gallery sends a verification mail to that address.</span></span> <span data-ttu-id="e4c11-118">O email de verificação tem um link para a Galeria do PowerShell para concluir o processo de alteração.</span><span class="sxs-lookup"><span data-stu-id="e4c11-118">The verification mail contains a link back to the PowerShell Gallery to complete the change process.</span></span> <span data-ttu-id="e4c11-119">Até a conclusão do processo de verificação, todas as notificações são enviadas para o endereço anterior.</span><span class="sxs-lookup"><span data-stu-id="e4c11-119">Until you complete the verification process, all notifications are sent to the previous address.</span></span>

## <a name="email-notifications"></a><span data-ttu-id="e4c11-120">Notificações por email</span><span class="sxs-lookup"><span data-stu-id="e4c11-120">Email notifications</span></span>

<span data-ttu-id="e4c11-121">A Galeria do PowerShell oferece as seguintes opções de notificação:</span><span class="sxs-lookup"><span data-stu-id="e4c11-121">PowerShell Gallery provides the following notification options:</span></span>

- <span data-ttu-id="e4c11-122">Os usuários podem entrar em contato comigo por meio da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4c11-122">Users can contact me through the PowerShell Gallery</span></span>
- <span data-ttu-id="e4c11-123">Notificar-me quando um item é movido para a Galeria do PowerShell usando minha conta</span><span class="sxs-lookup"><span data-stu-id="e4c11-123">Notify me when an item is pushed to the PowerShell Gallery using my account</span></span>

![Alterar o endereço de email](../../Images/PSGallery_AccountEmailOptions.png)

<span data-ttu-id="e4c11-125">Conforme observado na página, as notificações críticas da Galeria do PowerShell não podem ser desabilitadas.</span><span class="sxs-lookup"><span data-stu-id="e4c11-125">As noted on the page, critical notifications from the PowerShell Gallery can't be disabled.</span></span>
<span data-ttu-id="e4c11-126">Eles incluem:</span><span class="sxs-lookup"><span data-stu-id="e4c11-126">These include:</span></span>

- <span data-ttu-id="e4c11-127">Notificações de segurança</span><span class="sxs-lookup"><span data-stu-id="e4c11-127">Security notifications</span></span>
- <span data-ttu-id="e4c11-128">Notificações de gerenciamento de conta de administradores da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4c11-128">Account management notifications from PowerShell Gallery administrators</span></span>
- <span data-ttu-id="e4c11-129">Notificações sobre os testes executados na Galeria do PowerShell para envios feitos</span><span class="sxs-lookup"><span data-stu-id="e4c11-129">Notifications about the tests run by the PowerShell Gallery for submissions you have made</span></span>

## <a name="change-your-login-account"></a><span data-ttu-id="e4c11-130">Alterar sua conta de logon</span><span class="sxs-lookup"><span data-stu-id="e4c11-130">Change your login account</span></span>

<span data-ttu-id="e4c11-131">Para alterar a conta de logon, é necessário estar conectado com a conta atual.</span><span class="sxs-lookup"><span data-stu-id="e4c11-131">To change the login account, you must be signed in with the current account.</span></span> <span data-ttu-id="e4c11-132">Realize as seguintes etapas para concluir alteração.</span><span class="sxs-lookup"><span data-stu-id="e4c11-132">Use the following steps to complete the change.</span></span>

![Configurações da conta de logon](../../Images/PSGallery_LoginAccountSettings.png)

1. <span data-ttu-id="e4c11-134">Clique em **Alterar conta**.</span><span class="sxs-lookup"><span data-stu-id="e4c11-134">Click on **Change Account**.</span></span> <span data-ttu-id="e4c11-135">Uma janela pop-up explica que alterar a conta de logon se aplica a todos os usos dessa conta na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e4c11-135">A pop-up window explains that changing the login account applies to all uses of that account in the PowerShell Gallery.</span></span> <span data-ttu-id="e4c11-136">Examine as informações e clique em **OK** para continuar.</span><span class="sxs-lookup"><span data-stu-id="e4c11-136">Review the information, then click **OK** to continue.</span></span>

   ![Configurações da conta de logon](../../Images/PSGallery_LoginAccountChange-1.png)

2. <span data-ttu-id="e4c11-138">Em seguida, você precisará entrar usando a _nova conta_.</span><span class="sxs-lookup"><span data-stu-id="e4c11-138">You are then prompted to sign in using the _new account_.</span></span>

   ![Configurações da conta de logon](../../Images/PSGallery_LoginAccountChange-2.png)

3. <span data-ttu-id="e4c11-140">Ao clicar em **Próximo**, será exibida uma mensagem informando que você está conectado com a conta atual.</span><span class="sxs-lookup"><span data-stu-id="e4c11-140">When you click **Next**, you see a message that you are signed in using the current account.</span></span>
   <span data-ttu-id="e4c11-141">Clique em **Sair e entrar com uma conta diferente**.</span><span class="sxs-lookup"><span data-stu-id="e4c11-141">Click **Sign out and sign in with a different account**.</span></span>

   ![Configurações da conta de logon](../../Images/PSGallery_LoginAccountChange-3.png)

4. <span data-ttu-id="e4c11-143">Digite a senha da nova conta.</span><span class="sxs-lookup"><span data-stu-id="e4c11-143">Enter the password of the new account.</span></span> <span data-ttu-id="e4c11-144">Após inserir a senha, você retornará para a página "Configurações da conta" e verá que a conta de logon foi atualizada.</span><span class="sxs-lookup"><span data-stu-id="e4c11-144">After entering the password, you are returned to the Account Settings page showing you that the login account has been updated.</span></span>


## <a name="enable-two-factor-authentication-2fa"></a><span data-ttu-id="e4c11-145">Habilitar a 2FA (autenticação de dois fatores)</span><span class="sxs-lookup"><span data-stu-id="e4c11-145">Enable Two-Factor Authentication (2FA)</span></span>

<span data-ttu-id="e4c11-146">A autenticação de dois fatores é recomendada para todos os usuários que publicam manualmente na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e4c11-146">Two-factor authentication is recommended for all users who publish manually to the PowerShell Gallery.</span></span> <span data-ttu-id="e4c11-147">Para habilitar a autenticação de dois fatores, a conta de logon precisa ter pelo menos duas formas de autenticação registradas.</span><span class="sxs-lookup"><span data-stu-id="e4c11-147">To enable two-factor authentication, the login account must have at least two forms of authentication registered.</span></span> <span data-ttu-id="e4c11-148">Uma é uma senha, e as outras podem ser:</span><span class="sxs-lookup"><span data-stu-id="e4c11-148">One is a password and the other forms can be:</span></span>

- <span data-ttu-id="e4c11-149">Um número de telefone que possa receber mensagens de texto</span><span class="sxs-lookup"><span data-stu-id="e4c11-149">A phone number that can receive text messages</span></span>
- <span data-ttu-id="e4c11-150">Um aplicativo autenticador registrado, como o Microsoft Authenticator para celular</span><span class="sxs-lookup"><span data-stu-id="e4c11-150">A registered authenticator application, such as Microsoft Authenticator for your mobile phone</span></span>

<span data-ttu-id="e4c11-151">Essas formas de autenticação precisam ser configuradas nas informações da conta do AAD ou nas configurações de segurança da conta da ID da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e4c11-151">These forms of authentication must be configured in your AAD account information or in your Microsoft ID Account Security settings.</span></span>

<span data-ttu-id="e4c11-152">Após habilitar a 2FA, é necessário usar as formas configuradas de autenticação toda vez que você entrar na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e4c11-152">Once 2FA is enabled, you are required to authenticate using the configured forms of authentication every time you sign in to the PowerShell Gallery.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e4c11-153">Ao habilitar a autenticação de dois fatores no site da Galeria do PowerShell, não é necessário habilitar a 2FA para todos os usos da conta de logon.</span><span class="sxs-lookup"><span data-stu-id="e4c11-153">Enabling two-factor authentication for the PowerShell Gallery site does not require you to enable 2FA for all uses of your login account.</span></span> <span data-ttu-id="e4c11-154">Para saber mais, confira [Sobre a verificação em duas etapas](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span><span class="sxs-lookup"><span data-stu-id="e4c11-154">For more information, see [About two-step verification](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span></span>

## <a name="change-your-profile-picture"></a><span data-ttu-id="e4c11-155">Alterar a foto de perfil</span><span class="sxs-lookup"><span data-stu-id="e4c11-155">Change your profile picture</span></span>

<span data-ttu-id="e4c11-156">A Galeria do PowerShell usa o Gravatar para armazenar e exibir a imagem associada com seu perfil.</span><span class="sxs-lookup"><span data-stu-id="e4c11-156">The PowerShell Gallery relies on Gravatar to store and display the picture associated with your profile.</span></span> <span data-ttu-id="e4c11-157">Para atualizar sua imagem de perfil, acesse [Gravatar.com](http://www.gravatar.com/).</span><span class="sxs-lookup"><span data-stu-id="e4c11-157">To update your profile image, visit [Gravatar.com](http://www.gravatar.com/).</span></span>
