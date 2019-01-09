---
ms.date: 12/12/2018
keywords: DSC,powershell,configuração,instalação
title: Usando o Import-DSCResource
ms.openlocfilehash: 6bc3c1aa1d34a05e3188666da825322235c0672e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400259"
---
# <a name="using-import-dscresource"></a>Usando o Import-DSCResource

`Import-DScResource` é uma palavra-chave dynamic, que só pode ser usada dentro de um bloco de script de configuração. O `Import-DSCResource` palavra-chave para importar todos os recursos necessários em sua configuração. Recursos sob `$phsome` são importados automaticamente, mas ainda é considerado uma prática recomendada para importar explicitamente todos os recursos usados no seu [configuração](Configurations.md).

A sintaxe para `Import-DSCResource` é mostrado abaixo.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>]
```

|Parâmetro  |Descrição  |
|---------|---------|
|`-Name`|Os nomes de recurso de DSC, você deve importar. Se o nome do módulo for especificado, o comando procura por esses recursos de DSC neste módulo; Caso contrário, o comando procura os recursos de DSC em todos os caminhos de recurso de DSC. Caracteres curinga são suportados.|
|`-ModuleName`|O nome (s) módulo de contêiner ou especificações do módulo.  Se você especificar os recursos a serem importados de um módulo, o comando tente importar apenas os recursos. Se você especificar apenas o módulo, o comando importa todos os recursos de DSC no módulo.|

Você pode usar caracteres curinga com o `-Name` parâmetro ao usar `Import-DSCResource`.

```powershell
Import-DscResource -Name * -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Exemplo: Usar Import-DSCResource dentro de uma configuração

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName MS_DSC1 -name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    Import-DSCResource -Name File, TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
...
```

> [!NOTE]
> Não há suporte para especificar vários valores para os nomes de recursos e módulos no mesmo comando. Ele pode ter um comportamento não determinístico sobre qual recurso deve ser o caso mesmo recurso existe em vários módulos de carga do qual módulo. Comando abaixo resultará em erro durante a compilação.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Coisas a considerar ao usar somente o parâmetro de nome:

- É uma operação de uso intensivo de recursos, dependendo do número de módulos instalados no computador.
- Ele carregará o primeiro recurso encontrado com o nome fornecido. No caso em que há mais de um recurso com o mesmo nome instalado, ele foi possível carregar o recurso incorreto.

O uso recomendado é para especificar `–ModuleName` com o `-Name` parâmetro, conforme descrito abaixo.

Esse uso tem os seguintes benefícios:

- Ele reduz o impacto no desempenho, limitando o escopo da pesquisa para o recurso especificado.
- Ele define explicitamente o módulo de definição do recurso, garantindo que o recurso correto é carregado.

> [!NOTE]
> No PowerShell 5.0, recursos de DSC podem ter várias versões e as versões podem ser instaladas em um computador lado a lado. Isso é implementado por ter várias versões de um módulo de recursos que estão contidas na mesma pasta de módulo.
> Para obter mais informações, veja [Usando recursos com várias versões](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>IntelliSense com Import-DSCResource

Ao criar a configuração de DSC no ISE, o PowerShell fornece IntelliSence para recursos e propriedades do recurso. Definições de recurso sob a `$pshome` caminho do módulo são carregados automaticamente. Quando você importa os recursos usando o `Import-DSCResource` palavra-chave, as definições de recurso especificados são adicionadas e Intellisense foi expandido para incluir o esquema importado do recurso.

![Recurso Intellisense](/media/resource-intellisense.png)

> [!NOTE]
> A partir do PowerShell 5.0, o preenchimento com tab foi adicionado ao ISE para recursos de DSC e suas propriedades. Para obter mais informações, consulte [recursos](../resources/resources.md).

Ao compilar a configuração, o PowerShell usa as definições de recurso importada para validar todos os blocos de recurso na configuração.
Cada bloco de recurso é validado, usando a definição de esquema do recurso, para as regras a seguir.

- Apenas as propriedades definidas no esquema são usadas.
- Os tipos de dados para cada propriedade estão corretos.
- Propriedades de chaves são especificadas.
- Nenhuma propriedade de somente leitura é usada.
- Validação de valor mapeia tipos.

Considere a seguinte configuração:

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

Isso resulta de configuração em um erro de compilação.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

IntelliSense e validação de esquema permitem capturar mais erros durante o tempo de análise e compilação, evitando a complicações no tempo de execução.

> [!NOTE]
> Cada recurso de DSC pode ter um nome e uma **FriendlyName** definida pelo esquema do recurso. Abaixo estão as duas primeiras linhas de "MSFT_ServiceResource.shema.mof".
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> Ao usar esse recurso em uma configuração, você pode especificar **MSFT_ServiceResource** ou **serviço**.

## <a name="powershell-v4-and-v5-differences"></a>Diferenças de v4 e v5 do PowerShell

Há várias diferenças que você vê quando as configurações de criação no PowerShell 4.0 vs. PowerShell 5.0 e posterior. Esta seção realça as diferenças que você vê relevantes para este artigo.

### <a name="multiple-resource-versions"></a>Várias versões do recurso

Não havia suporte para instalar e usar várias versões de recursos lado a lado no PowerShell 4.0. Se você perceber problemas de importação de recursos em sua configuração, certifique-se de que você só tem uma versão do recurso instalado.

Na imagem abaixo, duas versões dos **xPSDesiredStateConfiguration** módulo são instalados.

![Várias versões de recurso fixas](/media/multiple-resource-versions-broken.md)

Copie o conteúdo da sua versão do módulo desejado para o nível superior do diretório do módulo.

![Várias versões de recurso fixas](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>Localização do recurso

Ao criar e compilar configurações, seus recursos podem ser armazenados em qualquer diretório especificado por seu [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). No PowerShell 4.0, o LCM requer que todos os módulos de recursos de DSC a ser armazenado em "Programa Files\WindowsPowerShell\Modules" ou `$pshome\Modules`. A partir do PowerShell 5.0, esse requisito foi removido e os módulos de recursos podem ser armazenados em qualquer diretório especificado por `PSModulePath`.

## <a name="see-also"></a>Consulte também

- [Recursos](../resources/resources.md)
