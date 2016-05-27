---
title:   Executar DSC com as credenciais do usuário 
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Executar DSC com as credenciais do usuário 

> Aplica-se a: Windows PowerShell 5.0

Você pode executar um recurso de DSC em um conjunto específico de credenciais usando a propriedade automática **PsDscRunAsCredential** na configuração. 
Por padrão, o DSC executa cada recurso como a conta do sistema. 
Há vezes em que executar como usuário é necessário, como ao fazer a instalação de pacotes MSI em um contexto de usuário específico, ao configurar as chaves do registro do um usuário, ao acessar o diretório local específico de um usuário ou ao acessar um compartilhamento de rede.

Cada recurso de DSC tem uma propriedade **PsDscRunAsCredential** que pode ser definida para qualquer credencial de usuário (um objeto [PSCredential](https://msdn.microsoft.com/en-us/library/ms572524(v=VS.85).aspx)).
A credencial pode ser embutida em código como o valor da propriedade na configuração ou você pode definir o valor para [Get-Credential](https://technet.microsoft.com/en-us/library/hh849815.aspx), que solicitará ao usuário uma credencial quando a configuração for compilada (para informações sobre como compilar configurações, confira [Configurações](configurations.md).

>**Observação:** a propriedade **PsDscRunAsCredential** não está disponível no PowerShell 4.0.

No exemplo a seguir, **Get-Credential** é usado para solicitar as credenciais do usuário. 
O recurso de [Registro](registryResource.md) é usado para alterar a chave do Registro que especifica a cor da tela de fundo da janela de prompt de comando do Windows.

```powershell
Configuration ChangeCmdBackGroundColor    
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        Registry CmdPath
        {
            Key                  = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'
            ValueName            = 'DefaultColor'
            ValueData            = '1F'
            ValueType            = 'DWORD'
            Ensure               = 'Present'
            Force                = $true
            Hex                  = $true
            PsDscRunAsCredential = Get-Credential
        }
    }                   
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost';
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

ChangeCmdBackGroundColor -ConfigurationData $configData
```
>**Observação:** Este exemplo pressupõe que você tenha um certificado válido em `C:\publicKeys\targetNode.cer`, e que a impressão digital desse certificado seja o valor exibido.
>Para saber mais sobre como criptografar credenciais em arquivos MOF de configuração de DSC, confira [Proteção do arquivo MOF](secureMOF.md).



<!--HONumber=May16_HO3-->


