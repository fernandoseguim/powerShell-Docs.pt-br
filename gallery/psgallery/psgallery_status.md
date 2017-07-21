---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery
title: psgallery_status
ms.openlocfilehash: 8c325ce1c665181cff646eef6c5e7d55e9081e5e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a name="powershell-gallery-status"></a><span data-ttu-id="57d53-103">Status da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="57d53-103">PowerShell Gallery Status</span></span>
=========================
## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a><span data-ttu-id="57d53-104">01/06/2017 – implantar na Automação do Azure indisponível no momento</span><span class="sxs-lookup"><span data-stu-id="57d53-104">06/01/2017 - Deploy to Azure Automation Currently Unavailable</span></span>

<span data-ttu-id="57d53-105">__Resumo do impacto__: implantar itens com dependências na Automação do Azure da Galeria do PowerShell não está disponível no momento.</span><span class="sxs-lookup"><span data-stu-id="57d53-105">__Summary of Impact__: Deploying items with dependencies to Azure Automation from the PowerShell Gallery is currently unavailable.</span></span>  <span data-ttu-id="57d53-106">Importar itens da Galeria do PowerShell de dentro da Automação do Azure ainda está disponível.</span><span class="sxs-lookup"><span data-stu-id="57d53-106">Importing items from the PowerShell Gallery from inside Azure Automation is still available.</span></span>  
 
<span data-ttu-id="57d53-107">__Causa raiz__: itens que têm dependências de outros e que já foram implantados anteriormente na Automação do Azure, não serão implantados na Automação do Azure.</span><span class="sxs-lookup"><span data-stu-id="57d53-107">__Root Cause__: Items that have dependencies on others, and have been previously deployed to Azure Automation, will not be deployed to Azure Automation.</span></span> <span data-ttu-id="57d53-108">Os engenheiros identificaram um problema em como os modelos ARM são gerados para os itens com dependências na funcionalidade Implantar na Automação do Azure.</span><span class="sxs-lookup"><span data-stu-id="57d53-108">Engineers have identified an issue with how ARM templates are generated for items with dependencies for the Deploy to Azure Automation functionality.</span></span>

<span data-ttu-id="57d53-109">__Resolução__: os engenheiros estão trabalhando para resolver o problema.</span><span class="sxs-lookup"><span data-stu-id="57d53-109">__Resolution__: Engineers are working to resolve issue.</span></span>  <span data-ttu-id="57d53-110">A solução alternativa atual para os usuários é importar o item da Galeria do PowerShell de dentro da Automação do Azure.</span><span class="sxs-lookup"><span data-stu-id="57d53-110">The current workaround for users is to import the item from the PowerShell Gallery from inside Azure Automation.</span></span> 

<span data-ttu-id="57d53-111">__Próximas etapas__: os engenheiros vão liberar a correção em breve.</span><span class="sxs-lookup"><span data-stu-id="57d53-111">__Next Steps__: Engineers will release the fix shortly.</span></span>  <span data-ttu-id="57d53-112">Enquanto isso, use a solução alternativa recomendada.</span><span class="sxs-lookup"><span data-stu-id="57d53-112">In the meantime, please use the recommended workaround.</span></span> 


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a><span data-ttu-id="57d53-113">11/04/2017 – os usuários não podem fazer logon nas contas do AAD (Azure Active Directory)</span><span class="sxs-lookup"><span data-stu-id="57d53-113">04/11/2017 - Users unable to log in with Azure Active Directory (AAD) accounts</span></span>

<span data-ttu-id="57d53-114">__Resumo do impacto__: alguns usuários não conseguem fazer logon na Galeria do PowerShell usando contas do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="57d53-114">__Summary of Impact__: Some users were unable to log in to the PowerShell Gallery using Azure AD Accounts.</span></span> 
 
<span data-ttu-id="57d53-115">__Causa raiz__: durante uma atualização para interagir com mais segurança com o AAD, uma alteração de configuração foi ignorada.</span><span class="sxs-lookup"><span data-stu-id="57d53-115">__Root Cause__: During an update to interact more securely with AAD, a setting change was missed.</span></span> <span data-ttu-id="57d53-116">O teste é feito para validar que a alteração não incluiu certos tipos de contas do AAD, portanto a implantação foi continuada.</span><span class="sxs-lookup"><span data-stu-id="57d53-116">The testing done to validate the change did not include certain types of AAD accounts, so the deployment proceeded.</span></span>

