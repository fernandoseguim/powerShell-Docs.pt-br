---
title:   Recursos File de DSC
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Recursos File de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso File na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para gerenciar arquivos e pastas no nó de destino.

## Sintaxe
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ] 
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ] 
    [ MatchSource = [bool] ]
}
```

## Propriedades

|  Propriedade  |  Descrição   | 
|---|---| 
| DestinationPath| Indica o local onde você deseja garantir o estado de um arquivo ou diretório.| 
| Atributos| Especifica o estado desejado dos atributos para o arquivo ou diretório de destino.| 
| Soma de verificação| Indica o tipo de soma de verificação que deve ser usado para determinar se dois arquivos são iguais. Se __Checksum__ não for especificado, somente o nome de arquivo ou diretório será usado para comparação. Os valores válidos incluem: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.| 
| Conteúdo| Especifica o conteúdo de um arquivo, como uma cadeia de caracteres específica.| 
| Credential| Indicará as credenciais necessárias para acessar recursos, como arquivos de origem, se tal acesso for necessário.| 
| Ensure| Indica se o arquivo ou diretório existe. Defina essa propriedade como "Absent" para garantir que o arquivo ou diretório não exista. Defina-a como "Present" para garantir que o arquivo ou diretório exista. O padrão é "Present".| 
| Force| Determinadas operações de arquivo (como substituição de um arquivo ou exclusão de um diretório que não esteja vazio) resultarão em erro. O uso da propriedade Force substitui esses erros. O valor padrão é __$false__.| 
| Recurse| Indica se subdiretórios são incluídos. Defina essa propriedade como __$true__ para indicar que você deseja que subdiretórios sejam incluídos. O padrão é __$false__. **Observação**: essa propriedade é válida somente quando a propriedade Type é definida como Directory.| 
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.| 
| SourcePath| Indica o caminho do qual o recurso de arquivo ou pasta deve ser copiado.| 
| Tipo| Indica se o recurso que está sendo configurado é um diretório ou um arquivo. Defina essa propriedade como "Directory" para indicar que o recurso é um diretório. Defina-a como "File" para indicar que o recurso é um arquivo. O valor padrão é “File”.| 
| MatchSource| Se definida como o valor padrão de __$false__, em seguida, todos os arquivos de origem (digamos, arquivos A, B e C) serão adicionados ao destino na primeira vez em que a configuração for aplicada. Se for adicionado um novo arquivo (D) à origem, ele não será adicionado ao destino, mesmo quando a configuração for reaplicada posteriormente. Se o valor for __$true__, em seguida, cada vez que a configuração for aplicada, os novos arquivos subsequentemente encontrados na origem (como arquivo D, neste exemplo) serão adicionados ao destino.| 

## Exemplo

O exemplo a seguir mostra como usar o recurso Files para garantir que um diretório com o caminho `C:\Users\Public\Documents\DSCDemo\DemoSource` em um computador de origem (como o servidor de “pull”) também esteja presente (juntamente com todos os subdiretórios) no nó de destino. Também escreve uma mensagem de confirmação no log quando for concluído e inclui uma declaração para garantir que a operação de verificação de arquivos seja executada antes da operação de registro em log.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"    
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```



<!--HONumber=May16_HO3-->


