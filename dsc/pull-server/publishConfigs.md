---
ms.date: 12/12/2018
keywords: DSC,powershell,configuração,instalação
title: Publicar em um servidor de Pull usando IDs de configuração (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400166"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>Publicar em um servidor de Pull usando IDs de configuração (v4/v5)

As seções a seguir pressupõem que você já configurou um servidor de recepção. Se você não tiver configurado seu servidor de Pull, você pode usar os guias a seguir:

- [Configurar um servidor de pull SMB de DSC](pullServerSmb.md)
- [Configurar um servidor de pull HTTP de DSC](pullServer.md)

Cada nó de destino pode ser configurado para baixar as configurações, recursos e até mesmo relatar seu status. Este artigo mostra como carregar recursos para que fiquem disponíveis para serem baixadas e configurar clientes para baixar os recursos automaticamente. Quando o nó recebe uma configuração atribuída, por meio **Pull** ou **Push** (v5), ele baixa automaticamente todos os recursos necessários para a configuração do local especificado no LCM.

## <a name="compile-configurations"></a>Compilar as configurações

A primeira etapa para armazenar [configurações](../configurations/configurations.md) em um servidor de recepção, deverá compilá-los em arquivos ". MOF". Para tornar uma configuração genérica e aplicáveis a mais clientes, use `localhost` em seu bloco de nó. O exemplo a seguir mostra um shell de configuração que usa `localhost` em vez de um nome de cliente específico.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

Depois de você ter compilado seu configuração genérica, você deve ter um arquivo de "localhost.mof".

## <a name="renaming-the-mof-file"></a>Renomeando o arquivo MOF

Você pode armazenar arquivos de configuração de ". MOF" em um servidor de Pull por **ConfigurationName** ou **ConfigurationID**. Dependendo de como você planeja configurar os clientes de pull, você pode escolher uma seção abaixo para renomear corretamente seus arquivos compilados ". MOF".

### <a name="configuration-ids-guid"></a>IDs de configuração (GUID)

Será necessário renomear o arquivo "localhost.mof" para "<GUID>. MOF" arquivo. Você pode criar um aleatório **Guid** usando o exemplo abaixo, ou usando o [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.

```powershell
[System.Guid]::NewGuid()
```

Saída de exemplo

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

Em seguida, você pode renomear o arquivo ". MOF" usando qualquer método aceitável. O exemplo a seguir, usa o [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

Para obter mais informações sobre como usar **Guids** em seu ambiente, consulte [planejar Guids](/powershell/dsc/secureserver#guids).

### <a name="configuration-names"></a>Nomes de configuração

Será necessário renomear o arquivo "localhost.mof" para "<Configuration Name>. MOF" arquivo. No exemplo a seguir, o nome da configuração da seção anterior é usado. Em seguida, você pode renomear o arquivo ". MOF" usando qualquer método aceitável. O exemplo a seguir, usa o [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>Criar a soma de verificação

Cada arquivo de ". MOF" armazenado em um servidor de Pull ou compartilhamento SMB precisa ter um arquivo associado ".checksum". Esse arquivo permite que os clientes saber quando o arquivo associado ". MOF" foi alterado e deve ser baixado novamente.

Você pode criar uma **soma de verificação** com o [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet. Você também pode executar `New-DSCCheckSum` em relação a um diretório de arquivos usando o `-Path` parâmetro. Se já existir uma soma de verificação, você pode forçá-lo a ser criada novamente com o `-Force` parâmetro. O exemplo a seguir especificou um diretório que contém o arquivo ". MOF" da seção anterior e usa o `-Force` parâmetro.

```powershell
New-DscChecksum -Path '.\' -Force
```

Nenhuma saída será mostrada, mas agora você deve ver um "<GUID or Configuration Name>. mof.checksum" arquivo.

## <a name="where-to-store-mof-files-and-checksums"></a>Onde armazenar os arquivos MOF e somas de verificação

### <a name="on-a-dsc-http-pull-server"></a>Em um servidor de Pull de HTTP de DSC

Ao configurar seu servidor de Pull de HTTP, conforme explicado em [configurar um servidor de recepção do DSC HTTP](pullServer.md), você especificar diretórios para o **ModulePath** e **ConfigurationPath** chaves. O **ConfigurationPath** chave indica onde todos os arquivos ". MOF" devem ser armazenados. O **ConfigurationPath** indica em que todos os arquivos ". MOF" e ".checksum" arquivos devem ser armazenados.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a>Em um compartilhamento SMB

Quando você configurar um cliente de Pull para usar um compartilhamento SMB, você especifica um **ConfigurationRepositoryShare**. Todos os arquivos ". MOF" e ".checksum" devem ser armazenados em, em seguida, o **SourcePath** diretório da **ConfigurationRepositoryShare** bloco.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>Próximas etapas

Em seguida, você desejará configurar clientes de Pull para extrair a configuração especificada. Para obter mais informações, consulte um dos seguintes guias:

- [Configurar um cliente de Pull usando IDs de configuração (v4)](pullClientConfigId4.md)
- [Configurar um cliente de Pull usando IDs de configuração (v5)](pullClientConfigId.md)
- [Configurar um cliente de Pull usando nomes de configuração (v5)](pullClientConfigNames.md)

## <a name="see-also"></a>Consulte também

- [Configurar um servidor de pull SMB de DSC](pullServerSmb.md)
- [Configurar um servidor de pull HTTP de DSC](pullServer.md)
- [Pacote e os recursos de Upload para um servidor de Pull](package-upload-resources.md)
