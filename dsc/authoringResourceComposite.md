# Recursos de composição: usando uma configuração DSC como um recurso

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Em situações reais, as configurações podem se tornar longas e complexas, chamando muitos recursos diferentes e definindo um grande número de propriedades. Para ajudar a resolver essa complexidade, é possível usar uma configuração do tipo Configuração de Estado Desejado (DSC) do Windows PowerShell como um recurso para outras configurações. Chamamos isso de recurso de composição. Um recurso de composição é uma configuração DSC que usa parâmetros. Os parâmetros da configuração atuam como as propriedades do recurso. A configuração é salva como um arquivo com uma extensão **. schema.psm1** e assume o lugar do esquema MOF e do script de recurso em um recurso típico de DSC (para obter mais informações sobre os recursos de DSC, consulte [Recursos de Configuração de Estado Desejado do Windows PowerShell](resources.md).

## Criando o recurso de composição

Em nosso exemplo, criamos uma configuração que invoca uma série de recursos existentes para configurar máquinas virtuais. Em vez de especificar os valores a serem definidos em blocos de configuração, a configuração pega uma série de parâmetros que são usados nos blocos de configuração.

```powershell
Configuration xVirtualMachine
{
    param
    (
        # Name of VMs
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String[]] $VMName,

        # Name of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchName,

        # Type of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchType,

        # Source Path for VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDParentPath,

        # Destination path for diff VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDPath,

        # Startup Memory for VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMStartupMemory,

        # State of the VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMState
    )

    # Import the module that defines custom resources
    Import-DscResource -Module xComputerManagement,xHyper-V

    # Install the Hyper-V role
    WindowsFeature HyperV
    {
        Ensure = "Present"
        Name = "Hyper-V"
    }

    # Create the virtual switch
    xVMSwitch $SwitchName
    {
        Ensure = "Present"
        Name = $SwitchName
        Type = $SwitchType
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check for Parent VHD file
    File ParentVHDFile
    {
        Ensure = "Present"
        DestinationPath = $VHDParentPath
        Type = "File"
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check the destination VHD folder
    File VHDFolder
    {
        Ensure = "Present"
        DestinationPath = $VHDPath
        Type = "Directory"
        DependsOn = "[File]ParentVHDFile"
    }

    # Creae VM specific diff VHD
    foreach ($Name in $VMName)
    {
        xVHD "VHD$Name"
        {
            Ensure = "Present"
            Name = $Name
            Path = $VHDPath
            ParentPath = $VHDParentPath
            DependsOn = @("[WindowsFeature]HyperV",
                          "[File]VHDFolder")
        }
    }

    # Create VM using the above VHD
    foreach($Name in $VMName)
    {
        xVMHyperV "VMachine$Name"
        {
            Ensure = "Present"
            Name = $Name
            VhDPath = (Join-Path -Path $VHDPath -ChildPath $Name)
            SwitchName = $SwitchName
            StartupMemory = $VMStartupMemory
            State = $VMState
            MACAddress = $MACAddress
            WaitForIP = $true
            DependsOn = @("[WindowsFeature]HyperV",
                          "[xVHD]VHD$Name")
        }
    }
}
```

### Salvando a configuração como um recurso de composição

Para usar a configuração com parâmetros como um recurso de DSC, salve-a em uma estrutura de diretórios semelhante à de qualquer outro recurso baseado em MOF e nomeie-a com uma extensão **. schema.psm1**. Para esse exemplo, chamaremos o arquivo de **xVirtualMachine.schema.psm1**. Você também precisa criar um manifesto chamado **xVirtualMachine.psd1**, que contém a linha a seguir. Observe que este se soma ao **MyDscResources.psd1**, o manifesto de módulo para todos os recursos na pasta **MyDscResources**.

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

Quando terminar, a estrutura de pastas deve ser a seguinte.

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSC Resources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

O recurso é detectável usando o cmdlet Get-DscResource; suas propriedades são detectáveis por meio desse cmdlet ou usando o preenchimento automático com **Ctrl + espaço** no ISE do Windows PowerShell.

## Usando o recurso de composição

Em seguida, criamos uma configuração que chama o recurso de composição. Essa configuração chama o recurso de composição xVirtualMachine para criar uma máquina virtual e, em seguida, chama o recurso **xComputer** para renomeá-lo.

```powershell

configuration RenameVM
{

    Import-DscResource -Module TestCompositeResource
    Node localhost
    {
        xVirtualMachine VM
        {
            VMName = "Test"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }

    Node "192.168.10.1"
    {
        xComputer Name
        {
            Name = "SQL01"
            DomainName = "fourthcoffee.com"
        }
    }
}
```

## Consulte Também
### Conceitos
* [Escrevendo um recurso personalizado de DSC com MOF](authoringResourceMOF.md)
* [Introdução à Configuração de Estado Desejado do Windows PowerShell](overview.md)
<!--HONumber=Feb16_HO4-->
