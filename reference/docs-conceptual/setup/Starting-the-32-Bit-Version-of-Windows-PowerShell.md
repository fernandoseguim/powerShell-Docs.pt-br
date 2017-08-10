---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: "Iniciando a versão de 32 bits do Windows PowerShell"
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: 927b4028fcab68cb26d92bf292df2f0270837457
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="3165d-103">Iniciando a versão de 32 bits do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3165d-103">Starting the 32-Bit Version of Windows PowerShell</span></span>
<span data-ttu-id="3165d-104">Quando você instala o Windows PowerShell em um computador de 64 bits, o **Windows PowerShell (x86)**, uma versão de 32 bits do Windows PowerShell é instalada com a versão de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="3165d-104">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="3165d-105">Quando você executa o Windows PowerShell, a versão de 64 bits é executada por padrão.</span><span class="sxs-lookup"><span data-stu-id="3165d-105">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="3165d-106">No entanto, ocasionalmente pode ser necessário executar o **Windows PowerShell (x86)**, como quando você estiver usando um módulo que requer a versão de 32 bits ou quando você quiser se conectar remotamente a um computador de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="3165d-106">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="3165d-107">Para iniciar uma versão de 32 bits do Windows PowerShell, use qualquer um dos procedimentos a seguir.</span><span class="sxs-lookup"><span data-stu-id="3165d-107">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="3165d-108">No Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="3165d-108">In Windows Server® 2012 R2</span></span>

-   <span data-ttu-id="3165d-109">Na tela **Iniciar**, clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3165d-109">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="3165d-110">Clique no bloco **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="3165d-110">Click the **Windows PowerShell x86** tile.</span></span>

-   <span data-ttu-id="3165d-111">Em **Gerenciador do Servidor**, no menu **Ferramentas**, selecione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3165d-111">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="3165d-112">Na área de trabalho, mova o cursor para o canto superior direito, clique em **Pesquisar**, digite **PowerShell x86** e clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3165d-112">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="3165d-113">Por meio da linha de comando, digite: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="3165d-113">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="3165d-114">No Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="3165d-114">In Windows Server® 2012</span></span>

-   <span data-ttu-id="3165d-115">Na tela **Iniciar**, digite **PowerShell** e clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3165d-115">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="3165d-116">Em **Gerenciador do Servidor**, no menu **Ferramentas**, selecione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3165d-116">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="3165d-117">Na área de trabalho, mova o cursor para o canto superior direito, clique em **Pesquisar**, digite **PowerShell** e clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3165d-117">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="3165d-118">Por meio da linha de comando, digite: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="3165d-118">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="3165d-119">No Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="3165d-119">In Windows® 8.1</span></span>

-   <span data-ttu-id="3165d-120">Na tela **Iniciar**, clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3165d-120">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="3165d-121">Clique no bloco **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="3165d-121">Click the **Windows PowerShell x86** tile.</span></span>

-   <span data-ttu-id="3165d-122">Se estiver executando as [Ferramentas de Administração de Servidor Remoto](http://go.microsoft.com/fwlink/?LinkID=304145) para o Windows 8.1, você também poderá abrir o Windows PowerShell x86 no menu **Ferramentas do Gerenciador do Servidor**.</span><span class="sxs-lookup"><span data-stu-id="3165d-122">If you are running [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="3165d-123">Selecione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3165d-123">Select **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="3165d-124">Na área de trabalho, mova o cursor para o canto superior direito, clique em **Pesquisar**, digite **PowerShell x86** e clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3165d-124">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
   
-   <span data-ttu-id="3165d-125">Por meio da linha de comando, digite: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="3165d-125">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="3165d-126">No Windows® 8</span><span class="sxs-lookup"><span data-stu-id="3165d-126">In Windows® 8</span></span>

-   <span data-ttu-id="3165d-127">Na tela **Iniciar**, mova o cursor para o canto superior direito, clique em **Configurações**, **Blocos** e mova o controle deslizante **Mostrar Ferramentas Administrativas** para Sim.</span><span class="sxs-lookup"><span data-stu-id="3165d-127">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="3165d-128">Em seguida, digite **PowerShell** e clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3165d-128">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="3165d-129">Se estiver executando as [Ferramentas de Administração de Servidor Remoto](http://www.microsoft.com/download/details.aspx?id=28972) para o Windows 8, você também poderá abrir o Windows PowerShell x86 no menu **Ferramentas do Gerenciador do Servidor**.</span><span class="sxs-lookup"><span data-stu-id="3165d-129">If you are running [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="3165d-130">Selecione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3165d-130">Select **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="3165d-131">Na tela **Iniciar** ou na área de trabalho, digite **PowerShell (x86)** e clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3165d-131">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="3165d-132">Por meio da linha de comando, digite: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="3165d-132">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

