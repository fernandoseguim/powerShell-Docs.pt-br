---
ms.date: 12/12/2018
keywords: DSC,powershell,configuração,instalação
title: Pacote e os recursos de Upload para um servidor de Pull
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400141"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>Pacote e os recursos de Upload para um servidor de Pull

As seções a seguir pressupõem que você já configurou um servidor de recepção. Se você não tiver configurado seu servidor de Pull, você pode usar os guias a seguir:

- [Configurar um servidor de pull SMB de DSC](pullServerSmb.md)
- [Configurar um servidor de pull HTTP de DSC](pullServer.md)

Cada nó de destino pode ser configurado para baixar as configurações, recursos e até mesmo relatar seu status. Este artigo mostra como carregar recursos para que fiquem disponíveis para serem baixadas e configurar clientes para baixar os recursos automaticamente. Quando o nó recebe uma configuração atribuída, por meio **Pull** ou **Push** (v5), ele baixa automaticamente todos os recursos necessários para a configuração do local especificado no LCM.

## <a name="package-resource-modules"></a>Módulos de recursos do pacote

Cada recurso disponível para baixar um cliente deve ser armazenado em um arquivo. zip". O exemplo a seguir mostra as etapas necessárias usando o [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) recursos.

> [!NOTE]
> Se você tiver todos os clientes usando o PowerShell 4.0, você precisará flaten a estrutura de pasta de recursos e remova quaisquer pastas de versão. Para obter mais informações, consulte [várias versões do recurso](../configurations/import-dscresource.md#multiple-resource-versions).

Você pode compactar o diretório de recursos usando qualquer utilitário, um script ou um método que preferir. No Windows, você pode *com o botão direito* no diretório "xPSDesiredStateConfiguration" e selecione "Enviar", em seguida, "Pasta compactada".

![Clicar com o botão direito do mouse](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a>Nomear o arquivo de recurso

O arquivo de recurso precisa ser nomeado com o seguinte formato:

```
{ModuleName}_{Version}.zip
```

No exemplo acima, "xPSDesiredStateConfiguration.zip" deve ser renomeado "xPSDesiredStateConfiguration_8.4.4.0.zip".

### <a name="create-checksums"></a>Crie somas de verificação

Quando o módulo de recurso foi compactado e renomeado, você precisará criar uma **soma de verificação**.  O **soma de verificação** é usado, por que o LCM no cliente, para determinar se o recurso foi alterado e precisa ser baixado novamente. Você pode criar uma **soma de verificação** com o [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, como mostrado no exemplo a seguir.

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

Nenhuma saída será mostrada, mas agora você deve ver "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum". Você também pode executar `New-DSCCheckSum` em relação a um diretório de arquivos usando o `-Path` parâmetro. Se já existir uma soma de verificação, você pode forçá-lo a ser criada novamente com o `-Force` parâmetro.

### <a name="where-to-store-resource-archives"></a>Onde armazenar os arquivos de recurso

#### <a name="on-a-dsc-http-pull-server"></a>Em um servidor de Pull de HTTP de DSC

Ao configurar seu servidor de Pull de HTTP, conforme explicado em [configurar um servidor de recepção do DSC HTTP](pullServer.md), você especificar diretórios para o **ModulePath** e **ConfigurationPath** chaves. O **ConfigurationPath** chave indica onde todos os arquivos ". MOF" devem ser armazenados. O **ModulePath** indica onde quaisquer módulos de recursos DSC deve ser armazenados.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a>Em um compartilhamento SMB

Se você tiver especificado uma **ResourceRepositoryShare**, quando a configuração do seu cliente de Pull, armazenar os arquivos e as somas de verificação na **SourcePath** diretório da **ResourceRepositoryShare** bloco.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

Se você tiver especificado apenas uma **ConfigurationRepositoryShare**, quando a configuração do seu cliente de Pull, armazenar os arquivos e as somas de verificação na **SourcePath** diretório da  **ConfigurationRepositoryShare** bloco.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>Atualização de recursos

Você pode forçar um nó para atualizar seus recursos, alterando o número de versão no nome de arquivo, ou criando uma nova soma de verificação. O cliente de Pull verificará se há versões mais recentes dos recursos necessários, bem como atualizadas as somas de verificação quando o LCM é atualizada.

## <a name="see-also"></a>Consulte também

- [Configurar um servidor de pull SMB de DSC](pullServerSmb.md)
- [Configurar um servidor de pull HTTP de DSC](pullServer.md)
