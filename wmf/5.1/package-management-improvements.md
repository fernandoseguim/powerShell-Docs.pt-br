---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
contributor: jianyunt, quoctruong
title: Melhorias ao Gerenciamento de Pacotes do WMF 5.1
ms.openlocfilehash: b55a1742530b7cd48d60d79b7d4866ebee80a3b6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="improvements-to-package-management-in-wmf-51"></a>Melhorias no gerenciamento de pacote no WMF 5.1#

## <a name="improvements-in-packagemanagement"></a>Melhorias ao PackageManagement ##
Veja a seguir as correções feitas no WMF 5.1: 

### <a name="version-alias"></a>Alias de versão

**Cenário**: se você tiver as versões 1.0 e 2.0 de um pacote, P1, instaladas em seu sistema e desejar desinstalar a versão 1.0, você executará `Uninstall-Package -Name P1 -Version 1.0` e esperará a versão 1.0 ser desinstalada após a execução do cmdlet. No entanto o resultado é que a versão 2.0 é desinstalada.  
    
Isso ocorre porque o parâmetro `-Version` é um alias do parâmetro `-MinimumVersion`. Quando PackageManagement está procurando um pacote qualificado com a versão mínima de 1.0, ele retorna a versão mais recente. Esse comportamento é esperado em casos normais, pois encontrar a versão mais recente é geralmente o resultado desejado. No entanto, ele não deve se aplicar ao caso de `Uninstall-Package`.
    
**Solução**: alias `-Version` removido inteiramente em PackageManagement (também conhecido como OneGet) e PowerShellGet. 

### <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a>Vários prompts para inicializar o provedor do NuGet

**Cenário**: ao executar `Find-Module` ou `Install-Module` ou outros cmdlets PackageManagement em seu computador pela primeira vez, o PackageManagement tenta inicializar o provedor de NuGet. Isso ocorre porque o provedor PowerShellGet também usa o provedor do NuGet para baixar os módulos do PowerShell. Depois, o PackageManagement solicita permissão do usuário para instalar o provedor de NuGet. Após o usuário selecionar "sim" para a inicialização, a versão mais recente do provedor do NuGet será instalada. 
    
No entanto, em alguns casos, quando há uma versão antiga do provedor de NuGet instalada em seu computador, a versão mais antiga do NuGet às vezes é carregada primeiro na sessão do PowerShell (ou seja, a condição de corrida no PackageManagement). No entanto, o PowerShellGet requer a versão mais recente do provedor de NuGet para funcionar, portanto, o PowerShellGet solicita que o PackageManagement inicialize o provedor de NuGet novamente. Isso resulta em vários prompts para inicializar o provedor do NuGet.

**Solução**: no WMF 5.1, o PackageManagement carrega a versão mais recente do provedor de NuGet para evitar vários prompts para inicialização do provedor de NuGet.

Você também pode utilizar uma solução alternativa para esse problema excluindo manualmente a versão antiga do provedor do NuGet (NuGet Anycpu.exe), caso ele exista, de $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies


### <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a>Suporte para PackageManagement em computadores somente com acesso à intranet

**Cenário**: para o cenário corporativo, as pessoas estão trabalhando em um ambiente em que não há acesso à Internet, somente à intranet. O PackageManagement não dava suporte a esse caso no WMF 5.0.

**Cenário**: no WMF 5.0, o PackageManagement não dava suporte a computadores com acesso somente à intranet (e não à Internet).

**Solução**: no WMF 5.1, você pode seguir estas etapas para permitir que computadores com intranet usem o PackageManagement:

1. Baixe o provedor de NuGet usando outro computador que tenha conexão com a Internet usando `Install-PackageProvider -Name NuGet`.

2. Localize o provedor de NuGet em `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` ou `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.

3. Copie os binários para um local de compartilhamento de rede ou pasta que o computador com intranet possa acessar e, em seguida, instale o provedor de NuGet com `Install-PackageProvider -Name NuGet -Source <Path to folder>`.


### <a name="event-logging-improvements"></a>Aprimoramentos de registro em log de eventos

Quando você instala pacotes, está alterando o estado do computador. No WMF 5.1, o PackageManagement agora registra eventos no log de eventos do Windows para atividades `Install-Package`, `Uninstall-Package` e `Save-Package`. O log de eventos é o mesmo do PowerShell, ou seja, `Microsoft-Windows-PowerShell, Operational`.

### <a name="support-for-basic-authentication"></a>Suporte para autenticação básica

No WMF 5.1, o PackageManagement dá suporte para localizar e instalar pacotes de um repositório que requer autenticação básica. Você pode fornecer suas credenciais para os cmdlets `Find-Package` e `Install-Package`. Por exemplo:

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
### <a name="support-for-using-packagemanagement-behind-a-proxy"></a>Suporte para usar o PackageManagement atrás de um proxy

No WMF 5.1, agora o PackageManagement leva novos parâmetros de proxy `-ProxyCredential` e `-Proxy`. Usando esses parâmetros, você pode especificar a URL do proxy e as credenciais para cmdlets do PackageManagement. Por padrão, as configurações de proxy do sistema são usadas. Por exemplo:

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```

