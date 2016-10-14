# Find-Command

Localiza comandos do PowerShell em módulos.

## Descrição
O cmdlet Find-Command localiza comandos do PowerShell, como cmdlets, aliases, funções e fluxos de trabalho. Find-Command faz pesquisas em módulos em repositórios registrados.
Para cada comando que localiza, esse cmdlet retorna um objeto PSGetCommandInfo. Você pode passar um objeto PSGetCommandInfo para o cmdlet Install-Module para instalar o módulo que contém o comando.

- Find-Command pode filtrar segundo os parâmetros de versão: MinimumVersion, RequiredVersion, AllVersions.
  - Esses parâmetros são mutuamente exclusivos.
  - Esses parâmetros de versão são permitidos apenas com o nome exclusivo do módulo, sem curingas.
  - Se o parâmetro RequiredVersion não for especificado, Find-Command retorna a versão mais recente do módulo que for igual ou maior que a versão mínima especificada ou a versão mais recente do módulo se nenhuma versão mínima tiver sido especificada.
  - Se o parâmetro RequiredVersion for especificado, Find-Command retornará apenas a versão do módulo que corresponde exatamente à versão especificada.
- Find-Command pode filtrar os metadados do módulo com o parâmetro -Tag
- Find-Command pode filtrar a linguagem de pesquisa específica do repositório com o parâmetro -Filter.
- Find-Command pode filtrar módulos de todos ou de alguns dos repositórios registrados.

## Sintaxe do cmdlet
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## Referência da ajuda online sobre cmdlets

[Find-Command](http://go.microsoft.com/fwlink/?LinkId=733636)

## Comandos de exemplo
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```

<!--HONumber=Aug16_HO3-->


