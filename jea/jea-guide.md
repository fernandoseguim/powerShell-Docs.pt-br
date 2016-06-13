# JEA (Just Enough Administration): uma introdução

## Sumário
Depois de ler este documento, você poderá criar, implantar, usar, manter e auditar uma implantação JEA (Just Enough Administration).
Estes são os tópicos abordados neste guia introdutório:

1.  [Introdução](#introduction): examinar rapidamente por que o JEA importa

2.  [Pré-requisitos](#prerequisites): configurar seu ambiente

3.  [Usando o JEA](#using-jea): comece compreendendo a experiência do operador ao usar JEA

4.  [Recrie a Demonstração](#remake-the-demo-endpoint): criar uma Configuração de Sessão JEA do zero

5.  [Capacidades de Função](#role-capabilities): saiba mais sobre como personalizar funcionalidades JEA com Arquivos de Capacidades de Função

6.  [Ponta a ponta - Active Directory](#end-to-end---active-directory): criar um ponto de extremidade totalmente novo para gerenciar o Active Directory

7.  [Implantação e Manutenção de Vários Computadores](#multi-machine-deployment-and-maintenance): descubra como a implantação e a criação mudam conforme a escala

8.  [Relatórios JEA](#reporting-on-jea): descubra como auditar e relatar todas as ações JEA e de infraestrutura

9.  [Apêndice](#appendix): habilidades importantes e pontos de discussão

## Introdução

### Motivação
Quando você concede acesso privilegiado aos sistemas a alguém, está oferecendo seu limite de confiança para essa pessoa.
Esse é um risco, pois os administradores são uma superfície de ataque.
Ataques internos e roubo de credenciais são reais e comuns.

Esse não é um problema novo.
Você provavelmente conhece muito bem o princípio de privilégios mínimos e pode usar alguma forma de RBAC (Controle de Acesso Baseado em Função) com aplicativos que o fornecem.
No entanto, a eficiência e a gerenciabilidade dessas soluções geralmente são limitadas por seu escopo amplo e imprecisão.
Além disso, existem lacunas na cobertura do RBAC.
Por exemplo, no Windows, o acesso privilegiado é basicamente um comutador binário, o que força você a conceder permissões desnecessárias ao adicionar usuários ao grupo Administradores.

O JEA (Administração Just Enough) fornece uma plataforma de RBAC por meio de Comunicação Remota do PowerShell.
*Ele permite que usuários específicos executem tarefas administrativas específicas nos servidores sem conceder direitos de administrador.*
Isso permite que você preencha as lacunas entre suas soluções existentes de RBAC e simplifica o gerenciamento dessas configurações.

## Pré-requisitos

### Estado Inicial
Antes de iniciar esta seção, verifique o seguinte:

1. O JEA está disponível no seu sistema. Confira o [LEIAME](./README.md) para ver os sistemas operacionais com suporte e os downloads necessários.
2. Você tem direitos administrativos no computador no qual está experimentando o JEA.
3. O computador está ingressado no domínio.
Consulte a seção [Criando um Controlador de Domínio](#creating-a-domain-controller) para configurar rapidamente um novo domínio em um servidor se você ainda não tiver um.

### Habilitar a Comunicação Remota do PowerShell
O gerenciamento com o JEA ocorre por meio da comunicação remota do PowerShell.
Execute o seguinte em uma janela de Administrador do PowerShell para verificar se está habilitado e configurado corretamente:

```PowerShell
Enable-PSRemoting 
```

Se você não estiver familiarizado com a comunicação remota do PowerShell, seria uma boa ideia executar `Get-Help about_Remote` para saber mais sobre esse importante conceito básico.

### Identificar os Usuários ou Grupos
Para demonstrar o JEA em ação, você precisa identificar os outros usuários e grupos não administradores que serão usados em todo este guia.
  
Se você estiver usando um domínio existente, identifique ou crie alguns grupos e usuários não privilegiados.
Você concederá acesso para esses usuários não administradores ao JEA.
Sempre que você consultar a variável `$NonAdministrator` na parte superior de um script, atribua-a aos usuários ou grupos de não administradores selecionados. 

Se você criou um novo domínio do zero, será muito mais fácil.
Use a seção [Configurar Usuários e Grupos](#set-up-users-and-groups) no apêndice para criar usuários e grupos não administradores.
Os valores padrão de `$NonAdministrator` serão os grupos criados nessa seção.

### Configurar o arquivo de Capacidade de Função de manutenção
Execute os seguintes comandos do PowerShell para criar o arquivo de Capacidade de Função de demonstração que usaremos para a próxima seção.
Posteriormente neste guia, você aprenderá sobre o que esse arquivo faz.

```PowerShell
# Fields in the role capability
$MaintenanceRoleCapabilityCreationParams = @{
    Author = 'Contoso Admin'
    CompanyName = 'Contoso'
    VisibleCmdlets = 'Restart-Service'
    FunctionDefinitions = 
            @{ Name = 'Get-UserInfo'; ScriptBlock = { $PSSenderInfo } }
}

# Create the demo module, which will contain the maintenance Role Capability File
New-Item -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module" -ItemType Directory
New-ModuleManifest -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\Demo_Module.psd1"
New-Item -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities" -ItemType Directory 

# Create the Role Capability file
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities\Maintenance.psrc" @MaintenanceRoleCapabilityCreationParams 
```
  
### Criar e registrar um arquivo de configuração de sessão de demonstração
Execute os seguintes comandos para criar e registrar o arquivo de Configuração de Sessão de demonstração que usaremos na próxima seção.
Posteriormente neste guia, você aprenderá sobre o que esse arquivo faz.

```PowerShell
# Determine domain
$domain = (Get-CimInstance -ClassName Win32_ComputerSystem).Domain

# Replace with your non-admin group name
$NonAdministrator = "$domain\JEA_NonAdmin_Operator"

# Specify the settings for this JEA endpoint
# Note: You will not be able to use a virtual account if you are using WMF 5.0 on Windows 7 or Windows Server 2008 R2
$JEAConfigParams = @{
    SessionType = 'RestrictedRemoteServer'
    RunAsVirtualAccount = $true
    RoleDefinitions = @{
        $NonAdministrator = @{ RoleCapabilities = 'Maintenance' }
    }
    TranscriptDirectory = "$env:ProgramData\JEAConfiguration\Transcripts"
}

# Set up a folder for the Session Configuration files
if (-not (Test-Path "$env:ProgramData\JEAConfiguration"))
{
    New-Item -Path "$env:ProgramData\JEAConfiguration" -ItemType Directory
}

# Specify the name of the JEA endpoint
$sessionName = 'JEA_Demo'

if (Get-PSSessionConfiguration -Name $sessionName -ErrorAction SilentlyContinue)
{
    Unregister-PSSessionConfiguration -Name $sessionName -ErrorAction Stop
}

New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo.pssc" @JEAConfigParams

# Register the session configuration
Register-PSSessionConfiguration -Name $sessionName -Path "$env:ProgramData\JEAConfiguration\JEADemo.pssc"
```
 
### Habilitar o registro em log do Módulo do PowerShell (opcional)
As etapas a seguir habilitam o log para todas as ações do PowerShell em seu sistema.
Você não precisa habilitar isso para que o JEA funcione, mas será útil na seção [Relatando JEA](#reporting-on-jea).

1. Abra o Editor de diretiva de Grupo Local
2. Navegue para “Configuração do Computador\Modelos Administrativos\Componentes do Windows\Windows PowerShell”
3. Clique duas vezes em "Ativar o Registro de Log de Módulo"
4. Clique em “Habilitado”
5. Na seção Opções, clique em "Mostrar" ao lado dos Nomes de Módulo
6. Digite "*" na janela pop-up. Isso significa que o PowerShell registrará comandos de todos os módulos.
7. Clique em OK e aplique a política

Observação: você também pode habilitar transcrição do PowerShell de todo o sistema por meio da Política de Grupo.

**Parabéns, você configurou seu computador com o ponto de extremidade de demonstração e está pronto para começar a usar JEA!**

## Usando JEA
Esta seção enfoca a compreensão da experiência do usuário final do *use do JEA*.
Na seção de pré-requisitos, você criou um ponto de extremidade JEA de demonstração.
Usaremos esta demonstração para mostrar o JEA em ação.
Nas próximas seções, o guia abordará ao contrário, apresentando as ações e os arquivos que tornaram a experiência do usuário final possível.

### Usando o JEA como não administrador
Para mostrar JEA em ação, você precisará usar a comunicação remota do PowerShell como se você fosse um usuário não administrador.
Execute o seguinte comando em uma nova janela do PowerShell:   

```PowerShell
$NonAdminCred = Get-Credential
```

Insira as credenciais para a conta não administradora quando solicitado.
Se você tiver seguido a seção [Configurar Usuários e Grupos](#set-up-users-and-groups), eles serão:
-   Nome do usuário = "OperatorUser"
-   Senha = "pa$$w0rd"

Em seguida, execute o comando a seguir para conectar-se ao ponto de extremidade de demonstração usando as credenciais fornecidas:

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred 
```

Agora você entrou em uma sessão comunicação remota interativa do PowerShell no computador local. Usando o parâmetro "Credential", você se conectou *como se fosse* o OperatorUser (ou a conta usada).
A alteração no prompt para `[localhost]: PS>` indica que você está operando em uma sessão remota.  

Execute o seguinte no prompt de comando remoto para mostrar os comandos disponíveis a você:

```PowerShell
Get-Command 
```

Como você pode ver, este é um subconjunto muito limitado de comandos disponíveis em uma janela normal do PowerShell (que geralmente pode incluir milhares de comandos).
Especificamente, ela mostra apenas os sete cmdlets JEA padrão (Clear-Host, Exit-PSSession, Get-Command, Get-FormatData, Get-Help, Measure-Object, Out-Default e Select-Object) e os dois comandos explicitamente incluídos no arquivo de Capacidade de Função de manutenção.

Em seguida, abordaremos o contexto do usuário no qual esta sessão está operando invocando a função personalizada incluída no arquivo de Capacidade de Função de manutenção:

```PowerShell
Get-UserInfo
```
 
A saída dessa função mostra "ConnectedUser" e "RunAsUser".
O usuário conectado é a conta conectada à sessão remota (por exemplo, sua conta).
O usuário conectado não precisa ter privilégios de administrador.
A conta "Executar como" é a conta que realmente executa as ações privilegiadas.
Ao conectar-se como um usuário e administrar como um usuário privilegiado, permitimos que usuários não privilegiados executem tarefas administrativas específicas sem lhes conceder direitos administrativos.

Para demonstrar isso em ação, execute o seguinte comando:

```PowerShell
Restart-Service -Name Spooler -Verbose
```

Normalmente, Restart-Service requer privilégios de administrador para ser executado.
Com a conta virtual JEA, no entanto, podemos executá-lo usando credenciais sem privilégios.

Dessa forma, o JEA permite fazer seu trabalho usando os comandos que você já usa.
Mas e quanto aos comandos que *não devem* poder ser usados?
Tente executar um comando diferente na sessão JEA, como `Restart-Computer`, e observe como o JEA impede que esses comandos sejam executados.

```PowerShell
[localhost]: PS> Restart-Computer
The term 'Restart-Computer' is not recognized as the name of a cmdlet, function, script file, or
operable program. Check the spelling of the name, or if a path was included, verify that the path
is correct and try again.
    + CategoryInfo          : ObjectNotFound: (Restart-Computer:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException 
```

Por fim, para deixar o ponto de extremidade JEA restrito, execute o seguinte comando:

```PowerShell
Exit-PSSession
```

Isso se desconecta da sessão de comunicação remota do PowerShell.

## Recriar o Ponto de Extremidade de Demonstração
Nesta seção, você aprenderá como gerar uma réplica exata do ponto de extremidade de demonstração usado na seção acima.
Ela apresentará os conceitos fundamentais que são necessários para compreender o JEA, incluindo as Configurações de Sessão e Capacidades de Função do PowerShell. 

### Configurações de Sessão do PowerShell
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
A maioria deles é fornecida com o Windows, mas a Configuração de Sessão "JEA_Demo" foi definida na seção [Pré-requisitos](#prerequisites).
Você pode ver que todas as Configurações de Sessão registradas executando o seguinte comando em um prompt de Administrador do PowerShell:

```PowerShell
Get-PSSessionConfiguration
```

### Arquivos de Configuração de Sessão do PowerShell
Você pode criar novas Configurações de Sessão registrando novos *Arquivos de Configuração de Sessão do PowerShell*.
Arquivos de Configuração de Sessão têm extensões de arquivo “.pssc”.
Você pode gerar os Arquivos de Configuração de Sessão com o cmdlet New-PSSessionConfigurationFile.

Em seguida, você criará e registrará uma nova Configuração de Sessão para JEA. 

### Gerar e modificar a Configuração de Sessão do PowerShell
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
O *RestrictedRemoteServer* define as configurações mínimas necessárias para o gerenciamento remoto. Por padrão, um ponto de extremidade *RestrictedRemoteServer* expõe Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host e Out-Default.
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

### Aplique a Configuração de Sessão do PowerShell 

Para criar um ponto de extremidade de um arquivo de Configuração de Sessão, você precisa registrar o arquivo.
Isso requer algumas informações:

1. O caminho para o arquivo de Configuração de Sessão.
2. O nome da sua Configuração de Sessão registrada. Esse é o mesmo nome que os usuários fornecem para o parâmetro "ConfigurationName" ao se conectarem ao ponto de extremidade com `Enter-PSSession` ou `New-PSSession`.

Para registrar a Configuração de Sessão no computador local, execute o seguinte comando:

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

Parabéns! Você configurou o seu ponto de extremidade JEA.

### Testar seu ponto de extremidade
Execute novamente as etapas listadas na seção [Usando JEA](#using-jea) no novo ponto de extremidade para confirmar se ele está funcionando conforme o esperado.
Use o novo nome de ponto de extremidade (JEADemo2) ao fornecer o nome de configuração para Enter-PSSession.

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

### Conceitos Principais
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

## Capacidades de Função

### Visão geral
Na seção acima, você aprendeu que o campo “RoleDefinitions” definiu quais grupos tinham acesso a quais Capacidades de Função.
Você pode se perguntar: “o que são as Capacidades de Função?"
Esta seção responderá essa pergunta.  

## Apresentando as Capacidades de Função do PowerShell
Capacidades de Função do PowerShell definem "o que" um usuário pode fazer em um ponto de extremidade JEA.
Eles fornecem detalhes sobre uma lista branca de coisas como comandos visíveis, aplicativos visíveis e muito mais.
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
É importante sempre fornecer o caminho completo para comandos externos para garantir que um programa com o mesmo nome (e potencialmente mal-intencionado) colocado no caminho do usuário não seja executado em vez dele.

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

### Criação de Capacidade de Função
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

# Create a RoleCapabilities folder in the AD_Module folder. PowerShell expects Role Capabilities to be located in a "RoleCapabilities" folder within a module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities' -ItemType Directory

# Create a blank Role Capability in your RoleCapabilities folder. Running this command without any additional parameters just creates a blank template.
New-PSRoleCapabilityFile -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc' 
```

Parabéns, você criou um arquivo de Capacidade de Função em branco.
Ele será usado na próxima seção.

### Conceitos Principais
**Capacidade de Função (.psrc)**: um arquivo que define "o que" um usuário pode fazer em um ponto de extremidade JEA.
Ele fornece detalhes sobre uma lista branca de coisas como comandos visíveis, aplicativos de console visíveis e muito mais.
Para que o PowerShell detecte as Capacidades de Função, você deve colocá-los em uma pasta "RoleCapabilities" em um módulo do PowerShell válido.

**Módulo do PowerShell**: um pacote da funcionalidade do PowerShell.
Ele podem conter funções, cmdlets, recursos da DSC, Capacidades de Função do PowerShell e muito mais.
Para ser carregado automaticamente, módulos do PowerShell devem estar localizados em um caminho em `$env:PSModulePath`. 

## Ponta a Ponta - Active Directory
Imagine que o escopo do seu programa aumentou.
Agora você é responsável por adicionar JEA a Controladores de Domínio para executar ações do Active Directory.
As pessoas do suporte técnico pretendem usar JEA para desbloquear contas, redefinir senhas e executar outras ações semelhantes.

Você precisa expor um conjunto totalmente novo de comandos para um grupo diferente de pessoas.
Além disso, você tem um monte de scripts do Active Directory existentes que precisa expor.
Esta seção guiará você pela criação de uma Configuração de Sessão e a Capacidade de Função para esta tarefa.

### Pré-requisitos
Para seguir esta seção passo a passo, você precisará estar operando em um controlador de domínio.
Se não tiver acesso ao controlador de domínio, não se preocupe.
Tente acompanhar trabalhando em outro cenário ou função com a qual você está familiarizado.
Se você quiser configurar rapidamente um novo controlador de domínio, confira o apêndice [Criando um Controlador de Domínio](#creating-a-domain-controller).

### Etapas para criar uma nova Capacidade de Função e Configuração de Sessão

Criar uma nova capacidade de função pode parecer intimidador num primeiro momento, mas pode ser dividido em etapas bem simples:

1.  Identificar as tarefas que você precisa habilitar
2.  Restringir as tarefas conforme necessário
3.  Confirmar se elas funcionam com JEA
4.  Colocá-las em um arquivo de Capacidade de Função
5.  Registrar uma Configuração de Sessão que expõe essa Capacidade de Função

### Etapa 1: Identificar o que precisa ser exposto
Antes de criar uma nova Capacidade de Função ou Configuração de Sessão, você precisará identificar todas as coisas que os usuários precisarão fazer por meio do ponto de extremidade JEA, bem como realizá-las por meio do PowerShell.
Isso envolverá uma quantidade razoável de requisito de coleta e pesquisa.
Como você efetuará esse processo dependerá das suas metas e da organização.
É importante destacar o requisito de coleta e de pesquisa como uma parte essencial do processo do mundo real.
Essa pode ser a etapa mais difícil no processo de adoção de JEA.

#### Encontrar Recursos
Veja este conjunto de recursos online que podem surgir na sua pesquisa sobre a criação de um ponto de extremidade de gerenciamento do Active Directory:
-   [Visão geral do Active Directory PowerShell](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx) 
-   [CMD para Guia do PowerShell para Active Directory](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx)

#### Faça uma lista
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

### Etapa 2: Restringir as tarefas conforme necessário

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

#### Ao lado: adicionar uma função ao seu Módulo
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

### Etapa 4: Editar o arquivo de Capacidade de Função
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

### Etapa 5: Registrar uma nova Configuração de Sessão
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
### Experimente!
Obtenha suas credenciais de usuário não administrador:
```PowerShell
$HelpDeskCred = Get-Credential
```
Se você tiver seguido a seção Configurar Usuários e Grupos, as credenciais serão:
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
### Conceitos Principais
**Modo NoLanguage**: quando o PowerShell está no modo "NoLanguage", os usuários somente podem executar comandos, mas não podem usar elementos de linguagem.
Para obter mais informações, execute `Get-Help about_Language_Modes`.

**Funções do PowerShell**: funções do PowerShell são partes do código do PowerShell que podem ser chamados por nome.
Para obter mais informações, execute `Get-Help about_Functions`.

**ValidateSet/ValidatePattern**: ao expor um comando, você pode restringir os argumentos válidos para os parâmetros específicos.
Um ValidateSet é uma lista específica de comandos válidos.
Um ValidatePattern é uma expressão regular à qual os argumentos para esse parâmetro devem corresponder.

## Manutenção e implantação de vários computador
Neste ponto, você já implantou o JEA para sistemas locais várias vezes.
Como seu ambiente de produção provavelmente consiste em mais de um computador, é importante seguir as etapas essenciais no processo de implantação que deve ser repetido em cada computador.

### Etapas de alto nível:
1.  Copie seus módulos (com Capacidades de Função) para cada nó.
2.  Copie os arquivos de configuração de sessão para cada nó.
3.  Execute `Register-PSSessionConfiguration` com sua sessão de configuração.
4.  Mantenha uma cópia da sua configuração de sessão e kits de ferramentas em um local seguro.
Ao fazer modificações, é recomendável ter uma "única fonte verdadeira".

### Script de Exemplo
Veja este exemplo de script de implantação.
Para usá-lo em seu ambiente, você terá que usar os nomes ou caminhos de compartilhamentos de arquivo reais e módulos.
```PowerShell
# First, copy the session configuration and modules (containing role capability files) onto a file share you have access to.
Copy-Item -Path 'C:\Demo\Demo.pssc' -Destination '\\FileShare\JEA\Demo.pssc'
Copy-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\SomeModule\' -Recurse -Destination '\\FileShare\JEA\SomeModule'

# Next, author a setup script (C:\JEA\Deploy.ps1) to run on each individual node
    # Contents of C:\JEA\Deploy.ps1
    New-Item -ItemType Directory -Path C:\JEADeploy
    Copy-Item -Path '\\FileShare\JEA\Demo.pssc' -Destination 'C:\JEADeploy\'
    Copy-Item -Path '\\FileShare\JEA\SomeModule' -Recurse -Destination 'C:\Program Files\WindowsPowerShell\Modules' # Remember, Role Capability Files are found in modules
    if (Get-PSSessionConfiguration -Name JEADemo -ErrorAction SilentlyContinue)
    {
        Unregister-PSSessionConfiguration -Name JEADemo -ErrorAction Stop
    }

    Register-PSSessionConfiguration -Name JEADemo -Path 'C:\JEADeploy\Demo.pssc'
    Remove-Item -Path 'C:\JEADeploy' # Don't forget to clean up!

# Now, invoke the script on all of the target machines.
# Note: this requires PowerShell Remoting be enabled on each machine. Enabling PowerShell remoting is a requirement to use JEA as well.
# You may need to provide the "-Credential" parameter if your current user account does not have admin permissions on these machines.
Invoke-Command –ComputerName 'Node1', 'Node2', 'Node3', 'NodeN' -FilePath 'C:\JEA\Deploy.ps1'

# Finally, delete the session configuration and role capability files from the file share.
Remove-Item -Path '\\FileShare\JEA\Demo.pssc'
Remove-Item -Path '\\FileShare\JEA\SomeModule' -Recurse
```
### Modificar Capacidades
Ao lidar com vários computadores, é importante que as modificações sejam distribuídas de maneira consistente.
Uma vez que JEA tem um recurso de DSC, isso ajuda a garantir que seu ambiente esteja sincronizado.
Até lá, é altamente recomendável manter uma cópia mestra de suas configurações de sessão e implantar novamente cada vez que fizer uma alteração.

### Remover Capacidades
Para remover a configuração de JEA de seus sistemas, use o seguinte comando em cada computador:
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo 
```
## Relatando no JEA
Como JEA permite que usuários sem privilégios executem em um contexto privilegiado, registro em log e auditoria são extremamente importantes.
Nesta seção, vamos percorrer as ferramentas que você pode usar para ajudá-lo com o log e relatórios.

### Relatar ações do JEA
#### Transcrição Over The Shoulder
Uma das maneiras mais rápidas de obter um resumo do que está acontecendo em uma sessão do PowerShell é realizar Over the Shoulder da pessoa que está digitando.
Você pode ver os comandos, a saída desses comandos e se tudo está bem.
Ou não, mas pelo menos você saberá.
A transcrição do PowerShell foi projetada para dar a você uma exibição semelhante após o fato.

Ao usar o campo "TranscriptDirectory" em sua configuração de sessão, o PowerShell gravará automaticamente uma transcrição de todas as ações executadas em uma determinada sessão.
Você pode encontrar transcrições de suas sessões aqui neste documento: "$env: ProgramData\JEAConfiguration\Transcripts"

Como você pode ver, a transcrição registra informações sobre o usuário "Conectado", o usuário "Executar como", os comandos executados na sessão e muito mais.
Para obter mais informações sobre transcrições do PowerShell, confira este [post de blog](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).

#### Logs de Eventos do PowerShell
Após ativar o registro em log no módulo, todas as ações do PowerShell também são registradas nos logs de Eventos do Windows regulares.
Isso é um pouco mais complicado de lidar quando comparado às transcrições, mas o nível de detalhes fornecido pode ser útil.

No log operacional do "PowerShell", a ID de Evento 4104 registrará cada comando invocado se você tiver habilitado o registro em log do módulo.

#### Outros logs de evento
Diferentemente dos logs do PowerShell e transcrições, outros mecanismos de registro em log não capturarão o "Usuário Conectado".
Você precisará fazer alguma correlação entre outros logs e os do PowerShell para corresponder as ações tomadas.

No log operacional do "Gerenciamento Remoto do Windows", a ID de Evento 193 registrará a SID do Usuário que se conecta e o Nome, bem como a SID da Conta Virtual RunAs auxiliar nessa correlação.
Você também pode ter observado que o nome da Conta Virtual RunAs inclui o domínio e nome de usuário do usuário conectado ao final.

### Relatórios sobre a configuração de JEA
#### Get-PSSessionConfiguration
Para relatar com precisão o estado do seu ambiente, é importante saber quantos pontos de extremidade JEA você tem configurados em seu computador.
`Get-PSSessionConfiguration` faz exatamente isso.
 
#### Get-PSSessionCapability
Relatar manualmente as capacidade de um dado usuário por meio de um ponto de extremidade JEA pode ser bastante complexo.
Potencialmente, você pode precisaria verificar várias capacidades de função.
Felizmente, o cmdlet "Get-PSSessionCapability" faz isso.

Para testar isso, execute o seguinte comando do prompt do administrador do PowerShell:
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```
## Conclusão 
Após a conclusão deste guia, você deverá ter as ferramentas e o vocabulário necessários para criar seu próprio ponto de extremidade JEA. Agradecemos sua leitura!

## Apêndice

## Conceitos fundamentais usados em todo este guia
**Comunicação Remota do PowerShell**: a comunicação remota do PowerShell permite que você execute comandos do PowerShell em computadores remotas.
Você pode operar em um ou vários computadores e usar conexões temporárias ou persistentes.
Nesta demonstração, você acessará remotamente seu computador local com uma sessão interativa.
O JEA restringe a funcionalidade disponível por meio de comunicação remota do PowerShell.
Para obter mais informações sobre a conexão remota do PowerShell, execute `Get-Help about_Remote`.

**Usuário "RunAs"**: ao usar JEA, um não administrador "é executado como" uma conta com privilégios de "Conta Virtual".
A Conta Virtual dura apenas pela duração da sessão remota.
Isso significa que ela é criada quando um usuário se conecta ao ponto de extremidade e é destruída quando o usuário encerra a sessão.
Por padrão, a Conta Virtual é um membro do grupo Administradores local.
Em um controlador de domínio, ele é um membro do grupo Administradores de Domínio.
Contas Virtuais são locais no computador no qual são criadas e não têm permissões fora desse computador.
Isso significa que eles não são registrados no Active Directory (nenhum RID atribuído).
Além disso, se um comando/script permitido tentar acessar recursos fora do computador local, ele acessará esses recursos com a identidade do computador, não da Conta Virtual.

**Usuário "Conectado"**: o usuário não administrador que se conecta ao ponto de extremidade JEA e ao qual são atribuídas as funções.
Quaisquer comandos executado por esse usuário são executados sob o contexto do usuário RunAs ou conta virtual.


### Criar um Controlador de Domínio

Este documento presume que seu computador está ingressado no domínio.
Se atualmente você não tiver um domínio para ingressar, esta seção poderá ajudar a preparar rapidamente um controlador de domínio usando o DSC.

#### Pré-requisitos

1.  O computador está em uma rede interna
2.  O computador não está associado a um domínio existente
3.  O computador está executando o Windows Server 2016 ou tem o WMF 5.0 instalado

#### Instalar xActiveDirectory
Se seu computador tiver uma conexão de Internet ativa, execute o seguinte comando em uma janela elevada do PowerShell:
```PowerShell
Install-Module xActiveDirectory -Force 
```
Se você não tiver uma conexão com a Internet, instale o xActiveDirectory em outro computador e copie a pasta de xActiveDirectory para "C:\Arquivos de Programas\WindowsPowerShell\Modules" em seu computador.

Para confirmar se a instalação foi bem-sucedida, execute o seguinte comando:
```PowerShell
Get-Module xActiveDirectory -ListAvailable
``` 

#### Configurar um nome de domínio com DSC
Copie o seguinte script do PowerShell para tornar o seu computador em um Controlador de Domínio em um novo domínio.
**NOTA DO AUTOR: HÁ UM PROBLEMA CONHECIDO COM AS CREDENCIAIS FORNECIDAS NÃO SENDO USADAS.  POR QUESTÕES DE SEGURANÇA, NÃO ESQUEÇA SUA SENHA DE ADMINISTRADOR LOCAL.**

```PowerShell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value $env:COMPUTERNAME -Force 

# This "MetaConfiguration" sets the DSC Engine to automatically reboot if required
[DscLocalConfigurationManager()]
Configuration MetaConfiguration
{
    Node $env:Computername
    {
        Settings
        {
            RebootNodeIfNeeded = $true
        }
    }
    
}

MetaConfiguration
# Apply the MetaConfiguration
Set-DscLocalConfigurationManager .\MetaConfiguration

# Configure a domain controller of a new "Contoso" domain
configuration DomainController
{
    param
    (
        $node,
        $cred
    )
    Import-DscResource -ModuleName xActiveDirectory

    Node $node
    {
        WindowsFeature ADDS
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain Contoso
        {
            DomainName = 'contoso.com'
            DomainAdministratorCredential = $cred
            SafemodeAdministratorPassword = $cred
            DependsOn = '[WindowsFeature]ADDS'
        }

        file temp
        {
            DestinationPath = 'C:\temp.txt'
            Contents = 'Domain has been created'
            DependsOn = '[xADDomain]Contoso'
        }
    }
}

$ConfigData = @{
    AllNodes = @(
        @{
            NodeName = $env:Computername
            PSDscAllowPlainTextPassword = $true
        }
    )
}

# Enter your desired password for the domain administrator (note, this will be stored as plain text)
DomainController -cred (Get-Credential -Message "Enter desired credential for domain administrator") -node $env:Computername -configurationData $ConfigData

# Apply the configuration to create the domain controller
Start-DSCConfiguration -path .\DomainController -ComputerName $env:Computername -Wait -Force -Verbose
```
O computador reiniciará algumas vezes.
Você saberá que o processo for concluído quando vir um arquivo chamado "C:\Temp.txt." que contém "O domínio foi criado." 

#### Configurar usuários e grupos
Os comandos a seguir configurarão um grupo de Operador e de Suporte Técnico no seu domínio e um usuário não administrador correspondente que é membro desse grupo.
```PowerShell
# Make Groups
$NonAdminOperatorGroup = New-ADGroup -Name "JEA_NonAdmin_Operator" -GroupScope DomainLocal -PassThru
$NonAdminHelpDeskGroup = New-ADGroup -Name "JEA_NonAdmin_HelpDesk" -GroupScope DomainLocal -PassThru
$TestGroup = New-ADGroup -Name "Test_Group" -GroupScope DomainLocal -PassThru

# Make Users
$OperatorUser = New-ADUser -Name "OperatorUser" -AccountPassword (ConvertTo-SecureString "pa`$`$w0rd" -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $OperatorUser

$HelpDeskUser = New-ADUser -name "HelpDeskUser" -AccountPassword (ConvertTo-SecureString "pa`$`$w0rd" -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $HelpDeskUser

# Add Users to Groups
Add-ADGroupMember -Identity $NonAdminOperatorGroup -Members $OperatorUser
Add-ADGroupMember -Identity $NonAdminHelpDeskGroup -Members $HelpDeskUser
```

### Sobre lista negra
Depois de explorar o JEA, você pode estar se perguntando se é possível colocar comandos na lista negra.
Essa é uma solicitação compreensível, mas ela não está planejada para JEA pelos seguintes motivos:

1.  Criamos o JEA para limitar os operadores somente às ações que eles precisam realizar.
Uma lista negra é o oposto.

2.  Os autores de comando do PowerShell não projetaram comandos dele tendo o JEA em mente.
Em uma instalação nova do Windows Server 2016, há cerca de 1520 comandos disponíveis imediatamente.
Os modelos de ameaças para esses comandos não incluem a possibilidade de que um usuário poderia executar comandos como uma conta com mais privilégios.
Por exemplo, determinados comandos permitem realizar injeção de código por design (por exemplo, Add-Type e Invoke-Command no módulo do núcleo do PowerShell).
O JEA pode avisá-lo quando você expõe os comandos específicos que conhecemos, mas não reavaliamos todos os outros comandos no Windows com base no novo modelo de ameaça.
Você deve compreender as capacidades dos comandos que são expostos por meio do JEA.  

3.  Além disso, mesmo que o JEA bloqueie todos os comandos com vulnerabilidades de injeção de código, não há nenhuma garantia de que um usuário mal-intencionado não poderá executar uma ação na lista negra com outro comando relacionado.
A menos que você compreenda todos os comandos que estiver expondo, é impossível assegurar que uma determinada ação não será possível.
Cabe a você entender os comandos que você está expondo, seja usando uma lista branca ou uma lista negra.
O número de comandos que uma lista negra poderia expor é impossível de gerenciar, portanto o JEA é implementado usando listas brancas.

### Considerações sobre a limitação de comandos
Há um ponto importante sobre esta etapa.
É fundamental que todos os recursos expostos por meio de JEA estejam localizados em áreas restritas pelo administrador.
Os usuários não administradores não devem ter a capacidade de modificar os scripts usados por meio de pontos de extremidade JEA.

Falando nisso, é essencial que você não conceda a usuários do JEA a capacidade de substituir configurações do JEA e scripts na lista branca dentro de suas sessões JEA.
Tenha muito cuidado ao expor comandos como `Copy-Item`!

### Armadilhas comuns de Capacidade de Função
Você pode se deparar com comum algumas armadilhas até passar por este processo por conta própria.
Veja este guia rápido que explica como identificar e corrigir esses problemas ao modificar ou criar um novo ponto de extremidade:

#### Funções vs. Cmdlets
Comandos do PowerShell gravados no PowerShell são funções dele.
Comandos do PowerShell gravados como classes especializadas de .NET são Cmdlets do PowerShell.
Você pode verificar o tipo de comando executando `Get-Command`.

#### VisibleProviders 
Você precisará expor quaisquer provedores que precisam de seus comandos.
O mais comum é o provedor do Sistema de Arquivos, mas você também pode precisar expor outros, como o provedor do Registro.
Para obter uma introdução aos provedores, verifique o [post do blog Hey, Scripting Guy](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).
Tenha cuidado ao expor provedores, visto que, geralmente, é melhor definir sua própria função que funciona com os provedores subjacentes do que expor diretamente o provedor em uma sessão JEA.
Dessa forma, você ainda pode permitir aos usuários trabalhar com arquivos, chaves do registro, etc., porém mantém o controle sobre com **quais* arquivos e chaves do Registro eles podem trabalhar usando lógica de validação personalizada.

<!--HONumber=Jun16_HO1-->


