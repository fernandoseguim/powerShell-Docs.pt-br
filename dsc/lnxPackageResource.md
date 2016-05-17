---
title:   Recurso nxPackage de DSC para Linux
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Recurso nxPackage de DSC para Linux

O recurso **nxPackage** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para gerenciar pacotes em um nó do Linux.

## Sintaxe

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]
    
}
```

## Propriedades

|  Propriedade |  Descrição | 
|---|---|
| Nome| O nome do pacote para o qual você deseja garantir um estado específico.| 
| Ensure| Determina se é necessário verificar se o pacote existe. Defina essa propriedade como "Present" para garantir que o pacote exista. Defina-a como "Absent" para garantir que o pacote não exista. O valor padrão é "Present".|  
| PackageManager| Há suporte para os valores "yum", "apt" e "zypper". Especifica o gerenciador de pacotes que deve ser usado ao instalar pacotes. Se **FilePath** for especificado, o caminho fornecido será usado para instalar o pacote. Caso contrário, será usado um Gerenciador de Pacotes para instalar o pacote por meio de um repositório pré-configurado. Se não for fornecido o **PackageManager** ou o **FilePath**, o gerenciador de pacotes padrão para o sistema será usado.| 
| FilePath| O caminho do arquivo em que o pacote reside| 
| PackageGroup| Se for **$true**, o **Nome** deverá ser o nome de um grupo de pacotes para usar com um **PackageManager**. **PackageGroup** não é válido ao fornecer um **FilePath**.| 
| Argumentos| Uma cadeia de caracteres de argumentos que será passada para o pacote exatamente conforme fornecido.| 
| ReturnCode| O código de retorno esperado. Se o código de retorno real não corresponder ao valor esperado fornecido aqui, a configuração gerará um erro.| 
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a **ID** do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.| 

## Exemplo

O exemplo a seguir assegura que o pacote denominado "httpd" seja instalado em um computador Linux usando o gerenciador de pacotes “Yum”.

```
Import-DSCResource -Module nx 

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```



<!--HONumber=May16_HO3-->