<span data-ttu-id="57d53-117">__Resolução__: engenheiros identificaram a configuração ausente e corrigiram o problema.</span><span class="sxs-lookup"><span data-stu-id="57d53-117">__Resolution__: Engineers identified the missing setting and corrected the problem.</span></span> 

<span data-ttu-id="57d53-118">__Próximas etapas__: modificaremos nossos testes para incluir um conjunto mais amplo de tipos de conta do AAD.</span><span class="sxs-lookup"><span data-stu-id="57d53-118">__Next Steps__: We will be modifying our testing to include a broader set of AAD account types.</span></span>

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="57d53-119">27/03/2017 – RESOLVIDO: não é possível ver as páginas de scripts e módulos individuais</span><span class="sxs-lookup"><span data-stu-id="57d53-119">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="57d53-120">__Resumo do Impacto__: os links diretos para páginas de scripts e módulos individuais em https://www.powershellgallery.com estavam corrompidos.</span><span class="sxs-lookup"><span data-stu-id="57d53-120">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="57d53-121">Isso está sendo relatado atualmente em todas as regiões.</span><span class="sxs-lookup"><span data-stu-id="57d53-121">This was being reported across all the regions.</span></span> <span data-ttu-id="57d53-122">Isso não afeta nenhum cmdlet do PowerShellGet, ou seja, Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt dev continuaram funcionando.</span><span class="sxs-lookup"><span data-stu-id="57d53-122">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt continued to work.</span></span>

<span data-ttu-id="57d53-123">__Causa Raiz__: os engenheiros identificaram a causa como um problema para exibir os botões de mídias sociais como o do Facebook na página.</span><span class="sxs-lookup"><span data-stu-id="57d53-123">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>  

<span data-ttu-id="57d53-124">__Resolução__: engenheiros corrigiram o problema desabilitando as informações de contagem do Facebook.</span><span class="sxs-lookup"><span data-stu-id="57d53-124">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="57d53-125">__Próximas etapas__: abrimos um problema de rastreamento interno para corrigir nosso uso da API do Facebook.</span><span class="sxs-lookup"><span data-stu-id="57d53-125">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="57d53-126">15/12/2016 – não é possível enviar emails por meio do site PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="57d53-126">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="57d53-127">__Resumo de impacto__: entre 13/12/2016 e 15/12/2016, todas as mensagens enviadas por meio de Contatar Proprietários, Gerenciar Proprietários, Contate o Suporte ou Relatar Abuso não foram recebidas pelos Administradores de Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57d53-127">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>  
<span data-ttu-id="57d53-128">__Causa Raiz__: os engenheiros identificaram a causa como um problema de autenticação com o servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="57d53-128">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>  
<span data-ttu-id="57d53-129">__Solução__: os engenheiros conseguiram resolver o problema de autenticação e restaurar a conexão com o servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="57d53-129">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>  
<span data-ttu-id="57d53-130">__Próximas etapas__: se você usou os links Contatar Proprietários, Gerenciar Proprietários, Contate o Suporte ou Relatar Abuso para enviar email para cgadmin@microsoft.com durante esse período e não obteve resposta, tente novamente.</span><span class="sxs-lookup"><span data-stu-id="57d53-130">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="57d53-131">Pedimos desculpas pelo transtorno.</span><span class="sxs-lookup"><span data-stu-id="57d53-131">We apologize for the inconvenience.</span></span>  



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="57d53-132">10/08/2016 – Resolvido: não é possível enviar emails para cgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="57d53-132">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>

