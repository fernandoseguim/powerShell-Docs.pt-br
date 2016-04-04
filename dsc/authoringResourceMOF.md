# Escrevendo um recurso personalizado de DSC com MOF

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Neste tópico, definiremos o esquema para um recurso personalizado de Configuração de Estado Desejado (DSC) do Windows PowerShell em um arquivo MOF, além de implementar o recurso em um arquivo de script do Windows PowerShell. Esse recurso personalizado serve para criar e manter um site da web.

## Criando o esquema MOF

O esquema define as propriedades do recurso que pode ser configurado por um script de configuração DSC.

### Estrutura de pastas para um recurso MOF

Para implementar um recurso personalizado de DSC com esquema MOF, crie a seguinte estrutura de pastas. O esquema MOF é definido no arquivo Demo_IISWebsite.schema.mof; o script de recurso é definido em Demo_IISWebsite.ps1. Opcionalmente, você pode criar um arquivo de manifesto do módulo (psd1).

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

Observe que é necessário criar uma pasta chamada DSCResources na pasta de nível superior e que a pasta para cada recurso deve ter o mesmo nome que o recurso.

### O conteúdo do arquivo MOF

Segue um exemplo de arquivo MOF que pode ser usado para um recurso de sites personalizados. Para seguir esse exemplo, salve o esquema em um arquivo e chame o arquivo de *Demo_IISWebsite.schema.mof*.

```
[ClassVersion("1.0.0"), FriendlyName("Website")] 
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

Observe o seguinte sobre o código anterior:

* `FriendlyName` define o nome que você pode usar para se referir a esse recurso personalizado em scripts de configuração DSC. Neste exemplo, `Website` é equivalente ao nome amigável `Archive` para o recurso interno Archive.
* A classe que você define para o recurso personalizado deve derivar de `OMI_BaseResource`.
* O qualificador de tipo, `[Key]`, em uma propriedade indica que essa propriedade identificará exclusivamente a instância do recurso. Uma propriedade `[Key]` também é necessária.
* O qualificador `[Required]` indica que a propriedade é necessária (um valor deve ser especificado em qualquer script de configuração que usa esse recurso).
* O qualificador `[write]` indica que essa propriedade é opcional ao usar o recurso personalizado em um script de configuração. O qualificador `[read]` indica que uma propriedade não pode ser definida por uma configuração e destina-se apenas para fins de relatório.
* `Values` restringe os valores que podem ser atribuídos à propriedade para a lista de valores definidos em `ValueMap`. Para obter mais informações, consulte [ValueMap e Qualificadores de Valor](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).
* Incluir uma propriedade chamada `Ensure` em seu recurso é recomendado como uma maneira de manter um estilo consistente com recursos internos de DSC.
* Nomeie o arquivo de esquema para o recurso personalizado da seguinte maneira: `classname.schema.mof`, em que `classname` é o identificador que segue a palavra-chave `class` na definição do esquema.

### Escrevendo o script de recurso

O script de recurso implementa a lógica do recurso. Neste módulo, você deve incluir três funções chamadas **Get-TargetResource**, **Set-TargetResource** e **Test-TargetResource**. As três funções precisam usar um conjunto de parâmetros que seja idêntico ao conjunto de propriedades definidas no esquema MOF criado para seu recurso. Neste documento, esse conjunto de propriedades é chamado de “propriedades de recursos”. Armazene essas três funções em um arquivo chamado <ResourceName>.psm1. No exemplo a seguir, as funções são armazenadas em um arquivo chamado Demo_IISWebsite.psm1.

> **Observação**: quando você executa o mesmo script de configuração no recurso mais de uma vez, não deve receber erros e o recurso deve permanecer no mesmo estado do script executado uma vez. Para fazer isso, verifique se suas funções **Get-TargetResource** e **Test-TargetResource** deixam o recurso inalterado e se chamar a função **Set-TargetResource** mais de uma vez em uma sequência com os mesmos valores de parâmetro é sempre equivalente a chamá-la uma vez.

Na implementação da função **Get-TargetResource**, utilize os valores da propriedade de recurso de chave que são fornecidos como parâmetros para verificar o status da instância do recurso especificado. Essa função deve gerar uma tabela de hash que liste todas as propriedades de recursos como chaves e os valores reais dessas propriedades como valores correspondentes. O código a seguir fornece um exemplo.

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance specified in the parameters for the target machine
function Get-TargetResource 
{
    param 
    (       
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <# Insert logic that uses the mandatory parameter values to get the website and assign it to a variable called $Website #>
        <# Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
                                      Name = $Website.Name; 
                                        Ensure = $ensureResult;
                                        PhysicalPath = $Website.physicalPath;
                                        State = $Website.state;
                                        ID = $Website.id;
                                        ApplicationPool = $Website.applicationPool;
                                        Protocol = $Website.bindings.Collection.protocol;
                                        Binding = $Website.bindings.Collection.bindingInformation;
                                    }
  
        $getTargetResourceResult;
}
```

Dependendo dos valores especificados para as propriedades do recurso no script de configuração, a função **Set-TargetResource** deve fazer o seguinte:

* Criar um novo site da web
* Atualizar um site da web existente
* Excluir um site da web existente

O exemplo a seguir mostra isso.

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine. 
function Set-TargetResource 
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param 
    (       
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )
 
    <# If Ensure is set to "Present" and the website specified in the mandatory input parameters does not exist, then create it using the specified parameter values #>
    <# Else, if Ensure is set to "Present" and the website does exist, then update its properties to match the values provided in the non-mandatory parameter values #>
    <# Else, if Ensure is set to "Absent" and the website does not exist, then do nothing #>
    <# Else, if Ensure is set to "Absent" and the website does exist, then delete the website #>
}
```

Por fim, a função **Test-TargetResource** precisa utilizar o mesmo parâmetro configurado como **Get-TargetResource** e **Set-TargetResource**. Na implementação de **Test-TargetResource**, verifique o status da instância do recurso que está especificada nos parâmetros de chave. Se o estado real da instância do recurso não coincidir com os valores especificados no conjunto de parâmetros, gere **$false**. Caso contrário, gere **$true**.

O código a seguir implementa a função **Test-TargetResource**.

```powershell
function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[parameter(Mandatory = $true)]
[System.String]
$Name,

[parameter(Mandatory = $true)]
[System.String]
$PhysicalPath,

[ValidateSet("Started","Stopped")]
[System.String]
$State,

[System.String[]]
$Protocol,

[System.String[]]
$BindingData,

[System.String]
$ApplicationPool
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


#Include logic to 
$result = [System.Boolean]
#Add logic to test whether the website is present and its status mathes the supplied parameter values. If it does, return true. If it does not, return false.
$result 
}
```

**Observação**: para uma depuração mais fácil, use o cmdlet **Write-Verbose** na implementação das três funções anteriores. Esse cmdlet escreve o texto para o fluxo de mensagem detalhada. Por padrão, o fluxo de mensagem detalhada não é exibido, mas você pode exibi-lo alterando o valor da variável **$VerbosePreference** ou usando o parâmetro **Verbose** nos cmdlets DSC = novo.

### Criando o manifesto de módulo

Por fim, use o cmdlet **New-ModuleManifest** para definir um arquivo <ResourceName>.psd1 para o módulo de recurso personalizado. Quando invocar esse cmdlet, faça referência ao arquivo de módulo do script (.psm1) descrito na seção anterior. Inclua **Get-TargetResource**, **Set-TargetResource** e **Test-TargetResource** na lista de funções para exportar. Segue um exemplo de arquivo de manifesto.

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```

<!--HONumber=Feb16_HO4-->


