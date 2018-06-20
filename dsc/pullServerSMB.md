---
ms.date: 04/11/2018
keywords: DSC,powershell,configuração,instalação
title: Configurando um servidor de pull de SMB para DSC
ms.openlocfilehash: 92c03c99afd612fa2b5475e8c26991ff080584e9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189662"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a>Configurando um servidor de pull de SMB para DSC

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> O Servidor de Recepção (Recurso do Windows *Serviço DSC*) é um componente compatível com o Windows Server, no entanto, não há planos de oferecer novos recursos ou funcionalidades. É recomendável começar a fazer a transição dos clientes gerenciados para o [DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started) (inclui recursos além do Servidor de Recepção no Windows Server) ou para uma das soluções da comunidade listadas [aqui](pullserver.md#community-solutions-for-pull-service).

Um servidor de pull do [SMB](https://technet.microsoft.com/library/hh831795.aspx) é um computador que hospeda compartilhamentos de arquivo SMB que disponibilizam arquivos de configuração DSC e/ou recursos de DSC para nós de destino quando esses nós os solicitam.

Para usar um servidor de pull de SMB para DSC, você precisa:
- Configurar um compartilhamento de arquivos SMB em um servidor executando o PowerShell 4.0 ou superior
- Configurar um cliente executando o PowerShell 4.0 ou superior para efetuar pull desse compartilhamento SMB

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>Usando o recurso xSmbShare para criar um compartilhamento de arquivos SMB

Há várias maneiras para configurar um compartilhamento de arquivos SMB, mas vamos ver como você pode fazer isso usando DSC.

### <a name="install-the-xsmbshare-resource"></a>Instalar o recurso xSmbShare

Chame o cmdlet [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) para instalar o módulo **xSmbShare**.
>**Observação**: **Install-Module** está incluído no módulo **PowerShellGet**, que está incluído no PowerShell 5.0. É possível baixar o módulo **PowerShellGet** para o PowerShell 3.0 e 4.0 em [Visualização de Módulos do PowerShell do PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186). O **xSmbShare** contém o recurso de DSC **xSmbShare**, que pode ser usado para criar um compartilhamento de arquivo SMB.

### <a name="create-the-directory-and-file-share"></a>Criar o diretório e o compartilhamento de arquivos

A configuração a seguir usa o recurso [File](fileResource.md) para criar o diretório para o compartilhamento e o recurso **xSmbShare** para configurar o compartilhamento SMB:

```powershell
Configuration SmbShare {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare

    Node localhost {

        File CreateFolder {

            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'

        }

        xSMBShare CreateShare {

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

A configuração cria o diretório `C:\DscSmbShare` se ele ainda não existir e, em seguida, usa esse diretório como um compartilhamento de arquivos SMB. **FullAccess** deve ser fornecido a qualquer conta que precise gravar no compartilhamento de arquivo ou excluir algo dele e **ReadAccess** deve ser fornecido a qualquer nó de cliente que obterá configurações e/ou recursos de DSC do compartilhamento (isso porque o DSC é executado como a conta do sistema por padrão, de modo que o computador em si precisa ter acesso ao compartilhamento).


### <a name="give-file-system-access-to-the-pull-client"></a>Conceder acesso ao sistema de arquivos para o cliente de pull

Conceder **ReadAccess** para um nó do cliente permite que esse nó acesse o compartilhamento SMB, mas não arquivos ou pastas dentro desse compartilhamento. Você precisa conceder explicitamente aos nós do cliente acesso à pasta e às subpastas de compartilhamento SMB. Podemos fazer isso com o DSC adicionando/usando o recurso **cNtfsPermissionEntry**, que está contido no módulo [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0). A configuração a seguir adiciona um bloco **cNtfsPermissionEntry**, que concede acesso ReadAndExecute ao cliente de pull:

```powershell
Configuration DSCSMB {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare
Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost {

        File CreateFolder {

            DestinationPath = 'DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'

        }

        xSMBShare CreateShare {

            Name = 'DscSmbShare'
            Path = 'DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'

        }

        cNtfsPermissionEntry PermissionSet1 {

        Ensure = 'Present'
        Path = 'C:\DSCSMB'
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

O arquivo MOF de configuração no servidor de pull deve ser nomeado como _ConfigurationID_.mof, em que _ConfigurationID_ é o valor da propriedade **ConfigurationID** do LCM do nó de destino. Para obter mais informações sobre como configurar clientes de pull, confira [Configurando um cliente de pull usando uma ID de configuração](pullClientConfigID.md).

>**Observação:** você deverá usar IDs de configuração se estiver usando um servidor de pull de SMB. Não há suporte para nomes de configuração para SMB.

Cada módulo de recurso precisa ser compactado e nomeado de acordo com o padrão a seguir `{Module Name}_{Module Version}.zip`. Por exemplo, um módulo chamado xWebAdminstration com uma versão do módulo correspondente a 3.1.2.0 seria nomeado 'xWebAdministration_3.2.1.0.zip'. Cada versão de um módulo deve estar contido em um único arquivo zip. Como há apenas uma única versão de um recurso em cada arquivo zip, não há suporte para o formato do módulo adicionado ao WMF 5.0 com suporte para várias versões de módulo em um único diretório. Isso significa que antes de empacotar módulos de recursos DSC para uso com o servidor de pull, você precisará fazer uma pequena alteração na estrutura de diretórios. O formato padrão dos módulos contendo o recurso DSC no WMF 5.0 é '{Pasta do Módulo}\{{Versão do Módulo}\DscResources\{{Pasta do Recurso DSC}\'. Antes do empacotamento para o servidor de pull, simplesmente remova a pasta **{Versão do módulo}** de modo que o caminho se torne '{Pasta do Módulo}\DscResources\{{Pasta do Recurso DSC}\'. Com essa alteração, compacte a pasta conforme descrito acima e coloque esses arquivos zip na pasta de compartilhamento SMB.

## <a name="creating-the-mof-checksum"></a>Criando a soma de verificação de MOF
Um arquivo MOF de configuração precisa ser emparelhado com um arquivo de soma de verificação para que um LCM em um nó de destino possa validar a configuração.
Para criar uma soma de verificação, chame o cmdlet [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx). O cmdlet usa um parâmetro **Path** que especifica a pasta na qual se encontra o MOF de configuração. O cmdlet cria um arquivo de soma de verificação chamado `ConfigurationMOFName.mof.checksum`, em que `ConfigurationMOFName` é o nome do arquivo MOF de configuração.
Se houver mais de um arquivo MOF de configuração na pasta especificada, será criada uma soma de verificação para cada configuração na pasta.

O arquivo de soma de verificação deve estar presente no mesmo diretório em que o arquivo MOF de configuração (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` por padrão) e ter o mesmo nome com a extensão `.checksum` anexada.

>**Observação**: se alterar o arquivo MOF de configuração de qualquer forma, você também deverá recriar o arquivo de soma de verificação.

## <a name="setting-up-a-pull-client-for-smb"></a>Configurando um cliente de pull para SMB

Para configurar um cliente que recebe as configurações e/ou recursos de um compartilhamento SMB, você configura o LCM (Gerenciador de Configurações Local) do cliente com blocos **ConfigurationRepositoryShare** e **ResourceRepositoryShare** que especificam o compartilhamento do qual efetuar o configurações de pull e recursos DSC.

Para obter mais informações sobre como configurar um LCM, consulte [Configurando um cliente de pull usando a ID de configuração](pullClientConfigID.md).

>**Observação:** para simplificar, este exemplo usa o **PSDscAllowPlainTextPassword** para permitir a passagem de uma senha de texto não criptografado para o parâmetro **Credencial**. Para obter informações sobre como passar credenciais de forma mais segura, consulte [Opções de Credenciais nos Dados de Configuração](configDataCredentials.md).

>**Observação:** você deve especificar uma **ConfigurationID** no bloco **Configurações** de uma metaconfiguração de um servidor de pull de SMB, mesmo que só esteja extraindo recursos.

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

Agradecimentos especiais às pessoas a seguir:

- Mike F. Robbins, cujas postagens sobre o uso de SMB para DSC ajudaram a informar o conteúdo deste tópico. Seu blog está em [Mike F Robbins](http://mikefrobbins.com/).
- Serge Nikalaichyk, que criou o módulo **cNtfsAccessControl**. A fonte para esse módulo está em https://github.com/SNikalaichyk/cNtfsAccessControl.

## <a name="see-also"></a>Consulte também
- [Visão Geral da Configuração de Estado Desejado do Windows PowerShell](overview.md)
- [Aplicando configurações](enactingConfigurations.md)
- [Configurando um cliente de pull usando uma ID de configuração](pullClientConfigID.md)