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
# <a name="powershell-gallery-account-settings"></a>Configurações de conta da Galeria do PowerShell

A conta da Galeria do PowerShell é um nome publicamente visível vinculado a uma identidade. Essa identidade é uma ID da Microsoft, como `user@hotmail.com` ou `user@outlook.com`, ou uma conta do AAD (Azure Active Directory).

A Galeria do PowerShell oferece as seguintes configurações de conta:

- A conta de email associada à sua conta da Galeria do PowerShell
- Opções para notificações por email enviadas da Galeria do PowerShell
- A conta de usuário associada à sua conta da Galeria do PowerShell
- A imagem associada à sua conta da Galeria do PowerShell

## <a name="email-address"></a>Endereço de email

O endereço de email é o destino para receber notificações de Galeria do PowerShell. Ele não precisa corresponder à conta de logon. É possível usar qualquer conta de email a que você tem acesso. Seu endereço de email nunca é diretamente fornecido pela Galeria do PowerShell para outros usuários.

![Alterar o endereço de email](../../Images/PSGallery_AcccountEmailAddress.png)

A Galeria do PowerShell envia uma mensagem de verificação quando um novo endereço de email é inserido. O email de verificação tem um link para a Galeria do PowerShell para concluir o processo de alteração. Até a conclusão do processo de verificação, todas as notificações são enviadas para o endereço anterior.

## <a name="email-notifications"></a>Notificações por email

A Galeria do PowerShell oferece as seguintes opções de notificação:

- Os usuários podem entrar em contato comigo por meio da Galeria do PowerShell
- Notificar-me quando um item é movido para a Galeria do PowerShell usando minha conta

![Alterar o endereço de email](../../Images/PSGallery_AccountEmailOptions.png)

Conforme observado na página, as notificações críticas da Galeria do PowerShell não podem ser desabilitadas.
Eles incluem:

- Notificações de segurança
- Notificações de gerenciamento de conta de administradores da Galeria do PowerShell
- Notificações sobre os testes executados na Galeria do PowerShell para envios feitos

## <a name="change-your-login-account"></a>Alterar sua conta de logon

Para alterar a conta de logon, é necessário estar conectado com a conta atual. Realize as seguintes etapas para concluir alteração.

![Configurações da conta de logon](../../Images/PSGallery_LoginAccountSettings.png)

1. Clique em **Alterar conta**. Uma janela pop-up explica que alterar a conta de logon se aplica a todos os usos dessa conta na Galeria do PowerShell. Examine as informações e clique em **OK** para continuar.

   ![Configurações da conta de logon](../../Images/PSGallery_LoginAccountChange-1.png)

2. Em seguida, você precisará entrar usando a _nova conta_.

   ![Configurações da conta de logon](../../Images/PSGallery_LoginAccountChange-2.png)

3. Ao clicar em **Próximo**, será exibida uma mensagem informando que você está conectado com a conta atual.
   Clique em **Sair e entrar com uma conta diferente**.

   ![Configurações da conta de logon](../../Images/PSGallery_LoginAccountChange-3.png)

4. Digite a senha da nova conta. Após inserir a senha, você retornará para a página "Configurações da conta" e verá que a conta de logon foi atualizada.


## <a name="enable-two-factor-authentication-2fa"></a>Habilitar a 2FA (autenticação de dois fatores)

A autenticação de dois fatores é recomendada para todos os usuários que publicam manualmente na Galeria do PowerShell. Para habilitar a autenticação de dois fatores, a conta de logon precisa ter pelo menos duas formas de autenticação registradas. Uma é uma senha, e as outras podem ser:

- Um número de telefone que possa receber mensagens de texto
- Um aplicativo autenticador registrado, como o Microsoft Authenticator para celular

Essas formas de autenticação precisam ser configuradas nas informações da conta do AAD ou nas configurações de segurança da conta da ID da Microsoft.

Após habilitar a 2FA, é necessário usar as formas configuradas de autenticação toda vez que você entrar na Galeria do PowerShell.

> [!IMPORTANT]
> Ao habilitar a autenticação de dois fatores no site da Galeria do PowerShell, não é necessário habilitar a 2FA para todos os usos da conta de logon. Para saber mais, confira [Sobre a verificação em duas etapas](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).

## <a name="change-your-profile-picture"></a>Alterar a foto de perfil

A Galeria do PowerShell usa o Gravatar para armazenar e exibir a imagem associada com seu perfil. Para atualizar sua imagem de perfil, acesse [Gravatar.com](http://www.gravatar.com/).
