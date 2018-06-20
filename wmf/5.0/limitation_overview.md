---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 4b006d2ac812abf1f281b6b4e382c2760f92a95c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186823"
---
# <a name="known-issues-and-limitations"></a><span data-ttu-id="961cd-102">Limitações e problemas conhecidos</span><span class="sxs-lookup"><span data-stu-id="961cd-102">Known Issues and Limitations</span></span>

<a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="961cd-103">Os Atalhos do PowerShell são desfeitos quando usados pela primeira vez</span><span class="sxs-lookup"><span data-stu-id="961cd-103">PowerShell Shortcuts are broken when used for the first time</span></span>
------------------------------------------------------------

<span data-ttu-id="961cd-104">**Resolução:** execute uma das seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="961cd-104">**Resolution:** Perform one of the following actions:</span></span>

1.  <span data-ttu-id="961cd-105">Clique com o botão direito do mouse no atalho do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="961cd-105">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="961cd-106">Selecione “Windows PowerShell” para iniciar em um modo sem privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="961cd-106">Select “Windows PowerShell” to launch in a non-elevated mode.</span></span>
2.  <span data-ttu-id="961cd-107">Clique com o botão direito do mouse no atalho do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="961cd-107">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="961cd-108">Clique com o botão direito do mouse em “Windows PowerShell” e selecione “Executar como Administrador” para iniciar em um modo com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="961cd-108">Right click on “Windows PowerShell” and select “Run As Administrator” to launch in an elevated mode.</span></span>

<span data-ttu-id="961cd-109">Depois de executar uma das ações acima, os atalhos do PowerShell funcionarão.</span><span class="sxs-lookup"><span data-stu-id="961cd-109">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="961cd-110">Essas ações precisarão ser executadas apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="961cd-110">These actions need to be performed only once.</span></span>


<a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="961cd-111">Os Módulos PowerShell e os Recursos DSC relatam erros sobre ExecutionPolicy no Windows 7</span><span class="sxs-lookup"><span data-stu-id="961cd-111">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>
-------------------------------------------------------------------------------------
<span data-ttu-id="961cd-112">No Windows 7, o uso de módulos PowerShell e recursos DSC pode fazer com que erros sobre ExecutionPolicy sejam relatados.</span><span class="sxs-lookup"><span data-stu-id="961cd-112">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="961cd-113">**Resolução:** defina ExecutionPolicy como RemoteSigned executando o seguinte comando em uma sessão do PowerShell com privilégios elevados (Executar como Administrador):</span><span class="sxs-lookup"><span data-stu-id="961cd-113">**Resolution:** Set the ExecutionPolicy to RemoteSigned by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="961cd-114">Conectar-se a um ponto de extremidade remoto antigo do Exchange causa uma falha</span><span class="sxs-lookup"><span data-stu-id="961cd-114">Connecting to an old remote Exchange endpoint causes a crash</span></span>
------------------------------------------------------------

<span data-ttu-id="961cd-115">O ponto de extremidade antigo do Exchange redireciona para um novo ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="961cd-115">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="961cd-116">Há um bug na lógica de redirecionamento que resulta em uma falha.</span><span class="sxs-lookup"><span data-stu-id="961cd-116">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="961cd-117">**Resolução:** conecte-se diretamente ao novo ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="961cd-117">**Resolution:** Connect directly to the new endpoint.</span></span>


<a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="961cd-118">O recurso de Log de Inventário de Software é interrompido incorretamente após a instalação do WMF 5.0 no Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="961cd-118">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>
-------------------------------------------------------------------------------------------------------------

<span data-ttu-id="961cd-119">Ao instalar o WMF 5.0 em um Windows Server 2012 R2 que já está executando o SIL, o recurso de Log de Inventário de Software será interrompido incorretamente após a instalação.</span><span class="sxs-lookup"><span data-stu-id="961cd-119">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="961cd-120">**Resolução:** execute o cmdlet Start-SilLogging uma vez após a instalação do WMF, pois o processo de instalação interromperá incorretamente o recurso de Log de Inventário de Software.</span><span class="sxs-lookup"><span data-stu-id="961cd-120">**Resolution:** Run the Start-SilLogging cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

<a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="961cd-121">Get-ChildItem não funcionará se -LiteralPath e -Recurse forem usados juntos</span><span class="sxs-lookup"><span data-stu-id="961cd-121">Get-ChildItem does not work if -LiteralPath and -Recurse are used together</span></span>
--------------------------------------------------------------------------

<span data-ttu-id="961cd-122">Caso um nome de diretório contenha um caractere curinga inválido, Get-ChildItem não produzirá os resultados esperados quando -LiteralPath e -Recurse são usados juntos.</span><span class="sxs-lookup"><span data-stu-id="961cd-122">If a directory name contains an invalid wildcard character, then Get-ChildItem will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="961cd-123">**Resolução:** a solução alternativa não ideal, mas atual, é implementar a recursão no script em vez de depender do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="961cd-123">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>


<a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="961cd-124">Falha de sysprep após instalação do WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="961cd-124">Sysprep fails after WMF 5.0 installation</span></span>
----------------------------------------

