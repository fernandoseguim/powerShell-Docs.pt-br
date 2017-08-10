---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: Instalar o Windows PowerShell
ms.assetid: 6fbb0409-5a54-48ec-95e6-7f8b7d8c4969
ms.openlocfilehash: 2b4cdec52dfc98649a81ab2265a204fcdb0bd8d7
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
# <a name="installing-windows-powershell"></a><span data-ttu-id="4b79e-103">Instalar o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4b79e-103">Installing Windows PowerShell</span></span>
<span data-ttu-id="4b79e-104">O Windows® 8 e o Windows Server® 2012 incluem o Windows PowerShell 3.0 e todos os seus pré-requisitos.</span><span class="sxs-lookup"><span data-stu-id="4b79e-104">Windows® 8 and Windows Server® 2012 include Windows PowerShell 3.0 and all of its prerequisites.</span></span> <span data-ttu-id="4b79e-105">O sistema também inclui o Mecanismo Windows PowerShell 2.0 para compatibilidade com programas host que não podem usar o Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="4b79e-105">The system also includes the Windows PowerShell 2.0 engine for backward compatibility with host programs that cannot use Windows PowerShell 3.0.</span></span>

<span data-ttu-id="4b79e-106">Este tópico explica como instalar o Windows PowerShell 3.0 em sistemas anteriores e instalar e habilitar os recursos necessários.</span><span class="sxs-lookup"><span data-stu-id="4b79e-106">This topic explains how to install Windows PowerShell 3.0 on earlier systems and install and enable the required features.</span></span>

<span data-ttu-id="4b79e-107">Este tópico inclui as seções a seguir:</span><span class="sxs-lookup"><span data-stu-id="4b79e-107">This topic includes the following sections:</span></span>

-   [<span data-ttu-id="4b79e-108">Instalar o Windows PowerShell no Windows 8 e no Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="4b79e-108">Installing Windows PowerShell on Windows 8 and Windows Server 2012</span></span>](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows8andWindowsServer2012)

-   [<span data-ttu-id="4b79e-109">Instalar o Windows PowerShell no Windows 7 e no Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="4b79e-109">Installing Windows PowerShell on Windows 7 and Windows Server 2008 R2</span></span>](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows7andWindowsServer2008R2)

-   [<span data-ttu-id="4b79e-110">Instalar o Windows PowerShell no Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="4b79e-110">Installing Windows PowerShell on Windows Server 2008</span></span>](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindowsServer2008LH)

