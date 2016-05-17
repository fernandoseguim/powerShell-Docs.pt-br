---
title:   Recurso Script de DSC
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Recurso Script de DSC

 
> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso **Script** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para executar blocos de script do Windows PowerShell em nós de destino. O recurso `Script` tem as propriedades `GetScript`, `SetScript` e `TestScript`. Essas propriedades devem ser definidas em blocos de script que serão executado em cada nó de destino. 

O bloco de script `GetScript` deve retornar uma tabela de hash que representa o estado do nó atual. Ele não precisa retornar nada. O DSC não faz nada com a saída desse bloco de script.

O bloco de script `TestScript` deve determinar se o nó atual precisa ser modificado. Ele deverá retornar `$true` se o nó for atualizado. Ele deverá retornar `$false` se a configuração do nó estiver desatualizada e deverá ser atualizada pelo bloco de script `SetScript`. O bloco de script `TestScript` é chamado pelo DSC.

O bloco de script `SetScript` deve modificar o nó. Ele será chamado pelo DSC, se o bloco `TestScript` retornar `$false`.

Se você precisa usar variáveis do seu script de configuração nos blocos de script `GetScript`, `TestScript` ou `SetScript`, use o escopo `$using:` (consulte abaixo para obter um exemplo).


## Sintaxe

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## Propriedades

|  Propriedade  |  Descrição   | 
|---|---| 
| GetScript| Fornece um bloco de script do Windows PowerShell que é executado quando você invoca o cmdlet [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx). Esse bloco deve gerar uma tabela de hash.| 
| SetScript| Fornece um bloco de script do Windows PowerShell. Quando você invoca o cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), o bloco **TestScript** é executado primeiro. Se o bloco **TestScript** gerar **$false**, o bloco **SetScript** será executado. Se o bloco **TestScript** gerar **$true**, o bloco **SetScript** não será executado.| 
| TestScript| Fornece um bloco de script do Windows PowerShell. Quando você invoca o cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), esse bloco é executado. Se gerar **$false**, o bloco SetScript será executado. Se gerar **$true**, o bloco SetScript não será executado. O bloco **TestScript** também é executado quando você invoca o cmdlet [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx). No entanto, nesse caso, o bloco **SetScript** não será executado, independentemente do valor gerado pelo bloco TestScript. O bloco **TestScript** precisará gerar True se a configuração real corresponder à configuração atual de estado desejado e False se não corresponder. (A configuração atual de estado desejado é a última configuração aplicada no nó que está usando a DSC.)| 
| Credential| Indica as credenciais que devem ser usadas para executar esse script, caso sejam necessárias.| 
| DependsOn| Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.

## Exemplo 1
```powershell
Script ScriptExample
{
    SetScript = { 
        $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
        $sw.WriteLine("Some sample string")
        $sw.Close()
    }
    TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
    GetScript = { <# This must return a hash table #> }          
}
```

## Exemplo 2
```powershell
$version = Get-Content 'version.txt'
Script UpdateConfigurationVersion
{
    GetScript = { 
        $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
        return @{ 'Version' = $currentVersion }
    }          
    TestScript = { 
        $state = GetScript
        if( $state['Version'] -eq $using:version )
        {
            Write-Verbose -Message ('{0} -eq {1}' -f $state['Version'],$using:version)
            return $true
        }
        Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
        return $false
    }
    SetScript = { 
        $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
    }
}
```

Este recurso está gravando a versão da configuração em um arquivo de texto. Esta versão está disponível no computador cliente, mas não está em nenhum dos nós, por isso deve ser passada para cada um dos blocos de script do recurso `Script` com o escopo `using` do PowerShell. Quando gera o arquivo MOF do nó, o valor da variável `$version` é lido de um arquivo de texto no computador cliente. O DSC substitui as variáveis `$using:version` em cada bloco de script pelo valor da variável `$version`.



<!--HONumber=May16_HO3-->


