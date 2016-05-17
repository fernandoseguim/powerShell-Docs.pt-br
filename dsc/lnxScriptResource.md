---
title:   Recurso nxScript de DSC para Linux
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Recurso nxScript de DSC para Linux

O recurso **nxScript** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para executar scripts do Linux em um nó do Linux.

## Sintaxe

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    { Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## Propriedades

|  Propriedade |  Descrição | 
|---|---|
| GetScript| Fornece um script que é executado quando você invoca o cmdlet [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx). O script precisa começar com um shebang, como #!/bin/bash.| 
| SetScript| Fornece um script. Quando você invoca o cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), o **TestScript** é executado primeiro. Se o bloco **TestScript** gerar um código de saída diferente de 0, o bloco **SetScript** será executado. Se o **TestScript** gerar um código de saída igual a 0, o **SetScript** não será executado. O script precisa começar com um shebang, como `#!/bin/bash`.| 
| TestScript| Fornece um script. Quando você invoca o cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), esse script é executado. Se gerar um código de saída diferente de 0, o SetScript será executado. Se gerar um código de saída igual a 0, o **SetScript** não será executado. O **TestScript** também é executado quando você invoca o cmdlet [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx). No entanto, nesse caso, o **SetScript** não será executado, não importa qual código de saída é gerado pelo **TestScript**. O **TestScript** deverá gerar um código de saída igual a 0 se a configuração real corresponder à configuração atual de estado desejado e um código de saída diferente de 0 se não corresponder. (A configuração atual de estado desejado é a última configuração aplicada no nó que está usando a DSC). O script precisa começar com um shebang, como 1#!/bin/bash.1| 
| User| O usuário com o qual o script será executado.| 
| Grupo| O grupo com o qual o script será executado.| 
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a **ID** do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.| 

## Exemplo

O exemplo a seguir demonstra o uso do recurso **nxScript** para executar um gerenciamento de configuração adicional.

```
Import-DSCResource -Module nx 

Node $node {
nxScript KeepDirEmpty{

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
} 
}
```



<!--HONumber=May16_HO3-->