-   [<span data-ttu-id="4b79e-111">Instalar o Windows PowerShell no Server Core</span><span class="sxs-lookup"><span data-stu-id="4b79e-111">Installing Windows PowerShell on Server Core</span></span>](Installing-Windows-PowerShell.md#BKMK_InstallingOnServerCore)

-   [<span data-ttu-id="4b79e-112">Implantar o Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="4b79e-112">Deploying Windows PowerShell Web Access</span></span>](https://technet.microsoft.com/en-us/library/639d0eff-98a3-4124-b52c-26921ebd98b0)

-   [<span data-ttu-id="4b79e-113">Instalar o Mecanismo do Windows PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="4b79e-113">Installing the Windows PowerShell 2.0 Engine</span></span>](Installing-the-Windows-PowerShell-2.0-Engine.md)

## <span data-ttu-id="4b79e-114"><a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>Instalar o Windows PowerShell no Windows 8 e no Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="4b79e-114"><a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>Installing Windows PowerShell on Windows 8 and Windows Server 2012</span></span>
<span data-ttu-id="4b79e-115">O Windows PowerShell 3.0 chega instalado, configurado e pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="4b79e-115">Windows PowerShell 3.0 arrives installed, configured, and ready to use.</span></span> <span data-ttu-id="4b79e-116">O ISE (Ambiente de Script Integrado) do Windows PowerShell está instalado e habilitado.</span><span class="sxs-lookup"><span data-stu-id="4b79e-116">Windows PowerShell Integrated Scripting Environment (ISE) is installed and enabled.</span></span> <span data-ttu-id="4b79e-117">Para obter informações sobre como iniciar o Windows PowerShell, consulte [Starting Windows PowerShell on Windows 8](https://technet.microsoft.com/en-us/library/d7be1668-8617-4890-ad90-dd9765fbd2c3) (Iniciando o Windows PowerShell no Windows 8) e [Starting Windows PowerShell on Windows Server 2012](https://technet.microsoft.com/library/hh831491.aspx#BKMK_powershell) (Iniciando o Windows PowerShell no Windows Server 2012).</span><span class="sxs-lookup"><span data-stu-id="4b79e-117">For information about starting Windows PowerShell, see [Starting Windows PowerShell on Windows 8](https://technet.microsoft.com/en-us/library/d7be1668-8617-4890-ad90-dd9765fbd2c3) and [Starting Windows PowerShell on Windows Server 2012](https://technet.microsoft.com/library/hh831491.aspx#BKMK_powershell).</span></span>

## <span data-ttu-id="4b79e-118"><a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>Instalar o Windows PowerShell no Windows 7 e no Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="4b79e-118"><a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>Installing Windows PowerShell on Windows 7 and Windows Server 2008 R2</span></span>
<span data-ttu-id="4b79e-119">Estas instruções explicam como instalar o Windows PowerShell 3.0 em computadores com o Windows 7 com Service Pack 1 e Windows Server 2008 R2 com Service Pack 1.</span><span class="sxs-lookup"><span data-stu-id="4b79e-119">These instructions explain how to install Windows PowerShell 3.0 on computers running Windows 7 with Service Pack 1 and Windows Server 2008 R2 with Service Pack 1.</span></span> <span data-ttu-id="4b79e-120">Há instruções de instalação separadas abaixo para computadores que executam com a opção de instalação Server Core do Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="4b79e-120">There are separate installation instructions below for computers running with the Server Core installation option of Windows Server 2008 R2.</span></span>

#### <a name="getting-ready-to-install"></a><span data-ttu-id="4b79e-121">Preparando para instalar</span><span class="sxs-lookup"><span data-stu-id="4b79e-121">Getting ready to install</span></span>

-   <span data-ttu-id="4b79e-122">Antes de instalar o Windows Management Framework 3.0, desinstale todas as versões anteriores do Windows Management Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="4b79e-122">Before installing Windows Management Framework 3.0, uninstall any previous versions of Windows Management Framework 3.0.</span></span>

#### <a name="to-install-windows-powershell-30"></a><span data-ttu-id="4b79e-123">Para instalar o Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="4b79e-123">To install Windows PowerShell 3.0</span></span>

1.  <span data-ttu-id="4b79e-124">Instale a instalação completa do Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).</span><span class="sxs-lookup"><span data-stu-id="4b79e-124">Install the full installation of Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).</span></span>

    <span data-ttu-id="4b79e-125">Ou, instale a instalação completa do Microsoft .NET Framework 4.5.(dotNetFx45_Full_setup.exe) do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).</span><span class="sxs-lookup"><span data-stu-id="4b79e-125">Or, install Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).</span></span>

2.  <span data-ttu-id="4b79e-126">Instale o Windows Management Framework 3.0 do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span><span class="sxs-lookup"><span data-stu-id="4b79e-126">Install Windows Management Framework 3.0 from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span>

<span data-ttu-id="4b79e-127">Para obter informações sobre como iniciar o Windows PowerShell 3.0, consulte [Starting Windows PowerShell on Earlier Versions of Windows](Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md) (Iniciando o Windows PowerShell em versões anteriores do Windows).</span><span class="sxs-lookup"><span data-stu-id="4b79e-127">For information about starting Windows PowerShell 3.0, see [Starting Windows PowerShell on Earlier Versions of Windows](Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md).</span></span>

