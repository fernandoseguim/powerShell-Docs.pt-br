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
ms.locfileid: "34189747"
---
# <a name="powershell-gallery-gdpr-compliance"></a><span data-ttu-id="aff20-103">Conformidade da Galeria do PowerShell com o GDPR</span><span class="sxs-lookup"><span data-stu-id="aff20-103">PowerShell Gallery GDPR compliance</span></span>

## <a name="overview"></a><span data-ttu-id="aff20-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="aff20-104">Overview</span></span>

<span data-ttu-id="aff20-105">Em maio de 2018, uma lei de privacidade europeia, o GDPR (Regulamento Geral sobre a Proteção de Dados), entrou em vigor.</span><span class="sxs-lookup"><span data-stu-id="aff20-105">In May 2018, a European privacy law, the General Data Protection Regulation (GDPR), takes effect.</span></span>
<span data-ttu-id="aff20-106">O GDPR impõe novas regras para empresas, agências governamentais, organizações sem fins lucrativos e outras entidades que oferecem produtos e serviços a pessoas da EU (União Europeia) ou que coletam e analisam dados vinculados a residentes da UE.</span><span class="sxs-lookup"><span data-stu-id="aff20-106">The GDPR imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data tied to EU residents.</span></span>
<span data-ttu-id="aff20-107">O GDPR aplica-se independentemente de onde você esteja localizado.</span><span class="sxs-lookup"><span data-stu-id="aff20-107">The GDPR applies no matter where you are located.</span></span>

