---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Usando dados de configuração
ms.openlocfilehash: f2d25b9ced805fb4c91378ebfe840104eb6ce52a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675606"
---
# <a name="using-configuration-data-in-dsc"></a>Usando dados de configuração em DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Usando o parâmetro **ConfigurationData** da DSC interna, você pode definir os dados que podem ser usados dentro de uma configuração.
Isso permite que você crie uma única configuração que pode ser usada para vários nós ou para ambientes diferentes.
Por exemplo, se estiver desenvolvendo um aplicativo, você pode usar uma configuração para os ambientes de desenvolvimento e produção e usar dados de configuração para especificar dados para cada ambiente.

Este tópico descreve a estrutura da tabela de hash **ConfigurationData**.
Para obter exemplos de como usar dados de configuração, consulte [Separando Dados de Configuração e de Ambiente](separatingEnvData.md).

## <a name="the-configurationdata-common-parameter"></a>O parâmetro comum de ConfigurationData

Uma configuração DSC usa um parâmetro comum, **ConfigurationData**, que você especifica ao compilar a configuração.
Para obter informações sobre configurações de compilação, consulte [configurações DSC](configurations.md).

O parâmetro **ConfigurationData** é uma tabela de hash que precisa ter pelo menos uma chave chamada **AllNodes**.
Ele também pode ter uma ou mais chaves.

> [!NOTE]
> Os exemplos neste tópico usam uma única chave adicional (que não é a chave nomeada **AllNodes**) denominada `NonNodeData`, mas você pode incluir qualquer número de chaves adicionais e nomeá-las como desejar.

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

O valor da chave **AllNodes** é uma matriz. Cada elemento dessa matriz também é uma tabela de hash que deve ter pelo menos uma chave chamada **NodeName**:

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

Você também pode adicionar outras chaves para cada tabela de hash:

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

Para aplicar uma propriedade para todos os nós, você pode criar um membro da matriz **AllNodes** que possua um **NodeName** de `*`.
Por exemplo, para atribuir uma propriedade `LogPath` a cada nó, você pode fazer o seguinte:

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

Isso é o equivalente a adicionar uma propriedade com um nome de `LogPath` com um valor de `"C:\Logs"` para cada um dos outros blocos (`VM-1`, `VM-2` e `VM-3`).

## <a name="defining-the-configurationdata-hashtable"></a>Definição da tabela de hash de ConfigurationData

Você pode definir **ConfigurationData** como uma variável dentro do mesmo arquivo de script que uma configuração (como em nossos exemplos anteriores) ou em um arquivo `.psd1` separado.
Para definir **ConfigurationData** em um arquivo `.psd1`, crie um arquivo que contenha somente a tabela de hash que representa os dados de configuração.

Por exemplo, você poderia criar um arquivo chamado `MyData.psd1` com o seguinte conteúdo:

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a>Compilando uma configuração com os dados de configuração

Para compilar uma configuração para a qual você definiu os dados de configuração, passe os dados de configuração como o valor do parâmetro **ConfigurationData**.

Isso criará um arquivo MOF para cada entrada na matriz **AllNodes**.
Cada arquivo MOF será nomeado com a propriedade `NodeName` da entrada de matriz correspondente.

Por exemplo, se você definir dados de configuração como o arquivo `MyData.psd1` acima, compilar uma configuração criará os arquivos `VM-1.mof` e `VM-2.mof`.

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a>Compilando uma configuração com os dados de configuração usando uma variável

Para usar dados de configuração que são definidos como uma variável no mesmo arquivo `.ps1` que a configuração, passe o nome da variável como o valor do parâmetro **ConfigurationData** ao compilar a configuração:

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a>Compilando uma configuração com os dados de configuração usando um arquivo de dados

Para usar dados de configuração que são definidos em um arquivo .psd1, você passa o caminho e o nome desse arquivo como o valor do parâmetro **ConfigurationData** ao compilar a configuração:

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>Usando variáveis de ConfigurationData em uma configuração

DSC fornece as seguintes variáveis especiais que podem ser usadas em um script de configuração:

- A **$AllNodes** refere-se a toda a coleção de nós definida em **ConfigurationData**. Você pode filtrar a coleção **AllNodes** usando **.Where()** e **.ForEach()**.
- O **ConfigurationData** refere-se à tabela de hash inteira que é passada como parâmetro ao compilar uma configuração.
- **MyTypeName** contém o [configuração](configurations.md) nome de variável é usada no. Por exemplo, na configuração `MyDscConfiguration`, o `$MyTypeName` terá um valor de `MyDscConfiguration`.
- O **Nó** refere-se a uma entrada específica na coleção **AllNodes** depois que ela é filtrada usando **.Where()** ou **.ForEach()**.
  - Leia mais sobre esses métodos em [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)

## <a name="using-non-node-data"></a>Usar dados sem nós

Como vimos nos exemplos anteriores, a tabela de hash **ConfigurationData** pode ter uma ou mais chaves além da chave **AllNodes** necessária.
Nos exemplos deste tópico, usamos apenas um único nó adicional e o nomeamos como `NonNodeData`.
No entanto, você pode definir quantas chaves adicionais quiser e nomeá-las da maneira desejada.

Para obter um exemplo de como usar dados que não são do nó, consulte [Separando Dados de Configuração e de Ambiente](separatingEnvData.md).

## <a name="see-also"></a>Consulte Também

- [Opções de credenciais nos dados de configuração](configDataCredentials.md)
- [Configurações DSC](configurations.md)