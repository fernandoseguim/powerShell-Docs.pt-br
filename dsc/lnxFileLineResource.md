# Recurso nxFileLine de DSC para Linux

O recurso **nxFileLine** na Configuração de Estado Desejado (DSC) do PowerShell fornece um mecanismo para gerenciar linhas dentro de um arquivo de configuração em um nó do Linux.

## Sintaxe

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## Propriedades

|  Propriedade |  Descrição | 
|---|---|
| FilePath| O caminho completo até o arquivo para gerenciar linhas no nó de destino.| 
| ContainsLine| Uma linha para garantir que exista no arquivo. Essa linha será acrescentada ao arquivo caso não exista nele. **ContainsLine** é obrigatório, mas poderá ser definido como uma cadeia de caracteres vazia (`ContainsLine = ‘’``) se não for necessário.| 
| DoesNotContainPattern| Um padrão de expressão regular para linhas que não devem existir no arquivo. Para todas as linhas existentes no arquivo que correspondem a essa expressão regular, a linha será removida do arquivo.| 
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a **ID** do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.| 

## Exemplo

Este exemplo demonstra como usar o recurso **nxFileLine** para configurar o arquivo `/etc/sudoers`, garantindo que o usuário: monuser esteja configurado como não requiretty.

```
Import-DSCResource -Module nx 

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
} 
```

<!--HONumber=Feb16_HO4-->
