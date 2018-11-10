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
# <a name="creating-a-powershell-gallery-account"></a>Criando uma conta da Galeria do PowerShell

É necessário criar uma conta antes de publicar algo na Galeria do PowerShell.
As contas da Galeria do PowerShell precisam estar vinculadas a uma conta de logon habilitada por email. Essa conta pode ser uma do Azure Active Directory ou uma ID da Microsoft, como uma conta de email do outlook.com ou hotmail.com.

Para criar uma conta da Galeria do PowerShell, acesse [https://PowerShellGallery.com](https://PowerShellGallery.com) e clique em **Entrar**, conforme mostrado na imagem a seguir.

![Registrar nova conta](../../Images/CreateAccount-Register.png)

Para usar uma conta do Azure Active Directory, selecione **Conta corporativa ou de estudante** e entre com sua conta. Para usar uma ID da Microsoft, escolha **Conta pessoal** e entre.

Em seguida, será solicitado que você crie um nome de usuário para a Galeria do PowerShell. Analise os Termos de Uso e a Política de Privacidade, insira um nome de usuário e, em seguida, clique em **Registrar**.

> [!NOTE]
> Este nome de conta não poderá ser alterado após a criação. Para saber mais, confira [Gerenciar proprietários de pacotes](managing-package-owners.md).

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>Práticas recomendadas para contas da Galeria do PowerShell

É importante que a conta de email usada com sua conta da Galeria do PowerShell seja monitorada ativamente. Toda a comunicação com os proprietários de pacotes da Galeria do PowerShell será feita por esse endereço de email. Quando não for possível entrar em contato com um proprietário de pacote, a equipe de operações da Galeria do PowerShell poderá precisar excluir o pacote.

As organizações que publicam na Galeria do PowerShell geralmente criam uma conta externa exclusiva para essa finalidade. É recomendável usar o encaminhamento de email para enviar as notificações para um endereço dentro da sua organização.

Quando vários proprietários estão associados a um pacote, todas as notificações da Galeria do PowerShell são enviadas a todos os proprietários. Para saber mais, confira [Gerenciar proprietários de pacotes](managing-package-owners.md).
