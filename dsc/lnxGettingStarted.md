---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Introdução à Configuração de Estado Desejado (DSC) para Linux
ms.openlocfilehash: 0534cede979eb2917adb608dba622539fe4bdc45
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="56b3d-103">Introdução à Configuração de Estado Desejado (DSC) para Linux</span><span class="sxs-lookup"><span data-stu-id="56b3d-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="56b3d-104">Este tópico explica como começar a usar a Configuração de Estado Desejado (DSC) do PowerShell para Linux.</span><span class="sxs-lookup"><span data-stu-id="56b3d-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="56b3d-105">Para obter informações gerais sobre o DSC, consulte [Introdução à Configuração de Estado Desejado do Windows PowerShell](overview.md).</span><span class="sxs-lookup"><span data-stu-id="56b3d-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="56b3d-106">Versões do sistema operacional Linux com suporte</span><span class="sxs-lookup"><span data-stu-id="56b3d-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="56b3d-107">Há suporte para as seguintes versões de sistema operacional do Linux para DSC para Linux.</span><span class="sxs-lookup"><span data-stu-id="56b3d-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>
- <span data-ttu-id="56b3d-108">CentOS 5, 6 e 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="56b3d-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="56b3d-109">Debian GNU/Linux 6, 7 e 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="56b3d-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="56b3d-110">Oracle Linux 5, 6 e 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="56b3d-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="56b3d-111">Red Hat Enterprise Linux Server 5, 6 e 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="56b3d-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="56b3d-112">SUSE Linux Enterprise Server 10, 11 e 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="56b3d-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="56b3d-113">Ubuntu Server 12.04 LTS, 14.04 LTS e 16.04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="56b3d-113">Ubuntu Server 12.04 LTS, 14.04 LTS and 16.04 LTS (x86/x64)</span></span>

<span data-ttu-id="56b3d-114">A tabela a seguir descreve as dependências de pacote necessárias para a DSC para Linux.</span><span class="sxs-lookup"><span data-stu-id="56b3d-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="56b3d-115">Pacote necessário</span><span class="sxs-lookup"><span data-stu-id="56b3d-115">Required package</span></span> |  <span data-ttu-id="56b3d-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="56b3d-116">Description</span></span> |  <span data-ttu-id="56b3d-117">Versão mínima</span><span class="sxs-lookup"><span data-stu-id="56b3d-117">Minimum version</span></span> |
|---|---|---|
| <span data-ttu-id="56b3d-118">glibc</span><span class="sxs-lookup"><span data-stu-id="56b3d-118">glibc</span></span>| <span data-ttu-id="56b3d-119">Biblioteca do GNU</span><span class="sxs-lookup"><span data-stu-id="56b3d-119">GNU Library</span></span>| <span data-ttu-id="56b3d-120">2…4 – 31.30</span><span class="sxs-lookup"><span data-stu-id="56b3d-120">2…4 – 31.30</span></span>|
| <span data-ttu-id="56b3d-121">python</span><span class="sxs-lookup"><span data-stu-id="56b3d-121">python</span></span>| <span data-ttu-id="56b3d-122">Python</span><span class="sxs-lookup"><span data-stu-id="56b3d-122">Python</span></span>| <span data-ttu-id="56b3d-123">2.4 – 3.4</span><span class="sxs-lookup"><span data-stu-id="56b3d-123">2.4 – 3.4</span></span>|
| <span data-ttu-id="56b3d-124">omiserver</span><span class="sxs-lookup"><span data-stu-id="56b3d-124">omiserver</span></span>| <span data-ttu-id="56b3d-125">Infraestrutura de gerenciamento aberta</span><span class="sxs-lookup"><span data-stu-id="56b3d-125">Open Management Infrastructure</span></span>| <span data-ttu-id="56b3d-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="56b3d-126">1.0.8.1</span></span>|
| <span data-ttu-id="56b3d-127">openssl</span><span class="sxs-lookup"><span data-stu-id="56b3d-127">openssl</span></span>| <span data-ttu-id="56b3d-128">Bibliotecas do OpenSSL</span><span class="sxs-lookup"><span data-stu-id="56b3d-128">OpenSSL Libraries</span></span>| <span data-ttu-id="56b3d-129">0.9.8 ou 1.0</span><span class="sxs-lookup"><span data-stu-id="56b3d-129">0.9.8 or 1.0</span></span>|
| <span data-ttu-id="56b3d-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="56b3d-130">ctypes</span></span>| <span data-ttu-id="56b3d-131">Biblioteca do Python CTypes</span><span class="sxs-lookup"><span data-stu-id="56b3d-131">Python CTypes library</span></span>| <span data-ttu-id="56b3d-132">Deve coincidir com a versão do Python</span><span class="sxs-lookup"><span data-stu-id="56b3d-132">Must match Python version</span></span>|
| <span data-ttu-id="56b3d-133">libcurl</span><span class="sxs-lookup"><span data-stu-id="56b3d-133">libcurl</span></span>| <span data-ttu-id="56b3d-134">biblioteca de cliente http do cURL</span><span class="sxs-lookup"><span data-stu-id="56b3d-134">cURL http client library</span></span>| <span data-ttu-id="56b3d-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="56b3d-135">7.15.1</span></span>|

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="56b3d-136">Instalando a DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="56b3d-136">Installing DSC for Linux</span></span>

