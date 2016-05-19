# Criando um recurso de DSC em C`#`

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Normalmente, um recurso personalizado de Configuração de Estado Desejado (DSC) do Windows PowerShell é implementado em um script do PowerShell. No entanto, também é possível implementar a funcionalidade de um recurso personalizado de DSC escrevendo cmdlets em C#. Para obter uma introdução sobre como escrever cmdlets em C#, consulte [Writing a Windows PowerShell Cmdlet](https://technet.microsoft.com/en-us/library/dd878294.aspx) (Escrevendo um cmdlet do Windows PowerShell).

Com exceção da implementação do recurso em C# como cmdlets, o processo de criar o esquema MOF, criar a estrutura de pastas, importar e usar o recurso de DSC personalizado é igual ao descrito em [Escrevendo um recurso personalizado de DSC com MOF](authoringResourceMOF.md).

## Escrevendo um recurso baseado em cmdlet
Para este exemplo, vamos implementar um recurso simples que gerencia um arquivo de texto e seu conteúdo.

### Escrevendo o esquema MOF

Segue uma definição de recurso MOF.

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;                   
};
```

### Configurando o projeto do Visual Studio
#### Configurando um projeto de cmdlet

1. Abra o Visual Studio.
1. Crie um projeto em C# e forneça o nome.
1. Selecione **Biblioteca de Classes** nos modelos de projeto disponíveis.
1. Clique em **Ok**.
1. Adicione uma referência de assembly a System.Automation.Management.dll ao seu projeto.
1. Altere o nome do assembly para corresponder ao nome do recurso. Nesse caso, o assembly deve se chamar **MSFT_XDemoFile**.

### Escrevendo o código do cmdlet

O código C# a seguir implementa os cmdlets **Get-TargetResource**, **Set-TargetResource** e **Test-TargetResource**.

```C#
Get-TargetResource
       [OutputType(typeof(System.Collections.Hashtable))]
       [Cmdlet(VerbsCommon.Get, "TargetResource")]
       public class GetTargetResource : PSCmdlet
       {
              [Parameter(Mandatory = true)]
              public string Path { get; set; }
 
///<summary>
/// Implement the logic to write the current state of the resource as a 
/// Hash table with keys being the resource properties 
/// and the Values are the corresponding current values on the target machine.
 
///</summary>
              protected override void ProcessRecord()
              {
// Download the zip file at the end of this blog to see sample implementation.
 }
 
Set-TargetResouce
         [OutputType(typeof(void))]
    [Cmdlet(VerbsCommon.Set, "TargetResource")]
    public class SetTargetResource : PSCmdlet
    {
        privatestring _ensure;
        privatestring _content;
        
[Parameter(Mandatory = true)]
        public string Path { get; set; }
        
[Parameter(Mandatory = false)]      
       [ValidateSet("Present", "Absent", IgnoreCase = true)]
       public string Ensure {
            get
            {
                // set the default to present.
               return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
           } 
            public string Content {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }
 
///<summary>
        /// Implement the logic to set the state of the machine to the desired state.
        ///</summary>
        protected override void ProcessRecord()
        {
//Implement the set method of the resource 
/* Uncomment this section if your resource needs a machine reboot.
PSVariable DscMachineStatus = new PSVariable("DSCMachineStatus", 1, ScopedItemOptions.AllScope);
                this.SessionState.PSVariable.Set(DscMachineStatus);
*/     
  }
    }
Test-TargetResource    
       [Cmdlet("Test", "TargetResource")]
    [OutputType(typeof(Boolean))]
    public class TestTargetResource : PSCmdlet
    {   
        
        private string _ensure;
        private string _content;
 
        [Parameter(Mandatory = true)]
        public string Path { get; set; }
 
        [Parameter(Mandatory = false)]
        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure
        {
            get
            {
                // set the default to present.
                return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
        }
 
        [Parameter(Mandatory = false)]
        public string Content
        {
            get { return (string.IsNullOrEmpty(this._content) ? "“:this._content);}
            set { this._content = value; }
        }
 
///<summary>
/// Write a Boolean value which indicates whether the current machine is in    
/// desired state or not.
        ///</summary>
        protected override void ProcessRecord()
        {
                // Implement the test method of the resource.
        }
}
```

### Implantando o recurso

O arquivo dll compilado deve ser salvo em uma estrutura de arquivos semelhante a um recurso baseado em script. Esta é a estrutura de pastas para esse recurso.

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- MyDscResources.psd1 (file, required)     
        |- DSCResources (folder)
            |- MSFT_XDemoFile (folder)
                |- MSFT_XDemoFile.psd1 (file, optional)
                |- MSFT_XDemoFile.dll (file, required)
                |- MSFT_XDemoFile.schema.mof (file, required)
```

### Consulte Também
#### Conceitos
[Escrevendo um recurso personalizado de DSC com MOF](authoringResourceMOF.md)
#### Outros recursos
[Escrevendo um Cmdlet do Windows PowerShell](https://msdn.microsoft.com/en-us/library/dd878294.aspx)


<!--HONumber=May16_HO2-->


