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
# <a name="managing-package-owners"></a>Gerenciar proprietários de pacote

A propriedade de um pacote na Galeria do PowerShell é definida pelo usuário que publicou o pacote na galeria.
Às vezes, esses metadados precisam ser gerenciados além da publicação de pacote inicial, o que significa que os metadados de proprietário precisam ser mutáveis, enquanto o próprio pacote não é.

Todos os proprietários de pacote são pares.
Isso significa que qualquer proprietário de pacote pode publicar uma nova versão de um pacote. Isso também significa que qualquer proprietário de pacote pode remover qualquer proprietário de pacote.
Nenhum proprietário tem mais autoridade que outros proprietários.

## <a name="setting-a-packages-initial-owner"></a>Configurar o proprietário inicial de um pacote

Quando um novo pacote é publicado na Galeria do PowerShell, o proprietário inicial é definido pelo usuário que publicou o pacote. Isso é determinado pela chave de API de quem foi usada no cmdlet Publish-Module.

## <a name="adding-owners"></a>Adicionando proprietários

Quando um pacote é publicado na Galeria do PowerShell, é fácil convidar outros usuários para se tornarem proprietários de pacote.

1. [Faça logon](https://powershellgallery.com/users/account/LogOn) na Galeria do PowerShell com a conta que é o proprietário atual de um pacote.
2. Navegue até uma página do pacote, usando a guia "Itens", pesquisando ou clicando em seu nome de usuário e em [**Gerenciar Meus Pacotes**](https://www.powershellgallery.com/account/Packages).
3. Quando estiver conectado como o proprietário de um pacote, você verá um link "Gerenciar proprietários" do lado esquerdo para clicar.
4. Insira o nome de usuário da pessoa a ser adicionada como um proprietário e clique em “Adicionar”.
5. Em seguida, é enviado um email para o novo coproprietário, como um convite para que ele se torne um proprietário de pacote.
6. Depois que o usuário clicar no link, ele será um coproprietário completo com controle total sobre um pacote, incluindo a capacidade de remover outros usuários como proprietários.

**OBSERVAÇÃO**: até que o novo proprietário confirme a propriedade, ele *não* será listado como um proprietário de pacote.
Ao exibir a página **Gerenciar Proprietários**, você verá uma entrada “aprovação pendente” nos proprietários atuais.
Esse convite pode ser removido, da mesma forma que outros proprietários podem ser removidos.
Esse processo de convites impede que os usuários adicionem outros usuários erroneamente como proprietários de seus pacotes.

Observe que os metadados de “Autores” são meramente texto de forma livre; somente “Proprietários” são controlados.


## <a name="removing-owners"></a>Removendo proprietários

Quando um pacote tem vários proprietários e um deles precisa ser removido, o processo é simples:

1. [Faça logon](https://powershellgallery.com/users/account/LogOn) na Galeria do PowerShell com a conta que é o proprietário atual de um pacote;
2. Navegue até uma página do pacote, usando a guia Pacotes, pesquisando ou clicando em seu nome de usuário e em [**Gerenciar Meus Pacotes**](https://www.powershellgallery.com/account/Packages).
3. Quando estiver conectado como o proprietário de um pacote, você verá um link "Gerenciar proprietários" do lado esquerdo para clicar;
4. Clique no link “Remover” ao lado do proprietário a ser removido.



## <a name="transferring-package-ownership"></a>Transferir a propriedade do pacote

Às vezes, recebemos solicitações de suporte para transferir a propriedade do pacote de um usuário para outro, mas quase sempre você pode fazer isso sozinho.
Transferir a propriedade de um usuário para outro é simplesmente uma combinação dos dois recursos acima.

1. O proprietário atual convida o novo usuário para se tornar um coproprietário e o novo usuário aceita o convite;
2. O novo usuário remove o usuário antigo da lista de proprietários.

Essa solicitação chegou de diversas maneiras, mas o processo funciona da mesma forma.

- A propriedade do pacote muda de um desenvolvedor para outro
- O pacote foi publicado acidentalmente usando a conta errada


## <a name="orphaned-packages"></a>Pacotes órfãos

Um último cenário ocorreu, mas não com muita frequência.
Alguns pacotes se tornaram órfãos, e a única conta de proprietário do pacote não pode ser usada para adicionar novos proprietários.
Estes são alguns exemplos desse cenário:

- A conta do proprietário é associada a um endereço de email que não existe mais, e o usuário esqueceu a senha
- O proprietário registrado saiu da empresa que produz o pacote, e não é possível entrar em contato com ele para que atualize a propriedade do pacote
- Devido a um bug que afetou apenas alguns dos pacotes, de alguma forma, não há proprietário para o pacote na galeria

Os administradores da Galeria do PowerShell podem acessar o link "Gerenciar Proprietários" de qualquer pacote.
Se você for o proprietário legítimo de um pacote e não conseguir acessar o proprietário atual para obter permissões de propriedade, use o link "Relatar Abuso" na galeria para entrar em contato com os Administradores da Galeria do PowerShell.
Em seguida, vamos seguir um processo para verificar sua propriedade do pacote.
Se determinarmos que você deve ser o proprietário do pacote, nós mesmos usaremos o link "Gerenciar Proprietários" do pacote e enviaremos o convite para que você se torne um proprietário.
Podemos fazer isso apenas depois de verificar que você deve ser um proprietário e o processo para essa verificação varia de acordo com as circunstâncias.
Muitas vezes, usaremos a URL do Projeto do pacote para encontrar uma maneira de entrar em contato com o proprietário do projeto, mas também podemos usar o Twitter, email ou outros meios para entrar em contato com ele.
