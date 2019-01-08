---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Trabalhando com instalações de software
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: bb97ad37c4295351c0fc2e3c6e1209c8dd673f06
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400582"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="01d1f-103">Trabalhando com instalações de software</span><span class="sxs-lookup"><span data-stu-id="01d1f-103">Working with Software Installations</span></span>

<span data-ttu-id="01d1f-104">Aplicativos que são projetados para usar o Windows Installer podem ser acessados por meio da classe do WMI **Win32_Product**, mas nem todos os aplicativos usados atualmente usam o Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="01d1f-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span> <span data-ttu-id="01d1f-105">Como o Windows Installer fornece a mais ampla variedade de técnicas padrão para trabalhar com aplicativos instalados, abordaremos principalmente estes aplicativos.</span><span class="sxs-lookup"><span data-stu-id="01d1f-105">Because the Windows Installer provides the widest range of standard techniques for working with installable applications, we will focus primarily on those applications.</span></span> <span data-ttu-id="01d1f-106">Aplicativos que usam rotinas de instalação alternativas geralmente não serão gerenciados pelo Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="01d1f-106">Applications that use alternate setup routines will generally not be managed by the Windows Installer.</span></span> <span data-ttu-id="01d1f-107">Técnicas específicas para trabalhar com esses aplicativos dependem do instalador do software e as decisões tomadas pelo desenvolvedor do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="01d1f-107">Specific techniques for working with those applications will depend on the installer software and decisions made by the application developer.</span></span>

> [!NOTE]
> <span data-ttu-id="01d1f-108">Aplicativos que estão instalados copiando os arquivos do aplicativo para o computador geralmente não podem ser gerenciados usando técnicas discutidas aqui.</span><span class="sxs-lookup"><span data-stu-id="01d1f-108">Applications that are installed by copying the application files to the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="01d1f-109">Você pode gerenciar esses aplicativos como arquivos e pastas usando as técnicas discutidas na seção "Trabalhando com arquivos e pastas".</span><span class="sxs-lookup"><span data-stu-id="01d1f-109">You can manage these applications as files and folders by using the techniques discussed in the "Working With Files and Folders" section.</span></span>

### <a name="listing-windows-installer-applications"></a><span data-ttu-id="01d1f-110">Listando aplicativos do Windows Installer</span><span class="sxs-lookup"><span data-stu-id="01d1f-110">Listing Windows Installer Applications</span></span>

<span data-ttu-id="01d1f-111">Para listar os aplicativos instalados com o Windows Installer em um sistema local ou remoto, use a seguinte consulta simples do WMI:</span><span class="sxs-lookup"><span data-stu-id="01d1f-111">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

<span data-ttu-id="01d1f-112">Para exibir todas as propriedades do objeto Win32_Product na tela, use o parâmetro Properties de cmdlets de formatação, como o cmdlet Format-List, com um valor de \* (all).</span><span class="sxs-lookup"><span data-stu-id="01d1f-112">To display all of the properties of the Win32_Product object to the display, use the Properties parameter of the formatting cmdlets, such as the Format-List cmdlet, with a value of \* (all).</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Microsoft .NET Framework 2.0"} | Format-List -Property *

