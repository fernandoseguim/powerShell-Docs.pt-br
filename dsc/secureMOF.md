# Protegendo o Arquivo MOF

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Para informar aos nós de destino qual configuração deveriam ter, a DSC envia um arquivo MOF com essas informações para cada nó, em que o Gerenciador de Configurações Local (LCM) implementa a configuração desejada. Como esse arquivo contém os detalhes da configuração, é importante mantê-lo em segurança. Para fazer isso, pode-se definir o Gerenciador de Configurações Local para verificar as credenciais de um usuário. Este tópico descreve como transmitir essas credenciais com segurança para o nó de destino criptografando-as com certificados.

## Pré-requisitos

Para criptografar com êxito as credenciais usadas para proteger uma configuração DSC, verifique se que você tem o seguinte:

* **Algum meio de emitir e distribuir certificados**. Este tópico e seus exemplos pressupõem que você está usando uma Autoridade de Certificação do Active Directory. Para obter mais informações sobre os Serviços de Certificados do Active Directory, consulte [Visão Geral dos Serviços de Certificados do Active Directory](https://technet.microsoft.com/library/hh831740.aspx) e [Serviços de Certificados do Active Directory no Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).
* **Acesso administrativo ao nó ou nós de destino**.
* **Cada nó de destino tem um certificado com capacidade de criptografia salvo no seu Repositório Pessoal**. No Windows PowerShell, o caminho até o repositório é Cert:\LocalMachine\My. Os exemplos neste tópico usam o modelo “autenticação de estação de trabalho”, que você pode encontrar (junto com outros modelos de certificado) em [Modelos de Certificados Padrão](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).
* Se você for executar essa configuração em um computador diferente do nó de destino, **exporte a chave pública do certificado** e, em seguida, importe-a para o computador no qual executará a configuração. Certifique-se de exportar apenas a chave **pública**; mantenha a chave privada em segurança.

## Processo geral

1. Configure os certificados, chaves e as impressões digitais, certificando-se de que cada nó de destino possua cópias do certificado e que o computador de configuração tenha a chave pública e a impressão digital.
1. Crie um bloco de dados de configuração que contenha o caminho e a impressão digital da chave pública.
1. Crie um script de configuração que defina a configuração desejada para o nó de destino e configure a descriptografia em nós de destino ao ordenar que o Gerenciador de Configurações Local descriptografe os dados de configuração usando o certificado e sua impressão digital.
1. Execute a configuração, que definirá as configurações do Gerenciador de Configurações Local e iniciará a configuração DSC.

## Dados de configuração

O bloco de dados de configuração define em quais nós de destino vai operar, se vai criptografar as credenciais ou não, o meio de criptografia e outras informações. Para obter mais informações sobre o bloco de dados de configuração, consulte [Separando Dados de Configuração e de Ambiente](configData.md).

Este exemplo mostra um bloco de dados de configuração que especifica um nó de destino para atuar no targetNode nomeado, o caminho até o arquivo de certificado de chave pública (denominado targetNode.cer) e a impressão digital da chave pública.

```powershell
$ConfigData= @{ 
    AllNodes = @(     
            @{  
                # The name of the node we are describing 
                NodeName = "targetNode" 

                # The path to the .cer file containing the 
                # public key of the Encryption Certificate 
                # used to encrypt credentials for this node 
                CertificateFile = "C:\publicKeys\targetNode.cer" 

         
                # The thumbprint of the Encryption Certificate 
                # used to decrypt the credentials on target node 
                Thumbprint = "AC23EA3A9E291A75757A556D0B71CBBF8C4F6FD8" 
            }; 
        );    
    }
```

## Script de configuração

No próprio script de configuração, use o parâmetro `PsCredential` para garantir que as credenciais sejam armazenadas pelo menor tempo possível. Quando você executa o exemplo fornecido, a DSC solicitará credenciais e, em seguida, criptografará o arquivo MOF usando o CertificateFile que está associado com o nó de destino no bloco de dados de configuração. Este exemplo de código copia um arquivo de um compartilhamento protegido para um usuário.

```
configuration CredentialEncryptionExample 
{ 
    param( 
        [Parameter(Mandatory=$true)] 
        [ValidateNotNullorEmpty()] 
        [PsCredential] $credential 
        ) 
    

    Node $AllNodes.NodeName 
    { 
        File exampleFile 
        { 
            SourcePath = "\\Server\share\path\file.ext" 
            DestinationPath = "C:\destinationPath" 
            Credential = $credential 
        } 
    } 
}
```

## Configurando a descriptografia

Antes que o `Start-DscConfiguration` possa funcionar, você precisa informar ao Gerenciador de Configurações Local em cada nó de destino qual certificado usar para descriptografar as credenciais, usando o recurso CertificateID para verificar a impressão digital do certificado. A função neste exemplo encontrará o certificado local apropriado (talvez seja necessário personalizá-lo para ele encontrar o certificado exato que você deseja usar):

```powershell
# Get the certificate that works for encryption 
function Get-LocalEncryptionCertificateThumbprint 
{ 
    (dir Cert:\LocalMachine\my) | %{
        # Verify the certificate is for Encryption and valid 
        if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify()) 
        { 
            return $_.Thumbprint 
        } 
    } 
}
```

Com o certificado identificado por sua impressão digital, o script de configuração pode ser atualizado para usar o valor:

```powershell
configuration CredentialEncryptionExample 
{ 
    param( 
        [Parameter(Mandatory=$true)] 
        [ValidateNotNullorEmpty()] 
        [PsCredential] $credential 
        ) 
    

    Node $AllNodes.NodeName 
    { 
        File exampleFile 
        { 
            SourcePath = "\\Server\share\path\file.ext" 
            DestinationPath = "C:\destinationPath" 
            Credential = $credential 
        } 
        
        LocalConfigurationManager 
        { 
             CertificateId = $node.Thumbprint 
        } 
    } 
}
```

## Executando a configuração

Neste ponto, você pode executar a configuração, o que resultará em dois arquivos:

* Um arquivo *.meta.mof que configura o Gerenciador de Configurações Local para descriptografar as credenciais usando o certificado armazenado no repositório do computador local e identificado por sua impressão digital. O Set-DscLocalConfigurationManager aplica o arquivo *.meta.mof.
* Um arquivo MOF que realmente aplica a configuração. O Start-DscConfiguration aplica a configuração.

Estes comandos realizarão estas etapas:

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose 
 
Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

Aqui está um exemplo completo que incorpora todas essas etapas, além de um cmdlet auxiliar que exporta e copia as chaves públicas:

```powershell
# A simple example of using credentials
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )
    

    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\server\share\file.txt"
            DestinationPath = "C:\Users\user"
            Credential = $credential
        }
        
        LocalConfigurationManager
        {
            CertificateId = $node.Thumbprint
        }
    }
}

# A Helper to invoke the configuration, with the correct public key 
# To encrypt the configuration credentials
function Start-CredentialEncryptionExample
{
    [CmdletBinding()]
    param ($computerName)


    [string] $thumbprint = Get-EncryptionCertificate -computerName $computerName -Verbose
    Write-Verbose "using cert: $thumbprint"

    $certificatePath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"         

    $ConfigData=    @{
        AllNodes = @(     
                        @{  
                            # The name of the node we are describing
                            NodeName = "$computerName"

                            # The path to the .cer file containing the
                            # public key of the Encryption Certificate
                            CertificateFile = "$certificatePath"

                            # The thumbprint of the Encryption Certificate
                            # used to decrypt the credentials
                            Thumbprint = $thumbprint
                        };
                    );    
    }

    Write-Verbose "Generate DSC Configuration..."
    CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample `
        -credential (Get-Credential -UserName "$env:USERDOMAIN\$env:USERNAME" -Message "Enter credentials for configuration") 

    Write-Verbose "Setting up LCM to decrypt credentials..."
    Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose 

    Write-Verbose "Starting Configuration..."
    Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose

}


