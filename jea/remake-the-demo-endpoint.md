---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "recriar o ponto de extremidade da demonstração"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: dabb5023012e90ace3fbc5f347c17821abd92595

---

# Recriar o Ponto de Extremidade de Demonstração
Nesta seção, você aprenderá como gerar uma réplica exata do ponto de extremidade de demonstração usado na seção acima.
Ela apresentará os conceitos fundamentais que são necessários para compreender o JEA, incluindo as Configurações de Sessão e Capacidades de Função do PowerShell.

## Configurações de Sessão do PowerShell
Ao usar o JEA na seção acima, você começou executando o seguinte comando:

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

Enquanto a maioria dos parâmetros são auto-explicativos, o *ConfigurationName* pode parecer confuso a princípio.
Esse parâmetro especificou a Configuração de Sessão do PowerShell para o qual você se conectou.

*Configuração de Sessão do PowerShell* é um termo especial para um ponto de extremidade do PowerShell.
Ele é o “local” figurativo no qual os usuários se conectam e obtém acesso à funcionalidade do PowerShell.
Dependendo de como você definiu uma Configuração de Sessão, ele pode fornecer uma funcionalidade diferente para conectar os usuários.
Para JEA, usamos as Configurações de Sessão para restringir o PowerShell a um conjunto limitado de funcionalidades e para executá-lo como uma conta virtual privilegiada.

Você já tem várias Configurações de Sessão do PowerShell registradas no seu computador, cada uma configurada de forma ligeiramente diferente.
A maioria deles é fornecida com o Windows, mas a Configuração de Sessão “JEA_Demo” foi definida na seção [Pré-requisitos](prerequisites.md).
Você pode ver que todas as Configurações de Sessão registradas executando o seguinte comando em um prompt de Administrador do PowerShell:

```PowerShell
Get-PSSessionConfiguration
```

## Arquivos de Configuração de Sessão do PowerShell
Você pode criar novas Configurações de Sessão registrando novos *Arquivos de Configuração de Sessão do PowerShell*.
Arquivos de Configuração de Sessão têm extensões de arquivo “.pssc”.
Você pode gerar os Arquivos de Configuração de Sessão com o cmdlet New-PSSessionConfigurationFile.

Em seguida, você criará e registrará uma nova Configuração de Sessão para JEA.

## Gerar e modificar a Configuração de Sessão do PowerShell
Execute o seguinte comando para gerar um arquivo “esqueleto” de Configuração de Sessão do PowerShell.

```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

> **DICA:** apenas as definições de configuração mais comuns são incluídas no arquivo esqueleto por padrão.
> Use o parâmetro `-Full` para incluir todas as configurações aplicáveis no PSSC gerado.

Abra o arquivo no ISE do PowerShell ou seu editor de texto favorito.

```PowerShell
ise "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

Atualize os campos a seguir no arquivo com os valores abaixo (lembre-se de substituir em seu próprio grupo de segurança não administrador):

```PowerShell
# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: # RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{'CONTOSO\JEA_NonAdmin_Operator' = @{ RoleCapabilities =  'Maintenance' }}
```

Aqui está o que significa cada uma dessas entradas:

1.  O campo *SessionType* define as configurações padrão predefinidas para serem usadas com esse ponto de extremidade.
O *RestrictedRemoteServer* define as configurações mínimas necessárias para o gerenciamento remoto.
Por padrão, um ponto de extremidade *RestrictedRemoteServer* expõe Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host e Out-Default.
Ele definirá *ExecutionPolicy* para *RemoteSigned* e *LanguageMode* para *NoLanguage*.
O efeito dessas configurações é um ponto de partida mínimo e seguro para configurar o ponto de extremidade.

