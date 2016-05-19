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


Falha de sysprep após instalação do WMF 5.0
----------------------------------------

Há duas soluções para este problema, dependendo da versão do Windows Server que você está executando.

**Resolução:**
- Para sistemas executando o **Windows Server 2008 R2**
  1.    Abrir o PowerShell como um administrador
  2.    Executar o seguinte comando
   ```powershell
    Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
   ```
  3.    Execute o comando e ignore o erro, uma vez que são esperados.
   ```powershell
    Publish-SilData
   ```
  4.    Exclua os arquivos no diretório \Windows\System32\Logfiles\SIL\
  ```powershell
  Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
  ```
  5.    Instale todas as atualizações importantes do Windows disponíveis e comece a operação de Sysprep normalmente.
  
- Para sistemas executando o **Windows Server 2012**
  1.    Depois de instalar WMF 5.0 no servidor para Sysprep, faça logon como administrador.
  2.    Copie Generize.xml do diretório \Windows\System32\Sysprep\ActionFiles\ a para uma localização fora do diretório do Windows, C:\ por exemplo.
  3.    Abra sua cópia Generalize.xml com bloco de notas.
  4.    Localize e remova o texto que segue, uma instância de cada precisa de ser excluída (estarão perto do fim do documento).
    ```
    <sysprepOrder order="0x3200"></sysprepOrder>
    
    <sysprepOrder order="0x3300"></sysprepOrder>
    ```
  5.    Salve a cópia editada de Generalize.xml e feche o arquivo.
  6.    Abra um prompt de comando como administrador
  7.    Execute o seguinte comando para se apropriar do arquivo Generalize.xml na pasta system32:
    ```
      Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml 
    ```
  8.    Execute o seguinte comando para definir a permissão adequada no arquivo:
    ```
      Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F 
    ```
      * Responda Sim ao pedido de confirmação. 
      * Observe que `<AdministratorUserName>` deve ser substituído pelo nome de usuário administrador do computador. Por exemplo, "Administrador".
      
  9.    Copie o arquivo editado e salvo no diretório de Sysprep usando o seguinte comando:
      ```
      xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml 
      ```
      * Responda Sim para substituir (observe que se não houver nenhum pedido para substituir, verifique com atenção o caminho inserido).
      * Assume que sua cópia editada de Generalize.xml foi copiado no C:\.
  10.   Generalize.xml é atualizado com a solução alternativa. Executar o Sysprep com a opção Generalizar habilitada.



<!--HONumber=May16_HO1-->


