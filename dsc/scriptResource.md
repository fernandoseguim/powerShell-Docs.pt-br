# Recurso Script de DSC

 
> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso **Script** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para executar blocos de script do Windows PowerShell em nós de destino.

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

## Exemplo
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

<!--HONumber=Feb16_HO4-->