2.  O campo *RoleDefinitions* atribui a Capacidades de Função para grupos específicos.
Ele define quem pode fazer o que como uma conta privilegiada.
Com este campo, você pode especificar a funcionalidade disponível para qualquer usuário conectado com base na associação de grupo.
Esse é o núcleo da funcionalidade de RBAC do JEA.
Neste exemplo, você está expondo o RoleCapability de "Demonstração" predefinido para membros do grupo "Contoso\JEA_NonAdmin_Operator".

3.  O campo *RunAsVirtualAccount* indica que PowerShell deve "Executar como" uma Conta Virtual neste ponto de extremidade.
Por padrão, a Conta Virtual é um membro do grupo Administradores interno.
Em um controlador de domínio, ele também é um membro do grupo Administradores de Domínio por padrão.
Posteriormente neste guia, você aprenderá como personalizar os privilégios da Conta Virtual.

4.  O campo *TranscriptDirectory* define onde as transcrições “Over the Shoulder” do PowerShell são salvas após cada sessão remota.
Essas transcrições permitem que você inspecione as ações executadas em cada sessão de forma legível.
Para obter mais informações sobre transcrições do PowerShell, confira este [post de blog](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).
Observação: os Eventos do Windows também capturam informações sobre o que cada usuário executou com o PowerShell.
Transcrições são apenas um pouco mais legíveis.

Por fim, salve suas alterações em *JEADemo2.pssc*.

## Aplique a Configuração de Sessão do PowerShell

Para criar um ponto de extremidade de um arquivo de Configuração de Sessão, você precisa registrar o arquivo.
Isso requer algumas informações:

1. O caminho para o arquivo de Configuração de Sessão.
2. O nome da sua Configuração de Sessão registrada. Esse é o mesmo nome que os usuários fornecem para o parâmetro "ConfigurationName" ao se conectarem ao ponto de extremidade com `Enter-PSSession` ou `New-PSSession`.

Para registrar a Configuração de Sessão no computador local, execute o seguinte comando:

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

Parabéns! Você configurou o seu ponto de extremidade JEA.

## Testar seu ponto de extremidade
Execute novamente as etapas listadas na seção [Usando o JEA](using-jea.md) no novo ponto de extremidade para confirmar se ele está funcionando conforme o esperado.
Use o novo nome de ponto de extremidade (JEADemo2) ao fornecer o nome de configuração para Enter-PSSession.

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

## Conceitos Principais
**Configuração de Sessão do PowerShell**: às vezes chamado de *Ponto de Extremidade do PowerShell*, esse é o "local" figurado em que os usuários se conectam e obtém acesso à funcionalidade do PowerShell.
Você pode listar as Configurações de Sessão registradas no sistema executando `Get-PSSessionConfiguration`.
Quando configurado de forma específica, uma Configuração de Sessão do PowerShell pode ser chamada de *Ponto de Extremidade JEA*.

**Arquivo de Configuração de Sessão do PowerShell (.pssc)**: um arquivo que, quando registrado, define as configurações para uma Configuração de Sessão do PowerShell.
Ele contém especificações para funções de usuário que podem se conectar ao ponto de extremidade, à Conta Virtual "Executar como" e muito mais.     

**Definições de Função**: o campo em um Arquivo de Configuração de Sessão que define a Capacidades de Função concedida para conectar usuários.
Ele define *quem* pode fazer *o que* como uma conta privilegiada.
Esse é o núcleo das capacidades de RBAC do JEA.

**SessionType**: um campo em um Arquivo de Configuração de Sessão que representa as configurações padrão para uma Configuração de Sessão.
Para pontos de extremidade JEA, é necessário definir isso como RestrictedRemoteServer.

**Transcrição de PowerShell**: um arquivo que contém uma exibição "Over The Shoulder" de uma sessão do PowerShell.
Você pode configurar o PowerShell para gerar transcrições para sessões JEA usando o campo TranscriptDirectory.
Para obter mais informações sobre transcrições, confira este [post de blog](https://technet.microsoft.com/en-us/magazine/ff687007.aspx).




<!--HONumber=Jun16_HO4-->


