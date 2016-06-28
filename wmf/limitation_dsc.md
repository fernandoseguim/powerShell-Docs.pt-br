# Limitações e problemas conhecidos do DSC (Configuração de Estado Desejado)

Alteração interruptiva: os certificados usados para criptografar/descriptografar senhas em configurações DSC podem não funcionar após a instalação do WMF 5.0 RTM
--------------------------------------------------------------------------------------------------------------------------------

Em versões da Preview do WMF 4.0 e 5.0, o DSC não permite que as senhas na configuração tenham um tamanho maior que 121 caracteres. O DSC forçava o uso de senhas curtas, mesmo que fosse desejável usar senhas longas e fortes. Essa alteração interruptiva permite que as senhas tenham um tamanho arbitrário na configuração DSC.

**Resolução:** crie novamente o certificado com o uso da Chave de Codificação de Dados ou de Codificação de Chave, bem como o uso Avançado de Chave de Criptografia de Documento (1.3.6.1.4.1.311.80.1). O artigo do TechNet <https://technet.microsoft.com/pt-br/library/dn807171.aspx> tem mais informações.


Os cmdlets do DSC poderão falhar após a instalação do WMF 5.0 RTM
------------------------------------------------------------------------------------
Start-DscConfiguration e outros cmdlets do DSC poderão falhar após a instalação do WMF 5.0 RTM com o seguinte erro:
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

**Resolução:** exclua DSCEngineCache.mof executando o seguinte comando em uma sessão do PowerShell com privilégios elevados (Executar como Administrador):
    
```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```


Os cmdlets do DSC poderão não funcionar se o WMF 5.0 RTM estiver instalado, além da Preview de Produção do WMF 5.0
------------------------------------------------------
**Resolução:** execute o seguinte comando em uma sessão do PowerShell com privilégios elevados (executar como administrador):
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```


O LCM pode entrar em um estado instável durante o uso de Get-DscConfiguration em DebugMode
-------------------------------------------------------------------------------

Se o LCM estiver em DebugMode, pressionar CTRL+C para interromper o processamento de Get-DscConfiguration poderá fazer com que o LCM entre em um estado instável, a tal ponto em que a maioria dos cmdlets do DSC não funcionará.

**Resolução:** não pressione CTRL+C durante a depuração do cmdlet Get-DscConfiguration.


Stop-DscConfiguration poderá parar de responder em DebugMode
------------------------------------------------------------------------------------------------------------------------
Se o LCM estiver em DebugMode, Stop-DscConfiguration poderá parar de responder durante a tentativa de interromper uma operação iniciada por Get-DscConfiguration

**Resolução:** conclua a depuração da operação iniciada por Get-DscConfiguration, conforme descrito na seção “[DEPURAÇÃO DE SCRIPT DO RECURSO DSC](#dsc-resource-script-debugging)”.


Nenhuma mensagem de erro detalhada é mostrada em DebugMode
-----------------------------------------------------------------------------------
Se o LCM estiver em DebugMode, nenhuma mensagem de erro detalhada será exibida nos Recursos DSC.

**Resolução:** desabilite *DebugMode* para ver as mensagens detalhadas no recurso


As operações Invoke-DscResource não podem ser recuperadas pelo cmdlet Get-DscConfigurationStatus
--------------------------------------------------------------------------------------
Depois de usar o cmdlet Invoke-DscResource para invocar diretamente os métodos de qualquer recurso, os registros dessa operação não poderão ser recuperados por meio de Get-DscConfigurationStatus em um momento posterior.

**Resolução:** nenhuma.


Get-DscConfigurationStatus retorna operações de ciclo de pull como o tipo *Consistência*
---------------------------------------------------------------------------------
Quando um nó é definido como o modo de atualização por PULL, para cada operação de recepção realizada, o cmdlet Get-DscConfigurationStatus relata o tipo de operação como *Consistência* em vez de *Inicial*

**Resolução:** nenhuma.

O cmdlet Invoke-DscResource não retorna as mensagens na ordem em que foram produzidas
---------------------------------------------------------------------------------
O cmdlet Invoke-DscResource não retorna mensagens detalhadas, de aviso e de erro na ordem em que foram produzidas pelo LCM ou pelo recurso DSC.

**Resolução:** nenhuma.


Os Recursos DSC não podem ser depurados com facilidade quando usados com Invoke-DscResource
-----------------------------------------------------------------------
Quando o LCM estiver sendo executado no modo de depuração (veja [DEPURAÇÃO DE SCRIPT DO RECURSO DSC](#dsc-resource-script-debugging) para obter mais detalhes), o cmdlet Invoke-DscResource não fornecerá informações sobre o runspace para se conectar para realizar a depuração.
**Resolução:** descubra e anexe-se ao runspace usando os cmdlets **Get-PSHostProcessInfo**, **Enter-PSHostProcess**, **Get-Runspace** e **Debug-Runspace** para depurar o recurso DSC.

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell 3932 DefaultAppDomain
powershell_ise 2304 DefaultAppDomain
WmiPrvSE 3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name ComputerName Type State Availability
-- ---- ------------ ---- ----- ------------
2 Runspace2 localhost Local Opened InBreakpoint
5 RemoteHost localhost Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```


