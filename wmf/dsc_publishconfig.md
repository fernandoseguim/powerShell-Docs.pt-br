# Entregar um documento de configuração sem aplicação

O cmdlet **Publish-DscConfiguration** faz uma cópia de um arquivo MOF de configuração e a cola em um nó de destino, mas não aplica a configuração. Essa configuração é aplicada durante a próxima passagem de consistência ou ao executar o cmdlet `Update-DscConfiguration`.

```powershell
Publish-DscConfiguration [-Path] <string> [[-ComputerName] <string[]>] [-Force] [-Credential <pscredential>] [-ThrottleLimit <int>] [-WhatIf] [-Confirm] [<CommonParameters>]

Publish-DscConfiguration [-Path] <string> -CimSession <CimSession[]> [-Force] [-ThrottleLimit <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<!--HONumber=Mar16_HO2-->