#region HelperFunctions

# The folder name for the exported public keys
$script:publicKeyFolder = "publicKeys"

# Get the certificate that works for encryptions
function Get-EncryptionCertificate
{
    [CmdletBinding()]
    param ($computerName)
    $returnValue= Invoke-Command -ComputerName $computerName -ScriptBlock {
            $certificates = dir Cert:\LocalMachine\my

            $certificates | %{
                    # Verify the certificate is for Encryption and valid
                    if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
                    {
                        # Create the folder to hold the exported public key
                        $folder= Join-Path -Path $env:SystemDrive\ -ChildPath $using:publicKeyFolder
                        if (! (Test-Path $folder))
                        {
                            md $folder | Out-Null
                        }

                        # Export the public key to a well known location
                        $certPath = Export-Certificate -Cert $_ -FilePath (Join-Path -path $folder -childPath "EncryptionCertificate.cer") 

                        # Return the thumbprint, and exported certificate path
                        return @($_.Thumbprint,$certPath);
                    }
                  }
        }
    Write-Verbose "Identified and exported cert..."
    # Copy the exported certificate locally
    $destinationPath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"
    Copy-Item -Path (join-path -path \\$computername -childPath $returnValue[1].FullName.Replace(":","$"))  $destinationPath | Out-Null

    # Return the thumbprint
    return $returnValue[0]
}
```<!--HONumber=Feb16_HO4-->
