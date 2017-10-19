---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery
title: psgallery_status
ms.openlocfilehash: af6111d3c511273571bd978c6d0e7447726c2917
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2017
---
<a name="powershell-gallery-status"></a>Status da Galeria do PowerShell
=========================
## <a name="10102017---powershell-gallery-unavailable-for-2-hours-101017"></a>10/10/2017 - Galeria do PowerShell indisponível por duas horas 10/10/17

__Resumo do impacto__: a Galeria do PowerShell apresentou um período de latência muito alta, resultando em problemas de conexão intermitente, começando aproximadamente às 17h (PDT) 10/10/17. Durante a resolução do problema, o site foi colocado offline por 2 horas, começando aproximadamente às 22h (PDT). O site foi restaurado logo antes da meia-noite 10/10/2017. 
 
__Causa raiz__: a causa raiz da alta latência ainda está sendo investigada.

__Resolução__: foi necessário colocar os serviços Web offline e restaurá-los para resolver o problema principal. 

__Próximas etapas__: a causa raiz do problema original está sendo investigada.

## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a>01/06/2017 – implantar na Automação do Azure indisponível no momento

__Resumo do impacto__: implantar itens com dependências na Automação do Azure da Galeria do PowerShell não está disponível no momento.  Importar itens da Galeria do PowerShell de dentro da Automação do Azure ainda está disponível.  
 
__Causa raiz__: itens que têm dependências de outros e que já foram implantados anteriormente na Automação do Azure, não serão implantados na Automação do Azure. Os engenheiros identificaram um problema em como os modelos ARM são gerados para os itens com dependências na funcionalidade Implantar na Automação do Azure.

__Resolução__: os engenheiros estão trabalhando para resolver o problema.  A solução alternativa atual para os usuários é importar o item da Galeria do PowerShell de dentro da Automação do Azure. 

__Próximas etapas__: os engenheiros vão liberar a correção em breve.  Enquanto isso, use a solução alternativa recomendada. 


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a>11/04/2017 – os usuários não podem fazer logon nas contas do AAD (Azure Active Directory)

__Resumo do impacto__: alguns usuários não conseguem fazer logon na Galeria do PowerShell usando contas do Azure AD. 
 
__Causa raiz__: durante uma atualização para interagir com mais segurança com o AAD, uma alteração de configuração foi ignorada. O teste é feito para validar que a alteração não incluiu certos tipos de contas do AAD, portanto a implantação foi continuada.

__Resolução__: engenheiros identificaram a configuração ausente e corrigiram o problema. 

__Próximas etapas__: modificaremos nossos testes para incluir um conjunto mais amplo de tipos de conta do AAD.

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

```powershell
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

```powershell
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

