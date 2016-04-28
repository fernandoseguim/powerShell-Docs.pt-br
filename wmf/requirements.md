# Requisitos do Sistema

- Instale as atualizações mais recentes do Windows antes de instalar o WMF 5.0 RTM.
- É possível instalar o WMF 5.0 RTM apenas nos seguintes sistemas operacionais:

    | Sistema operacional       | Edições         | Pré-requisitos        |  Links do pacote |
    |------------------------|--------------|------------------|----------------------| --------------|
    | Windows Server 2012 R2 |  |  | <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717507)">Win8.1AndW2K12R2-KB3134758-x64.msu</ctype="x-NOTFOUND"> |
    | Windows Server 2012    |  |  | <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717506)">W2K12-KB3134759-x64.msu</ctype="x-NOTFOUND"> |
    | Windows Server 2008 R2 SP1 | Todas, exceto IA64 | O <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://www.microsoft.com/en-us/download/details.aspx?id=40855)">WMF 4.0</ctype="x-NOTFOUND"> e o <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)">.NET Framework 4.5 ou posterior</ctype="x-NOTFOUND"> são instalados | <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717504)">Win7AndW2K8R2-KB3134760-x64.msu</ctype="x-NOTFOUND">|
    | Windows 8.1 | Pro, Enterprise | | <ctype="x-NOTFOUND" mdpre="**" mdpost="**">x64:</ctype="x-NOTFOUND">  <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717507)">Win8.1AndW2K12R2-KB3134758-x64.msu</ctype="x-NOTFOUND"> </br> <ctype="x-NOTFOUND" mdpre="**" mdpost="**">x86:</ctype="x-NOTFOUND">  <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkID=717963)">Win8.1-KB3134758-x86.msu</ctype="x-NOTFOUND">|
    | Windows 7 SP1 | Todas | O <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://www.microsoft.com/en-us/download/details.aspx?id=40855)">WMF 4.0</ctype="x-NOTFOUND"> e o <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)">.NET Framework 4.5 ou posterior</ctype="x-NOTFOUND"> são instalados | <ctype="x-NOTFOUND" mdpre="**" mdpost="**">x64:</ctype="x-NOTFOUND"> <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717504)">Win7AndW2K8R2-KB3134760-x64.msu</ctype="x-NOTFOUND">  </br> <ctype="x-NOTFOUND" mdpre="**" mdpost="**">x86:</ctype="x-NOTFOUND">  <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkID=717962)">Win7-KB3134760-x86.msu</ctype="x-NOTFOUND">|

# Instruções de instalação

### Para instalar o WMF 5.0 do Windows Explorer (ou Explorador de Arquivos):

1. Navegue até a pasta na qual você baixou o arquivo MSU.

2. Clique duas vezes no MSU para executá-lo.

### Para instalar o WMF 5.0 do Prompt de Comando:

1. Depois de baixar o pacote correto para a arquitetura de seu computador, abra uma janela do Prompt de Comando com direitos de usuário elevados (Executar como Administrador). Nas opções de instalação Server Core do Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1, por padrão, o Prompt de Comando é aberto com direitos de usuário elevados.

2. Altere os diretórios para a pasta na qual você baixou ou copiou o pacote de instalação do WMF 5.0.

3. Execute um dos seguintes comandos:
    - Nos computadores que executam o Windows Server 2012 R2 ou Windows 8.1 x64, execute <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Win8.1AndW2K12R2-KB3134758-x64.msu /quiet</ctype="x-NOTFOUND">.
    - Nos computadores que executam o Windows Server 2012, execute <ctype="x-NOTFOUND" mdpre="**" mdpost="**">W2K12-KB3134759-x64.msu /quiet</ctype="x-NOTFOUND">.
    - Nos computadores que executam o Windows Server 2008 R2 SP1 ou Windows 7 SP1 x64, execute <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Win7AndW2K8R2-KB3134760-x64.msu /quiet</ctype="x-NOTFOUND">.
    - Nos computadores que executam o Windows 8.1 x86, execute <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Win8.1-KB3134758-x86.msu /quiet</ctype="x-NOTFOUND">.
    - Nos computadores que executam o Windows 7 SP1 x86, execute <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Win7-KB3134760-x86.msu /quiet</ctype="x-NOTFOUND">.

### Notas de instalação adicionais para o Windows Server 2008 R2 SP1 e Windows 7 SP1:

