---
title:   Recurso nxArchive de DSC para Linux
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Recurso nxArchive de DSC para Linux

O recurso **nxArchive** na Configuração de Estado Desejado (DSC) do PowerShell fornece um mecanismo para descompactar arquivos mortos (.tar, .zip) em um caminho específico em um nó do Linux.

## Sintaxe

```
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## Propriedades

|  Propriedade |  Descrição | 
|---|---|
| SourcePath| Especifica o caminho de origem do arquivo morto. Deve ser um arquivo .tar, .zip ou .tar.gz. | 
| DestinationPath| Especifica o local onde você deseja garantir que o conteúdo do arquivo seja extraído.| 
| Soma de verificação| Define o tipo que deve ser usado ao determinar se o arquivo de origem foi atualizado. Os valores são: "ctime", "mtime" ou "md5". O valor padrão é "md5".| 
| Force| Determinadas operações de arquivo (como substituição de um arquivo ou exclusão de um diretório que não esteja vazio) resultarão em erro. O uso da propriedade **Force** substitui esses erros. O valor padrão é **$false**.| 
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a **ID** do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.| 
| Ensure| Determina se é necessário verificar se o conteúdo do arquivo existe em **Destination**. Defina essa propriedade como "Present" para garantir que o conteúdo exista. Defina-a como "Absent" para garantir que não exista. O valor padrão é "Present".| 

## Exemplo

O exemplo a seguir mostra como usar o recurso **nxArchive** para garantir que o conteúdo de um arquivo morto chamado `website.tar` exista e seja extraído em um destino específico.

```
Import-DSCResource -Module nx 

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
} 
```



<!--HONumber=May16_HO3-->


