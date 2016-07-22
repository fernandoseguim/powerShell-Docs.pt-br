---
title: Melhorias para o OneGet no WMF 5.1 (Preview)
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 1d0bd545b52ef56045f2ec740b05c4e0fd93bb67

---

# Melhorias do OneGet
O WMF 5.1 inclui várias correções e aprimoramentos para abordar algumas das lacunas na experiência do usuário na versão 5.0 do WMF. 

##Alias de versão removido

**Cenário**: se você tiver as versões 1.0 e 2.0 de um pacote, P1, instaladas em seu sistema e desejar desinstalar a versão 1.0, você executará "uninstall-package -name P1 -version 1.0" e esperará a versão 1.0 ser desinstalada após a execução do cmdlet. No entanto o resultado é que a versão 2.0 é desinstalada. 
    
Isso ocorre porque o parâmetro "-version" é um alias do parâmetro "-minimumversion". Quando OneGet está procurando um pacote qualificado com a versão mínima de 1.0, ele retorna a versão mais recente. Esse comportamento é esperado em casos normais, pois encontrar a versão mais recente é geralmente o resultado desejado. No entanto, ele não deve aplicar ao caso de pacote de desinstalação.
    
**Solução**: no WMF 5.1, o alias -version é removido inteiramente no OneGet e no PowerShellGet. 

##Vários prompts para inicializar o provedor do NuGet

**Cenário**: ao executar Find-Module ou Install-module ou outros cmdlets OneGet em seu computador pela primeira vez, o OneGet tenta inicializar o provedor do NuGet. Isso ocorre porque o provedor PowerShellGet também usa o provedor do NuGet para baixar os módulos do PowerShell. O OneGet então solicita permissão do usuário para instalar o provedor do NuGet. Após o usuário selecionar "sim" para a inicialização, a versão mais recente do provedor do NuGet será instalada. 
    
No entanto, em alguns casos, quando há uma versão antiga do provedor do NuGet instalada em seu computador, a versão mais antiga do NuGet às vezes é carregada primeiro na sessão do PowerShell (ou seja, a condição de corrida no OneGet). No entanto, o PowerShellGet requer a versão mais recente do provedor do NuGet para funcionar, portanto, o PowerShellGet solicita que o OneGet inicialize o provedor NuGet novamente. Isso resulta em vários prompts para inicializar o provedor do NuGet.

**Solução**: no WMF 5.1, o OneGet agora carrega a versão mais recente do provedor do NuGet para evitar vários prompts para inicializar o provedor do NuGet.

Você também pode utilizar uma solução alternativa para esse problema excluindo manualmente a versão antiga do provedor do NuGet (NuGet Anycpu.exe), caso ele exista, de $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies


##Suporte para OneGet em computadores somente com acesso à intranet

**Cenário**: no WMF 5.0, o OneGet não dava suporte a computadores com acesso somente à intranet (e não à Internet).

**Solução**: no WMF 5.1, você pode seguir estas etapas para permitir que computadores com intranet usem o OneGet:

1. Baixe o provedor do NuGet usando outro computador que tenha conexão com a Internet usando Install-PackageProvider NuGet.

2. Localize o provedor do NuGet em $env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget ou $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget. 

3. Copie os binários para um local de compartilhamento de rede ou pasta que o computador com intranet possa acessar e, em seguida, instale o provedor do NuGet com "Install-PackageProvider NuGet -Source <Path to folder>".


##Aprimoramentos de registro em log de eventos

Quando você instala pacotes, está alterando o estado do computador. No WMF 5.1, o OneGet agora registra eventos no log de eventos do Windows para atividades de instalar, desinstalar e salvar pacote. O canal de Evento é o mesmo que para o PowerShell, ou seja, Microsoft-Windows-PowerShell, Operacional.

##Suporte para autenticação básica

No WMF 5.1, o OneGet dá suporte para localizar e instalar pacotes de um repositório que requer autenticação básica. Você pode fornecer suas credenciais para os cmdlets Find-Package e Install-Package. Por exemplo:

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
##Suporte para usar OneGet atrás de um proxy

No WMF 5.1, o OneGet agora assume novos parâmetros de proxy: -ProxyCredential e -Proxy. Usando esses parâmetros, você pode especificar a URL do proxy e as credenciais para cmdlets do OneGet. Por padrão, as configurações de proxy do sistema são usadas. Por exemplo:

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```



<!--HONumber=Jul16_HO3-->


