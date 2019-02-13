---
ms.date: 04/11/2018
keywords: DSC,powershell,configuração,instalação
title: Configurando um servidor de pull de SMB para DSC
ms.openlocfilehash: 722120369df9ff383a02c69111e0bacf2e2e76a5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675675"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a>Configurando um servidor de pull de SMB para DSC

Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> O Servidor de Recepção (Recurso do Windows *Serviço DSC*) é um componente compatível com o Windows Server, no entanto, não há planos de oferecer novos recursos ou funcionalidades. É recomendável começar a fazer a transição dos clientes gerenciados para o [DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started) (inclui recursos além do Servidor de Recepção no Windows Server) ou para uma das soluções da comunidade listadas [aqui](pullserver.md#community-solutions-for-pull-service).

Um servidor de pull do [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) é um computador que hospeda compartilhamentos de arquivo SMB que disponibilizam arquivos de configuração DSC e/ou recursos de DSC para nós de destino quando esses nós os solicitam.

Para usar um servidor de pull de SMB para DSC, você precisa:

- Configurar um compartilhamento de arquivos SMB em um servidor executando o PowerShell 4.0 ou superior
- Configurar um cliente executando o PowerShell 4.0 ou superior para efetuar pull desse compartilhamento SMB

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>Usando o recurso xSmbShare para criar um compartilhamento de arquivos SMB

Há várias maneiras para configurar um compartilhamento de arquivos SMB, mas vamos ver como você pode fazer isso usando DSC.

### <a name="install-the-xsmbshare-resource"></a>Instalar o recurso xSmbShare

Chame o cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module) para instalar o módulo **xSmbShare**.

> [!NOTE]
> `Install-Module` está incluído no módulo **PowerShellGet**, que está incluído no PowerShell 5.0. É possível baixar o módulo **PowerShellGet** para o PowerShell 3.0 e 4.0 em [Visualização de Módulos do PowerShell do PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).
> O **xSmbShare** contém o recurso de DSC **xSmbShare**, que pode ser usado para criar um compartilhamento de arquivo SMB.

### <a name="create-the-directory-and-file-share"></a>Criar o diretório e o compartilhamento de arquivos

A configuração a seguir usa o recurso **File** para criar o diretório para o compartilhamento e o recurso **xSmbShare** para configurar o compartilhamento SMB:

```powershell
Configuration SmbShare
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'admininstrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

A configuração cria o diretório `C:\DscSmbShare`, se ainda não existir e, em seguida, usa esse diretório como um compartilhamento de arquivos SMB. **FullAccess** deve ser fornecido a qualquer conta que precise gravar ou excluir do compartilhamento de arquivos. **ReadAccess** deve ser fornecido a quaisquer nós de cliente que obtêm as configurações e/ou recursos de DSC do compartilhamento.

> [!NOTE]
> DSC é executado como a conta do sistema por padrão, o próprio computador deve ter acesso ao compartilhamento.

### <a name="give-file-system-access-to-the-pull-client"></a>Conceder acesso ao sistema de arquivos para o cliente de pull

Conceder **ReadAccess** para um nó do cliente permite que esse nó acesse o compartilhamento SMB, mas não arquivos ou pastas dentro desse compartilhamento. Você precisa conceder explicitamente acesso de nós para a pasta de compartilhamento SMB e as subpastas de cliente. Podemos fazer isso com o DSC adicionando/usando o recurso **cNtfsPermissionEntry**, que está contido no módulo [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0). A configuração a seguir adiciona um bloco **cNtfsPermissionEntry**, que concede acesso ReadAndExecute ao cliente de pull:

```powershell
Configuration DSCSMB
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare
    Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }

        cNtfsPermissionEntry PermissionSet1
        {
            Ensure = 'Present'
            Path = 'C:\DscSmbShare'
            Principal = 'myDomain\Contoso-Server$'
            AccessControlInformation = @(
                cNtfsAccessControlInformation
                {
                    AccessControlType = 'Allow'
                    FileSystemRights = 'ReadAndExecute'
                    Inheritance = 'ThisFolderSubfoldersAndFiles'
                    NoPropagateInherit = $false
                }
            )
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

## <a name="placing-configurations-and-resources"></a>Colocando configurações e recursos

Salve todos os arquivos MOF de configuração e/ou recursos DSC que você deseja que sejam obtidos por pull do compartilhamento de pasta SMB pelos nós do cliente.

O arquivo MOF de configuração no servidor de pull deve ser nomeado como *ConfigurationID*.mof, em que *ConfigurationID* é o valor da propriedade **ConfigurationID** do LCM do nó de destino. Para obter mais informações sobre como configurar clientes de pull, confira [Configurando um cliente de pull usando uma ID de configuração](pullClientConfigID.md).

> [!NOTE]
> Você deverá usar IDs de configuração se estiver usando um servidor de pull de SMB. Não há suporte para nomes de configuração para SMB.

Cada módulo de recurso precisa ser compactado e nomeado de acordo com o seguinte padrão `{Module Name}_{Module Version}.zip`. Por exemplo, um módulo chamado xWebAdminstration com uma versão do módulo correspondente a 3.1.2.0 seria nomeado 'xWebAdministration_3.2.1.0.zip'. Cada versão de um módulo deve estar contido em um único arquivo zip. Não há suporte para versões separadas de um módulo em um arquivo zip. Antes de empacotar módulos de recursos de DSC para uso com o servidor de pull, você precisa fazer uma pequena alteração na estrutura de diretório.

O formato padrão de módulos contendo recursos DSC no WMF 5.0 é `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.

Antes de empacotar o servidor de pull, simplesmente remova a pasta `{Module version}` para que o caminho se torne `{Module Folder}\DscResources\{DSC Resource Folder}\`. Com essa alteração, compacte a pasta conforme descrito acima e coloque esses arquivos zip na pasta de compartilhamento SMB.

## <a name="creating-the-mof-checksum"></a>Criando a soma de verificação de MOF

Um arquivo MOF de configuração precisa ser emparelhado com um arquivo de soma de verificação para que um LCM em um nó de destino possa validar a configuração.
Para criar uma soma de verificação, chame o cmdlet [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum). O cmdlet usa um parâmetro `Path` que especifica a pasta na qual se encontra o MOF de configuração. O cmdlet cria um arquivo de soma de verificação chamado `ConfigurationMOFName.mof.checksum`, em que `ConfigurationMOFName` é o nome do arquivo MOF de configuração.
Se houver mais de um arquivo MOF de configuração na pasta especificada, será criada uma soma de verificação para cada configuração na pasta.

O arquivo de soma de verificação deve estar presente no mesmo diretório em que o arquivo MOF de configuração (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` por padrão) e ter o mesmo nome com a extensão `.checksum` anexada.

