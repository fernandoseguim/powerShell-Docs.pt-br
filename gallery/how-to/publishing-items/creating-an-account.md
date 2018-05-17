---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery
title: Criando uma conta da Galeria do PowerShell
ms.openlocfilehash: 3ec9ad8f979fc0b88fbee72fc28ad1e3394eb01d
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
## <a name="creating-a-powershell-gallery-account"></a>Criando uma conta da Galeria do PowerShell

Uma conta da Galeria do PowerShell deve ser estabelecida antes de publicar algo na Galeria do PowerShell.
As contas da Galeria do PowerShell devem ser vinculadas a uma conta do Azure Active Directory habilitada por email ou a uma conta de email da Microsoft (com um domínio do outlook.com, do hotmail.com, etc.)

Para criar uma conta da Galeria do PowerShell, acesse https://PowerShellGallery.com e clique em "Registrar" (veja a imagem abaixo).

![Registrar nova conta](../../Images/CreatingAccount-Register.png)

Na próxima página, para usar uma conta do Azure Active Directory, selecione "Conta de trabalho ou de escola" e faça logon com sua conta.
Para usar uma conta da Microsoft, como uma no domínio Hotmail.com ou Outlook.com, escolha "Conta pessoal" e faça logon.

Depois de fazer logon, será solicitado que você crie um nome de usuário para a Galeria do PowerShell.
Examine os termos de uso e a política de privacidade vinculados, insira um nome de usuário e, em seguida, clique em Registrar.

Observação: este nome de conta não poderá ser alterado após a criação.
Consulte [Gerenciando proprietários do item](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) para obter detalhes adicionais relacionados a isso.

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>Práticas recomendadas para contas da Galeria do PowerShell

É importante que a conta de email usada com sua conta da Galeria do PowerShell seja monitorada ativamente.
Toda a comunicação com os proprietários de itens da Galeria do PowerShell é feita por email usando o endereço associado à sua conta da Galeria do PowerShell.
Quando não for possível entrar em contato com um proprietário de item, a equipe de operações poderá precisar excluir o item em algumas circunstâncias.

As organizações que publicam na Galeria do PowerShell geralmente criam uma conta exclusiva para essa finalidade no Outlook.com ou em outro domínio de conta da Microsoft.
Em muitos casos essa conta não é monitorada regularmente.
Nesse caso, uma prática recomendada é usar o encaminhamento do Outlook para enviar email para outra conta, normalmente uma conta da organização, que será monitorada pelos proprietários do item.

Se houver vários proprietários associados a um item, todas as comunicações que vierem da Galeria do PowerShell irão para todos os proprietários.
Consulte [Gerenciando proprietários do item](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) para obter detalhes adicionais de como adicionar proprietários para um item.