Name              : Microsoft .NET Framework 2.0
Version           : 2.0.50727
InstallState      : 5
Caption           : Microsoft .NET Framework 2.0
Description       : Microsoft .NET Framework 2.0
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
InstallDate       : 20060506
InstallDate2      : 20060506000000.000000-000
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\619ab2.msi
SKUNumber         :
Vendor            : Microsoft Corporation
```

<span data-ttu-id="01d1f-113">Ou você pode usar o parâmetro **Get-WmiObject Filter** para selecionar somente Microsoft .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="01d1f-113">Or, you could use the **Get-WmiObject Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="01d1f-114">Como o filtro usado neste comando é um filtro WMI, ele usa a sintaxe de linguagem de consulta WMI (WQL), não a sintaxe do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01d1f-114">Because the filter used in this command is a WMI filter, it uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="01d1f-115">Em vez disso:</span><span class="sxs-lookup"><span data-stu-id="01d1f-115">Instead,:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

<span data-ttu-id="01d1f-116">Observe que as consultas WQL frequentemente usam caracteres que têm um significado especial no Windows PowerShell, como espaços ou sinais de igual.</span><span class="sxs-lookup"><span data-stu-id="01d1f-116">Note that WQL queries frequently use characters, such as spaces or equal signs, that have a special meaning in Windows PowerShell.</span></span> <span data-ttu-id="01d1f-117">Por esse motivo, é recomendável sempre colocar o valor do parâmetro Filter entre aspas.</span><span class="sxs-lookup"><span data-stu-id="01d1f-117">For this reason, it is prudent to always enclose the value of the Filter parameter in quotation marks.</span></span> <span data-ttu-id="01d1f-118">Você também pode usar o caractere de escape do Windows PowerShell, um acento grave (\`), embora isso possa não melhorar a legibilidade.</span><span class="sxs-lookup"><span data-stu-id="01d1f-118">You can also use the Windows PowerShell escape character, a backtick (\`), although it may not improve readability.</span></span> <span data-ttu-id="01d1f-119">O comando a seguir é equivalente ao comando anterior e retorna os mesmos resultados, mas usa o acento grave como escape de caracteres especiais, em vez de delimitar toda a cadeia de caracteres do filtro.</span><span class="sxs-lookup"><span data-stu-id="01d1f-119">The following command is equivalent to the previous command and returns the same results, but uses the backtick to escape special characters, instead of quoting the entire filter string.</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

<span data-ttu-id="01d1f-120">Para listar somente as propriedades que lhe interessam, use o parâmetro Property dos cmdlets formatação para listar as propriedades desejadas.</span><span class="sxs-lookup"><span data-stu-id="01d1f-120">To list only the properties that interest you, use the Property parameter of the formatting cmdlets to list the desired properties.</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName . | Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
...
Name              : HighMAT Extension to Microsoft Windows XP CD Writing Wizard
InstallDate       : 20051022
InstallLocation   : C:\Program Files\HighMAT CD Writing Wizard\
PackageCache      : C:\WINDOWS\Installer\113b54.msi
Vendor            : Microsoft Corporation
Version           : 1.1.1905.1
IdentifyingNumber : {FCE65C4E-B0E8-4FBD-AD16-EDCBE6CD591F}
...
```

<span data-ttu-id="01d1f-121">Por fim, para localizar apenas os nomes dos aplicativos instalados, uma simples instrução **Format-Wide** simplifica o resultado:</span><span class="sxs-lookup"><span data-stu-id="01d1f-121">Finally, to find only the names of installed applications, a simple **Format-Wide** statement simplifies the output:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

<span data-ttu-id="01d1f-122">Embora haja várias maneiras de ver aplicativos que usaram o Windows Installer para a instalação, outros aplicativos não foram considerados.</span><span class="sxs-lookup"><span data-stu-id="01d1f-122">Although we now have several ways to look at applications that used the Windows Installer for installation, we have not considered other applications.</span></span> <span data-ttu-id="01d1f-123">Como a maioria dos aplicativos padrão registram seu desinstalador com o Windows, podemos trabalhar com aqueles localmente, localizando-os no registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="01d1f-123">Because most standard applications register their uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span>

### <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="01d1f-124">Listando todos os aplicativos desinstaláveis</span><span class="sxs-lookup"><span data-stu-id="01d1f-124">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="01d1f-125">Embora não haja nenhuma forma garantida para localizar todos os aplicativos em um sistema, é possível encontrar todos os programas com listagens exibidas na caixa de diálogo Adicionar ou Remover Programas.</span><span class="sxs-lookup"><span data-stu-id="01d1f-125">Although there is no guaranteed way to find every application on a system, it is possible to find all programs with listings displayed in the Add or Remove Programs dialog box.</span></span> <span data-ttu-id="01d1f-126">Adicionar ou Remover Programas encontra esses aplicativos na seguinte chave do registro:</span><span class="sxs-lookup"><span data-stu-id="01d1f-126">Add or Remove Programs finds these applications in the following registry key:</span></span>

<span data-ttu-id="01d1f-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span><span class="sxs-lookup"><span data-stu-id="01d1f-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span></span>

