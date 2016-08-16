---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "capacidades de função"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 81fd386d58576a8930093b4f18ce36a4ff6cecd0
ms.openlocfilehash: a3dd4a217f5b1fd80e97adf802c65073ca015bbc

---

# Capacidades de Função

## Visão geral
Na seção acima, você aprendeu que o campo “RoleDefinitions” definiu quais grupos tinham acesso a quais Capacidades de Função.
Você pode se perguntar: “o que são as Capacidades de Função?"
Esta seção responderá essa pergunta.  

## Apresentando as Capacidades de Função do PowerShell
Capacidades de Função do PowerShell definem "o que" um usuário pode fazer em um ponto de extremidade JEA.
Eles fornecem detalhes sobre uma lista de permissões de coisas como comandos visíveis, aplicativos visíveis e muito mais.
Capacidades de Função são definidas por arquivos com uma extensão ".psrc".

## Conteúdo do Capacidade de Função
Começamos examinando e modificando o arquivo de Capacidade de Função usado anteriormente.
Imagine que você implantou sua Configuração de Sessão no seu ambiente, mas recebeu comentários de que precisa alterar os recursos expostos aos usuários.
Operadores precisam ser capazes de reinicializar os computadores e também desejam poder obter informações sobre as configurações de rede.
Além disso, a equipe de segurança lhe disse que permitir que usuários executem "Restart-Service" sem qualquer restrição não é aceitável.
É necessário restringir os serviços que os operadores podem reiniciar.

Para fazer essas alterações, comece executando o ISE do PowerShell como Administrador e abra o seguinte arquivo:

```
C:\Program Files\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities\Maintenance.psrc
```

Agora, encontre e atualize as seguintes linhas no arquivo:

```PowerShell
# OLD: VisibleCmdlets = 'Restart-Service'
VisibleCmdlets = 'Restart-Computer',
                 @{
                     Name = 'Restart-Service'
                     Parameters = @{ Name = 'Name'; ValidateSet = 'Spooler' }
                 },
                 'NetTCPIP\Get-*'

# OLD: VisibleExternalCommands = 'Item1', 'Item2'
VisibleExternalCommands = 'C:\Windows\system32\ipconfig.exe'
```

Elas contém alguns exemplos interessantes:

1.  Você restringiu Restart-Service de modo que os operadores só poderá usar a Restart-Service com o parâmetro -Name e eles só terão permissão para fornecer "Spooler" como um argumento para esse parâmetro.
Se desejar, você também poderá restringir os argumentos usando uma expressão regular usando "ValidatePattern" em vez de "ValidateSet".

2.  Você expôs todos os comandos com o verbo "Get" do módulo NetTCPIP.
Como comandos "Get" normalmente não alteram o estado do sistema, esta é uma ação relativamente segura.
Dito isso, é altamente recomendável examinar atentamente cada comando exposto por meio do JEA.

3.  Você expôs um executável (ipconfig) usando VisibleExternalCommands.
Você também pode expor scripts do PowerShell completos com este campo.
É importante sempre informar o caminho completo para comandos externos para garantir que um programa com um nome similar (e potencialmente mal-intencionado) colocado no caminho do usuário não seja executado em vez dele.

Salve o arquivo e conecte-se ao ponto de extremidade de demonstração novamente para confirmar se as alterações funcionaram.

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
Get-Command
```
Como somente você modificou o arquivo de Capacidade de função, não é necessário registrar novamente a Configuração de Sessão.
O PowerShell localiza automaticamente suas Capacidades de Função atualizadas quando um usuário se conecta.
Como as Capacidades de Função são carregadas quando a sessão é iniciada, as sessões existentes não são afetadas por atualizações para os arquivos de Capacidade de Função.

Agora, confirme se você pode reiniciar o computador executando Restart-Computer com o parâmetro -WhatIf (a menos que você realmente deseje reiniciar o computador).

```PowerShell
Restart-Computer -WhatIf
```

Confirme se você pode executar "ipconfig"

```PowerShell
ipconfig
```

Por fim, confirme se Restart-Service funciona apenas para o serviço de Spooler.

```PowerShell
Restart-Service Spooler # This should work
Restart-Service WSearch # This should fail
```

Saia da sessão quando tiver terminado.

```PowerShell
Exit-PSSession
```

## Criação de Capacidade de Função
Na próxima seção, você criará um ponto de extremidade JEA para os usuários do suporte técnico do AD.
Para preparar isso, criaremos um arquivo de Capacidade de Função em branco para preencher essa seção.
As Capacidades de Função devem ser criadas dentro de uma pasta "RoleCapabilities" dentro de um módulo do PowerShell válido para ser resolvido quando uma sessão é iniciada.

Módulos do PowerShell são essencialmente pacotes da funcionalidade do PowerShell.
Eles podem conter funções, cmdlets, recursos da DSC, Capacidades de Função do PowerShell e muito mais.
Você pode encontrar informações sobre os módulos que executam `Get-Help about_Modules` em um console do PowerShell.

Para criar um novo módulo do PowerShell com um arquivo de Capacidade de Função em branco, execute os seguintes comandos:  

```PowerShell
# Create a new folder for the module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module' -ItemType Directory

# Add a module manifest to contain metadata for this module.
New-ModuleManifest -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psd1' -RootModule Contoso_AD_Module.psm1

# Create a blank script module. You'll use this for custom functions in the next section.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1' -ItemType File

# Create a RoleCapabilities folder in the Contoso_AD_Module folder. PowerShell expects Role Capabilities to be located in a "RoleCapabilities" folder within a module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities' -ItemType Directory

# Create a blank Role Capability in your RoleCapabilities folder. Running this command without any additional parameters just creates a blank template.
New-PSRoleCapabilityFile -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc'
```

Parabéns, você criou um arquivo de Capacidade de Função em branco.
Ele será usado na próxima seção.

## Conceitos Principais
**Capacidade de Função (.psrc)**: um arquivo que define "o que" um usuário pode fazer em um ponto de extremidade JEA.
Ele fornece detalhes sobre uma lista de permissões de coisas como comandos visíveis, aplicativos de console visíveis e muito mais.
Para que o PowerShell detecte as Capacidades de Função, você deve colocá-los em uma pasta "RoleCapabilities" em um módulo do PowerShell válido.

**Módulo do PowerShell**: um pacote da funcionalidade do PowerShell.
Ele podem conter funções, cmdlets, recursos da DSC, Capacidades de Função do PowerShell e muito mais.
Para ser carregado automaticamente, módulos do PowerShell devem estar localizados em um caminho em `$env:PSModulePath`.




<!--HONumber=Jul16_HO1-->


