---
ms.date: 12/12/2018
keywords: DSC, powershell, recursos, da galeria, instalação
title: Adicionar parâmetros a uma configuração
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400205"
---
# <a name="add-parameters-to-a-configuration"></a>Adicionar parâmetros a uma configuração

Assim como as funções, [configurações](configurations.md) pode ser parametrizado para permitir que as configurações mais dinâmicas com base na entrada do usuário. As etapas são semelhantes aos descritos em [funções com parâmetros](/powershell/module/microsoft.powershell.core/about/about_functions).

Este exemplo começa com uma configuração básica que configura o serviço de "Spooler" para "Running".

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a>Parâmetros de configuração internos

Ao contrário de uma função, o [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) atributo não adiciona nenhuma funcionalidade. Além [parâmetros comuns de](/powershell/module/microsoft.powershell.core/about/about_commonparameters), as configurações também podem usar as seguintes internas em parâmetros, sem a necessidade de você defini-las.

|Parâmetro  |Descrição  |
|---------|---------|
|`-InstanceName`|Usado na definição [configurações composto](compositeconfigs.md)|
|`-DependsOn`|Usado na definição [configurações composto](compositeconfigs.md)|
|`-PSDSCRunAsCredential`|Usado na definição [configurações composto](compositeconfigs.md)|
|`-ConfigurationData`|Usado para passar em estruturado [dados de configuração](configData.md) para uso na configuração.|
|`-OutputPath`|Usado para especificar onde o "\<computername\>. MOF" arquivo será compilado|

## <a name="adding-your-own-parameters-to-configurations"></a>Adicionar seus próprios parâmetros a configurações

Além dos parâmetros internos, você também pode adicionar seus próprios parâmetros para suas configurações. O bloco de parâmetro vai diretamente dentro da declaração de configuração, assim como uma função. Um bloco de parâmetro de configuração deve estar fora de qualquer **nó** declarações e acima de qualquer *importar* instruções. Adicionando parâmetros, você pode fazer suas configurações mais robustos e dinâmicos.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>Adicionar um parâmetro ComputerName

O primeiro parâmetro, você pode adicionar é um `-Computername` parâmetro, portanto, você pode compilar um arquivo ". MOF" dinamicamente para qualquer `-Computername` passar à sua configuração. Como funções, você também pode definir um valor padrão, caso o usuário não passa um valor para `-ComputerName`

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

Em sua configuração, em seguida, você pode especificar seu `-ComputerName` parâmetro ao definir seu bloco de nó.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>Chamar a sua configuração com parâmetros

Depois de adicionar parâmetros à sua configuração, você pode usá-los exatamente como você faria com um cmdlet.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>Compilar vários arquivos. MOF

O bloco de nó também pode aceitar uma lista separada por vírgulas de nomes de computador e irá gerar os arquivos ". MOF" para cada um. Você pode executar o exemplo a seguir para gerar arquivos de ". MOF" para todos os computadores no passado para o `-ComputerName` parâmetro.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a>Parâmetros avançados em configurações

Além um `-ComputerName` parâmetro, podemos adicionar parâmetros para o nome do serviço e o estado. O exemplo a seguir adiciona um bloco de parâmetro com um `-ServiceName` parâmetro e o utiliza para definir dinamicamente o **Service** bloco de recurso. Ele também adiciona uma `-State` parâmetro para definir dinamicamente o **estado** no **serviço** bloco de recurso.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> Em mais cenários de advacned, pode fazer mais sentido para mover os dados dinâmicos em um estruturados [dados de configuração](configData.md).

O exemplo de configuração agora leva dinâmico `$ServiceName`, mas se um não for especificado, resulta em um erro de compilação. Você pode adicionar um valor padrão, como neste exemplo.

```powershell
[String]
$ServiceName="Spooler"
```

Nesse caso, faz mais sentido simplesmente forçar o usuário especifique um valor para o `$ServiceName` parâmetro. O `parameter` atributo permite que você adicionar a validação adicional e o pipeline que dão suporte a parâmetros de configuração.

Acima de qualquer declaração de parâmetro, adicione o `parameter` bloco de atributo, como no exemplo a seguir.

```powershell
[parameter()]
[String]
$ServiceName
```

Você pode especificar argumentos para cada `parameter` atributo aos aspectos de controle do parâmetro definido. O exemplo a seguir faz o `$ServiceName` uma **obrigatório** parâmetro.

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

Para o `$State` parâmetro, gostaríamos de impedir que o usuário especificar valores fora de um conjunto predefinido (como em execução, parado) a `ValidationSet*`atributo possam impedir o usuário especificar valores fora de um conjunto predefinido (como em execução, Parado). O exemplo a seguir adiciona o `ValidationSet` de atributo para o `$State` parâmetro. Uma vez que não queremos nos assegurar a `$State` parâmetro **obrigatório**, precisamos adicionar um valor padrão para ele.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> Você não precisará especificar uma `parameter` atributo ao usar um `validation` atributo.

Você pode ler mais sobre o `parameter` e os atributos de validação na [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).

## <a name="fully-parameterized-configuration"></a>Totalmente com parâmetros de configuração

Agora temos uma configuração com parâmetros que força o usuário a especificar uma `-InstanceName`, `-ServiceName`e valida o `-State` parâmetro.

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a>Consulte também

- [Gravar ajuda para configurações de DSC](configHelp.md)
- [Configurações dinâmicas](flow-control-in-configurations.md)
- [Usar dados de configuração em suas configurações](configData.md)
- [Dados de configuração e de ambiente separado](separatingEnvData.md)