Certifique-se de que os seguintes pré-requisitos foram atendidos:
- O service pack mais recente está instalado.
- O <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://www.microsoft.com/en-us/download/details.aspx?id=40855)">WMF 4.0</ctype="x-NOTFOUND"> está instalado.
- O <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)">.NET Framework 4.5 ou posterior</ctype="x-NOTFOUND"> está instalado.

**Dependência do WMF 4.0**

Os sistemas Windows Server 2008 R2 SP1 e Windows 7 SP1 têm PowerShell 2.0, WinRM e WMI internos. Os pacotes WMF 3.0 e WMF 4.0, que atualizam esses componentes internos, foram lançados após o lançamento do Windows Server 2008 R2 SP1 e do Windows 7 SP1. A Instalação/Desinstalação dos pacotes do WMF 3.0 e WMF 4.0 revelou alguns problemas no caminho de atualização a seguir:

- Interno --> WMF 4.0
- Interno --> WMF 3.0 --> WMF4.0. 

Corrigimos todos esses problemas em pacotes do WMF 4.0. Portanto, há um pré-requisito de WMF 4.0 para instalação WMF 5.0 no Windows Server 2008 R2 SP1 e Windows 7 SP1. Abaixo estão os problemas específicos que poderão ocorrer se você não instalar o WMF 4.0 antes de atualizar para o WMF 5.0:

- O Log de eventos encaminhado não está disponível e o log de EventCollector não é exibido no Visualizador de Eventos após a desinstalação do WMF 3.0 ou WMF 5.0 (sem o pré-requisito WMF 4.0 instalado) no Windows 7 SP1 e no Windows Server 2008 R2 SP1 (<ctype="x-NOTFOUND" mdpre="[" mdpost="](https://support.microsoft.com/en-us/kb/2809215)">KB2809215</ctype="x-NOTFOUND">).
- A personalização para a variável de ambiente <ctype="x-NOTFOUND" mdpre="*" mdpost="*">PSModulePath</ctype="x-NOTFOUND"> é redefinida para o valor padrão quando você atualiza diretamente do PowerShell 2.0 interno para WMF 5.0 (<ctype="x-NOTFOUND" mdpre="[" mdpost="](https://support.microsoft.com/en-us/kb/2872035)">KB2872035</ctype="x-NOTFOUND">) ou do WMF 3.0 para o WMF 5.0. (<ctype="x-NOTFOUND" mdpre="[" mdpost="](https://support.microsoft.com/en-us/kb/2872047)">KB2872047</ctype="x-NOTFOUND">) no Windows 7 SP1 e no Windows Server 2008 R2 SP1.

**Dependência do WinRM**

O DSC (Configuração de Estado Desejado) do Windows PowerShell depende do WinRM. O WinRM não é habilitado por padrão no Windows Server 2008 R2 SP1 e Windows 7 SP1. Para habilitar o WinRM, em uma sessão com privilégios elevados do Windows PowerShell, execute <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Set-WSManQuickConfig</ctype="x-NOTFOUND">.

# Instruções de desinstalação

### Usando o Prompt de Comando

1.  Abra o <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Prompt de Comando.</ctype="x-NOTFOUND">

2.  Execute o <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://support.microsoft.com/en-us/kb/934307)">Inicializador Autônomo do Windows Update</ctype="x-NOTFOUND">, conforme mostrado abaixo:

No Windows Server 2012 R2 e Windows 8.1:
```powershell
wusa /uninstall /kb:3134758
```
No Windows Server 2012:
```powershell
wusa /uninstall /kb:3134759
```
No Windows Server 2008 R2 SP1 e Windows 7 SP1:
```powershell
wusa /uninstall /kb:3134760
```

### Usando o Painel de Controle

1.  Abra o <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Painel de Controle.</ctype="x-NOTFOUND">

2.  Abra <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Programas</ctype="x-NOTFOUND"> e, em seguida, <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Desinstalar um programa.</ctype="x-NOTFOUND">

3.  Clique em <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Exibir atualizações instaladas.</ctype="x-NOTFOUND">

4.  Selecione <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Windows Management Framework 5.0</ctype="x-NOTFOUND"> na lista de atualizações instaladas. Isso corresponde a <ctype="x-NOTFOUND" mdpre="*" mdpost="*">KB3134758</ctype="x-NOTFOUND">, <ctype="x-NOTFOUND" mdpre="*" mdpost="*">KB3134759</ctype="x-NOTFOUND"> ou <ctype="x-NOTFOUND" mdpre="*" mdpost="*">KB3134760</ctype="x-NOTFOUND">. Clique em <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Desinstalar.</ctype="x-NOTFOUND">


<!--HONumber=Mar16_HO4-->


