---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: ponta a ponta Active Directory
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 0a262e2c83174db7041d3cf35d97542b1cac4386

---

# Ponta a Ponta - Active Directory
Imagine que o escopo do seu programa aumentou.
Agora você é responsável por adicionar JEA a Controladores de Domínio para executar ações do Active Directory.
As pessoas do suporte técnico pretendem usar JEA para desbloquear contas, redefinir senhas e executar outras ações semelhantes.

Você precisa expor um conjunto totalmente novo de comandos para um grupo diferente de pessoas.
Além disso, você tem um monte de scripts do Active Directory existentes que precisa expor.
Esta seção guiará você pela criação de uma Configuração de Sessão e a Capacidade de Função para esta tarefa.

## Pré-requisitos
Para seguir esta seção passo a passo, você precisará estar operando em um controlador de domínio.
Se não tiver acesso ao controlador de domínio, não se preocupe.
Tente acompanhar trabalhando em outro cenário ou função com a qual você está familiarizado.
Se você quiser configurar rapidamente um novo controlador de domínio, confira o apêndice [Criando um Controlador de Domínio](#creating-a-domain-controller).

## Etapas para criar uma nova Capacidade de Função e Configuração de Sessão

Criar uma nova capacidade de função pode parecer intimidador num primeiro momento, mas pode ser dividido em etapas bem simples:

1.  Identificar as tarefas que você precisa habilitar
2.  Restringir as tarefas conforme necessário
3.  Confirmar se elas funcionam com JEA
4.  Colocá-las em um arquivo de Capacidade de Função
5.  Registrar uma Configuração de Sessão que expõe essa Capacidade de Função

## Etapa 1: Identificar o que precisa ser exposto
Antes de criar uma nova Capacidade de Função ou Configuração de Sessão, você precisará identificar todas as coisas que os usuários precisarão fazer por meio do ponto de extremidade JEA, bem como realizá-las por meio do PowerShell.
Isso envolverá uma quantidade razoável de requisito de coleta e pesquisa.
Como você efetuará esse processo dependerá das suas metas e da organização.
É importante destacar o requisito de coleta e de pesquisa como uma parte essencial do processo do mundo real.
Essa pode ser a etapa mais difícil no processo de adoção de JEA.

### Encontrar Recursos
Veja este conjunto de recursos online que podem surgir na sua pesquisa sobre a criação de um ponto de extremidade de gerenciamento do Active Directory:
-   [Visão geral do Active Directory PowerShell](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx)
-   [CMD para Guia do PowerShell para Active Directory](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx)

### Faça uma lista
Veja este conjunto das dez ações das quais você estará trabalhando pelo restante desta seção.
Tenha em mente que este é apenas um exemplo, os requisitos das suas organizações podem ser diferentes:

|Ação                                                         |Comando do PowerShell                                             |
|---------------------------------------------------------------|---------------------------------------------------------------|
|Desbloquear Conta                                                 |`Unlock-ADAccount`                                             |
|Redefinir Senha                                                 |`Set-ADAccountPassword` e `Set-ADUser -ChangePasswordAtLogon`|
|Alterar o título do usuário                                          |`Set-ADUser -Title`                                            |  
|Localizar contas do AD que estão bloqueadas, desabilitadas, inativa, etc. |`Search-ADAccount`                                             |
|Adicionar o usuário ao grupo                                              |`Add-ADGroupMember -Identity (with whitelist) -Members`        |
|Remover usuário de grupo                                         |`Remove-ADGroupMember -Identity (with whitelist) -Members`     |
|Habilitar uma conta de usuário                                          |`Enable-ADAccount`                                             |
|Desabilitar uma conta de usuário                                         |`Disable-ADAccount`                                            |

## Etapa 2: Restringir as tarefas conforme necessário

Agora que você tem sua lista de ações, precisará considerar os recursos de cada comando.
Há dois motivos importantes para fazer isso:

1.  É fácil expor para os usuários mais recursos do que você pretendia.
Por exemplo, `Set-ADUser` é um comando incrivelmente poderoso e flexível.
É recomendável não expor tudo o que ele pode fazer para ajudar os usuários do suporte técnico.  

2.  Pior ainda, é possível expor comandos que permitem aos usuários fugir das restrições do JEA.
Se isso acontecer, o JEA deixará de funcionar como um limite de segurança.
Tenha cuidado ao selecionar comandos.
Por exemplo, Invoke-Expression permitirá que os usuários executem código irrestrito.
Para ver mais discussões sobre esse tópico, consulte a seção Considerações ao restringir comandos.

Depois de revisar cada comando, você decide restringir o seguinte:

1.  `Set-ADUser` só deve ter permissão para executar o parâmetro "-Title"

2.  `Add-ADGroupMember` e `Remove-ADGroupMember` devem funcionar apenas com determinados grupos

### Etapa 3: Confirmar o trabalho de tarefas com JEA
De fato suar esses cmdlets pode não ser simples no ambiente JEA restrito.
O JEA é executado em modo *Sem Linguagem*, entre outras coisas, que impede que os usuários possam usar variáveis.
Para garantir que os usuários finais tenham uma experiência positiva, é importante verificar algumas coisas.

Por exemplo, considere `Set-ADAccountPassword`.
O parâmetro "-NewPassword" requer uma cadeia de caracteres segura.
Muitas vezes, os usuários criam uma cadeia de caracteres e passam-na como uma variável (como abaixo):

```PowerShell
$newPassword = (Read-Host -Prompt "Specify a new password" -AsSecureString)
Set-ADAccountPassword -Identity mollyd -NewPassword $newPassword -Reset
```

No entanto, o modo de linguagem não impede o uso de variáveis.
Você pode contornar essa restrição de duas maneiras:

1.  Você pode exigir que os usuários executem o comando sem atribuir variáveis.
Ele é fácil de configurar, mas pode ser penoso para os operadores usando o ponto de extremidade.
Quem deseja digitar essa saída sempre que você redefinir uma senha?
```PowerShell
Set-ADAccountPassword -Identity mollyd -NewPassword (Read-Host -Prompt "Specify a new password" -AsSecureString) -Reset
```

2.  Você pode encapsular a complexidade em um script ou uma função que você expõe para os usuários finais.
Scripts e funções que você expõe são executados em um contexto irrestrito; você pode escrever funções que usam variáveis e chamar outros comandos sem nenhum problema.
Essa abordagem simplifica a experiência do usuário final, evita erros, reduz o conhecimento necessário do PowerShell e reduz a exposição de funcionalidade em excesso.
A única desvantagem é o custo de criação e manutenção da função.

### Ao lado: adicionar uma função ao seu Módulo
Adotando a abordagem nº 2, você vai escrever uma função do PowerShell chamada `Reset-ContosoUserPassword`.
Essa função está prestes a fazer tudo o que deve acontecer quando você redefinir a senha do usuário.
Na sua organização, isso pode envolver fazer coisas sofisticadas e complicadas.
Como esse é apenas um exemplo, o comando apenas redefinirá a senha e exigirá a alteração da senha pelo usuário no momento de logon.
Nós o colocaremos no módulo Contoso_AD_Module criado na última seção.

1. No ISE do PowerShell, abra "Contoso_AD_Module.psm1"
```PowerShell
ISE 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1'
```

2. Pressione CTRL + J para abrir o menu de trechos de código.

3. Pressione a seta para baixo até localizar "função" e pressione enter.
Isso prepara um esqueleto muito básico de uma função.

4. Renomeie a função "Reset-ContosoUserPassword".  

5. Renomeie um dos parâmetros "Identity" e exclua o segundo.

6. Copie o seguinte no corpo da função.
```PowerShell
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
```

7. Salve o arquivo.
Você deve terminar com algo parecido com isso:
```PowerShell
function Reset-ContosoUserPassword ($Identity)
{
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
}
```
Agora, os usuários podem simplesmente chamar `Reset-ContosoUserPassword` e não precisam se lembrar a sintaxe para criar um cadeia de caracteres segura embutida.

## Etapa 4: Editar o arquivo de Capacidade de Função
Na seção [Criação de Capacidade de Função](#role-capability-creation), você criou um arquivo de Capacidade de Função em branco.
Nesta seção, você preencherá os valores nesse arquivo.

Comece abrindo o arquivo de capacidade de função no ISE.
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc'
```
Atualize o arquivo com as seguintes alterações:
```PowerShell
# OLD: VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleCmdlets =
    'Unlock-ADAccount',
    'Search-ADAccount',
    'Enable-ADAccount',
    'Disable-ADAccount',
    @{ Name = 'Set-ADUser'; Parameters = @{ Name = 'Title'; ValidateSet = 'Manager', 'Engineer' }},
    @{ Name = 'Add-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}},
    @{ Name = 'Remove-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}}

# OLD: VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleFunctions = 'Reset-ContosoUserPassword'
```

Há algumas coisas a observar sobre o que foi indicado acima:
1.  O PowerShell tentará carregar automaticamente os módulos necessários para a sua Capacidade de Função.
Você precisará listar explicitamente nomes de módulo no campo "ModulesToImport" se você encontrar problemas com um módulo que não está sendo carregado automaticamente.

2.  Se você não tiver certeza se um comando é uma função ou um cmdlet, execute `Get-Command` e examine o "CommandType"

3.  O ValidatePattern permite que você use uma expressão regular para restringir os argumentos do parâmetro se não for fácil de definir um conjunto de valores permitidos.
Você não pode definir um ValidatePattern e ValidateSet para um único parâmetro.

## Etapa 5: Registrar uma nova Configuração de Sessão
Em seguida, você criará um novo arquivo de configuração de sessão que irá expor sua Capacidade de Função para os membros do grupo de AD "JEA_NonAdmin_HelpDesk".

Comece criando e abrindo um novo arquivo de Configuração de Sessão em branco no ISE do PowerShell.
```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
ise "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
Modifique os campos a seguir no arquivo PSSC.
Se você estiver trabalhando em seu próprio ambiente, substitua "CONTOSO\JEA_NonAdmins_Helpdesk" por seu próprio usuário ou grupo não administrador.
```PowerShell
# OLD: Description = ''
Description = 'An endpoint for active directory tasks.'

# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{ 'CONTOSO\JEA_NonAdmin_HelpDesk' = @{ RoleCapabilities =  'ADHelpDesk' }}
```
Salve e registrar a Configuração de Sessão
```PowerShell
Register-PSSessionConfiguration -Name ADHelpDesk -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
## Experimente!
Obtenha suas credenciais de usuário não administrador:
```PowerShell
$HelpDeskCred = Get-Credential
```
Se você acompanhou a seção [Configurar usuários e grupos](creating-a-domain-controller.md#set-up-users-and-groups), as credenciais serão:
-   Nome de usuário = "HelpDeskUser"
-   Senha = "pa$$w0rd"

Conexão remota para o ponto de extremidade do Suporte Técnico de AD usando a credencial de não administrador:
```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName ADHelpDesk -Credential $HelpDeskCred
```
Use Set-ADUser para redefinir o título do usuário.
```PowerShell
Set-ADUser -Identity OperatorUser -Title Engineer
```
Verifique se que o título foi alterado.
```PowerShell
Get-ADUser -Identity OperatorUser -Property Title
```
Agora, use Add-ADGroupMember para adicionar um usuário ao TestGroup.
Observação: verifique se você criou o TestGroup com antecedência.
```PowerShell
Add-ADGroupMember TestGroup -Member OperatorUser -Verbose
```
Sair da sessão:
```PowerShell
Exit-PSSession
```
## Conceitos Principais
**Modo NoLanguage**: quando o PowerShell está no modo "NoLanguage", os usuários somente podem executar comandos, mas não podem usar elementos de linguagem.
Para obter mais informações, execute `Get-Help about_Language_Modes`.

**Funções do PowerShell**: funções do PowerShell são partes do código do PowerShell que podem ser chamados por nome.
Para obter mais informações, execute `Get-Help about_Functions`.

**ValidateSet/ValidatePattern**: ao expor um comando, você pode restringir os argumentos válidos para os parâmetros específicos.
Um ValidateSet é uma lista específica de comandos válidos.
Um ValidatePattern é uma expressão regular à qual os argumentos para esse parâmetro devem corresponder.




<!--HONumber=Jun16_HO4-->


