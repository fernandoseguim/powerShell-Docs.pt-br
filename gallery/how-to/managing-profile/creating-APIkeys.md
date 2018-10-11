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
# <a name="managing-api-keys"></a>Gerenciar chaves de API

A Galeria do PowerShell dá suporte à criação de várias chaves de API compatíveis com uma série de requisitos de publicação. Uma chave de API pode ser aplicada a um ou mais pacotes, permite privilégios específicos e tem uma data de validade.

> [!IMPORTANT]
> Os usuários que publicaram na Galeria do PowerShell antes da introdução das chaves de API com escopo terão uma "chave de API de acesso completo". As chaves de acesso completo não têm as melhorias de segurança incorporadas às chaves de API com escopo. As chaves de acesso completo nunca perdem a validade e são aplicadas a tudo o que pertence ao usuário. Se essa chave for excluída, não poderá ser recriada.

A imagem a seguir mostra as opções disponíveis ao criar uma chave de API com escopo.

![Criar chaves de API](../../Images/PSGallery_KeyScoped.png)

Neste exemplo, criamos uma chave de API com o nome **AzureRMDataFactory**. Esse valor de chave pode ser usado para efetuar push de pacotes com nomes que começam com "AzureRM.DataFactory" e é válido por 365 dias. Trata-se de um cenário normal quando equipes diferentes trabalham em pacotes distintos dentro da mesma organização. Os membros da equipe têm uma chave que concede privilégios para o pacote específico em que estão trabalhando.
O valor de expiração impede o uso de chaves obsoletas ou esquecidas.

## <a name="using-glob-patterns"></a>Usar padrões glob

Caso você trabalhe com vários pacotes, poderá usar padrões glob para combinar vários pacotes em um grupo. As permissões de chave de API se aplicam a todos os novos pacotes que correspondem ao padrão glob. Por exemplo, o exemplo anterior usa um valor **Padrão Glob** de "AzureRM.DataFactory*". É possível efetuar push de um pacote chamado "AzureRm.DataFactoryV2.Netcore" usando essa chave, pois o pacote corresponde ao padrão glob.

## <a name="create-api-keys-securely"></a>Criar chaves de API com segurança

Por questões de segurança, um valor de chave recém-criado nunca é exibido na tela e só fica disponível com o botão Copiar, conforme mostrado abaixo.

![Obter um novo valor de chave de API](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> Só é possível copiar o valor da chave de API imediatamente após criá-lo ou atualizá-lo. Esse valor não será exibido e não ficará acessível novamente após a atualização da página. Se você perder o valor da chave, será necessário regenerá-lo e copiar a chave depois disso.

## <a name="key-permissions-and-expiration"></a>Expiração e permissões de chave

As chaves de API com escopo podem atribuir qualquer uma das seguintes permissões:

- Efetuar push de novos pacotes
- Efetuar push de pacotes novos ou de atualização
- Remover pacotes da lista

Toda nova chave tem uma expiração. O valor de expiração é medido em dias. Os valores possíveis para expiração são:

- Um dia
- 90 dias
- 180 dias
- 270 dias
- 365 dias (padrão)

Essas configurações não podem ser alteradas após a criação da chave. Não é possível criar uma nova chave que não expira.

## <a name="editing-and-deleting-existing-api-keys"></a>Editar e excluir chaves de API existentes

É possível alterar algumas configurações de uma chave existente. Conforme mencionado anteriormente, não é possível modificar o escopo de segurança de uma chave de API existente ou alterar a expiração. As opções que podem ser alteradas são mostradas na captura de tela a seguir:

![Obter um novo valor de chave de API](../../Images/PSGallery_EditAPIKey.png)

Para alterar os pacotes controlados por uma chave, escolha pacotes individuais na lista ou altere o padrão glob.

Ao clicar em **Regenerar**, um novo valor de chave é criado. Do mesmo modo que a chave foi inicialmente criada, é necessário **Copiar** o valor de chave imediatamente após a atualização. A opção **Copiar** não estará mais disponível depois que você sair da página.

Clicar em **Excluir** mostra uma mensagem de confirmação. Depois de excluída, uma chave não pode mais ser usada.

## <a name="key-expiration"></a>Expiração da chave

Dez dias antes da expiração, a Galeria do PowerShell envia um aviso para o email do titular da conta da chave de API. Após a expiração, a chave não pode mais ser usada. Uma mensagem de aviso é exibida na parte superior da página de gerenciamento de chaves de API, mostrando quais delas não são mais válidas. É possível gerar um novo valor de chave.
