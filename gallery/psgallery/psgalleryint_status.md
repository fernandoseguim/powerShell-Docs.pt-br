---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery
title: psgalleryint_status
ms.openlocfilehash: 4f7d300bb07fcbdb100c2fb029f8f66ab260fe7a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
<a name="powershell-gallery-status"></a><span data-ttu-id="f19e2-103">Status da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f19e2-103">PowerShell Gallery Status</span></span>
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="f19e2-104">27/03/2017 – RESOLVIDO: não é possível ver as páginas de scripts e módulos individuais</span><span class="sxs-lookup"><span data-stu-id="f19e2-104">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="f19e2-105">__Resumo do Impacto__: os links diretos para páginas de scripts e módulos individuais em https://www.powershellgallery.com estavam corrompidos.</span><span class="sxs-lookup"><span data-stu-id="f19e2-105">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="f19e2-106">Isso está sendo relatado atualmente em todas as regiões.</span><span class="sxs-lookup"><span data-stu-id="f19e2-106">This was being reported across all the regions.</span></span> <span data-ttu-id="f19e2-107">Isso não afetou nenhum cmdlet do PowerShellGet, ou seja, Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script continuaram funcionando.</span><span class="sxs-lookup"><span data-stu-id="f19e2-107">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script continued to work.</span></span>

<span data-ttu-id="f19e2-108">__Causa Raiz__: os engenheiros identificaram a causa como um problema para exibir os botões de mídias sociais como o do Facebook na página.</span><span class="sxs-lookup"><span data-stu-id="f19e2-108">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>

<span data-ttu-id="f19e2-109">__Resolução__: engenheiros corrigiram o problema desabilitando as informações de contagem do Facebook.</span><span class="sxs-lookup"><span data-stu-id="f19e2-109">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="f19e2-110">__Próximas etapas__: abrimos um problema de rastreamento interno para corrigir nosso uso da API do Facebook.</span><span class="sxs-lookup"><span data-stu-id="f19e2-110">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="f19e2-111">15/12/2016 – não é possível enviar emails por meio do site PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="f19e2-111">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="f19e2-112">__Resumo de impacto__: entre 13/12/2016 e 15/12/2016, todas as mensagens enviadas por meio de Contatar Proprietários, Gerenciar Proprietários, Contate o Suporte ou Relatar Abuso não foram recebidas pelos Administradores de Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f19e2-112">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="f19e2-113">__Causa Raiz__: os engenheiros identificaram a causa como um problema de autenticação com o servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="f19e2-113">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>
<span data-ttu-id="f19e2-114">__Solução__: os engenheiros conseguiram resolver o problema de autenticação e restaurar a conexão com o servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="f19e2-114">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>
<span data-ttu-id="f19e2-115">__Próximas etapas__: se você usou os links Contatar Proprietários, Gerenciar Proprietários, Contate o Suporte ou Relatar Abuso para enviar email para cgadmin@microsoft.com durante esse período e não obteve resposta, tente novamente.</span><span class="sxs-lookup"><span data-stu-id="f19e2-115">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="f19e2-116">Pedimos desculpas pelo transtorno.</span><span class="sxs-lookup"><span data-stu-id="f19e2-116">We apologize for the inconvenience.</span></span>


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="f19e2-117">10/08/2016 – Resolvido: não é possível enviar emails para cgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="f19e2-117">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>
<span data-ttu-id="f19e2-118">__Resumo de Impacto__: entre 05/08/2016 e 10/08/2016, os clientes não conseguiram enviar emails para cgadmin@microsoft.com nem usar o recurso Fale conosco.</span><span class="sxs-lookup"><span data-stu-id="f19e2-118">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>
<span data-ttu-id="f19e2-119">__Causa raiz__: engenheiros identificaram a causa como uma alteração na configuração da conta de email.</span><span class="sxs-lookup"><span data-stu-id="f19e2-119">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>
<span data-ttu-id="f19e2-120">__Resolução__: engenheiros trabalharam para resolver o problema de configuração.</span><span class="sxs-lookup"><span data-stu-id="f19e2-120">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>
<span data-ttu-id="f19e2-121">__Próximas etapas__: se você utilizou o link Fale conosco ou enviou email para cgadmin@microsoft.com durante esse período e nós não respondemos, tente novamente.</span><span class="sxs-lookup"><span data-stu-id="f19e2-121">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="f19e2-122">Agradecemos sua paciência.</span><span class="sxs-lookup"><span data-stu-id="f19e2-122">Thank you for your patience.</span></span>