<span data-ttu-id="01d1f-128">Podemos também examinar essa chave para encontrar aplicativos.</span><span class="sxs-lookup"><span data-stu-id="01d1f-128">We can also examine this key to find applications.</span></span> <span data-ttu-id="01d1f-129">Para facilitar ainda mais a exibição da Chave de desinstalação, podemos mapear uma unidade do Windows PowerShell neste local do registro:</span><span class="sxs-lookup"><span data-stu-id="01d1f-129">To make it easier to view the Uninstall key, we can map a Windows PowerShell drive to this registry location:</span></span>

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> <span data-ttu-id="01d1f-130">A unidade **HKLM:** está mapeada para a raiz de **HKEY_LOCAL_MACHINE**, portanto, usamos essa unidade no caminho para a chave de Desinstalação.</span><span class="sxs-lookup"><span data-stu-id="01d1f-130">The **HKLM:** drive is mapped to the root of **HKEY_LOCAL_MACHINE**, so we used that drive in the path to the Uninstall key.</span></span> <span data-ttu-id="01d1f-131">Em vez de **HKLM:**, também é possível especificar o caminho do Registro usando **HKLM** ou **HKEY_LOCAL_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="01d1f-131">Instead of **HKLM:** we could have specified the registry path by using either **HKLM** or **HKEY_LOCAL_MACHINE**.</span></span> <span data-ttu-id="01d1f-132">A vantagem de usar uma unidade do registro existente é que podemos usar o preenchimento de guias para preencher os nomes de chaves, não sendo necessário digitá-los.</span><span class="sxs-lookup"><span data-stu-id="01d1f-132">The advantage of using an existing registry drive is that we can use tab-completion to fill in the keys names, so we do not need to type them.</span></span>

<span data-ttu-id="01d1f-133">Agora temos uma unidade chamada "Desinstalação" que pode ser usada como uma maneira rápida e conveniente de procurar as instalações de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="01d1f-133">We now have a drive named "Uninstall" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="01d1f-134">Podemos encontrar o número de aplicativos instalados contando o número de chaves de registro na Desinstalação: Unidade do Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="01d1f-134">We can find the number of installed applications by counting the number of registry keys in the Uninstall: Windows PowerShell drive:</span></span>

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="01d1f-135">Podemos pesquisar esta lista de aplicativos ainda mais detalhadamente usando uma variedade de técnicas, começando com **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="01d1f-135">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="01d1f-136">Para obter uma lista de aplicativos e salvá-los na variável **$UninstallableApplications**, use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="01d1f-136">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> <span data-ttu-id="01d1f-137">Estamos usando um longo nome de variável aqui para maior clareza.</span><span class="sxs-lookup"><span data-stu-id="01d1f-137">We are using a lengthy variable name here for clarity.</span></span> <span data-ttu-id="01d1f-138">Na utilização real, não há nenhum motivo para usar nomes longos.</span><span class="sxs-lookup"><span data-stu-id="01d1f-138">In actual use, there is no reason to use long names.</span></span> <span data-ttu-id="01d1f-139">Embora você possa usar o preenchimento de guias para nomes de variáveis, você também pode usar nomes com um ou dois caracteres para maior velocidade.</span><span class="sxs-lookup"><span data-stu-id="01d1f-139">Although you can use tab-completion for variable names, you can also use 1-2 character names for speed.</span></span> <span data-ttu-id="01d1f-140">Nomes mais longos e descritivos são mais úteis quando você estiver desenvolvendo código para reutilização.</span><span class="sxs-lookup"><span data-stu-id="01d1f-140">Longer, descriptive names are most useful when you are developing code for reuse.</span></span>

<span data-ttu-id="01d1f-141">Para exibir os valores das entradas do registro nas chaves do registro em Desinstalação, use o método GetValue das chaves do registro.</span><span class="sxs-lookup"><span data-stu-id="01d1f-141">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="01d1f-142">O valor do método é o nome da entrada do registro.</span><span class="sxs-lookup"><span data-stu-id="01d1f-142">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="01d1f-143">Por exemplo, para localizar os nomes para exibição dos aplicativos na Chave de desinstalação, use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="01d1f-143">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="01d1f-144">Não há nenhuma garantia de que esses valores sejam exclusivos.</span><span class="sxs-lookup"><span data-stu-id="01d1f-144">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="01d1f-145">No exemplo a seguir, dois itens instalados aparecem como "Windows Media Encoder 9 Series":</span><span class="sxs-lookup"><span data-stu-id="01d1f-145">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

### <a name="installing-applications"></a><span data-ttu-id="01d1f-146">Instalando aplicativos</span><span class="sxs-lookup"><span data-stu-id="01d1f-146">Installing Applications</span></span>

