---
ms.date: 12/12/2018
keywords: DSC,powershell,configuração,instalação
title: Recursos de DSC
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675841"
---
# <a name="dsc-resources"></a>Recursos de DSC

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Os Recursos de Configuração de Estado Desejado (DSC) fornecem os blocos de construção para uma configuração DSC. Um recurso expõe propriedades que podem ser configuradas (esquema) e contém as funções de script do PowerShell que o Gerenciador de Configurações Local (LCM) chama de "realizar".

Um recurso pode modelar algo tão genérico quanto um arquivo ou tão específico quanto uma configuração de servidor do IIS.  Grupos de recursos semelhantes são combinados em um Módulo de DSC, que organiza todos os arquivos necessários em uma estrutura que é portátil e inclui metadados para identificar como os recursos devem ser usados.

Cada recurso tem um * esquema que determina a sintaxe necessária para usar o recurso em um [configuração](../configurations/configurations.md). Esquema do recurso pode ser definida das seguintes maneiras:

- **'Schema'** arquivo: A maioria dos recursos definir seus *esquema* em um 'Schema' de arquivos, usando o [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).
- **'\<Nome do recurso\>. schema.psm1'** arquivo: [Recursos de composição](../configurations/compositeConfigs.md) definir seus *esquema* em um '<ResourceName>. schema.psm1' arquivo usando um [bloco de parâmetro](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).
- **'\<Nome do recurso\>psm1 '** arquivo: Classe com recursos de DSC definem seus *esquema* na definição de classe. Itens de sintaxe são indicados como propriedades de classe. Para obter mais informações, consulte [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).

Para recuperar a sintaxe para um recurso de DSC, use o [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet com o `-Syntax` parâmetro. Esse uso é semelhante ao uso de [Get-Command](/powershell/module/microsoft.powershell.core/get-command) com o `-Syntax` para obter a sintaxe do cmdlet. A saída que você consulte mostrará o modelo usado para um bloco de recursos para o recurso que você especificar.

```powershell
Get-DscResource -Syntax Service
```

A saída que você veja deve ser semelhante à saída abaixo, embora a sintaxe deste recurso foi alterado no futuro. Como a sintaxe do cmdlet, o *chaves* visto entre colchetes, são opcionais. Os tipos de especificam o tipo de dados espera que cada chave.

> [!NOTE]
> O **Certifique-se de** chave é opcional porque o padrão é "Present".

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

Dentro de uma configuração, uma **Service** bloco de recurso poderia se parecer com a **Certifique-se de** que o serviço de Spooler está em execução.

> [!NOTE]
> Antes de usar um recurso em uma configuração, você deve importá-lo usando [Import-DSCResource](../configurations/import-dscresource.md).

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

Configurações podem conter várias instâncias do mesmo tipo de recurso. Cada instância deve ser nomeada exclusivamente. No exemplo a seguir, um segundo **serviço** bloco de recurso é adicionado ao configurar o serviço "DHCP".

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> A partir do PowerShell 5.0, o intellisense foi adicionado para DSC. Esse novo recurso permite que você use \<guia\> e \<Ctrl + espaço\> para preenchimento automático de nomes de chave.

![Conclusão de guia do recurso](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a>Recursos internos

Além dos recursos da comunidade, há recursos internos para recursos de dependência de nó cruzado, recursos para Linux e Windows. Você pode usar as etapas acima para determinar a sintaxe desses recursos e como usá-los. As páginas que atendem a esses recursos foram arquivadas sob **referência**.

Windows built-in resources (Recursos internos do Windows)

* [Recurso Archive](../reference/resources/windows/archiveResource.md)
* [Recurso Environment](../reference/resources/windows/environmentResource.md)
* [Recurso File](../reference/resources/windows/fileResource.md)
* [Recurso Group](../reference/resources/windows/groupResource.md)
* [Recurso GroupSet](../reference/resources/windows/groupSetResource.md)
* [Recurso Log](../reference/resources/windows/logResource.md)
* [Recurso Package](../reference/resources/windows/packageResource.md)
* [Recurso ProcessSet](../reference/resources/windows/ProcessSetResource.md)
* [Recurso Registry](../reference/resources/windows/registryResource.md)
* [Recurso Script](../reference/resources/windows/scriptResource.md)
* [Recurso Service](../reference/resources/windows/serviceResource.md)
* [Recurso ServiceSet](../reference/resources/windows/serviceSetResource.md)
* [Recurso User](../reference/resources/windows/userResource.md)
* [Recurso WindowsFeature](../reference/resources/windows/windowsFeatureResource.md)
* [Recurso WindowsFeatureSet](../reference/resources/windows/windowsFeatureSetResource.md)
* [Recurso WindowsOptionalFeature](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [Recurso WindowsOptionalFeatureSet](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [Recurso WindowsPackageCabResource](../reference/resources/windows/windowsPackageCabResource.md)
* [Recurso WindowsProcess](../reference/resources/windows/windowsProcessResource.md)

[Dependência de nó cruzado](../configurations/crossNodeDependencies.md) recursos

* [WaitForAll recursos](../reference/resources/windows/waitForAllResource.md)
* [WaitForSome recursos](../reference/resources/windows/waitForSomeResource.md)
* [WaitForAny recursos](../reference/resources/windows/waitForAnyResource.md)

Recursos do pacote de gerenciamento

* [Recurso PackageManagement](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [Recurso PackageManagementSource](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

Recursos do Linux

* [Recurso Archive do Linux](../reference/resources/linux/lnxArchiveResource.md)
* [Recursos de ambiente do Linux](../reference/resources/linux/lnxEnvironmentResource.md)
* [Recurso de FileLine do Linux](../reference/resources/linux/lnxFileLineResource.md)
* [Recursos de arquivo do Linux](../reference/resources/linux/lnxFileResource.md)
* [Recurso de grupo Linux](../reference/resources/linux/lnxGroupResource.md)
* [Recurso do pacote do Linux](../reference/resources/linux/lnxPackageResource.md)
* [Recursos de Script do Linux](../reference/resources/linux/lnxScriptResource.md)
* [Recurso de serviço do Linux](../reference/resources/linux/lnxServiceResource.md)
* [Linux SshAuthorizedKeys Resource](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [Recurso de usuário do Linux](../reference/resources/linux/lnxUserResource.md)
