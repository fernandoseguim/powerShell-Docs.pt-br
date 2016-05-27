---
title:   Escrever ajuda para configurações de DSC
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Escrever ajuda para configurações de DSC

>Aplica-se a: Windows Windows PowerShell 5.0

Você pode usar a ajuda baseada em comentários em configurações de DSC. Os usuários podem acessar a ajuda chamando a função de configuração com `-?` ou usando o cmdlet [Get-Help](https://technet.microsoft.com/en-us/library/hh849696.aspx). Para saber mais sobre a ajuda baseada em comentários do PowerShell, veja [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/hh847834.aspx).

O exemplo a seguir mostra um script que contém duas configurações e ajuda baseada em comentários para cada configuração:

```powershell
<#
.SYNOPSIS
A brief description of the function or script. This keyword can be used only once for each configuration.


.DESCRIPTION
A detailed description of the function or script. This keyword can be used only once for each configuration.


.PARAMETER computername
The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword. 
Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description. 
The description can include paragraph breaks.

The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters 
(and their descriptions) appear in help topic. To change the order, change the syntax.

.PARAMETER filePath
Provide a PARAMETER section for each parameter that your script or function accepts.

.EXAMPLE
A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example. If you have multiple examples,
there is no need to number them. PowerShell will number the examples in help text.

.EXAMPLE
This example will be labeled "EXAMPLE 2" when help is displayed to the user.
#>

configuration HelpSample1
{
    param([string]$computername,[string]$filePath)
    File f
    {
        Contents="Hello World"
        DestinationPath = "c:\Destination.txt"
    }
}
```

## Exibindo a ajuda de configuração

Para exibir a ajuda para uma configuração, use o cmdlet **Get-Help** com o nome da função, ou digite o nome da função seguido por `-?`. Veja a seguir a saída da função anterior quando passada para **Get-Help**:

```powershell
PS C:\> Get-Help HelpSample1

NAME
    HelpSample1
    
SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.
    
    
SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-computername] 
    <String>] [[-filePath] <String>] [<CommonParameters>]
    
    
DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.
    

RELATED LINKS

REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

## Consulte Também
* [Configurações DSC](configurations.md)



<!--HONumber=May16_HO3-->