<span data-ttu-id="56b3d-137">É necessário instalar a [Infraestrutura de Gerenciamento Aberta (OMI)](https://github.com/Microsoft/omi) antes de instalar a DSC para Linux.</span><span class="sxs-lookup"><span data-stu-id="56b3d-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="56b3d-138">Instalando a OMI</span><span class="sxs-lookup"><span data-stu-id="56b3d-138">Installing OMI</span></span>

<span data-ttu-id="56b3d-139">A Desired State Configuration para Linux requer o servidor CIM da OMI (Infraestrutura de Gerenciamento Aberta), versão 1.0.8.1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="56b3d-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="56b3d-140">A OMI pode ser baixada do The Open Group: [Infraestrutura de Gerenciamento Aberta (OMI)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="56b3d-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="56b3d-141">Para instalar a OMI, instale o pacote adequado para seu sistema Linux (.rpm ou .deb), a versão do OpenSSL (ssl_098 ou ssl_100) e a arquitetura (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="56b3d-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="56b3d-142">Pacotes de RPM são adequados para CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server e Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="56b3d-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="56b3d-143">Pacotes de DEB são adequados para Debian GNU/Linux e Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="56b3d-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="56b3d-144">Os pacotes ssl_098 são adequados para computadores com OpenSSL 0.9.8 instalado, enquanto os pacotes ssl_100 são adequados para computadores com OpenSSL 1.0 instalado.</span><span class="sxs-lookup"><span data-stu-id="56b3d-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> <span data-ttu-id="56b3d-145">**Observação**: para determinar a versão instalada do OpenSSL, execute o comando `openssl version`.</span><span class="sxs-lookup"><span data-stu-id="56b3d-145">**Note**: To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="56b3d-146">Execute o seguinte comando para instalar a OMI em um sistema CentOS 7 x64.</span><span class="sxs-lookup"><span data-stu-id="56b3d-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="56b3d-147">Instalando a DSC</span><span class="sxs-lookup"><span data-stu-id="56b3d-147">Installing DSC</span></span>

<span data-ttu-id="56b3d-148">DSC para Linux está disponível para download [aqui](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="56b3d-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest).</span></span>

<span data-ttu-id="56b3d-149">Para instalar a DSC, instale o pacote adequado para seu sistema Linux (.rpm ou .deb), a versão do OpenSSL (ssl_098 ou ssl_100) e a arquitetura (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="56b3d-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="56b3d-150">Pacotes de RPM são adequados para CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server e Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="56b3d-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="56b3d-151">Pacotes de DEB são adequados para Debian GNU/Linux e Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="56b3d-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="56b3d-152">Os pacotes ssl_098 são adequados para computadores com OpenSSL 0.9.8 instalado, enquanto os pacotes ssl_100 são adequados para computadores com OpenSSL 1.0 instalado.</span><span class="sxs-lookup"><span data-stu-id="56b3d-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> <span data-ttu-id="56b3d-153">**Observação**: para determinar a versão instalada do OpenSSL, execute a versão do comando openssl.</span><span class="sxs-lookup"><span data-stu-id="56b3d-153">**Note**: To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="56b3d-154">Execute o seguinte comando para instalar a DSC em um sistema CentOS 7 x64.</span><span class="sxs-lookup"><span data-stu-id="56b3d-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`


## <a name="using-dsc-for-linux"></a><span data-ttu-id="56b3d-155">Usando a DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="56b3d-155">Using DSC for Linux</span></span>

<span data-ttu-id="56b3d-156">As seções a seguir explicam como criar e executar configurações DSC em computadores Linux.</span><span class="sxs-lookup"><span data-stu-id="56b3d-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="56b3d-157">Criando um documento MOF de configuração</span><span class="sxs-lookup"><span data-stu-id="56b3d-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="56b3d-158">A palavra-chave Configuration do Windows PowerShell é usada para criar uma configuração para computadores Linux, assim como para computadores Windows.</span><span class="sxs-lookup"><span data-stu-id="56b3d-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="56b3d-159">As etapas a seguir descrevem a criação de um documento de configuração para um computador Linux usando o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56b3d-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="56b3d-160">Importe o módulo nx.</span><span class="sxs-lookup"><span data-stu-id="56b3d-160">Import the nx module.</span></span> <span data-ttu-id="56b3d-161">O módulo nx do Windows PowerShell contém o esquema para recursos internos para DSC para Linux e deve ser instalado no seu computador local e importado na configuração.</span><span class="sxs-lookup"><span data-stu-id="56b3d-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

    <span data-ttu-id="56b3d-162">-Para instalar o módulo nx, copie o diretório do módulo nx para `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` ou `$PSHOME\Modules`.</span><span class="sxs-lookup"><span data-stu-id="56b3d-162">-To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="56b3d-163">O módulo nx está incluído no pacote de instalação da DSC para Linux (MSI).</span><span class="sxs-lookup"><span data-stu-id="56b3d-163">The nx module is included in the DSC for Linux installation package (MSI).</span></span> <span data-ttu-id="56b3d-164">Para importar o módulo nx na sua configuração, use o comando __Import-DSCResource__:</span><span class="sxs-lookup"><span data-stu-id="56b3d-164">To import the nx module in your configuration, use the __Import-DSCResource__ command:</span></span>

```powershell
Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

}
```
2. <span data-ttu-id="56b3d-165">Definir uma configuração e gerar o documento de configuração:</span><span class="sxs-lookup"><span data-stu-id="56b3d-165">Define a configuration and generate the configuration document:</span></span>

```powershell
Configuration ExampleConfiguration{

    Import-DscResource -Module nx

    Node  "linuxhost.contoso.com"{
    nxFile ExampleFile {

        DestinationPath = "/tmp/example"
        Contents = "hello world `n"
        Ensure = "Present"
        Type = "File"
    }

    }
}
ExampleConfiguration -OutputPath:"C:\temp"
```

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="56b3d-166">Envie a configuração por push para o computador Linux</span><span class="sxs-lookup"><span data-stu-id="56b3d-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="56b3d-167">Documentos de configuração (arquivos MOF) podem ser enviados por push para o computador Linux usando o cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx).</span><span class="sxs-lookup"><span data-stu-id="56b3d-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span> <span data-ttu-id="56b3d-168">Para usar esse cmdlet, juntamente com os cmdlets [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) ou [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx), remotamente em um computador Linux, você deve utilizar uma CIMSession.</span><span class="sxs-lookup"><span data-stu-id="56b3d-168">In order to use this cmdlet, along with the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx), or [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="56b3d-169">O cmdlet [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) é usado para criar uma CIMSession para o computador Linux.</span><span class="sxs-lookup"><span data-stu-id="56b3d-169">The [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="56b3d-170">O código a seguir mostra como criar uma CIMSession para DSC para Linux.</span><span class="sxs-lookup"><span data-stu-id="56b3d-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90
```

> <span data-ttu-id="56b3d-171">**Observação**:</span><span class="sxs-lookup"><span data-stu-id="56b3d-171">**Note**:</span></span>
* <span data-ttu-id="56b3d-172">No modo de “push”, a credencial do usuário precisa ser o usuário raiz no computador Linux.</span><span class="sxs-lookup"><span data-stu-id="56b3d-172">For “Push” mode, the user credential must be the root user on the Linux computer.</span></span>
* <span data-ttu-id="56b3d-173">Há suporte apenas para conexões SSL/TLS para DSC para Linux; a New-CimSession precisa ser usada com o parâmetro –UseSSL definido como $true.</span><span class="sxs-lookup"><span data-stu-id="56b3d-173">Only SSL/TLS connections are supported for DSC for Linux, the New-CimSession must be used with the –UseSSL parameter set to $true.</span></span>
* <span data-ttu-id="56b3d-174">O certificado SSL usado pela OMI (para DSC) é especificado no arquivo: `/opt/omi/etc/omiserver.conf` com as propriedades: pemfile e keyfile.</span><span class="sxs-lookup"><span data-stu-id="56b3d-174">The SSL certificate used by OMI (for DSC) is specified in the file: `/opt/omi/etc/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
<span data-ttu-id="56b3d-175">Se o computador Windows em que você está executando o cmdlet [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) não confiar nesse certificado, será possível optar por ignorar a validação do certificado com as Opções de CIMSession: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span><span class="sxs-lookup"><span data-stu-id="56b3d-175">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span></span>

<span data-ttu-id="56b3d-176">Execute o seguinte comando para enviar a configuração DSC por push para o nó do Linux.</span><span class="sxs-lookup"><span data-stu-id="56b3d-176">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="56b3d-177">Distribuir a configuração com um servidor de pull</span><span class="sxs-lookup"><span data-stu-id="56b3d-177">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="56b3d-178">As configurações podem ser distribuídas para um computador Linux com um servidor de pull, assim como para computadores Windows.</span><span class="sxs-lookup"><span data-stu-id="56b3d-178">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="56b3d-179">Para obter orientações sobre como usar um servidor de pull, consulte [Servidores de Pull de Configuração de Estado Desejado do Windows PowerShell](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="56b3d-179">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="56b3d-180">Para obter informações adicionais e se informar sobre as limitações relacionadas ao uso de computadores Linux com um servidor pull, consulte as Notas de versão para a configuração de estado desejado para Linux.</span><span class="sxs-lookup"><span data-stu-id="56b3d-180">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="56b3d-181">Trabalhando com configurações localmente</span><span class="sxs-lookup"><span data-stu-id="56b3d-181">Working with configurations locally</span></span>

<span data-ttu-id="56b3d-182">A DSC para Linux inclui scripts para trabalhar com a configuração no computador Linux local.</span><span class="sxs-lookup"><span data-stu-id="56b3d-182">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="56b3d-183">Esses scripts estão localizados em `/opt/microsoft/dsc/Scripts` e incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="56b3d-183">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>
* <span data-ttu-id="56b3d-184">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="56b3d-184">GetDscConfiguration.py</span></span>

 <span data-ttu-id="56b3d-185">Gera a configuração atual aplicada ao computador.</span><span class="sxs-lookup"><span data-stu-id="56b3d-185">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="56b3d-186">Semelhante ao cmdlet Get-DscConfiguration do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56b3d-186">Similar to the Windows PowerShell cmdlet Get-DscConfiguration cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

* <span data-ttu-id="56b3d-187">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="56b3d-187">GetDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="56b3d-188">Gera a metaconfiguração atual aplicada ao computador.</span><span class="sxs-lookup"><span data-stu-id="56b3d-188">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="56b3d-189">Semelhante ao cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx).</span><span class="sxs-lookup"><span data-stu-id="56b3d-189">Similar to the cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

* <span data-ttu-id="56b3d-190">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="56b3d-190">InstallModule.py</span></span>

 <span data-ttu-id="56b3d-191">Instala um módulo personalizado de recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="56b3d-191">Installs a custom DSC resource module.</span></span> <span data-ttu-id="56b3d-192">Requer o caminho para um arquivo. zip que contém a biblioteca de objeto compartilhado do módulo e os arquivos MOF do esquema.</span><span class="sxs-lookup"><span data-stu-id="56b3d-192">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

* <span data-ttu-id="56b3d-193">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="56b3d-193">RemoveModule.py</span></span>

 <span data-ttu-id="56b3d-194">Remove um módulo personalizado de recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="56b3d-194">Removes a custom DSC resource module.</span></span> <span data-ttu-id="56b3d-195">Requer o nome do módulo que será removido.</span><span class="sxs-lookup"><span data-stu-id="56b3d-195">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

* <span data-ttu-id="56b3d-196">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="56b3d-196">StartDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="56b3d-197">Aplica um arquivo MOF de configuração ao computador.</span><span class="sxs-lookup"><span data-stu-id="56b3d-197">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="56b3d-198">Semelhante ao cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx).</span><span class="sxs-lookup"><span data-stu-id="56b3d-198">Similar to the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span> <span data-ttu-id="56b3d-199">Exige o caminho até o MOF de configuração para aplicar.</span><span class="sxs-lookup"><span data-stu-id="56b3d-199">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

* <span data-ttu-id="56b3d-200">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="56b3d-200">SetDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="56b3d-201">Aplica um arquivo MOF de metaconfiguração ao computador.</span><span class="sxs-lookup"><span data-stu-id="56b3d-201">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="56b3d-202">Semelhante ao cmdlet [Set-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx).</span><span class="sxs-lookup"><span data-stu-id="56b3d-202">Similar to the [Set-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) cmdlet.</span></span> <span data-ttu-id="56b3d-203">Exige o caminho até o MOF de metaconfiguração para aplicar.</span><span class="sxs-lookup"><span data-stu-id="56b3d-203">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="56b3d-204">Arquivos de Log da Configuração de Estado Desejado do PowerShell para Linux</span><span class="sxs-lookup"><span data-stu-id="56b3d-204">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="56b3d-205">Os seguintes arquivos de log são gerados para mensagens da DSC para Linux.</span><span class="sxs-lookup"><span data-stu-id="56b3d-205">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="56b3d-206">Arquivo de log</span><span class="sxs-lookup"><span data-stu-id="56b3d-206">Log file</span></span>|<span data-ttu-id="56b3d-207">Directory</span><span class="sxs-lookup"><span data-stu-id="56b3d-207">Directory</span></span>|<span data-ttu-id="56b3d-208">Descrição</span><span class="sxs-lookup"><span data-stu-id="56b3d-208">Description</span></span>|
|---|---|---|
|<span data-ttu-id="56b3d-209">omiserver.log</span><span class="sxs-lookup"><span data-stu-id="56b3d-209">omiserver.log</span></span>|<span data-ttu-id="56b3d-210">/var/opt/omi/log</span><span class="sxs-lookup"><span data-stu-id="56b3d-210">/var/opt/omi/log</span></span>|<span data-ttu-id="56b3d-211">Mensagens relacionadas à operação do servidor CIM da OMI.</span><span class="sxs-lookup"><span data-stu-id="56b3d-211">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="56b3d-212">dsc.log</span><span class="sxs-lookup"><span data-stu-id="56b3d-212">dsc.log</span></span>|<span data-ttu-id="56b3d-213">/var/opt/omi/log</span><span class="sxs-lookup"><span data-stu-id="56b3d-213">/var/opt/omi/log</span></span>|<span data-ttu-id="56b3d-214">Mensagens relacionadas à operação das operações de recurso do Gerenciador de Configurações Local (LCM) e da DSC.</span><span class="sxs-lookup"><span data-stu-id="56b3d-214">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|