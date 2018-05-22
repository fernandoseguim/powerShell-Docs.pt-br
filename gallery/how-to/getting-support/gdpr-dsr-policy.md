---
ms.date: 03/27/2018
contributor: JKeithB
keywords: galeria,powershell,psgallery,GDPR
title: Conformidade da Galeria do PowerShell com o GDPR
ms.openlocfilehash: dca1a82952c284980a84caafa13b2807e47e25a0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="powershell-gallery-gdpr-compliance"></a>Conformidade da Galeria do PowerShell com o GDPR

## <a name="overview"></a>Visão geral

Em maio de 2018, uma lei de privacidade europeia, o GDPR (Regulamento Geral sobre a Proteção de Dados), entrou em vigor.
O GDPR impõe novas regras para empresas, agências governamentais, organizações sem fins lucrativos e outras entidades que oferecem produtos e serviços a pessoas da EU (União Europeia) ou que coletam e analisam dados vinculados a residentes da UE.
O GDPR aplica-se independentemente de onde você esteja localizado.

> [!NOTE]
> Este artigo mostra as etapas para excluir dados pessoais da Galeria do PowerShell e pode ser usado para ajudá-lo a cumprir suas obrigações com o GDPR. Se você estiver buscando informações gerais sobre o GDPR, confira a [seção GDPR do portal do serviço de confiança](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## <a name="personally-identifiable-data"></a>Dados de identificação pessoal

A Galeria do PowerShell armazena as seguintes informações que podem ser fornecidas pelos usuários podendo conter informações pessoais:

* Conta da Galeria do PowerShell
* Itens publicados na Galeria do PowerShell
* Correspondência de email com a equipe da Galeria do PowerShell

A maioria dos usuários não cria uma conta da Galeria do PowerShell.
Não é necessário ter uma conta, a menos que você pretenda publicar um item ou usar o recurso "Contatar Proprietário" na Galeria do PowerShell.
Além da correspondência de email iniciada pelo usuário, a Galeria do PowerShell não armazena dados de identificação pessoal de usuários que não criaram uma conta.

Os usuários que criam uma conta da Galeria do PowerShell podem publicar itens na Galeria do PowerShell.
Espera-se que esses itens sejam o código do PowerShell, mas eles podem conter outras informações, inclusive informações pessoais.
As informações abaixo mostrarão como você pode obter todos os itens que já publicou na Galeria do PowerShell.

## <a name="dsr-export-of-powershell-gallery-data"></a>Exportação de DSR de dados da Galeria do PowerShell

As seções a seguir descrevem como a Galeria do PowerShell permite DSR (solicitações de entidade de dados), explicando como exportar as informações armazenadas na Galeria do PowerShell e como solicitar a exclusão dessas informações.

### <a name="email"></a>Email

A correspondência de email a seguir pode incluir:

* Email enviado aos proprietários de itens da Galeria do PowerShell se as verificações de análise de código tiverem detectado algum problema em um item publicado por eles na Galeria do PowerShell
* Email enviado por qualquer pessoa para a equipe da Galeria do PowerShell usando o endereço de email na página "Fale Conosco" (cgadmin@microsoft.com)
* Usuários registrados que usam o recurso "Contatar Proprietário" na Galeria do PowerShell para enviar email ao proprietário de um item da Galeria do PowerShell

Os emails enviados pela Galeria do PowerShell ou para ela têm uma política de retenção de 90 dias para embasar possíveis investigações de segurança caso seja descoberto algum código mal-intencionado na Galeria do PowerShell.
Os emails são excluídos pela política após 90 dias.

Você pode solicitar cópias de todos os emails enviados e recebidos entre o seu endereço de email e a Galeria do PowerShell nos últimos 90 dias.
Para solicitar essa correspondência, envie um email para cgadmin@microsoft.com, com o título: "Solicitação de DSR de emails relacionados a essa conta".
No corpo da mensagem, indique quais informações você está solicitando (por exemplo: Envie-me os emails enviados deste endereço de email ou recebidos por ele.) Todos os emails que envolverem o seu endereço de email nos 90 dias anteriores à solicitação serão enviados em até sete dias úteis.

### <a name="powershell-gallery-account-information"></a>Informações de conta da Galeria do PowerShell

Se você tiver criado uma conta da Galeria do PowerShell, encontre todas as informações pessoais que foram armazenadas na Galeria do PowerShell executando as seguintes etapas:

1. Entre na Galeria do PowerShell e clique no seu nome de usuário
2. A próxima página exibida é a página da Conta, que mostra o endereço de email usado para a conta da Galeria do PowerShell

Se você tiver criado mais de uma conta na Galeria do PowerShell, será necessário repetir essas etapas para cada conta.

### <a name="items-in-the-powershell-gallery"></a>Itens na Galeria do PowerShell

Para facilitar a exportação de itens publicados na Galeria do PowerShell, nós publicamos o script "GetPSGalleryItemsForAuthor" na Galeria do PowerShell.
Esse script exporta uma cópia de cada versão de cada item inserido na Galeria do PowerShell com base nas informações do autor armazenadas no item.

> [!NOTE]
> O autor é armazenado no manifesto do item quando o item é publicado.
> Não há nenhuma garantia de que o autor seja a mesma identidade que a da conta usada na Galeria do PowerShell.
> Se você usar algum outro valor no campo Autor, será necessário fornecer esse valor ao usar esse script.

Você pode baixar o script usando o seguinte comando do PowerShell:

```powershell
Save-Script GetPSGalleryItemsForAuthor -path <local folder location> -repository psgallery
```

Em seguida, você pode executar o script diretamente, executando os seguintes comandos do PowerShell:

```powershell
cd <local folder location >
.\GetPSGalleryItemsForAuthor.ps1
```

Será solicitado que você forneça o autor e uma pasta no sistema na qual deseja que os itens sejam salvos.

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>Excluindo dados pessoais da Galeria do PowerShell

Para excluir sua conta da Galeria do PowerShell ou qualquer item que você tenha na Galeria do PowerShell, envie um email para cgadmin@microsoft.com com o título: "Solicitação do GDPR para itens relacionados a essa conta".
No corpo da mensagem indique quais informações você deseja excluir. Por exemplo:

* Exclua a versão x.y.z do meu item "nome do item"
* Exclua todas as versões do meu item "nome do item"
* Exclua a minha conta da Galeria do PowerShell

Os administradores da Galeria do PowerShell responderão em até sete dias úteis.
Os itens especificados serão excluídos em até 30 dias após o envio da solicitação.