Vários documentos de Configuração Parcial para o mesmo nó não podem ter nomes de recursos idênticos
------------------------------------------------------------------------------------------

Para várias configurações parciais que são implantadas em um único nó, nomes idênticos de recursos causam um erro de tempo de execução.

**Resolução:** use nomes diferentes até para os mesmos recursos em configurações parciais diferentes.


–UseExisting de Start-DscConfiguration não funciona com –Credential
------------------------------------------------------------------

Ao usar Start-DscConfiguration com o parâmetro –UseExisting, o parâmetro –Credential é ignorado. O DSC usa a identidade de processo padrão para continuar a operação. Isso causa erros quando uma credencial diferente é necessária para continuar no nó remoto.

**Resolução:** use a sessão CIM para operações do DSC remotas:
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```


Endereços IPv6 como Nomes de Nó em configurações DSC
--------------------------------------------------
Nesta versão, não há suporte para endereços IPv6 como nomes de nó em scripts de configuração DSC.

**Resolução:** nenhuma.


Depuração de recursos DSC baseados em classe
--------------------------------------
Nesta versão, não há suporte para a depuração de recursos DSC baseados em classe.

**Resolução:** nenhuma.


As variáveis e funções definidas no escopo de $script no Recurso DSC Baseado em Classe não são preservadas em várias chamadas para um Recurso DSC 
-------------------------------------------------------------------------------------------------------------------------------------

Várias chamadas consecutivas para Start-DSCConfiguration falharão se a configuração estiver usando qualquer recurso baseado em classe que tenha variáveis ou funções definidas no escopo de $script.

**Resolução:** defina todas as variáveis e funções na própria classe do Recurso DSC. Nenhuma variável/função do escopo de $script.


Depuração do Recurso DSC quando um recurso estiver usando PSDscRunAsCredential
----------------------------------------------------------------------
Nesta versão, não há suporte para a depuração do Recurso DSC quando um recurso usa a propriedade *PSDscRunAsCredential* na configuração.

**Resolução:** nenhuma.


Não há suporte para PsDscRunAsCredential nos recursos de composição DSC
----------------------------------------------------------------

**Resolução:** use a propriedade Credential se estiver disponível. ServiceSet e WindowsFeatureSet de exemplo


*Get-DscResource -Syntax* não reflete PsDscRunAsCredential corretamente
-------------------------------------------------------------------------
Get-DscResource -Syntax não reflete PsDscRunAsCredential corretamente quando o recurso o marca como obrigatório ou não dá suporte a ele.

**Resolução:** nenhuma. No entanto, a criação de configuração no ISE reflete metadados corretos sobre a propriedade PsDscRunAsCredential ao usar o IntelliSense.


WindowsOptionalFeature não está disponível no Windows 7
-----------------------------------------------------

O recurso DSC de WindowsOptionalFeature não está disponível no Windows 7. Este recurso exige o módulo DISM e os cmdlets do DISM que estão disponíveis começando do Windows 8 e versões mais recentes do sistema operacional Windows.

Para obter recursos de DSC baseados em classes, Import-DscResource -ModuleVersion pode não funcionar como esperado   
------------------------------------------------------------------------------------------
Se o nó compilação tiver várias versões de um módulo de recurso de DSC baseado em classes, o `Import-DscResource -ModuleVersion` não selecionará a versão especificada e resulta no seguinte erro de compilação.

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**Resolução:** importe a versão necessária definindo o objeto *ModuleSpecification* para o `-ModuleName` com a chave `RequiredVersion` especificada da seguinte maneira:
``` PowerShell  
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}  
```  

Alguns recursos DSC, como recursos de Registro podem começar a levar muito tempo para processar a solicitação.
--------------------------------------------------------------------------------------------------------------------------------

**Resolution1:** criar uma tarefa agendada que limpa periodicamente a pasta a seguir.
``` PowerShell 
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis 
```

**Resolution2:** alterar a configuração DSC para limpar a pasta *CommandAnalysis* no final da configuração.
``` PowerShell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config 
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn="[Registry]SetRegisteredOwner"
        getscript="@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```


<!--HONumber=Jun16_HO4-->


