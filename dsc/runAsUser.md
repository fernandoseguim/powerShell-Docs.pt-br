---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Executar DSC com as credenciais do usuário"
ms.openlocfilehash: 11c13d852b506be3e202b798d135eba73d84cfe0
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="running-dsc-with-user-credentials"></a><span data-ttu-id="22ea9-103">Executar DSC com as credenciais do usuário</span><span class="sxs-lookup"><span data-stu-id="22ea9-103">Running DSC with user credentials</span></span> 

> <span data-ttu-id="22ea9-104">Aplica-se a: Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="22ea9-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="22ea9-105">Você pode executar um recurso de DSC em um conjunto específico de credenciais usando a propriedade automática **PsDscRunAsCredential** na configuração.</span><span class="sxs-lookup"><span data-stu-id="22ea9-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span> <span data-ttu-id="22ea9-106">Por padrão, o DSC executa cada recurso como a conta do sistema.</span><span class="sxs-lookup"><span data-stu-id="22ea9-106">By default, DSC runs each resource as the system account.</span></span>
<span data-ttu-id="22ea9-107">Há vezes em que executar como usuário é necessário, como ao fazer a instalação de pacotes MSI em um contexto de usuário específico, ao configurar as chaves do registro do um usuário, ao acessar o diretório local específico de um usuário ou ao acessar um compartilhamento de rede.</span><span class="sxs-lookup"><span data-stu-id="22ea9-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span>

<span data-ttu-id="22ea9-108">Cada recurso de DSC tem uma propriedade **PsDscRunAsCredential** que pode ser definida para qualquer credencial de usuário (um objeto [PSCredential](https://msdn.microsoft.com/library/ms572524(v=VS.85).aspx)).</span><span class="sxs-lookup"><span data-stu-id="22ea9-108">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](https://msdn.microsoft.com/library/ms572524(v=VS.85).aspx) object).</span></span>
<span data-ttu-id="22ea9-109">A credencial pode ser embutida em código como o valor da propriedade na configuração ou você pode definir o valor para [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx), que solicitará ao usuário uma credencial quando a configuração for compilada (para informações sobre como compilar configurações, confira [Configurações](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="22ea9-109">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

><span data-ttu-id="22ea9-110">**Observação:** no PowerShell 5.0, o uso da propriedade **PsDscRunAsCredential** nas configurações chamando recursos de composição não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="22ea9-110">**Note:** In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span> 
><span data-ttu-id="22ea9-111">No PowerShell 5.1, a propriedade **PsDscRunAsCredential** tem suporte nas configurações chamando recursos de composição.</span><span class="sxs-lookup"><span data-stu-id="22ea9-111">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span>

><span data-ttu-id="22ea9-112">**Observação:** a propriedade **PsDscRunAsCredential** não está disponível no PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="22ea9-112">**Note:** The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="22ea9-113">No exemplo a seguir, **Get-Credential** é usado para solicitar as credenciais do usuário.</span><span class="sxs-lookup"><span data-stu-id="22ea9-113">In the following example, **Get-Credential** is used to prompt the user for credentials.</span></span> <span data-ttu-id="22ea9-114">O recurso de [Registro](registryResource.md) é usado para alterar a chave do Registro que especifica a cor da tela de fundo da janela de prompt de comando do Windows.</span><span class="sxs-lookup"><span data-stu-id="22ea9-114">The [Registry](registryResource.md) resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

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
><span data-ttu-id="22ea9-115">**Observação:** Este exemplo pressupõe que você tenha um certificado válido em `C:\publicKeys\targetNode.cer`, e que a impressão digital desse certificado seja o valor exibido.</span><span class="sxs-lookup"><span data-stu-id="22ea9-115">**Note:** This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span>
><span data-ttu-id="22ea9-116">Para saber mais sobre como criptografar credenciais em arquivos MOF de configuração de DSC, confira [Proteção do arquivo MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="22ea9-116">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](secureMOF.md).</span></span>

