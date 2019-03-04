---
title: Parâmetros comuns de fluxo de trabalho | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5891467-8e13-484d-b7af-32e6bffab35d
caps.latest.revision: 4
ms.openlocfilehash: 2aca4483e500432ef9f52804e85678d2268aa4cd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856132"
---
# <a name="common-workflow-parameters"></a>Parâmetros de fluxo de trabalho comuns

Uma atividade de fluxo de trabalho gerada a partir de um cmdlet do Windows PowerShell define um número de parâmetros ou comuns a todas as atividades. Um subconjunto desses parâmetros pode ser especificado no momento da criação para que os autores de fluxo de trabalho possam personalizar as atividades. Outro subconjunto desses parâmetros pode ser especificado pelo usuário ao chamar a atividade.

Os parâmetros comuns de fluxo de trabalho são agrupados em várias categorias.

## <a name="connectivity-parameters"></a>Parâmetros de conectividade

|Nome|Tipo|Descrição|Pode ser especificado pelo usuário final em tempo de execução?|Pode ser especificado pelo autor de fluxo de trabalho no momento da criação?|Pode ser especificado pelo autor de fluxo de trabalho na instanciação?|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|String[]|Uma lista de nomes de computador para o qual iniciar trabalhos.|Sim|Sim|Sim|
|PSCredential|[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)|A credencial de autenticação a usar para fazer logon no computador especificado pelo parâmetro PSComputerName. Esse parâmetro é válido somente se PSComputerName for especificado.|Sim|Sim|Sim|
|PSPort|UInt32|A porta a ser usado para executar o fluxo de trabalho.|Sim|Sim|Sim|
|PSUseSSL|Booliano|Use protocolo seguro Sockets Layer (SSL) para estabelecer uma conexão segura com o computador remoto para executar o fluxo de trabalho.|Sim|Sim|Sim|
|PSConfigurationName|Cadeia de caracteres|A configuração de sessão usada para executar o fluxo de trabalho.|Sim|Sim|Sim|
|PSApplicationName|Cadeia de caracteres|A parte do nome de aplicativo do URI de conexão para a execução de fluxo de trabalho. Use este parâmetro somente quando você não estiver usando o parâmetro ConnectionURI.|Sim|Sim|Sim|
|PSThrottleLimit|UInt32|O número máximo de conexões simultâneas que podem ser estabelecidas para executar o fluxo de trabalho.|Sim|TBD|Sim|
|PSConnectionURI|String[]|Uma matriz de URIs totalmente qualificado que especificam os pontos de extremidade para as sessões interativas, usadas para executar o fluxo de trabalho.|Sim|Sim|Sim|
|PSAllowRedirection|Booliano|Especifica se deve permitir o redirecionamento dessa conexão para um URI alternativo para executar o fluxo de trabalho.|Sim|Sim|Sim|
|PSSessionOption|[System.Management.Automation.Remoting.Pssessionoption](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|Opções avançadas para a sessão usada para executar o fluxo de trabalho.|Sim|Sim|Sim|
|PSAuthentication|[System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|Um valor igual a [authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism) enumeração que especifica o mecanismo de autenticação usado para autenticar as credenciais do usuário.|Sim|Sim|Sim|
|PSCertificateThumbprint|Cadeia de caracteres|Digital certificado de chave pública (X509) de uma conta de usuário que tenha permissão para executar o fluxo de trabalho.|Sim|Sim|Sim|

### <a name="behavior-parameters"></a>Parâmetros de comportamento