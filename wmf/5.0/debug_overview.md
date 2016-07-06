# Melhorias na depuração de script do PowerShell

Várias melhorias foram feitas no PowerShell 5.0 a fim de aprimorar a experiência de depuração:

## Interromper Tudo

O console do PowerShell e o ISE do Windows PowerShell agora permitem que você interrompa o depurador para executar scripts. Isso funciona em sessões locais e remotas.

No console, pressione **Ctrl+Break**.

No ISE, pressione **Ctrl+B** ou use o comando de menu **Depurar -> Interromper Tudo**.

## Depuração remota e edição de arquivos remota no ISE do Windows PowerShell

O ISE do Windows PowerShell agora permite abrir e editar arquivos em uma sessão remota com a execução do comando PSEdit.
Por exemplo, é possível abrir um arquivo para edição desde a linha de comando em uma sessão remota da seguinte maneira:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Além disso, agora é possível editar e salvar alterações em um arquivo remoto aberto automaticamente no ISE do Windows PowerShell ao atingir um ponto de interrupção.
Agora, você pode depurar um arquivo de script que está em execução em um computador remoto, editar o arquivo para corrigir um erro e executar novamente o script modificado.

## Depuração de script avançada

Há novos e avançados recursos de depuração que permitem anexar a qualquer processo de computador local que tenha carregado o Windows PowerShell e depurar runspaces arbitrários no processo.

### Depuração de runspaces

Foram adicionados novos cmdlets que permitem listar os runspaces atuais em um processo e anexar o console do Windows PowerShell ou o depurador do ISE a esse runspace para a depuração de script:

-   Get-Runspace
-   Debug-Runspace
-   Enable-RunspaceDebug
-   Disable-RunspaceDebug
-   Get-RunspaceDebug

### Anexar a um processo que hospeda o PowerShell

Agora é possível anexar a qualquer processo de computador que tenha o Windows PowerShell carregado. É possível fazer isso entrando em uma sessão interativa com o processo, de forma semelhante a como você entra em uma sessão remota interativa executando o cmdlet Enter-PSSession:

-   Enter-PSHostProcess
-   Exit-PSHostProcess

<!--HONumber=Jun16_HO4-->


