---
title: Instalar e configurar o WMF 5.1
ms.date: 2017-01-18
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
contributor: keithb
manager: carmonm
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 55a2e03385b90c7631d1b0373bf85602aa7d769b
ms.sourcegitcommit: 267688f61dcc76fd685c1c34a6c7bfd9be582046
translationtype: HT
---
# <a name="install-and-configure-wmf-51"></a>Instalar e configurar o WMF 5.1 #


## <a name="download-and-install-the-wmf-51-package"></a>Baixar e instalar o pacote do WMF 5.1

Baixe o pacote do WMF 5.1 para o sistema operacional e a arquitetura em que você deseja instalá-lo:

| Sistema operacional         | Pré-requisitos       | Links de pacote             |
|------------------------|---------------------|---------------------------|
| Windows Server 2012 R2 | | [Win8.1AndW2K12R2-KB3191564-x64.msu](https://go.microsoft.com/fwlink/?linkid=839516)|
| Windows Server 2012     | | [W2K12-KB3191565-x64.msu](https://go.microsoft.com/fwlink/?linkid=839513)|
| Windows Server 2008 R2 | [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642) | [Win7AndW2K8R2-KB3191566-x64.ZIP](https://go.microsoft.com/fwlink/?linkid=839523) | 
| Windows 8.1            |  | **x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu](https://go.microsoft.com/fwlink/?linkid=839516) </br> **x86:** [Win8.1-KB3191564-x86.msu](https://go.microsoft.com/fwlink/?linkid=839521) |
| Windows 7 SP1          | [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642) | **x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP](https://go.microsoft.com/fwlink/?linkid=839523) </br> **x86:** [Win7-KB3191566-x86.ZIP](https://go.microsoft.com/fwlink/?linkid=839522)



## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>Instale o WMF 5.1 para Windows Server 2008 R2 e Windows 7

> **Observação:** as instruções de instalação do Windows Server 2008 R2 e Windows 7 foram alteradas e diferem das instruções de outros pacotes. As instruções de instalação do Windows Server 2012 R2, Windows Server 2012 e Windows 8.1 estão abaixo.

**Instalar o WMF 5.1 no Windows Server 2008 R2 e Windows 7**

1. Navegue até a pasta na qual você baixou o arquivo ZIP. 

2. Clique com botão direito no arquivo ZIP e selecione "Extrair todos…". O Zip contém 2 arquivos: um MSU e o arquivo de script Install-WMF5.1.PS1. Depois que você descompactar o arquivo ZIP, é possível copiar os conteúdos para qualquer computador que execute o Windows 7 ou Windows Server 2008 R2.  

3. Depois de extrair os conteúdos do arquivo ZIP, abra o PowerShell como administrador e navegue até a pasta onde está o  
conteúdo do arquivo ZIP. 

4. Execute o script Install-Wmf5.1.ps1 nessa pasta e siga as instruções. Esse script verificará os pré-requisitos no computador local e instalará o WMF 5.1 se os pré-requisitos forem atendidos. Os pré-requisitos estão listados abaixo. 

O Install-WMF5.1.ps1 usa os seguintes parâmetros para facilitar a automação e instalação no Windows Server 2008 R2 e Windows 7:

- AcceptEula: quando este parâmetro é incluído, o EULA é aceito automaticamente e não será exibido.
- AllowRestart: este parâmetro só pode ser usado se o AcceptEula for especificado. Se esse parâmetro for incluído e for necessário reiniciar após a instalação do WMF 5.1, o reinício ocorrerá sem solicitação imediatamente após a conclusão da instalação. 

**Pré-requisitos do WMF 5.1 para Windows Server 2008 R2 SP1 e Windows 7 SP1**

A instalação do WMF 5.1 no Windows Server 2008 R2 SP1 ou no Windows 7 SP1 exige o seguinte:
- O service pack mais recente deve ser instalado.
- O WMF 3.0 **não deve** ser instalado. Instalar o WMF 5.1 no lugar do WMF 3.0 resultará na perda de PSModulePath, o que pode causar a falha de outros aplicativos. Antes de instalar o WMF 5.1, você desinstalar o WMF 3.0 ou salvar o PSModulePath e, em seguida, restaurá-lo manualmente após a conclusão da instalação do WMF 5.1. 
- O WMF 5.1 requer o [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642) Você pode instalar o Microsoft .NET Framework 4.5.2, seguindo as instruções no local de download.

**Dependência do WinRM** 

O DSC (Configuração de Estado Desejado) do Windows PowerShell depende do WinRM. O WinRM não é habilitado por padrão no Windows Server 2008 R2 e Windows 7. Execute `Set-WSManQuickConfig`, em uma sessão de privilégios elevados do Windows PowerShell, para habilitar o WinRM.


## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>Instalar o WMF 5.1 para Windows Server 2012 R2, Windows Server 2012 e Windows 8.1
**Instale do Windows Explorer (ou Explorador de Arquivos no Windows Server 2012 R2 ou Windows 8.1)**

1. Navegue até a pasta na qual você baixou o arquivo MSU.

2. Clique duas vezes no MSU para executá-lo.

**Instalar por meio do Prompt de Comando**

1. Depois de baixar o pacote correto para a arquitetura de seu computador, abra uma janela do Prompt de Comando com direitos de usuário elevados (Executar como Administrador). Nas opções de instalação Server Core do Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1, por padrão, o Prompt de Comando é aberto com direitos de usuário elevados.

2. Altere os diretórios para a pasta para a qual você baixou ou copiou o pacote de instalação do WMF 5.1.

3. Execute um dos seguintes comandos:
    - Em computadores que executem o Windows Server 2012 R2 ou o Windows 8.1 x64, execute `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.
    - Em computadores que executem o Windows Server 2012, execute `W2K12-KB3191565-x64.msu /quiet`.
    - Em computadores que executem o Windows 8.1 x86, execute `Win8.1-KB3191564-x86.msu /quiet`.
    
