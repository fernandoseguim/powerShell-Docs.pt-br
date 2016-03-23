# Recurso Archive da DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso Archive na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para descompactar arquivos mortos (.zip) em um caminho específico.

## Sintaxe 
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## Propriedades

|  Propriedade  |  Descrição   | 
|---|---| 
| Destination| Especifica o local onde você deseja garantir que o conteúdo do arquivo seja extraído.| 
| Caminho| Especifica o caminho de origem do arquivo morto.| 
| __Soma de verificação__| Define o tipo que deve ser usado para determinar se dois arquivos são iguais. Se __Checksum__ não for especificado, somente o nome de arquivo ou diretório será usado para comparação. Os valores válidos incluem: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate e none (padrão). Se você especificar __Checksum__ sem __Validate__, ocorrerá uma falha na configuração.| 
| Ensure| Determina se é necessário verificar se o conteúdo do arquivo existe em __Destination__. Defina essa propriedade como __Present__ para garantir que o conteúdo exista. Defina-a como __Absent__ para garantir que não exista. O valor padrão é __Present__.| 
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for ResourceName e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.| 
| Validar| Usa a propriedade Checksum para determinar se o arquivo corresponde à assinatura. Se você especificar Checksum sem Validate, ocorrerá uma falha na configuração. Se você especificar Validate sem Checksum, uma soma de verificação SHA-256 será usada por padrão.| 
| Force| Determinadas operações de arquivo (como substituição de um arquivo ou exclusão de um diretório que não esteja vazio) resultarão em erro. O uso da propriedade Force substitui esses erros. O valor padrão é False.| 

## Exemplo

O exemplo a seguir mostra como usar o recurso Archive para garantir que o conteúdo de um arquivo morto chamado Test.zip exista e seja extraído em um destino específico.

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
} 
```
<!--HONumber=Feb16_HO4-->
