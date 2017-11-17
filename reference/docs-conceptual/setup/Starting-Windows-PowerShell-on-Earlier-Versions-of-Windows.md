---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: "Iniciando o Windows PowerShell em versões anteriores do Windows"
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: 52e3acc1fd3009ecad3b7134008e38d4edfb5ca7
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2017
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="80aa2-103">Iniciando o Windows PowerShell em versões anteriores do Windows</span><span class="sxs-lookup"><span data-stu-id="80aa2-103">Starting Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="80aa2-104">Esta seção explica como iniciar o Windows PowerShell e o ISE (Ambiente de Script Integrado) do Windows PowerShell no Windows® 7, Windows Server® 2008 R2 e Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="80aa2-104">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="80aa2-105">Também explica como habilitar o recurso opcional para o ISE do Windows PowerShell no Windows PowerShell 2.0 no Windows Server® 2008 R2 e Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="80aa2-105">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="80aa2-106">Para instalar o Windows PowerShell 4.0 em sistemas com suporte, baixe e instale o [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span><span class="sxs-lookup"><span data-stu-id="80aa2-106">To install Windows PowerShell 4.0 on supported systems, download and install [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span></span> <span data-ttu-id="80aa2-107">Para saber mais, consulte [Instalar o Windows PowerShell](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="80aa2-107">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

<span data-ttu-id="80aa2-108">Para instalar o Windows PowerShell 3.0 em sistemas com suporte, baixe e instale o [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span><span class="sxs-lookup"><span data-stu-id="80aa2-108">To install Windows PowerShell 3.0 on supported systems, download and install [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span> <span data-ttu-id="80aa2-109">Para saber mais, consulte [Instalar o Windows PowerShell](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="80aa2-109">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="80aa2-110">Como iniciar o Windows PowerShell em versões anteriores do Windows</span><span class="sxs-lookup"><span data-stu-id="80aa2-110">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="80aa2-111">Use qualquer um dos seguintes métodos para iniciar a versão instalada do Windows PowerShell 3.0 ou o Windows PowerShell 4.0, quando aplicável.</span><span class="sxs-lookup"><span data-stu-id="80aa2-111">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="80aa2-112">Do menu Iniciar</span><span class="sxs-lookup"><span data-stu-id="80aa2-112">From the Start Menu</span></span>

- <span data-ttu-id="80aa2-113">Clique em **Iniciar**, digite **PowerShell** e clique em **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="80aa2-113">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>

- <span data-ttu-id="80aa2-114">No menu **Iniciar**, clique em **Iniciar**, **Todos os Programas**, **Acessórios**, clique na pasta **Windows PowerShell** e clique em **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="80aa2-114">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="80aa2-115">No prompt de comando</span><span class="sxs-lookup"><span data-stu-id="80aa2-115">At the Command Prompt</span></span>

- <span data-ttu-id="80aa2-116">No Cmd.exe, Windows PowerShell ou ISE do Windows PowerShell, para iniciar o Windows PowerShell, digite:</span><span class="sxs-lookup"><span data-stu-id="80aa2-116">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell
    ```

    <span data-ttu-id="80aa2-117">Você também pode usar os parâmetros do programa PowerShell.exe para personalizar a sessão.</span><span class="sxs-lookup"><span data-stu-id="80aa2-117">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="80aa2-118">Para obter mais informações, consulte [Ajuda de linha de comando do PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="80aa2-118">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="80aa2-119">Com privilégios administrativos (“Executar como administrador”)</span><span class="sxs-lookup"><span data-stu-id="80aa2-119">With Administrative privileges ("Run as administrator")</span></span>

1. <span data-ttu-id="80aa2-120">Clique em **Iniciar**, digite **PowerShell**, clique com o botão direito do mouse em **Windows PowerShell** e depois clique em **Executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="80aa2-120">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="80aa2-121">Como iniciar o ISE do Windows PowerShell em versões anteriores do Windows</span><span class="sxs-lookup"><span data-stu-id="80aa2-121">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="80aa2-122">Use qualquer um dos seguintes métodos para iniciar o ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80aa2-122">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="80aa2-123">Do menu Iniciar</span><span class="sxs-lookup"><span data-stu-id="80aa2-123">From the Start Menu</span></span>

- <span data-ttu-id="80aa2-124">Clique em **Iniciar**, digite **ISE** e clique em **ISE do Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="80aa2-124">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>

- <span data-ttu-id="80aa2-125">No menu **Iniciar**, clique em **Iniciar**, **Todos os Programas**, **Acessórios**, clique na pasta **Windows PowerShell** e clique em **ISE do Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="80aa2-125">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="80aa2-126">No prompt de comando</span><span class="sxs-lookup"><span data-stu-id="80aa2-126">At the Command Prompt</span></span>

- <span data-ttu-id="80aa2-127">No Cmd.exe, Windows PowerShell ou ISE do Windows PowerShell, para iniciar o Windows PowerShell, digite:</span><span class="sxs-lookup"><span data-stu-id="80aa2-127">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell_ISE
    ```

    <span data-ttu-id="80aa2-128">ou</span><span class="sxs-lookup"><span data-stu-id="80aa2-128">or</span></span>

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="80aa2-129">Com privilégios administrativos (“Executar como administrador”)</span><span class="sxs-lookup"><span data-stu-id="80aa2-129">With Administrative privileges ("Run as administrator")</span></span>

1. <span data-ttu-id="80aa2-130">Clique em **Iniciar**, digite **ISE**, clique com o botão direito do mouse em **ISE do Windows PowerShell** e depois clique em **Executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="80aa2-130">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="80aa2-131">Como habilitar o ISE do Windows PowerShell em versões anteriores do Windows</span><span class="sxs-lookup"><span data-stu-id="80aa2-131">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="80aa2-132">No Windows PowerShell 4.0 e Windows PowerShell 3.0, o ISE do Windows PowerShell é habilitado por padrão em todas as versões do Windows.</span><span class="sxs-lookup"><span data-stu-id="80aa2-132">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="80aa2-133">Se ele ainda não estiver habilitado, o Windows Management Framework 4.0 ou Windows Management Framework 3.0 o habilitará.</span><span class="sxs-lookup"><span data-stu-id="80aa2-133">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="80aa2-134">No Windows PowerShell 2.0, o ISE do Windows PowerShell é habilitado por padrão no Windows 7.</span><span class="sxs-lookup"><span data-stu-id="80aa2-134">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="80aa2-135">No entanto, no Windows Server 2008 R2 e Windows Server 2008, é um recurso opcional.</span><span class="sxs-lookup"><span data-stu-id="80aa2-135">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="80aa2-136">Para habilitar o ISE do Windows PowerShell no Windows PowerShell 2.0 no Windows Server 2008 R2 ou Windows Server 2008, use o seguinte procedimento.</span><span class="sxs-lookup"><span data-stu-id="80aa2-136">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="80aa2-137">Para habilitar o ISE (Ambiente de Script Integrado) do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="80aa2-137">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="80aa2-138">Inicie o Gerenciador do Servidor.</span><span class="sxs-lookup"><span data-stu-id="80aa2-138">Start Server Manager.</span></span>

2. <span data-ttu-id="80aa2-139">Clique em **Recursos** e depois em **Adicionar Recursos**.</span><span class="sxs-lookup"><span data-stu-id="80aa2-139">Click **Features** and then click **Add Features**.</span></span>

3. <span data-ttu-id="80aa2-140">Em Selecionar Recursos, clique em ISE (Ambiente de Script Integrado) do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80aa2-140">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