> [!NOTE]
> Se alterar o arquivo MOF de configuração de qualquer forma, você também deverá recriar o arquivo de soma de verificação.

## <a name="setting-up-a-pull-client-for-smb"></a>Configurando um cliente de pull para SMB

Para configurar um cliente que recebe as configurações e/ou recursos de um compartilhamento SMB, você configura o LCM (Gerenciador de Configurações Local) do cliente com blocos **ConfigurationRepositoryShare** e **ResourceRepositoryShare** que especificam o compartilhamento do qual efetuar o configurações de pull e recursos DSC.

Para obter mais informações sobre como configurar um LCM, consulte [Configurando um cliente de pull usando a ID de configuração](pullClientConfigID.md).

> [!NOTE]
> Para simplificar, este exemplo usa o **PSDscAllowPlainTextPassword** para permitir a passagem de uma senha de texto não criptografado para o parâmetro **Credencial**. Para obter informações sobre como passar credenciais de forma mais segura, consulte [Opções de Credenciais nos Dados de Configuração](../configurations/configDataCredentials.md).
>
> Você **DEVE** especificar uma **ConfigurationID** no bloco **Configurações** de uma metaconfiguração de um servidor de pull de SMB, mesmo que só esteja extraindo recursos.

```powershell
$secpasswd = ConvertTo-SecureString “Pass1Word” -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential (“TestUser”, $secpasswd)

[DSCLocalConfigurationManager()]
configuration SmbCredTest
{
    Node $AllNodes.NodeName
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
            ConfigurationID    = '16db7357-9083-4806-a80c-ebbaf4acd6c1'
        }

         ConfigurationRepositoryShare SmbConfigShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds
        }

        ResourceRepositoryShare SmbResourceShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds

        }
    }
}

$ConfigurationData = @{
    AllNodes = @(
        @{
            #the "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="localhost"
            PSDscAllowPlainTextPassword = $true
        })
}
```

## <a name="acknowledgements"></a>Agradecimentos

Agradecimentos especiais a seguintes pessoas:

- Mike F. Robbins, cujas postagens sobre o uso de SMB para DSC ajudaram a informar o conteúdo deste tópico. Seu blog está em [Mike F Robbins](http://mikefrobbins.com/).
- Serge Nikalaichyk, que criou o módulo **cNtfsAccessControl**. A fonte para esse módulo está em [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).

## <a name="see-also"></a>Consulte também

[Visão Geral da Configuração de Estado Desejado do Windows PowerShell](../overview/overview.md)

[Aplicando configurações](enactingConfigurations.md)

[Configurando um cliente de pull usando uma ID de configuração](pullClientConfigID.md)
