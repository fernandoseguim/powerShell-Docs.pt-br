# O cmdlet Test-DscConfiguration dá suporte a configurações de referência

O cmdlet Test-DscConfiguration foi atualizado para permitir o teste do estado de configuração desejado de um ou mais nós de destino, especificando um documento de configuração de referência para comparação.

Os novos conjuntos de parâmetros a seguir usam configurações DSC no caminho especificado para apenas testar e nunca aplicar cada configuração no(s) nó(s) de destino especificado(s). Assim como acontece com Start-DscConfiguration e outros cmdlets do DSC, o nome de cada MOF é usado para determinar em qual nó de destino a configuração deverá ser testada. 

```PowerShell
Test-DscConfiguration   [-Path] <string> 
                        [[-ComputerName] <string[]>] 
                        [-Credential <pscredential>] 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]

Test-DscConfiguration   [-Path] <string> 
                        -CimSession <CimSession[]> 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]
```

Os novos conjuntos de parâmetros a seguir usam uma única configuração DSC para apenas testar e nunca aplicar a configuração no(s) nó(s) de destino especificado(s). 

```PowerShell
Test-DscConfiguration   -ReferenceConfiguration <string> 
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>] 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]

Test-DscConfiguration   -ReferenceConfiguration <string> 
                        -CimSession <CimSession[]> 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]
```


<!--HONumber=Jun16_HO4-->