<span data-ttu-id="57d53-133">__Resumo de Impacto__: entre 05/08/2016 e 10/08/2016, os clientes não conseguiram enviar emails para cgadmin@microsoft.com nem usar o recurso Fale conosco.</span><span class="sxs-lookup"><span data-stu-id="57d53-133">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>  
<span data-ttu-id="57d53-134">__Causa raiz__: engenheiros identificaram a causa como uma alteração na configuração da conta de email.</span><span class="sxs-lookup"><span data-stu-id="57d53-134">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>  
<span data-ttu-id="57d53-135">__Resolução__: engenheiros trabalharam para resolver o problema de configuração.</span><span class="sxs-lookup"><span data-stu-id="57d53-135">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>  
<span data-ttu-id="57d53-136">__Próximas etapas__: se você utilizou o link Fale conosco ou enviou email para cgadmin@microsoft.com durante esse período e nós não respondemos, tente novamente.</span><span class="sxs-lookup"><span data-stu-id="57d53-136">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="57d53-137">Agradecemos sua paciência.</span><span class="sxs-lookup"><span data-stu-id="57d53-137">Thank you for your patience.</span></span>



## <a name="7132016---download-items-failed"></a><span data-ttu-id="57d53-138">13/07/2016 – Baixar itens com falha</span><span class="sxs-lookup"><span data-stu-id="57d53-138">7/13/2016 - Download Items Failed</span></span>

<span data-ttu-id="57d53-139">__Resumo de impacto__: entre 11/07/2016 e 13/07/2016, um subconjunto de clientes teve problemas para baixar itens da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57d53-139">__Summary of Impact__: Between 7/11/2016 and 7/13/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="57d53-140">O problema provavelmente se manifesta na seguinte mensagem de erro retornada de Install-Module/Install-Script e Save-Module/Save-Script:</span><span class="sxs-lookup"><span data-stu-id="57d53-140">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```PowerShell
PS C:\> Install-Module xStorage 
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because: 
End of Central Directory record could not be found. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ... 
$null = PackageManagement\Install-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult: 
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}' 
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage 
```

<span data-ttu-id="57d53-141">__Causa raiz preliminar__: engenheiros identificaram um problema na CDN (Rede de Distribuição de Conteúdo) do Azure, que foi implantada na Galeria do PowerShell em 11/07/2016.</span><span class="sxs-lookup"><span data-stu-id="57d53-141">__Preliminary root cause__: Engineers identified an issue with Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 7/11/2016.</span></span>  
<span data-ttu-id="57d53-142">__Mitigação__: engenheiros desabilitaram a CDN do Azure na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57d53-142">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>  
<span data-ttu-id="57d53-143">__Próximas etapas__: investigar a causa raiz subjacente e desenvolver uma solução para evitar ocorrências futuras.</span><span class="sxs-lookup"><span data-stu-id="57d53-143">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>


## <a name="5192016---download-items-failed"></a><span data-ttu-id="57d53-144">19/05/2016 – Baixar itens com falha</span><span class="sxs-lookup"><span data-stu-id="57d53-144">5/19/2016 - Download Items Failed</span></span>
<span data-ttu-id="57d53-145">__Resumo de impacto__: entre 17/05/2016 e 19/05/2016, um subconjunto de clientes teve problemas para baixar itens da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57d53-145">__Summary of Impact__: Between 5/17/2016 and 5/19/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="57d53-146">O problema provavelmente se manifesta na seguinte mensagem de erro retornada de Install-Module/Install-Script e Save-Module/Save-Script:</span><span class="sxs-lookup"><span data-stu-id="57d53-146">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```PowerShell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because: 
End of Central Directory record could not be found. 
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install. 
WARNING: Package 'AzureRM' failed to install. 
VERBOSE: Module 'AzureRM.Network' was saved successfully. 
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the 
module 'AzureRM'. 
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully. 
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 + 
$null = PackageManagement\Save-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + 
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage) 
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage 
```

<span data-ttu-id="57d53-147">__Causa raiz preliminar__: engenheiros identificaram uma interrupção no provedor subjacente da CDN (Rede de Distribuição de Conteúdo) do Azure, que foi implantada na Galeria do PowerShell em 17/05/2016.</span><span class="sxs-lookup"><span data-stu-id="57d53-147">__Preliminary root cause__: Engineers identified an outage in the underlying provider of Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 5/17/2016.</span></span>  
<span data-ttu-id="57d53-148">__Mitigação__: engenheiros desabilitaram a CDN do Azure na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57d53-148">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>  
<span data-ttu-id="57d53-149">__Próximas etapas__: investigar a causa raiz subjacente e desenvolver uma solução para evitar ocorrências futuras.</span><span class="sxs-lookup"><span data-stu-id="57d53-149">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>

