---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
contributor: keithb
title: Instalar e configurar o WMF 5.1
ms.openlocfilehash: 74c19d2eb04b77b1e2b1c8d8977f9b4db6e94e4f
ms.sourcegitcommit: 9910675e8758042b5949c99b381a926d2b4e8c21
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2017
---
# <a name="install-and-configure-wmf-51"></a>Como instalar e configurar o WMF 5.1 #


## <a name="download-and-install-the-wmf-51-package"></a>Como baixar e instalar o pacote do WMF 5.1

Baixe o pacote do WMF 5.1 para o sistema operacional e a arquitetura em que você deseja instalá-lo:

| Sistema operacional       | Pré-requisitos       | Links de pacote             |
|------------------------|---------------------|---------------------------|
| Windows Server 2012 R2 | | [Win8.1AndW2K12R2-KB3191564-x64.msu](https://go.microsoft.com/fwlink/?linkid=839516)|
| Windows Server 2012    | | [W2K12-KB3191565-x64.msu](https://go.microsoft.com/fwlink/?linkid=839513)|
| Windows Server 2008 R2 | [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642) | [Win7AndW2K8R2-KB3191566-x64.ZIP](https://go.microsoft.com/fwlink/?linkid=839523) | 
| Windows 8.1            |  | **x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu](https://go.microsoft.com/fwlink/?linkid=839516) </br> **x86:** [Win8.1-KB3191564-x86.msu](https://go.microsoft.com/fwlink/?linkid=839521) |
| Windows 7 SP1          | [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642) | **x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP](https://go.microsoft.com/fwlink/?linkid=839523) </br> **x86:** [Win7-KB3191566-x86.ZIP](https://go.microsoft.com/fwlink/?linkid=839522)



## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>Instale o WMF 5.1 para Windows Server 2008 R2 e Windows 7

> **Observação:** as instruções de instalação do Windows Server 2008 R2 e do Windows 7 foram alteradas e diferem das instruções dos outros pacotes. Veja a seguir as instruções de instalação do Windows Server 2012 R2, do Windows Server 2012 e do Windows 8.1.

**Instalação do WMF 5.1 em Windows Server 2008 R2 e Windows 7**

1. Navegue até a pasta em que você baixou o arquivo ZIP. 

2. Clique com botão direito no arquivo ZIP e selecione "Extrair tudo…". O Zip contém 2 arquivos: um MSU e o script Install-WMF5.1.PS1. Depois que você descompactar o arquivo ZIP, poderá copiar todo o conteúdo em qualquer computador que execute Windows 7 ou Windows Server 2008 R2.  

3. Depois de extrair o conteúdo do arquivo ZIP, abra o PowerShell como administrador e navegue até a pasta onde está o  
conteúdo do arquivo ZIP. 

4. Execute o script Install-Wmf5.1.ps1 nessa pasta e siga as instruções. Esse script verificará os pré-requisitos no computador local e, caso eles sejam atendidos, instalará o WMF 5.1. Os pré-requisitos estão listados a seguir. 

O Install-WMF5.1.ps1 usa os seguintes parâmetros para facilitar a automação e a instalação no Windows Server 2008 R2 e no Windows 7:

- AcceptEula: quando este parâmetro é incluído, o EULA é aceito automaticamente e, portanto, não é exibido.
- AllowRestart: este parâmetro só pode ser usado se o AcceptEula for especificado. Se esse parâmetro for incluído e for necessário reiniciar após a instalação do WMF 5.1, o reinício ocorrerá automaticamente após a conclusão da instalação. 

**Pré-requisitos do WMF 5.1 para Windows Server 2008 R2 SP1 e Windows 7 SP1**

Os pré-requisitos para instalação do WMF 5.1 no Windows Server 2008 R2 SP1 ou no Windows 7 SP1 são:
- O service pack mais recente deve estar instalado.
- O WMF 3.0 **não deve** estar instalado. Se você instalar o WMF 5.1 no lugar do WMF 3.0, ocorrerá a perda do PSModulePath, o que pode causar falhas em outros aplicativos. Antes de instalar o WMF 5.1, você deve desinstalar o WMF 3.0 ou salvar o PSModulePath e, depois, restaurá-lo manualmente após a conclusão da instalação do WMF 5.1. 
- O WMF 5.1 exige pelo menos [do .NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).
Você pode instalar o Microsoft .NET Framework 4.5.2, seguindo as instruções no local fazer o download.

**Dependência do WinRM** 

O DSC (Desired State Configuration) do Windows PowerShell depende do WinRM. O WinRM não é habilitado por padrão no Windows Server 2008 R2 nem no Windows 7. Execute o `Set-WSManQuickConfig`, em uma sessão com privilégios elevados do Windows PowerShell para habilitar o WinRM.


## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>Como instalar o WMF 5.1 em Windows Server 2012 R2, Windows Server 2012 e Windows 8.1
**Como instalar usando o Windows Explorer (ou Explorador de Arquivos no Windows Server 2012 R2 ou no Windows 8.1)**

1. Navegue até a pasta em que você baixou o arquivo MSU.

2. Clique duas vezes no MSU para executá-lo.

**Como instalar usando o Prompt de Comando**

1. Após baixar o pacote correto de acordo com a arquitetura do seu computador, abra uma janela do Prompt de Comando com direitos de usuário elevados (Executar como Administrador). Nas opções de instalação Server Core do Windows Server 2012 R2, do Windows Server 2012 ou do Windows Server 2008 R2 SP1 o Prompt de Comando é aberto por padrão com direitos de usuário elevados.

2. Altere os diretórios para a pasta em que você baixou ou copiou o pacote de instalação do WMF 5.1.

3. Execute um dos seguintes comandos:
    - Em computadores com Windows Server 2012 R2 ou Windows 8.1 x64, execute o `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.
    - Em computadores com Windows Server 2012, execute o `W2K12-KB3191565-x64.msu /quiet`.
    - Em computadores com Windows 8.1 x86, execute o `Win8.1-KB3191564-x86.msu /quiet`.
    
