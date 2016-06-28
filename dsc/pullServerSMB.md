---
title: Configurando um servidor de pull de SMB para DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 35ac9b38086b12fb48844c56a488854f63529e21

---

# Configurando um servidor de pull de SMB para DSC

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Um servidor de pull do [SMB](https://technet.microsoft.com/en-us/library/hh831795.aspx) para DSC é um compartilhamento de arquivos SMB que disponibiliza arquivos de configuração DSC e/ou recursos de DSC para nós de destino quando esses nós os solicitam.

Para usar um servidor de pull de SMB para DSC, você precisa:
- Configurar um compartilhamento de arquivos SMB em um servidor executando o PowerShell 4.0 ou superior
- Configurar um cliente executando o PowerShell 4.0 ou superior para efetuar pull desse compartilhamento SMB

## Usando o recurso xSmbShare para criar um compartilhamento de arquivos SMB

Há várias maneiras para configurar um compartilhamento de arquivos SMB, mas vamos ver como você pode fazer isso usando DSC.

### Instalar o recurso xSmbShare

Chame o cmdlet [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) para instalar o módulo **xSmbShare**.
>**Observação**: **Install-Module** está incluído no módulo **PowerShellGet**, que está incluído no PowerShell 5.0. É possível baixar o módulo **PowerShellGet** para o PowerShell 3.0 e 4.0 em [Visualização de Módulos do PowerShell do PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186). O **xSmbShare** contém o recurso de DSC **xSmbShare**, que pode ser usado para criar um compartilhamento de arquivo SMB.

### Criar o diretório e o compartilhamento de arquivos

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


### Conceder acesso ao sistema de arquivos para o cliente de pull

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

## Colocando configurações e recursos

Salve todos os arquivos MOF de configuração e/ou recursos DSC que você deseja que sejam obtidos por pull do compartilhamento de pasta SMB pelos nós do cliente.

O arquivo MOF de configuração no servidor de pull deve ser nomeado como _ConfigurationID_.mof, em que _ConfigurationID_ é o valor da propriedade **ConfigurationID** do LCM do nó de destino. Para obter mais informações sobre como configurar clientes de pull, confira [Configurando um cliente de pull usando uma ID de configuração](pullClientConfigID.md).

>**Observação:** você deverá usar IDs de configuração se estiver usando um servidor de pull de SMB. Não há suporte para nomes de configuração para SMB.

Todos os recursos exigidos pelo cliente devem ser colocados na pasta de compartilhamento de SMB como arquivos `.zip` arquivados.  

## Criando a soma de verificação de MOF
Um arquivo MOF de configuração precisa ser emparelhado com um arquivo de soma de verificação para que um LCM em um nó de destino possa validar a configuração. Para criar uma soma de verificação, chame o cmdlet [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx). O cmdlet usa um parâmetro **Path** que especifica a pasta na qual se encontra o MOF de configuração. O cmdlet cria um arquivo de soma de verificação chamado `ConfigurationMOFName.mof.checksum`, em que `ConfigurationMOFName` é o nome do arquivo MOF de configuração. Se houver mais de um arquivo MOF de configuração na pasta especificada, será criada uma soma de verificação para cada configuração na pasta.

O arquivo de soma de verificação deve estar presente no mesmo diretório em que o arquivo MOF de configuração (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` por padrão) e ter o mesmo nome com a extensão `.checksum` anexada.

>**Observação**: se alterar o arquivo MOF de configuração de qualquer forma, você também deverá recriar o arquivo de soma de verificação.

## Agradecimentos

Agradecimentos especiais às pessoas a seguir:

- Mike F. Robbins, cujas postagens sobre o uso de SMB para DSC ajudaram a informar o conteúdo deste tópico. Seu blog está em [Mike F Robbins](http://mikefrobbins.com/).
- Serge Nikalaichyk, que criou o módulo **cNtfsAccessControl**. A fonte para esse módulo está em https://github.com/SNikalaichyk/cNtfsAccessControl.

## Consulte também
- [Visão Geral da Configuração de Estado Desejado do Windows PowerShell](overview.md)
- [Aplicando configurações](enactingConfigurations.md)
- [Configurando um cliente de pull usando uma ID de configuração](pullClientConfigID.md)

 



<!--HONumber=Jun16_HO4-->


