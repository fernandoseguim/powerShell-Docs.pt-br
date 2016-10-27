---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet, galeria
ms.date: 2016-10-14
contributor: manikb
title: "Gerenciando proprietários do item"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 00fe57762c6b2bb690255ecaea642f97124f4328

---

# Gerenciando proprietários do item

A propriedade de um item na Galeria do PowerShell é definida pelo usuário que publicou o item na galeria.
Às vezes, esses metadados precisam ser gerenciados além da publicação de item inicial, o que significa que os metadados de proprietário precisam ser mutáveis, enquanto o próprio item não é mutável.

Todos os proprietários de item são pares. Isso significa que qualquer proprietário do item pode publicar uma nova versão de um item. Isso também significa que qualquer proprietário do item pode remover qualquer proprietário do item. Nenhum proprietário tem mais autoridade que outros proprietários.  

## Configurando o proprietário inicial de um item 

Quando um novo item é publicado na Galeria do PowerShell, o proprietário inicial é definido pelo usuário que publicou o item. Isso é determinado pela chave de API de quem foi usada no cmdlet Publish-Module.

## Adicionando proprietários

Quando um item tiver sido publicado na Galeria do PowerShell, é fácil convidar outros usuários para se tornarem proprietários de um item.

1. [Faça logon](https://powershellgallery.com/users/account/LogOn) na Galeria do PowerShell com a conta que é o proprietário atual de um item.
2. Navegue até uma página de item usando a guia “Itens”, pesquisando ou clicando em seu nome de usuário e em [**Gerenciar Meus Itens**](https://www.powershellgallery.com/account/Packages).
3. Quando estiver conectado como o proprietário de um item, você verá um link “Gerenciar proprietários” do lado esquerdo para clicar.
4. Insira o nome de usuário da pessoa a ser adicionada como um proprietário e clique em “Adicionar”.
5. Em seguida, é enviado um email para o novo coproprietário, como um convite para que ele se torne um proprietário de um item.
6. Depois que o usuário clicar no link, ele será um coproprietário completo com controle total sobre um item, incluindo a capacidade de remover outros usuários como proprietários.

**OBSERVAÇÃO**: até que o novo proprietário confirme a propriedade, ele *não* será listado como um proprietário de um item.
Ao exibir a página **Gerenciar Proprietários**, você verá uma entrada “aprovação pendente” nos proprietários atuais.
Esse convite pode ser removido, da mesma forma que outros proprietários podem ser removidos.
Esse processo de convites impede que os usuários adicionem outros usuários erroneamente como proprietários de seus itens.

Observe que os metadados de “Autores” são meramente texto de forma livre; somente “Proprietários” são controlados.


## Removendo proprietários
Quando um item tem vários proprietários e um deles precisa ser removido, o processo é simples:

1. [Faça logon](https://powershellgallery.com/users/account/LogOn) na Galeria do PowerShell com a conta que é o proprietário atual de um item;
2. Navegue até uma página de item usando a guia Itens, pesquisando ou clicando em seu nome de usuário e em [**Gerenciar Meus Itens**](https://www.powershellgallery.com/account/Packages).
3. Quando estiver conectado como o proprietário de um item, você verá um link “Gerenciar proprietários” do lado esquerdo para clicar;
4. Clique no link “Remover” ao lado do proprietário a ser removido.



## Transferindo a propriedade do item
Às vezes, recebemos solicitações de suporte para transferir a propriedade do item de um usuário para outro, mas quase sempre você pode fazer isso sozinho.
Transferir a propriedade de um usuário para outro é simplesmente uma combinação dos dois recursos acima.

1. O proprietário atual convida o novo usuário para se tornar um coproprietário e o novo usuário aceita o convite;
2. O novo usuário remove o usuário antigo da lista de proprietários.

Essa solicitação chegou de diversas maneiras, mas o processo funciona da mesma forma.

* A propriedade do item muda de um desenvolvedor para outro
* O item foi publicado acidentalmente usando a conta errada


## Itens órfãos
Um último cenário ocorreu, mas não com muita frequência.
Alguns itens se tornaram órfãos e a única conta de proprietário do item não pode ser usada para adicionar novos proprietários.
Estes são alguns exemplos desse cenário:

* A conta do proprietário é associada a um endereço de email que não existe mais, e o usuário esqueceu a senha
* O proprietário registrado saiu da empresa que produz o item e não pode ser contatado para atualizar a propriedade do item
* Devido a um bug que afetou apenas alguns dos itens, de alguma forma, não há proprietário para o item na galeria

Os administradores da Galeria do PowerShell podem acessar o link “Gerenciar proprietários” de qualquer item.
Se você for o proprietário legítimo de um item e não conseguir acessar o proprietário atual para obter permissões de propriedade, use o link “Relatar abuso” na galeria para entrar em contato com os Administradores da Galeria do PowerShell.
Em seguida, vamos seguir um processo para verificar sua propriedade do item.
Se determinarmos que você deve ser o proprietário do item, nós mesmos usaremos o link “Gerenciar proprietários” do item e lhe enviaremos o convite para que você se torne um proprietário.
Podemos fazer isso apenas depois de verificar que você deve ser um proprietário e o processo para essa verificação varia de acordo com as circunstâncias.
Muitas vezes, usaremos a URL do Projeto do item para encontrar uma maneira de entrar em contato com o proprietário do projeto, mas também podemos usar o Twitter, email ou outros meios para entrar em contato com o proprietário do projeto.




<!--HONumber=Oct16_HO2-->