<span data-ttu-id="01d1f-147">Você pode usar a classe **Win32_Product** para instalar os pacotes do Windows Installer, local ou remotamente.</span><span class="sxs-lookup"><span data-stu-id="01d1f-147">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="01d1f-148">Para instalar um aplicativo no Windows Vista, Windows Server 2008 e versões posteriores do Windows, você deve iniciar o Windows PowerShell com a opção "Executar como administrador".</span><span class="sxs-lookup"><span data-stu-id="01d1f-148">On Windows Vista, Windows Server 2008, and later versions of Windows, to install an application, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="01d1f-149">Ao instalar remotamente, use um caminho de rede da Convenção de Nomenclatura Universal (UNC) para especificar o caminho para o pacote .msi, porque o subsistema WMI não entende caminhos do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01d1f-149">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand Windows PowerShell paths.</span></span> <span data-ttu-id="01d1f-150">Por exemplo, para instalar o pacote NewPackage.msi localizado no compartilhamento de rede \\\\AppServ\\dsp no computador remoto PC01, digite o seguinte comando no prompt do Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="01d1f-150">For example, to install the NewPackage.msi package located in the network share \\\\AppServ\\dsp on the remote computer PC01, type the following command at the Windows PowerShell prompt:</span></span>

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

<span data-ttu-id="01d1f-151">Aplicativos que não usam a tecnologia Windows Installer podem ter métodos específicos de aplicativos disponíveis para a implantação automática.</span><span class="sxs-lookup"><span data-stu-id="01d1f-151">Applications that do not use Windows Installer technology may have application-specific methods available for automated deployment.</span></span> <span data-ttu-id="01d1f-152">Para determinar se há um método para a automação de implantação, consulte a documentação do aplicativo ou consulte o sistema de suporte do fornecedor do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="01d1f-152">To determine whether there is a method for deployment automation, check the documentation for the application or consult the application vendor's support system.</span></span> <span data-ttu-id="01d1f-153">Em alguns casos, mesmo que o fornecedor do aplicativo não tenha projetado especificamente o aplicativo para a automação da instalação, o fabricante do instalador de software pode conter algumas técnicas de automação.</span><span class="sxs-lookup"><span data-stu-id="01d1f-153">In some cases, even if the application vendor did not specifically design the application for installation automation, the installer software manufacturer may have some techniques for automation.</span></span>

### <a name="removing-applications"></a><span data-ttu-id="01d1f-154">Removendo aplicativos</span><span class="sxs-lookup"><span data-stu-id="01d1f-154">Removing Applications</span></span>

<span data-ttu-id="01d1f-155">Remover um pacote do Windows Installer usando o Windows PowerShell funciona quase da mesma forma que a instalação de um pacote.</span><span class="sxs-lookup"><span data-stu-id="01d1f-155">Removing a Windows Installer package by using Windows PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="01d1f-156">Aqui está um exemplo que seleciona o pacote para desinstalar com base em seu nome; em alguns casos pode ser mais fácil de filtrar com o **IdentifyingNumber**:</span><span class="sxs-lookup"><span data-stu-id="01d1f-156">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

<span data-ttu-id="01d1f-157">Remover outros aplicativos não é tão simples, mesmo quando feito localmente.</span><span class="sxs-lookup"><span data-stu-id="01d1f-157">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="01d1f-158">Podemos encontrar as cadeias de caracteres de desinstalação de linha de comando para esses aplicativos por meio da extração da propriedade **UninstallString**.</span><span class="sxs-lookup"><span data-stu-id="01d1f-158">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span> <span data-ttu-id="01d1f-159">Esse método funciona para aplicativos do Windows Installer em programas mais antigos que aparecem sob a Chave de desinstalação:</span><span class="sxs-lookup"><span data-stu-id="01d1f-159">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="01d1f-160">Você pode filtrar a saída pelo nome da exibição, se desejar:</span><span class="sxs-lookup"><span data-stu-id="01d1f-160">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="01d1f-161">No entanto, essas cadeias de caracteres podem não ser diretamente utilizáveis no prompt do Windows PowerShell sem modificação.</span><span class="sxs-lookup"><span data-stu-id="01d1f-161">However, these strings may not be directly usable from the Windows PowerShell prompt without some modification.</span></span>

### <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="01d1f-162">Atualizando aplicativos do Windows Installer</span><span class="sxs-lookup"><span data-stu-id="01d1f-162">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="01d1f-163">Para atualizar um aplicativo, você precisa saber o nome do aplicativo e o caminho para o pacote de atualização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="01d1f-163">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="01d1f-164">Com essas informações, você pode atualizar um aplicativo com um único comando do Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="01d1f-164">With that information, you can upgrade an application with a single Windows PowerShell command:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```