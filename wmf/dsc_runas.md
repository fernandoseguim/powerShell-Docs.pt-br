# Suporte automático de RunAs para recursos DSC
Suporte para credencial de RunAs do DSC
--------------------------------

A Preview do WMF 5.0 de abril de 2015 inclui suporte para a execução de **qualquer** recurso DSC sob um conjunto de credenciais especificado usando a propriedade PsDscRunAsCredential. Ele permite cenários como instalar pacotes MSI em um contexto de usuário específico, acessar o hive do Registro de um usuário, acessar um diretório de local específico de um usuário, acessar um compartilhamento de rede, etc.

O código a seguir mostra um exemplo de como usar a propriedade PsDscRunAsCredential no DSC para alterar a cor da tela de fundo do prompt de comando de um usuário.

Configuração ChangeCmdBackGroundColor

{

    Node ("localhost")

    {

        Registry CmdPath

        {

            Key = "HKEY\_CURRENT\_USER\\\\Software\\Microsoft\\\\Command Processor"

            ValueName = "DefaultColor"

            ValueData = '1F'

            ValueType = "DWORD"

            Ensure = "Present"

            Force = $true

            Hex = $true

            PsDscRunAsCredential = get-credential

        }

    }

}

$configData = @{

AllNodes = @(

@{

NodeName="localhost";

CertificateFile = "C:\\publicKeys\\targetNode.cer"

}

)

}

ChangeCmdBackGroundColor -ConfigurationData $configData

## Problemas conhecidos

Nesta versão, os seguintes problemas são problemas conhecidos do recurso de credencial de RunAs do DSC:

-   O recurso WindowsProcess não dá suporte à credencial de RunAs.

<!--HONumber=Mar16_HO2-->
