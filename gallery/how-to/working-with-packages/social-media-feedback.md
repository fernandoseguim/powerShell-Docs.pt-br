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
# <a name="providing-feedback-via-social-media-or-comments"></a>Fornecendo comentários por meio de mídia social ou do recurso Comentários

A Galeria do PowerShell dá suporte a duas abordagens para que os usuários forneçam comentários públicos sobre um pacote:

- Use os links na borda esquerda para "compartilhar" um pacote nos sites de mídia social Facebook, LinkedIn ou Twitter;
- Use o recurso Comentário para enviar comentários sobre um pacote e para permitir que os autores detectem comentários sobre os pacotes que eles publicaram.

## <a name="social-media-feedback"></a>Comentários em mídia social

No lado esquerdo da página de cada pacote da Galeria do PowerShell, há links para o LinkedIn, o Facebook e o Twitter.
Clicar nesses links abrirá o site de mídia social e permitirá o compartilhamento rápido de um link para o pacote.

Os usuários precisam fazer logon no site que escolheram para compartilhar o pacote da Galeria do PowerShell.

Recomenda-se fazer isso quando o usuário acha que um pacote é algo que ele recomendaria a outros usuários.
A Galeria do PowerShell verificará cada site de mídia social buscando "compartilhamentos" do pacote e exibirá quantas vezes o pacote foi compartilhado em cada um dos sites de mídia social.
Como isso mostra apenas o número de vezes que algo foi compartilhado, será interpretado que os outros usuários "gostaram" do pacote.

## <a name="comments"></a>Comentários

A Galeria do PowerShell usa o serviço LiveFyre para permitir que os usuários comentem sobre os pacotes.
Os usuários que têm recomendações ou comentários podem usar esse recurso para fornecer comentários que ficam visíveis para qualquer pessoa que visitar a página do pacote.
Os proprietários do pacote podem Seguir este comentário e ser notificados quando alguém postar um comentário.

O sistema de Comentário é baseado no LiveFyre, que é um serviço separado que não é gerenciado pela Microsoft e requer o uso de logon exclusivo.
Na primeira vez que desejar deixar um comentário ou seguir os comentários em um de seus pacotes, será solicitado que você crie uma conta do LiveFyre.

Se você tiver criado uma conta do LiveFyre e feito logon, você poderá criar um comentário que forneça comentários sobre o pacote e, em seguida, clicar em "Postar comentário..." O comentário não ficará visível imediatamente.
Os comentários de pacotes da galeria são moderados pelos administradores da Galeria do PowerShell e todas as postagens são examinadas pelos moderadores antes de serem publicadas e ficarem visíveis para outras pessoas.
Nosso objetivo ao moderar os comentários é garantir que eles se alinhem a um comportamento público consistente com os [Termos de uso](https://www.powershellgallery.com/policies/Terms) da Galeria do PowerShell.

Os proprietários de pacote são incentivados a Seguir os comentários postados no LiveFyre.
É necessária uma conta do LiveFyre e é recomendável usar o mesmo endereço de email usado para publicar o pacote no LiveFyre.
Para Seguir comentários, faça logon no LiveFyre e navegue para qualquer pacote em que você esteja listado como Proprietário.
Abaixo da caixa Comentário na parte inferior de cada pacote, será exibido "+Seguir".
Depois de clicar nisso, o LiveFyre enviará um email para o endereço de email registrado sempre que novos comentários forem feitos no pacote.
