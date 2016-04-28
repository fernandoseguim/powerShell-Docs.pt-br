# Executar DSC com as credenciais do usuário 

> Aplica-se a: Windows PowerShell 5.0

Você pode executar uma configuração DSC em um conjunto específico de credenciais usando a propriedade **PsDscRunAsCredential** na configuração. Por padrão, a DSC executa
como a conta do sistema. Há vezes em que é necessário executar como um usuário, como ao instalar pacotes MSI em um contexto de usuário específico, definir as chaves de registro de um usuário,
acessar o diretório local específico de um usuário ou acessar um compartilhamento de rede.

Cada recurso DSC tem uma propriedade **PsDscRunAsCredential** que pode ser definida para quaisquer credenciais de usuário (um objeto [PSCredential](https://msdn.microsoft.com/en-us/library/ms572524(v=VS.85).aspx)).
A credencial pode ser embutida em código como o valor da propriedade na configuração, ou você pode definir o valor para [Get-Credential](https://technet.microsoft.com/en-us/library/hh849815.aspx),
que solicitará uma credencial ao usuário quando a configuração for compilada (para obter informações sobre configurações ao compilar, consulte [Configurações](configurations.md)).

>**Observação:** a propriedade **PsDscRunAsCredential** não está disponível no PowerShell 4.0.

No exemplo a seguir, **Get-Credential** é usada para solicitar as credenciais do usuário. O recurso [Registry](registryResource.md) é usado para alterar a chave do registro que especifica a cor da tela de fundo
para a janela de prompt de comando do Windows.

```powershell
Configuration ChangeCmdBackGroundColor    

{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName

    {
        Registry CmdPath

        {

            Key = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'

            ValueName = "DefaultColor"

            ValueData = '1F'

            ValueType = "DWORD"

            Ensure = "Present"

            Force = $true

            Hex = $true

            PsDscRunAsCredential = Get-Credential
        }
    }                   
}

$configData = @{

    AllNodes = @(

    @{

        NodeName="localhost";
        PSDscAllowDomainUser = $true
        CertificateFile = "C:\publicKeys\targetNode.cer"
        Thumbprint = "7ee7f09d-4be0-41aa-a47f-96b9e3bdec25"

    })

}

ChangeCmdBackGroundColor -ConfigurationData $configData
```
>**Observação:** este exemplo pressupõe que você tenha um certificado válido em `C:\publicKeys\targetNode.cer` e a impressão digital desse certificado é o valor exibido.
>Para obter informações sobre como criptografar credenciais em arquivos MOF de configuração DSC, consulte [Protegendo o arquivo MOF](secureMOF.md). 



<!--HONumber=Mar16_HO2-->


