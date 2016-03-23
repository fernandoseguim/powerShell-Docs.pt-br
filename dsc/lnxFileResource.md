# Recurso nxFile de DSC para Linux

O recurso **nxFile** na Configuração de Estado Desejado (DSC) do PowerShell fornece um mecanismo para gerenciar arquivos e diretórios em um nó do Linux.

## Sintaxe

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## Propriedades

|  Propriedade |  Descrição | 
|---|---|
| DestinationPath| Especifica o local onde você deseja garantir o estado de um arquivo ou diretório.| 
| SourcePath| Especifica o caminho do qual o recurso de arquivo ou pasta deve ser copiado. Esse caminho poderá ser um caminho local ou uma URL `http/https/ftp`. Há suporte para URLs `http/https/ftp` remotas apenas quando o valor da propriedade **Type** é file.| 
| Ensure| Determina se é necessário verificar se o arquivo existe. Defina essa propriedade como "Present" para garantir que o arquivo exista. Defina-a como "Absent" para garantir que o arquivo não exista. O valor padrão é "Present".| 
| Tipo| Especifica se o recurso que está sendo configurado é um diretório ou um arquivo. Defina essa propriedade como "directory" para indicar que o recurso é um diretório. Defina-a como "file" para indicar que o recurso é um arquivo. O valor padrão é "file"| 
| Conteúdo| Especifica o conteúdo de um arquivo, como uma cadeia de caracteres específica.| 
| Soma de verificação| Define o tipo que deve ser usado para determinar se dois arquivos são iguais. Se **Checksum** não for especificado, somente o nome de arquivo ou diretório será usado para comparação. Os valores são: "ctime", "mtime" ou "md5".| 
| Recurse| Indica se subdiretórios são incluídos. Defina essa propriedade como **$true** para indicar que você deseja que subdiretórios sejam incluídos. O padrão é **$false**. **Observação:** essa propriedade é válida somente quando a propriedade **Type** é definida como directory.| 
| Force| Determinadas operações de arquivo (como substituição de um arquivo ou exclusão de um diretório que não esteja vazio) resultarão em erro. O uso da propriedade **Force** substitui esses erros. O valor padrão é **$false**.| 
| Links| Especifica o comportamento desejado para links simbólicos. Defina essa propriedade como "follow" para seguir links simbólicos e agir sobre o destino de links (por exemplo, copiar o arquivo em vez do link). Defina essa propriedade como "manage" para agir sobre o link (por exemplo, copiar o próprio link). Defina essa propriedade como "ignore" para ignorar links simbólicos.| 
| Grupo| O nome do **Grupo** que será proprietário do arquivo ou diretório.| 
| Modo| Especifica as permissões desejadas para o recurso, na notação octal ou simbólica. (por exemplo, 777 ou rwxrwxrwx). Se usar notação simbólica, não forneça o primeiro caractere que indica o diretório ou arquivo.| 
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a **ID** do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.| 

## Informações adicionais


Linux e Windows usam diferentes caracteres de quebra de linha em arquivos de texto por padrão; isso pode causar resultados inesperados ao configurar alguns arquivos em um computador Linux com __nxFile__. Há várias maneiras de gerenciar o conteúdo de um arquivo do Linux e, ao mesmo tempo, evitar problemas causados por caracteres de quebra de linha inesperada:

Etapa 1: copie o arquivo de uma origem remota (http, https ou ftp): crie um arquivo em Linux com o conteúdo desejado e prepare-o em m servidor da web ou ftp acessível com o(s) nó(s) que vai configurar. Defina a propriedade __SourcePath__ no recurso __nxFile__ com a URL da web ou do ftp para o arquivo.

```
Import-DSCResource -Module nx
Node $Node
{
nxFile resolvConf
{
    SourcePath = "http://10.185.85.11/conf/resolv.conf"
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    
}
        
}
```


Etapa 2: leia o conteúdo do arquivo no script do PowerShell com [Get-Content](https://technet.microsoft.com/en-us/library/hh849787.aspx) depois de definir a propriedade __$OFS__ para usar o caractere de quebra de linha do Linux.


```
Import-DSCResource -Module nx
Node $Node
{
$OFS = "`n"
$Contents = Get-Content C:\temp\resolv.conf

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    Contents = "$Contents"
}

}
```


Etapa 3: use uma função do PowerShell para substituir as quebras de linha do Windows com caracteres de quebra de linha do Linux.

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
    Return $outputStr
}

Import-DSCResource -Module nx
Node $Node
{

$Contents = @'
search contoso.com
domain contoso.com
nameserver 10.185.85.11
'@

$Contents = LinuxString $Contents

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    Contents = $Contents
    
}
}
```

## Exemplo

O exemplo a seguir garante que o diretório `/opt/mydir` exista e que um arquivo com conteúdo especificado exista nesse diretório.

```
Import-DSCResource -Module nx 

Node $node {
nxFile DirectoryExample
{
   Ensure = "Present"
   DestinationPath = "/opt/mydir"
   Type = "Directory"
}

nxFile FileExample
{
    Ensure = "Present"
    Destinationpath = "/opt/mydir/myfile"
    Contents=@"
#!/bin/bash`necho "hello world"`n
"@ 
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
} 
}
```

<!--HONumber=Feb16_HO4-->
