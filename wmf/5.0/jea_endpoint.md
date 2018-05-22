---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 66db78cfb136f22cad9078d7113dad085ee667a5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="creating-and-connecting-to-a-jea-endpoint"></a><span data-ttu-id="566c1-102">Criando e conectando-se a um ponto de extremidade JEA</span><span class="sxs-lookup"><span data-stu-id="566c1-102">Creating and Connecting to a JEA Endpoint</span></span>
<span data-ttu-id="566c1-103">Para criar um ponto de extremidade JEA, é necessário criar e registrar um arquivo de Configuração de Sessão do PowerShell especialmente configurado, que possa ser gerado com o cmdlet **New-PSSessionConfigurationFile**.</span><span class="sxs-lookup"><span data-stu-id="566c1-103">To create a JEA endpoint, you need to create and register a specially-configured PowerShell Session Configuration file, which can be generated with the **New-PSSessionConfigurationFile** cmdlet.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc"
```

<span data-ttu-id="566c1-104">Isso criará um arquivo de configuração de sessão que tem uma aparência semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="566c1-104">This will create a session configuration file that looks like this:</span></span>
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
<span data-ttu-id="566c1-105">Ao criar um ponto de extremidade JEA, os seguintes parâmetros do comando (e as chaves correspondentes no arquivo) devem ser definidos:</span><span class="sxs-lookup"><span data-stu-id="566c1-105">When creating a JEA endpoint, the following parameters of the command (and corresponding keys in the file) must be set:</span></span>
1.  <span data-ttu-id="566c1-106">SessionType como RestrictedRemoteServer</span><span class="sxs-lookup"><span data-stu-id="566c1-106">SessionType to RestrictedRemoteServer</span></span>
2.  <span data-ttu-id="566c1-107">RunAsVirtualAccount como **$true**</span><span class="sxs-lookup"><span data-stu-id="566c1-107">RunAsVirtualAccount to **$true**</span></span>
3.  <span data-ttu-id="566c1-108">TranscriptPath como o diretório em que as transcrições “over the shoulder” serão salvas após cada sessão</span><span class="sxs-lookup"><span data-stu-id="566c1-108">TranscriptPath to the directory where “over the shoulder” transcripts will be saved after each session</span></span>
4.  <span data-ttu-id="566c1-109">RoleDefinitions como uma tabela de hash que define quais grupos têm acesso a quais “Funcionalidades da Função”.</span><span class="sxs-lookup"><span data-stu-id="566c1-109">RoleDefinitions to a hashtable that defines which groups have access to which “Role Capabilities.”</span></span>  <span data-ttu-id="566c1-110">Este campo define **quem** pode fazer **o quê** nesse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="566c1-110">This field defines **who** can do **what** on this endpoint.</span></span>   <span data-ttu-id="566c1-111">Funcionalidades da Função são arquivos especiais que serão explicados em breve.</span><span class="sxs-lookup"><span data-stu-id="566c1-111">Role Capabilities are special files that will be explained shortly.</span></span>


<span data-ttu-id="566c1-112">O campo RoleDefinitions define quais grupos tinham acesso a quais Funcionalidades da Função.</span><span class="sxs-lookup"><span data-stu-id="566c1-112">The RoleDefinitions field defines which groups had access to which Role Capabilities.</span></span>  <span data-ttu-id="566c1-113">Uma Funcionalidade de Função é um arquivo que define um conjunto de funcionalidades que serão expostas aos usuários que estão se conectando.</span><span class="sxs-lookup"><span data-stu-id="566c1-113">A Role Capability is a file that defines a set of capabilities that will be exposed to connecting users.</span></span>  <span data-ttu-id="566c1-114">É possível criar Funcionalidades da Função com o comando **New-PSRoleCapabilityFile**.</span><span class="sxs-lookup"><span data-stu-id="566c1-114">You can create Role Capabilities with the **New-PSRoleCapabilityFile** command.</span></span>

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc"
```

<span data-ttu-id="566c1-115">Isso gerará uma funcionalidade de função de modelo que tem uma aparência semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="566c1-115">This will generate a template role capability that looks like this:</span></span>
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
<span data-ttu-id="566c1-116">Para ser usadas por uma configuração de sessão JEA, as Funcionalidades da Função devem ser salvas como um módulo PowerShell válido em um diretório chamado “RoleCapabilities”.</span><span class="sxs-lookup"><span data-stu-id="566c1-116">To be used by a JEA session configuration, Role Capabilities must be saved as a valid PowerShell module in a directory named “RoleCapabilities”.</span></span> <span data-ttu-id="566c1-117">Um módulo pode ter vários arquivos de funcionalidades da função, se desejado.</span><span class="sxs-lookup"><span data-stu-id="566c1-117">A module may have multiple role capability files, if desired.</span></span>

<span data-ttu-id="566c1-118">Para começar a configurar quais cmdlets, funções, aliases e scripts um usuário poderá acessar ao se conectar a uma sessão JEA, adicione suas próprias regras ao arquivo de Funcionalidade da Função seguindo os modelos comentados.</span><span class="sxs-lookup"><span data-stu-id="566c1-118">To start configuring which cmdlets, functions, aliases, and scripts a user may access when connecting to a JEA session, add your own rules to the Role Capability file following the commented out templates.</span></span> <span data-ttu-id="566c1-119">Para obter uma análise mais profunda sobre como você pode configurar Funcionalidades da Função, confira o [guia de experiência](http://aka.ms/JEA) completo.</span><span class="sxs-lookup"><span data-stu-id="566c1-119">For a deeper look into how you can configure Role Capabilities, check out the full [experience guide](http://aka.ms/JEA).</span></span>

<span data-ttu-id="566c1-120">Finalmente, depois de terminar de personalizar a configuração de sessão e as Funcionalidades da Função relacionadas, registre essa configuração de sessão e crie o ponto de extremidade executando **Register-PSSessionConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="566c1-120">Finally, once you have finished customizing your session configuration and related Role Capabilities, register this session configuration and create the endpoint by running **Register-PSSessionConfiguration**.</span></span>

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc"
```

## <a name="connect-to-a-jea-endpoint"></a><span data-ttu-id="566c1-121">Conectar-se a um ponto de extremidade JEA</span><span class="sxs-lookup"><span data-stu-id="566c1-121">Connect to a JEA Endpoint</span></span>
<span data-ttu-id="566c1-122">A conexão a um Ponto de Extremidade JEA funciona da mesma forma que a conexão a qualquer outro ponto de extremidade de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="566c1-122">Connecting to a JEA Endpoint works the same way connecting to any other PowerShell endpoint works.</span></span>  <span data-ttu-id="566c1-123">Basta nomear o ponto de extremidade JEA como o parâmetro “ConfigurationName” para **New-PSSession**, **Invoke-Command** ou **Enter-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="566c1-123">You simply have to give your JEA endpoint name as the “ConfigurationName” parameter for **New-PSSession**, **Invoke-Command**, or **Enter-PSSession**.</span></span>

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```
<span data-ttu-id="566c1-124">Depois de se conectar à sessão JEA, você estará limitado à execução de comandos na lista de permissões nas Funcionalidades da Função às quais você tem acesso.</span><span class="sxs-lookup"><span data-stu-id="566c1-124">Once you have connected to the JEA session, you will be limited to running the commands whitelisted in the Role Capabilities that you have access to.</span></span> <span data-ttu-id="566c1-125">Caso tente executar algum comando que não seja permitido para sua função, você encontrará um erro.</span><span class="sxs-lookup"><span data-stu-id="566c1-125">If you try to run any command not allowed for your role, you will encounter an error.</span></span>
