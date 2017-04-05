---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet, galeria
ms.date: 2016-10-14
contributor: manikb
title: psgallery_status
ms.technology: powershell
ms.openlocfilehash: 48f554793d25c2d5ea10bc202489845f4225b2b9
ms.sourcegitcommit: ba8ed836799ef465e507fa1b8d341ba38459d863
translationtype: HT
---
<a name="powershell-gallery-status"></a>Status da Galeria do PowerShell
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>27/03/2017 – RESOLVIDO: não é possível ver as páginas de scripts e módulos individuais

__Resumo do Impacto__: os links diretos para páginas de scripts e módulos individuais em https://www.powershellgallery.com estavam corrompidos. Isso está sendo relatado atualmente em todas as regiões. Isso não afeta nenhum cmdlet do PowerShellGet, ou seja, Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt dev continuaram funcionando.

__Causa Raiz__: os engenheiros identificaram a causa como um problema para exibir os botões de mídias sociais como o do Facebook na página.  

__Resolução__: engenheiros corrigiram o problema desabilitando as informações de contagem do Facebook.

__Próximas etapas__: abrimos um problema de rastreamento interno para corrigir nosso uso da API do Facebook.

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a>15/12/2016 – não é possível enviar emails por meio do site PowerShellGallery

__Resumo de impacto__: entre 13/12/2016 e 15/12/2016, todas as mensagens enviadas por meio de Contatar Proprietários, Gerenciar Proprietários, Contate o Suporte ou Relatar Abuso não foram recebidas pelos Administradores de Galeria do PowerShell.  
__Causa Raiz__: os engenheiros identificaram a causa como um problema de autenticação com o servidor SMTP.  
__Solução__: os engenheiros conseguiram resolver o problema de autenticação e restaurar a conexão com o servidor SMTP.  
__Próximas etapas__: se você usou os links Contatar Proprietários, Gerenciar Proprietários, Contate o Suporte ou Relatar Abuso para enviar email para cgadmin@microsoft.com durante esse período e não obteve resposta, tente novamente. Pedimos desculpas pelo transtorno.  



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>10/08/2016 – Resolvido: não é possível enviar emails para cgadmin@microsoft.com

__Resumo de Impacto__: entre 05/08/2016 e 10/08/2016, os clientes não conseguiram enviar emails para cgadmin@microsoft.com nem usar o recurso Fale conosco.  
__Causa raiz__: engenheiros identificaram a causa como uma alteração na configuração da conta de email.  
__Resolução__: engenheiros trabalharam para resolver o problema de configuração.  
__Próximas etapas__: se você utilizou o link Fale conosco ou enviou email para cgadmin@microsoft.com durante esse período e nós não respondemos, tente novamente. Agradecemos sua paciência.



## <a name="7132016---download-items-failed"></a>13/07/2016 – Baixar itens com falha

__Resumo de impacto__: entre 11/07/2016 e 13/07/2016, um subconjunto de clientes teve problemas para baixar itens da Galeria do PowerShell. O problema provavelmente se manifesta na seguinte mensagem de erro retornada de Install-Module/Install-Script e Save-Module/Save-Script:

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

__Causa raiz preliminar__: engenheiros identificaram um problema na CDN (Rede de Distribuição de Conteúdo) do Azure, que foi implantada na Galeria do PowerShell em 11/07/2016.  
__Mitigação__: engenheiros desabilitaram a CDN do Azure na Galeria do PowerShell.  
__Próximas etapas__: investigar a causa raiz subjacente e desenvolver uma solução para evitar ocorrências futuras.


## <a name="5192016---download-items-failed"></a>19/05/2016 – Baixar itens com falha
__Resumo de impacto__: entre 17/05/2016 e 19/05/2016, um subconjunto de clientes teve problemas para baixar itens da Galeria do PowerShell. O problema provavelmente se manifesta na seguinte mensagem de erro retornada de Install-Module/Install-Script e Save-Module/Save-Script:

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

__Causa raiz preliminar__: engenheiros identificaram uma interrupção no provedor subjacente da CDN (Rede de Distribuição de Conteúdo) do Azure, que foi implantada na Galeria do PowerShell em 17/05/2016.  
__Mitigação__: engenheiros desabilitaram a CDN do Azure na Galeria do PowerShell.  
__Próximas etapas__: investigar a causa raiz subjacente e desenvolver uma solução para evitar ocorrências futuras.

