# Limitações e problemas conhecidos

Os Atalhos do PowerShell são desfeitos quando usados pela primeira vez
------------------------------------------------------------

**Resolução:** execute uma das seguintes ações:

1.  Clique com o botão direito do mouse no atalho do PowerShell. Selecione “Windows PowerShell” para iniciar em um modo sem privilégios elevados.
2.  Clique com o botão direito do mouse no atalho do PowerShell. Clique com o botão direito do mouse em “Windows PowerShell” e selecione “Executar como Administrador” para iniciar em um modo com privilégios elevados.

Depois de executar uma das ações acima, os atalhos do PowerShell funcionarão. Essas ações precisarão ser executadas apenas uma vez.


Os Módulos PowerShell e os Recursos DSC relatam erros sobre ExecutionPolicy no Windows 7
-------------------------------------------------------------------------------------
No Windows 7, o uso de módulos PowerShell e recursos DSC pode fazer com que erros sobre ExecutionPolicy sejam relatados.

**Resolução:** defina ExecutionPolicy como RemoteSigned executando o seguinte comando em uma sessão do PowerShell com privilégios elevados (Executar como Administrador):

```powershell
Set-ExecutionPolicy RemoteSigned
```

Conectar-se a um ponto de extremidade remoto antigo do Exchange causa uma falha
------------------------------------------------------------

O ponto de extremidade antigo do Exchange redireciona para um novo ponto de extremidade. Há um bug na lógica de redirecionamento que resulta em uma falha.

**Resolução:** conecte-se diretamente ao novo ponto de extremidade.


O recurso de Log de Inventário de Software é interrompido incorretamente após a instalação do WMF 5.0 no Windows Server 2012 R2
-------------------------------------------------------------------------------------------------------------

Ao instalar o WMF 5.0 em um Windows Server 2012 R2 que já está executando o SIL, o recurso de Log de Inventário de Software será interrompido incorretamente após a instalação.

**Resolução:** execute o cmdlet Start-SilLogging uma vez após a instalação do WMF, pois o processo de instalação interromperá incorretamente o recurso de Log de Inventário de Software.

Get-ChildItem não funcionará se -LiteralPath e -Recurse forem usados juntos
--------------------------------------------------------------------------

Caso um nome de diretório contenha um caractere curinga inválido, Get-ChildItem não produzirá os resultados esperados quando
-LiteralPath e -Recurse forem usados juntos.

**Resolução:** a solução alternativa não ideal, mas atual, é implementar a recursão no script em vez de depender do cmdlet.
<!--HONumber=Mar16_HO2-->