## <span data-ttu-id="4b79e-128"><a name="BKMK_InstallingOnServerCore"></a>Instalar o Windows PowerShell no Server Core</span><span class="sxs-lookup"><span data-stu-id="4b79e-128"><a name="BKMK_InstallingOnServerCore"></a>Installing Windows PowerShell on Server Core</span></span>
<span data-ttu-id="4b79e-129">Essas instruções explicam como instalar o Windows PowerShell 3.0 em computadores que executam a opção de instalação Server Core do Windows Server 2008 R2 com Service Pack 1.</span><span class="sxs-lookup"><span data-stu-id="4b79e-129">These instructions explain how to install Windows PowerShell 3.0 on computers running the Server Core installation option of Windows Server 2008 R2 with Service Pack 1.</span></span>

<span data-ttu-id="4b79e-130">Os primeiros passos do procedimento usam os comandos DISM (Gerenciamento e Manutenção de Imagens de Implantação) para instalar o Microsoft .NET Framework 2.0 para Server Core e Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="4b79e-130">The first steps in the procedure use Deployment Image Servicing and Management (DISM) commands to install Microsoft .NET Framework 2.0 for Server Core and Windows PowerShell 2.0.</span></span> <span data-ttu-id="4b79e-131">Esses programas são pré-requisitos para o Windows Management Framework 3.0, que é instalado em uma etapa posterior.</span><span class="sxs-lookup"><span data-stu-id="4b79e-131">These programs are prerequisites for Windows Management Framework 3.0, which is installed in a subsequent step.</span></span>

#### <a name="getting-ready-to-install"></a><span data-ttu-id="4b79e-132">Preparando para instalar</span><span class="sxs-lookup"><span data-stu-id="4b79e-132">Getting ready to install</span></span>

-   <span data-ttu-id="4b79e-133">Antes de instalar o Windows Management Framework 3.0, desinstale todas as versões anteriores do Windows Management Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="4b79e-133">Before installing Windows Management Framework 3.0, uninstall any previous versions of Windows Management Framework 3.0.</span></span>

#### <a name="to-install-windows-powershell-30"></a><span data-ttu-id="4b79e-134">Para instalar o Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="4b79e-134">To install Windows PowerShell 3.0</span></span>

1.  <span data-ttu-id="4b79e-135">Iniciar Cmd.exe</span><span class="sxs-lookup"><span data-stu-id="4b79e-135">Start Cmd.exe</span></span>

2.  <span data-ttu-id="4b79e-136">Execute um dos seguintes comandos DISM.</span><span class="sxs-lookup"><span data-stu-id="4b79e-136">Run the following DISM commands.</span></span> <span data-ttu-id="4b79e-137">Esses comandos instalam o .NET Framework 2.0 e Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="4b79e-137">These commands install .NET Framework 2.0 and Windows PowerShell 2.0.</span></span>

    ```
    dism /online /enable-feature:NetFx2-ServerCore
    dism /online /enable-feature:MicrosoftWindowsPowerShell
    dism /online /enable-feature:NetFx2-ServerCore-WOW64
    ```

3.  <span data-ttu-id="4b79e-138">Instale a instalação completa do Microsoft .NET Framework 4.0 para Server Core do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450).</span><span class="sxs-lookup"><span data-stu-id="4b79e-138">Install Microsoft .NET Framework 4.0 full installation for Server Core from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450).</span></span>

4.  <span data-ttu-id="4b79e-139">Instale o Windows Management Framework 3.0 do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span><span class="sxs-lookup"><span data-stu-id="4b79e-139">Install Windows Management Framework 3.0 from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span>

## <span data-ttu-id="4b79e-140"><a name="BKMK_InstallingOnWindowsServer2008LH"></a>Instalar o Windows PowerShell no Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="4b79e-140"><a name="BKMK_InstallingOnWindowsServer2008LH"></a>Installing Windows PowerShell on Windows Server 2008</span></span>
<span data-ttu-id="4b79e-141">Essas instruções explicam como instalar o Windows PowerShell 3.0 em computadores com o Windows Server 2008 com o Service Pack 2.</span><span class="sxs-lookup"><span data-stu-id="4b79e-141">These instructions explain how to install Windows PowerShell 3.0 on computers running Windows Server 2008 with Service Pack 2.</span></span>