> [!NOTE]
> <span data-ttu-id="aff20-108">Este artigo mostra as etapas para excluir dados pessoais da Galeria do PowerShell e pode ser usado para ajudá-lo a cumprir suas obrigações com o GDPR.</span><span class="sxs-lookup"><span data-stu-id="aff20-108">This article provides steps for how to delete personal data from the PowerShell Gallery and can be used to support your obligations under the GDPR.</span></span> <span data-ttu-id="aff20-109">Se você estiver buscando informações gerais sobre o GDPR, confira a [seção GDPR do portal do serviço de confiança](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span><span class="sxs-lookup"><span data-stu-id="aff20-109">If you’re looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span></span>

## <a name="personally-identifiable-data"></a><span data-ttu-id="aff20-110">Dados de identificação pessoal</span><span class="sxs-lookup"><span data-stu-id="aff20-110">Personally identifiable data</span></span>

<span data-ttu-id="aff20-111">A Galeria do PowerShell armazena as seguintes informações que podem ser fornecidas pelos usuários podendo conter informações pessoais:</span><span class="sxs-lookup"><span data-stu-id="aff20-111">The PowerShell Gallery stores the following information that may be provided by users, which may contain personal information:</span></span>

* <span data-ttu-id="aff20-112">Conta da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="aff20-112">PowerShell Gallery account</span></span>
* <span data-ttu-id="aff20-113">Itens publicados na Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="aff20-113">Items published to the PowerShell Gallery</span></span>
* <span data-ttu-id="aff20-114">Correspondência de email com a equipe da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="aff20-114">Email correspondence with the PowerShell Gallery team</span></span>

<span data-ttu-id="aff20-115">A maioria dos usuários não cria uma conta da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aff20-115">Most users do not create a PowerShell Gallery account.</span></span>
<span data-ttu-id="aff20-116">Não é necessário ter uma conta, a menos que você pretenda publicar um item ou usar o recurso "Contatar Proprietário" na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aff20-116">An account is not required unless you are going to publish an item or use the "Contact Owner" feature in the PowerShell Gallery.</span></span>
<span data-ttu-id="aff20-117">Além da correspondência de email iniciada pelo usuário, a Galeria do PowerShell não armazena dados de identificação pessoal de usuários que não criaram uma conta.</span><span class="sxs-lookup"><span data-stu-id="aff20-117">Other than email correspondence initiated by the user, the PowerShell Gallery does not store personally identifiable data for users who have not created an account.</span></span>

<span data-ttu-id="aff20-118">Os usuários que criam uma conta da Galeria do PowerShell podem publicar itens na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aff20-118">Users who create a PowerShell Gallery account can publish items to the PowerShell Gallery.</span></span>
<span data-ttu-id="aff20-119">Espera-se que esses itens sejam o código do PowerShell, mas eles podem conter outras informações, inclusive informações pessoais.</span><span class="sxs-lookup"><span data-stu-id="aff20-119">Those items are expected to be PowerShell code, but may contain other information including personal information.</span></span>
<span data-ttu-id="aff20-120">As informações abaixo mostrarão como você pode obter todos os itens que já publicou na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aff20-120">The information below will show how you can get all the items you have published to the PowerShell Gallery.</span></span>

## <a name="dsr-export-of-powershell-gallery-data"></a><span data-ttu-id="aff20-121">Exportação de DSR de dados da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="aff20-121">DSR Export of PowerShell Gallery Data</span></span>

<span data-ttu-id="aff20-122">As seções a seguir descrevem como a Galeria do PowerShell permite DSR (solicitações de entidade de dados), explicando como exportar as informações armazenadas na Galeria do PowerShell e como solicitar a exclusão dessas informações.</span><span class="sxs-lookup"><span data-stu-id="aff20-122">The following sections describe how the PowerShell Gallery supports data subject requests (DSR), by explaining how to export information stored in the PowerShell Gallery, and how to request deletion of this information.</span></span>

### <a name="email"></a><span data-ttu-id="aff20-123">Email</span><span class="sxs-lookup"><span data-stu-id="aff20-123">Email</span></span>

<span data-ttu-id="aff20-124">A correspondência de email a seguir pode incluir:</span><span class="sxs-lookup"><span data-stu-id="aff20-124">Email correspondence may include any of the following:</span></span>

* <span data-ttu-id="aff20-125">Email enviado aos proprietários de itens da Galeria do PowerShell se as verificações de análise de código tiverem detectado algum problema em um item publicado por eles na Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="aff20-125">Email sent to the owners of PowerShell Gallery items if the code analysis scans detected an issue with any item they have published to the PowerShell Gallery</span></span>
* <span data-ttu-id="aff20-126">Email enviado por qualquer pessoa para a equipe da Galeria do PowerShell usando o endereço de email na página "Fale Conosco" (cgadmin@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="aff20-126">Email sent by anyone to the PowerShell Gallery team using the email address in the "Contact Us" page (cgadmin@microsoft.com)</span></span>
* <span data-ttu-id="aff20-127">Usuários registrados que usam o recurso "Contatar Proprietário" na Galeria do PowerShell para enviar email ao proprietário de um item da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="aff20-127">Registered users who use the "Contact Owner" feature in the PowerShell Gallery to send email to the owner of an item in the PowerShell Gallery</span></span>

<span data-ttu-id="aff20-128">Os emails enviados pela Galeria do PowerShell ou para ela têm uma política de retenção de 90 dias para embasar possíveis investigações de segurança caso seja descoberto algum código mal-intencionado na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aff20-128">Emails sent by or to the PowerShell Gallery have a retention policy of 90 days to support possible security investigations should malicious code be discovered on the PowerShell Gallery.</span></span>
<span data-ttu-id="aff20-129">Os emails são excluídos pela política após 90 dias.</span><span class="sxs-lookup"><span data-stu-id="aff20-129">Emails are deleted by policy after 90 days.</span></span>

<span data-ttu-id="aff20-130">Você pode solicitar cópias de todos os emails enviados e recebidos entre o seu endereço de email e a Galeria do PowerShell nos últimos 90 dias.</span><span class="sxs-lookup"><span data-stu-id="aff20-130">You may request copies of all emails sent to or from your email address and the PowerShell Gallery within the previous 90 days.</span></span>
<span data-ttu-id="aff20-131">Para solicitar essa correspondência, envie um email para cgadmin@microsoft.com, com o título: "Solicitação de DSR de emails relacionados a essa conta".</span><span class="sxs-lookup"><span data-stu-id="aff20-131">To request this correspondence, send an email to cgadmin@microsoft.com, with the title: "DSR Request for emails relating to this account".</span></span>
<span data-ttu-id="aff20-132">No corpo da mensagem, indique quais informações você está solicitando (por exemplo: Envie-me os emails enviados deste endereço de email ou recebidos por ele.) Todos os emails que envolverem o seu endereço de email nos 90 dias anteriores à solicitação serão enviados em até sete dias úteis.</span><span class="sxs-lookup"><span data-stu-id="aff20-132">In the body of the message, state what information you are requesting (for example: Please send all emails sent to or received from this email address.) All emails involving your email address within 90 days of the request will be sent within 7 business days.</span></span>

### <a name="powershell-gallery-account-information"></a><span data-ttu-id="aff20-133">Informações de conta da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="aff20-133">PowerShell Gallery Account Information</span></span>

<span data-ttu-id="aff20-134">Se você tiver criado uma conta da Galeria do PowerShell, encontre todas as informações pessoais que foram armazenadas na Galeria do PowerShell executando as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="aff20-134">If you have created a PowerShell Gallery account, you can find all personal information that has been stored in PowerShell Gallery by taking the following steps:</span></span>

1. <span data-ttu-id="aff20-135">Entre na Galeria do PowerShell e clique no seu nome de usuário</span><span class="sxs-lookup"><span data-stu-id="aff20-135">Sign in to the PowerShell Gallery, then click on your username</span></span>
2. <span data-ttu-id="aff20-136">A próxima página exibida é a página da Conta, que mostra o endereço de email usado para a conta da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="aff20-136">The next page displayed is the Account page, which shows the email address used for the PowerShell Gallery account</span></span>

<span data-ttu-id="aff20-137">Se você tiver criado mais de uma conta na Galeria do PowerShell, será necessário repetir essas etapas para cada conta.</span><span class="sxs-lookup"><span data-stu-id="aff20-137">If you have created more than one account in the PowerShell Gallery, you will need to repeat these steps for each account.</span></span>

### <a name="items-in-the-powershell-gallery"></a><span data-ttu-id="aff20-138">Itens na Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="aff20-138">Items in the PowerShell Gallery</span></span>

<span data-ttu-id="aff20-139">Para facilitar a exportação de itens publicados na Galeria do PowerShell, nós publicamos o script "GetPSGalleryItemsForAuthor" na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aff20-139">To facilitate exporting items published to the PowerShell Gallery, we have published the script "GetPSGalleryItemsForAuthor" to the PowerShell Gallery.</span></span>
<span data-ttu-id="aff20-140">Esse script exporta uma cópia de cada versão de cada item inserido na Galeria do PowerShell com base nas informações do autor armazenadas no item.</span><span class="sxs-lookup"><span data-stu-id="aff20-140">This script exports a copy of every version of every item put into the PowerShell Gallery based on the author information stored in the item.</span></span>

> [!NOTE]
> <span data-ttu-id="aff20-141">O autor é armazenado no manifesto do item quando o item é publicado.</span><span class="sxs-lookup"><span data-stu-id="aff20-141">The Author is stored in the item manifest when you publish your item.</span></span>
> <span data-ttu-id="aff20-142">Não há nenhuma garantia de que o autor seja a mesma identidade que a da conta usada na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aff20-142">There is no guarantee that the Author is the same identity as the account you use in the PowerShell Gallery.</span></span>
> <span data-ttu-id="aff20-143">Se você usar algum outro valor no campo Autor, será necessário fornecer esse valor ao usar esse script.</span><span class="sxs-lookup"><span data-stu-id="aff20-143">If you use some other value in the Author field, you will need to supply that value when using this script.</span></span>

<span data-ttu-id="aff20-144">Você pode baixar o script usando o seguinte comando do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="aff20-144">You may download the script by using the following PowerShell command:</span></span>

```powershell
Save-Script GetPSGalleryItemsForAuthor -path <local folder location> -repository psgallery
```

<span data-ttu-id="aff20-145">Em seguida, você pode executar o script diretamente, executando os seguintes comandos do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="aff20-145">You can then run the script directly, by running the following PowerShell commands:</span></span>

```powershell
cd <local folder location >
.\GetPSGalleryItemsForAuthor.ps1
```

<span data-ttu-id="aff20-146">Será solicitado que você forneça o autor e uma pasta no sistema na qual deseja que os itens sejam salvos.</span><span class="sxs-lookup"><span data-stu-id="aff20-146">You will be prompted to supply the Author and a folder on your system where you want the items to be saved.</span></span>

## <a name="deleting-personal-data-from-the-powershell-gallery"></a><span data-ttu-id="aff20-147">Excluindo dados pessoais da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="aff20-147">Deleting Personal Data From The PowerShell Gallery</span></span>

<span data-ttu-id="aff20-148">Para excluir sua conta da Galeria do PowerShell ou qualquer item que você tenha na Galeria do PowerShell, envie um email para cgadmin@microsoft.com com o título: "Solicitação do GDPR para itens relacionados a essa conta".</span><span class="sxs-lookup"><span data-stu-id="aff20-148">To delete your PowerShell Gallery account or any item you own in the PowerShell Gallery, send email to cgadmin@microsoft.com with the title: "GDPR Request for items relating to this account".</span></span>
<span data-ttu-id="aff20-149">No corpo da mensagem indique quais informações você deseja excluir.</span><span class="sxs-lookup"><span data-stu-id="aff20-149">In the body of the message state what information you want deleted.</span></span> <span data-ttu-id="aff20-150">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="aff20-150">For example:</span></span>

* <span data-ttu-id="aff20-151">Exclua a versão x.y.z do meu item "nome do item"</span><span class="sxs-lookup"><span data-stu-id="aff20-151">Please delete version x.y.z of my item "item name"</span></span>
* <span data-ttu-id="aff20-152">Exclua todas as versões do meu item "nome do item"</span><span class="sxs-lookup"><span data-stu-id="aff20-152">Please delete all versions of my item "item name"</span></span>
* <span data-ttu-id="aff20-153">Exclua a minha conta da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="aff20-153">Please delete my PowerShell Gallery account</span></span>

<span data-ttu-id="aff20-154">Os administradores da Galeria do PowerShell responderão em até sete dias úteis.</span><span class="sxs-lookup"><span data-stu-id="aff20-154">The PowerShell Gallery administrators will reply within 7 business days.</span></span>
<span data-ttu-id="aff20-155">Os itens especificados serão excluídos em até 30 dias após o envio da solicitação.</span><span class="sxs-lookup"><span data-stu-id="aff20-155">The items specified will be deleted within 30 days after the request is sent.</span></span>
