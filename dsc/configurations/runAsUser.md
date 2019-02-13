---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Usar credenciais com recursos de DSC
ms.openlocfilehash: af54c286ce744cd7db0b0e2d05087f60cdf1a33c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675953"
---
# <a name="use-credentials-with-dsc-resources"></a>Usar credenciais com recursos de DSC

> Aplica-se a: Windows PowerShell 5.0, Windows PowerShell 5.1

Você pode executar um recurso de DSC em um conjunto específico de credenciais usando a propriedade automática **PsDscRunAsCredential** na configuração.
Por padrão, o DSC executa cada recurso como a conta do sistema.
Há vezes em que executar como usuário é necessário, como ao fazer a instalação de pacotes MSI em um contexto de usuário específico, ao configurar as chaves do registro do um usuário, ao acessar o diretório local específico de um usuário ou ao acessar um compartilhamento de rede.

Cada recurso de DSC tem uma propriedade **PsDscRunAsCredential** que pode ser definida para qualquer credencial de usuário (um objeto [PSCredential](/dotnet/api/system.management.automation.pscredential)).
A credencial pode ser embutida em código como o valor da propriedade na configuração ou você pode definir o valor para [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), que solicitará ao usuário uma credencial quando a configuração for compilada (para informações sobre como compilar configurações, confira [Configurações](configurations.md).

> [!NOTE]
> No PowerShell 5.0, o uso da propriedade **PsDscRunAsCredential** nas configurações chamando recursos de composição não tem suporte.
> No PowerShell 5.1, a propriedade **PsDscRunAsCredential** tem suporte nas configurações chamando recursos de composição.
> A propriedade **PsDscRunAsCredential** não está disponível no PowerShell 4.0.

No exemplo a seguir, `Get-Credential` é usado para solicitar as credenciais do usuário.
O recurso de **Registro** é usado para alterar a chave do Registro que especifica a cor da tela de fundo da janela de prompt de comando do Windows.

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

> [!NOTE]
> Este exemplo pressupõe que você tenha um certificado válido em `C:\publicKeys\targetNode.cer`, e que a impressão digital desse certificado seja o valor exibido.
> Para saber mais sobre como criptografar credenciais em arquivos MOF de configuração de DSC, confira [Proteção do arquivo MOF](../pull-server/secureMOF.md).