<span data-ttu-id="4b79e-142">Em sistemas Windows Server 2008, o Windows Management Framework (Windows PowerShell 2.0, KB 968930) é um pré-requisito para Windows Management Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="4b79e-142">On Windows Server 2008 systems, Windows Management Framework (Windows PowerShell 2.0, KB 968930) is a prerequisite for Windows Management Framework 3.0.</span></span> <span data-ttu-id="4b79e-143">O recurso de "Proteção Estendida para Autenticação" protege o computador contra ataques de encaminhamento de autenticação e permite que você use parâmetro **UseSSL** ao criar sessões remotas.</span><span class="sxs-lookup"><span data-stu-id="4b79e-143">The "Extended Protection for Authentication" feature protects the computer from authentication forwarding attacks and allows you to use the **UseSSL** parameter when creating remote sessions.</span></span> <span data-ttu-id="4b79e-144">Para instalar o Windows PowerShell 3.0 e o Mecanismo Windows PowerShell 2.0, utilize o seguinte procedimento.</span><span class="sxs-lookup"><span data-stu-id="4b79e-144">To install Windows PowerShell 3.0 and the Windows PowerShell 2.0 Engine, use the following procedure.</span></span>

#### <a name="getting-ready-to-install"></a><span data-ttu-id="4b79e-145">Preparando para instalar</span><span class="sxs-lookup"><span data-stu-id="4b79e-145">Getting ready to install</span></span>

-   <span data-ttu-id="4b79e-146">Antes de instalar o Windows Management Framework 3.0, desinstale todas as versões anteriores do Windows Management Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="4b79e-146">Before installing Windows Management Framework 3.0, uninstall any previous versions of Windows Management Framework 3.0.</span></span>

#### <a name="to-install-windows-powershell-30"></a><span data-ttu-id="4b79e-147">Para instalar o Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="4b79e-147">To install Windows PowerShell 3.0</span></span>

1.  <span data-ttu-id="4b79e-148">Instale o Microsoft .NET Framework 3.5 com Service Pack 1 no Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910).</span><span class="sxs-lookup"><span data-stu-id="4b79e-148">Install Microsoft .NET Framework 3.5 with Service Pack 1 from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910).</span></span>

2.  <span data-ttu-id="4b79e-149">Instale o Windows Management Framework (Windows PowerShell 2.0, KB 968930) do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkId=243035](http://go.microsoft.com/fwlink/?LinkId=243035).</span><span class="sxs-lookup"><span data-stu-id="4b79e-149">Install Windows Management Framework (Windows PowerShell 2.0, KB 968930) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkId=243035](http://go.microsoft.com/fwlink/?LinkId=243035).</span></span>

3.  <span data-ttu-id="4b79e-150">Instale a instalação completa do Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).</span><span class="sxs-lookup"><span data-stu-id="4b79e-150">Install the full installation of Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).</span></span>

    <span data-ttu-id="4b79e-151">Ou, instale a instalação completa do Microsoft .NET Framework 4.5.(dotNetFx45_Full_setup.exe) do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).</span><span class="sxs-lookup"><span data-stu-id="4b79e-151">Or, install Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).</span></span>

4.  <span data-ttu-id="4b79e-152">Instale a "Proteção Estendida para Autenticação" (KB 968389) de [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398).</span><span class="sxs-lookup"><span data-stu-id="4b79e-152">Install "Extended Protection for Authentication" (KB 968389) from [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398).</span></span>

5.  <span data-ttu-id="4b79e-153">Instale o Windows Management Framework 3.0 do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span><span class="sxs-lookup"><span data-stu-id="4b79e-153">Install Windows Management Framework 3.0 from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span>

## <a name="see-also"></a><span data-ttu-id="4b79e-154">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="4b79e-154">See Also</span></span>
- [<span data-ttu-id="4b79e-155">Requisitos do Sistema do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4b79e-155">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)
- [<span data-ttu-id="4b79e-156">Iniciando o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4b79e-156">Starting Windows PowerShell</span></span>](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)

