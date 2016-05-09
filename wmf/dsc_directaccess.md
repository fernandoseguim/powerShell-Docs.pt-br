# Acesso direto aos métodos de recurso DSC


O cmdlet `Invoke-DscResource` foi adicionado para permitir o acesso direto aos recursos DSC e seus métodos (Get, Set ou Test). Ele pode ser usado por terceiros que desejam tirar proveito dos recursos DSC. Geralmente, esse cmdlet é usado em combinação com `refreshMode = ‘Disabled’`, mas poderá ser usado independentemente de qual refreshMode for definido. Veja abaixo alguns exemplos de como usar o novo cmdlet:

## Certificar-se de que um arquivo está presente

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## Testar se um arquivo está presente

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## Obter o conteúdo do arquivo

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```


<!--HONumber=Apr16_HO4-->


