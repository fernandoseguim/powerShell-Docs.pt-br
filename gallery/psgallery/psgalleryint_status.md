---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet, galeria
ms.date: 2016-10-14
contributor: manikb
title: psgalleryint_status
ms.technology: powershell
ms.openlocfilehash: 58f06ca061a4f171288e75b30698910c701f1da1
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


