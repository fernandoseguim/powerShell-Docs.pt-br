---
title: "Melhorias do PackageManagement (também conhecido como OneGet)"
contributor: jianyunt, quoctruong
translationtype: Human Translation
ms.sourcegitcommit: 3b5a3bb0ef9cf123c0cee4a36890ac61431c85ff
ms.openlocfilehash: bb1129e6aa20b64e94ddb6d7b7cf7b51b1df9ca3

---

>Observação: dê um título descritivo proposto e uma breve descrição

## Melhorias do PackageManagement (também conhecido como OneGet) ##
A seguir estão as correções feitas do WMF 5.1 abordar algumas das lacunas na experiência do usuário versão 5.0 do WMF. 

1 **Alias de versão**

**Cenário**: supondo que você tenha a versão 1.0 e 2.0 de um pacote, P1, instaladas em seu sistema, e agora você deseja desinstalar a versão 1.0, execute "uninstall-package -name P1 -version 1.0". Você espera que a versão 1.0 seja desinstalada após a execução do cmdlet. No entanto o resultado é que a versão 2.0 é desinstalada. 
    
A causa do problema é que o parâmetro "-version" é um alias do parâmetro "-minimumversion". Quando OneGet está procurando por um pacote qualificado com a versão mínima de 1.0, ele retorna a versão mais recente. Esse comportamento é esperado em casos normais, pois encontrar a versão mais recente é o que a maioria das pessoas quer. No entanto, ele não deve aplicar ao caso de pacote de desinstalação.
    
**Solução**: alias -version removido totalmente em OneGet e PowerShellGet. 

2 **Vários prompts para inicializar o provedor do NuGet**

**Cenário**: ao executar Find-Module, install-module ou outros cmdlets OneGet em seu computador pela primeira vez, o OneGet tenta inicializar o provedor NuGet. Isso ocorre porque o provedor PowershellGet também usa o provedor do NuGet para baixar os módulos do PowerShell. O OneGet então solicita permissão do usuário para instalar o provedor do NuGet. Após o usuário selecionar "sim" para a inicialização, a versão mais recente do provedor do NuGet será instalada. 
    
No entanto, há um caso em que você tem uma versão antiga do provedor do NuGet instalada em seu computador, e a versão mais antiga do NuGet às vezes é carregada primeiro na sessão do PowerShell (ou seja, a condição de corrida no OneGet). No entanto, o PowerShellGet requer a versão mais recente do provedor do Nuget para funcionar, portanto, o PowerShellGet solicita que o OneGet inicialize o provedor NuGet novamente. É por isso que você vê vários prompts para inicializar o provedor do NuGet.

**Solução**: o OneGet agora carrega a versão mais recente do provedor do NuGet para evitar vários prompts para inicializar o provedor do NuGet.

Também existe uma solução alternativa, que é excluir manualmente a versão antiga do provedor do NuGet (NuGet Anycpu.exe), caso ela exista, de $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies


3 **Computador com intranet apenas**

**Cenário**: para o cenário corporativo, as pessoas estão trabalhando em um ambiente em que não há acesso à Internet, somente à Intranet. O OneGet não dava suporte a esse caso no WMF 5.0.

**Solução**:
- Você pode baixar o provedor do NuGet em outro computador conectado à Internet usando o comando "Install-PackageProvider -Name NuGet".

- Localize o provedor do NuGet que você acabou de instalar em $env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget ou $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget. 

- Copie os binários para um local de compartilhamento de rede ou pasta ao qual seu computador (aquele sem Internet) também tenha acesso e instale o provedor do NuGet com "Install-PackageProvider NuGet -Source <Path to folder>".


4 **Log de evento**

Ao instalar pacotes, você está alterando o estado do computador. Para fins de diagnóstico, o OneGet agora registra eventos no log de eventos do Windows para atividades de instalar, desinstalar e salvar pacote. O canal de Evento é o mesmo que para o PowerShell, ou seja, Microsoft-Windows-PowerShell, Operacional.

5 **Suporte à autenticação** O OneGet agora dá suporte a localizar e instalar pacotes de um repositório que requer a autenticação básica. Você pode fornecer sua credencial para os cmdlets Find-Package e Install-Package. Por exemplo:
``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
6 **Usando OneGet atrás de um Proxy**

O OneGet agora assume parâmetros de proxy: -ProxyCredential e -Proxy. Usando esses parâmetros, você pode especificar a URL do proxy e a credencial de proxy para cmdlets do OneGet (por padrão, usamos as configurações de proxy do sistema). Por exemplo:
``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```



<!--HONumber=Jul16_HO3-->