<span data-ttu-id="961cd-125">Há duas soluções para este problema, dependendo da versão do Windows Server que você está executando.</span><span class="sxs-lookup"><span data-stu-id="961cd-125">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="961cd-126">**Resolução:**</span><span class="sxs-lookup"><span data-stu-id="961cd-126">**Resolution:**</span></span>
- <span data-ttu-id="961cd-127">Para sistemas executando o **Windows Server 2008 R2**</span><span class="sxs-lookup"><span data-stu-id="961cd-127">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="961cd-128">Abrir o PowerShell como um administrador</span><span class="sxs-lookup"><span data-stu-id="961cd-128">Open Powershell as an administrator</span></span>
  2. <span data-ttu-id="961cd-129">Executar o seguinte comando</span><span class="sxs-lookup"><span data-stu-id="961cd-129">Run the following command</span></span>

  ```powershell
    Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
  ```
  3. <span data-ttu-id="961cd-130">Execute o comando e ignore o erro, uma vez que são esperados.</span><span class="sxs-lookup"><span data-stu-id="961cd-130">Run the command and ignore the error, as they are expected.</span></span>

  ```powershell
    Publish-SilData
   ```
  4. <span data-ttu-id="961cd-131">Exclua os arquivos no diretório \Windows\System32\Logfiles\SIL\\</span><span class="sxs-lookup"><span data-stu-id="961cd-131">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

  ```powershell
    Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
  ```
  5. <span data-ttu-id="961cd-132">Instale todas as atualizações importantes do Windows disponíveis e comece a operação de Sysprep normalmente.</span><span class="sxs-lookup"><span data-stu-id="961cd-132">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="961cd-133">Para sistemas executando o **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="961cd-133">For systems running **Windows Server 2012**</span></span>
  1.    <span data-ttu-id="961cd-134">Depois de instalar WMF 5.0 no servidor para Sysprep, faça logon como administrador.</span><span class="sxs-lookup"><span data-stu-id="961cd-134">After installing WMF 5.0 on the server to be Sysprep’d, login as administrator.</span></span>
  2.    <span data-ttu-id="961cd-135">Copie Generize.xml do diretório \Windows\System32\Sysprep\ActionFiles\ a para uma localização fora do diretório do Windows, C:\ por exemplo.</span><span class="sxs-lookup"><span data-stu-id="961cd-135">Copy Generize.xml from directory \Windows\System32\Sysprep\ActionFiles\ to a location outside of the Windows directory, C:\ for example.</span></span>
  3.    <span data-ttu-id="961cd-136">Abra sua cópia Generalize.xml com bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="961cd-136">Open your Generalize.xml copy with notepad.</span></span>
  4.    <span data-ttu-id="961cd-137">Localize e remova o texto que segue, uma instância de cada precisa de ser excluída (estarão perto do fim do documento).</span><span class="sxs-lookup"><span data-stu-id="961cd-137">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

    ```
    <sysprepOrder order="0x3200"></sysprepOrder>
    <sysprepOrder order="0x3300"></sysprepOrder>
    ```

  5.    <span data-ttu-id="961cd-138">Salve a cópia editada de Generalize.xml e feche o arquivo.</span><span class="sxs-lookup"><span data-stu-id="961cd-138">Save the edited copy of Generalize.xml and close the file.</span></span>
  6.    <span data-ttu-id="961cd-139">Abra um prompt de comando como administrador</span><span class="sxs-lookup"><span data-stu-id="961cd-139">Open a command prompt as administrator</span></span>
  7.    <span data-ttu-id="961cd-140">Execute o seguinte comando para se apropriar do arquivo Generalize.xml na pasta system32:</span><span class="sxs-lookup"><span data-stu-id="961cd-140">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

    ```
    Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```

  8.    <span data-ttu-id="961cd-141">Execute o seguinte comando para definir a permissão adequada no arquivo:</span><span class="sxs-lookup"><span data-stu-id="961cd-141">Run the following command to set appropriate permission on the file:</span></span>

    ```
    Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
    ```
      * <span data-ttu-id="961cd-142">Responda Sim ao pedido de confirmação.</span><span class="sxs-lookup"><span data-stu-id="961cd-142">Answer Yes at the prompt for confirmation.</span></span>
      * <span data-ttu-id="961cd-143">Observe que `<AdministratorUserName>` deve ser substituído pelo nome de usuário administrador do computador.</span><span class="sxs-lookup"><span data-stu-id="961cd-143">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="961cd-144">Por exemplo, "Administrador".</span><span class="sxs-lookup"><span data-stu-id="961cd-144">For example, "Administrator".</span></span>

  9.    <span data-ttu-id="961cd-145">Copie o arquivo editado e salvo no diretório de Sysprep usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="961cd-145">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

    ```
    xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```
      * <span data-ttu-id="961cd-146">Responda Sim para substituir (observe que se não houver nenhum pedido para substituir, verifique com atenção o caminho inserido).</span><span class="sxs-lookup"><span data-stu-id="961cd-146">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
      * <span data-ttu-id="961cd-147">Assume que sua cópia editada de Generalize.xml foi copiado no C:\.</span><span class="sxs-lookup"><span data-stu-id="961cd-147">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10.   <span data-ttu-id="961cd-148">Generalize.xml é atualizado com a solução alternativa.</span><span class="sxs-lookup"><span data-stu-id="961cd-148">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="961cd-149">Executar o Sysprep com a opção Generalizar habilitada.</span><span class="sxs-lookup"><span data-stu-id="961cd-149">Please run Sysprep with the generalize option enabled.</span></span>
