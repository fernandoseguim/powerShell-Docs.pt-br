# Instruções de instalação

Baixe o pacote correto para sua arquitetura e seu sistema operacional:

| Sistema operacional       | Arquitetura | Nome do pacote              | 
|------------------------|--------------|---------------------------| 
| Windows Server 2012 R2 | x64      | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) | 
| Windows Server 2012    | x64      | [W2K12-KB3134759-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) | 
| Windows Server 2008 R2 | x64      | [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 8.1            | x64          | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows 8.1            | x86          | [Win8.1-KB3134758-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963) |
| Windows 7 SP1          | x64          | [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 7 SP1          | x86          | [Win7-KB3134760-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962) |


**Para instalar o WMF 5.0 do Windows Explorer (ou Explorador de Arquivos no Windows Server 2012 R2 e Windows 8.1):**

1. Navegue até a pasta na qual você baixou o arquivo MSU.

2. Clique duas vezes no MSU para executá-lo.

**Para instalar o WMF 5.0 do Prompt de Comando:** 

1. Depois de baixar o pacote correto para a arquitetura de seu computador, abra uma janela do Prompt de Comando com direitos de usuário elevados (Executar como Administrador). Nas opções de instalação Server Core do Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1, por padrão, o Prompt de Comando é aberto com direitos de usuário elevados.

2. Altere os diretórios para a pasta na qual você baixou ou copiou o pacote de instalação do WMF 5.0.

3. Execute um dos seguintes comandos:
    - Nos computadores que executam o Windows Server 2012 R2 ou Windows 8.1 x64, execute **Win8.1AndW2K12R2-KB3134758-x64.msu /quiet**.
    - Nos computadores que executam o Windows Server 2012, execute **W2K12-KB3134759-x64.msu /quiet**.
    - Nos computadores que executam o Windows Server 2008 R2 SP1 ou Windows 7 SP1 x64, execute **Win7AndW2K8R2-KB3134760-x64.msu /quiet**.
    - Nos computadores que executam o Windows 8.1 x86, execute **Win8.1-KB3134758-x86.msu /quiet**.
    - Nos computadores que executam o Windows 7 SP1 x86, execute **Win7-KB3134760-x86.msu /quiet**.

**Notas de instalação adicionais para o Windows Server 2008 SP1 e Windows 7 SP1:**

Certifique-se de que os seguintes pré-requisitos foram atendidos:
- O service pack mais recente está instalado.
- O [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) está instalado

*Dependência do WinRM:*
O DSC (Configuração de Estado Desejado) do Windows PowerShell depende do WinRM. O WinRM não é habilitado por padrão no Windows Server 2008 R2 e Windows 7. Para habilitar o WinRM, em uma sessão com privilégios elevados do Windows PowerShell, execute **Set-WSManQuickConfig**.


<!--HONumber=Mar16_HO2-->
