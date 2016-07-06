# Criando e conectando-se a um ponto de extremidade JEA
Para criar um ponto de extremidade JEA, é necessário criar e registrar um arquivo de Configuração de Sessão do PowerShell especialmente configurado, que possa ser gerado com o cmdlet **New-PSSessionConfigurationFile**.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc" 
```

Isso criará um arquivo de configuração de sessão que tem uma aparência semelhante à seguinte: 
```powershell
@{

# Version number of the schema used for this document
SchemaVersion = '2.0.0.0'

# ID used to uniquely identify this document
GUID = 'a384fdd3-5830-4a2c-ac86-cdd1822c3afd'

# Author of this document
Author = 'Administrator'

# Description of the functionality provided by these settings
# Description = ''

# Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
SessionType = 'RestrictedRemoteServer'

# Directory to place session transcripts for this session configuration
TranscriptDirectory = 'C:\ProgramData\JEATranscripts'

# Whether to run this session configuration as the machine's (virtual) administrator account
RunAsVirtualAccount = $true

# Groups associated with machine's (virtual) administrator account
# RunAsVirtualAccountGroups = 'Remote Desktop Users', 'Remote Management Users'

# Scripts to run when applied to a session
# ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

# User roles (security groups), and the Role Capabilities that should be applied to them when applied to a session
RoleDefinitions = @{
    'CONTOSO\NonAdmin_Operators' = @{
        'RoleCapabilities' = 'Maintenance' } }

} 
```
Ao criar um ponto de extremidade JEA, os seguintes parâmetros do comando (e as chaves correspondentes no arquivo) devem ser definidos:
1.  SessionType como RestrictedRemoteServer
2.  RunAsVirtualAccount como **$true**
3.  TranscriptPath como o diretório em que as transcrições “over the shoulder” serão salvas após cada sessão
4.  RoleDefinitions como uma tabela de hash que define quais grupos têm acesso a quais “Funcionalidades da Função”.  Este campo define **quem** pode fazer **o quê** nesse ponto de extremidade.   Funcionalidades da Função são arquivos especiais que serão explicados em breve.


O campo RoleDefinitions define quais grupos tinham acesso a quais Funcionalidades da Função.  Uma Funcionalidade de Função é um arquivo que define um conjunto de funcionalidades que serão expostas aos usuários que estão se conectando.  É possível criar Funcionalidades da Função com o comando **New-PSRoleCapabilityFile**.

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc" 
```

Isso gerará uma funcionalidade de função de modelo que tem uma aparência semelhante à seguinte:
```
@{

# ID used to uniquely identify this document
GUID = '9287a34f-3f0e-4fbe-9dd7-f1361ba9fd65'

# Author of this document
Author = 'Administrator'

# Description of the functionality provided by these settings
# Description = ''

# Company associated with this document
CompanyName = 'Unknown'

# Copyright statement for this document
Copyright = '(c) 2015 Administrator. All rights reserved.'

# Modules to import when applied to a session
# ModulesToImport = 'MyCustomModule', @{ ModuleName = 'MyCustomModule'; ModuleVersion = '1.0.0.0'; GUID = '4d30d5f0-cb16-4898-812d-f20a6c596bdf' }

# Aliases to make visible when applied to a session
# VisibleAliases = 'Item1', 'Item2'

# Cmdlets to make visible when applied to a session
# VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

# Functions to make visible when applied to a session
# VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

# External commands (scripts and applications) to make visible when applied to a session
# VisibleExternalCommands = 'Item1', 'Item2'

# Providers to make visible when applied to a session
# VisibleProviders = 'Item1', 'Item2'

# Scripts to run when applied to a session
# ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

# Aliases to be defined when applied to a session
# AliasDefinitions = @{ Name = 'Alias1'; Value = 'Invoke-Alias1'}, @{ Name = 'Alias2'; Value = 'Invoke-Alias2'}

# Functions to define when applied to a session
# FunctionDefinitions = @{ Name = 'MyFunction'; ScriptBlock = { param($MyInput) $MyInput } }

# Variables to define when applied to a session
# VariableDefinitions = @{ Name = 'Variable1'; Value = { 'Dynamic' + 'InitialValue' } }, @{ Name = 'Variable2'; Value = 'StaticInitialValue' }

# Environment variables to define when applied to a session
# EnvironmentVariables = @{ Variable1 = 'Value1'; Variable2 = 'Value2' }

# Type files (.ps1xml) to load when applied to a session
# TypesToProcess = 'C:\ConfigData\MyTypes.ps1xml', 'C:\ConfigData\OtherTypes.ps1xml'

# Format files (.ps1xml) to load when applied to a session
# FormatsToProcess = 'C:\ConfigData\MyFormats.ps1xml', 'C:\ConfigData\OtherFormats.ps1xml'

# Assemblies to load when applied to a session
# AssembliesToLoad = 'System.Web', 'System.OtherAssembly, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

} 

```
Para ser usadas por uma configuração de sessão JEA, as Funcionalidades da Função devem ser salvas como um módulo PowerShell válido em um diretório chamado “RoleCapabilities”. Um módulo pode ter vários arquivos de funcionalidades da função, se desejado.

Para começar a configurar quais cmdlets, funções, aliases e scripts um usuário poderá acessar ao se conectar a uma sessão JEA, adicione suas próprias regras ao arquivo de Funcionalidade da Função seguindo os modelos comentados. Para obter uma análise mais profunda sobre como você pode configurar Funcionalidades da Função, confira o [guia de experiência](http://aka.ms/JEA) completo.

Finalmente, depois de terminar de personalizar a configuração de sessão e as Funcionalidades da Função relacionadas, registre essa configuração de sessão e crie o ponto de extremidade executando **Register-PSSessionConfiguration**.

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc" 
```

## Conectar-se a um ponto de extremidade JEA
A conexão a um Ponto de Extremidade JEA funciona da mesma forma que a conexão a qualquer outro ponto de extremidade de PowerShell.  Basta nomear o ponto de extremidade JEA como o parâmetro “ConfigurationName” para **New-PSSession**, **Invoke-Command** ou **Enter-PSSession**.

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```
Depois de se conectar à sessão JEA, você estará limitado à execução de comandos na lista de permissões nas Funcionalidades da Função às quais você tem acesso. Caso tente executar algum comando que não seja permitido para sua função, você encontrará um erro.<!--HONumber=Mar16_HO2-->
