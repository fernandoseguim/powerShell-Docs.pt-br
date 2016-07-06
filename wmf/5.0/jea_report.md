# Relatando no JEA
Para relatar o estado da configuração JEA, é possível usar:
1.  **Get-PSSessionConfiguration** para retornar uma lista de todos os pontos de extremidade registrados em determinado computador.
2.  **Get-PSSessionCapability** para relatar as funcionalidades que determinado usuário tem em relação a um ponto de extremidade específico.

Aqui está um exemplo de **Get-PSSessionCapability**:
```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source           
-----------     ----                                               -------    ------           
Alias           clear -> Clear-Host                                                            
Alias           cls -> Clear-Host                                                              
Alias           exsn -> Exit-PSSession                                                         
Alias           gcm -> Get-Command                                                             
Alias           measure -> Measure-Object                                                      
Alias           select -> Select-Object                                                        
Function        Clear-Host                                                                     
Function        Exit-PSSession                                                                 
Function        Get-Command                                                                    
Function        Get-FormatData                                                                 
Function        Get-Help                                                                       
Function        Get-UserInfo                                                                   
Function        Measure-Object                                                                 
Function        Out-Default                                                                    
Function        Select-Object                                                                  
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...


```

Para relatar as _ações_ executadas pelos usuários durante uma sessão JEA, é possível:
1. Habilitar as transcrições “over the shoulder” para o ponto de extremidade JEA e consultar o diretório de transcrições para obter um log completo das ações de cada usuário
2. Ativar o registro de módulo PowerShell e inspecionar os logs de eventos do PowerShell.<!--HONumber=Mar16_HO2-->
