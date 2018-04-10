---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Como criar uma guia do PowerShell no ISE do Windows PowerShell
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 4d4388d889f2178b2cd24cb0f3350aee37327625
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="d77f6-103">Como criar uma guia do PowerShell no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d77f6-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>

<span data-ttu-id="d77f6-104">As guias no ISE (Ambiente de Script Integrado) do Windows PowerShell permitem criar e usar simultaneamente vários ambientes de execução dentro do mesmo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d77f6-104">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span>
<span data-ttu-id="d77f6-105">Cada guia do PowerShell corresponde a uma sessão ou ambiente de execução separado.</span><span class="sxs-lookup"><span data-stu-id="d77f6-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> <span data-ttu-id="d77f6-106">**OBSERVAÇÃO**:</span><span class="sxs-lookup"><span data-stu-id="d77f6-106">**NOTE**:</span></span>
>
> <span data-ttu-id="d77f6-107">Variáveis, funções e aliases que você criar em uma guia não serão transferidos para outra.</span><span class="sxs-lookup"><span data-stu-id="d77f6-107">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="d77f6-108">Eles são sessões diferentes do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d77f6-108">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="d77f6-109">Use as etapas a seguir para abrir ou fechar uma guia no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d77f6-109">Use the following steps to open or close a tab in Windows PowerShell.</span></span>
<span data-ttu-id="d77f6-110">Para renomear uma guia, defina a propriedade [DisplayName](The-PowerShellTab-Object.md#displayname) no objeto de script de guia do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d77f6-110">To rename a tab, set the [DisplayName](The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="d77f6-111">Para criar e usar uma nova guia do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d77f6-111">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="d77f6-112">No menu **Arquivo**, clique em **Nova Guia do PowerShell**. A nova guia do PowerShell sempre é aberta como a janela ativa.</span><span class="sxs-lookup"><span data-stu-id="d77f6-112">On the **File** menu, click **New PowerShell Tab**. The new PowerShell tab always opens as the active window.</span></span>
<span data-ttu-id="d77f6-113">Guias do PowerShell são numeradas incrementalmente na ordem em que são abertas.</span><span class="sxs-lookup"><span data-stu-id="d77f6-113">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span>
<span data-ttu-id="d77f6-114">Cada guia é associada à sua própria janela de console do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d77f6-114">Each tab is associated with its own Windows PowerShell console window.</span></span>
<span data-ttu-id="d77f6-115">Você pode ter até 32 guias do PowerShell com sua própria sessão aberta de cada vez (isso é limitado a 8 no ISE do Windows PowerShell 2.0.)</span><span class="sxs-lookup"><span data-stu-id="d77f6-115">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="d77f6-116">Observe que clicar nos ícones **Novo** ou **Abrir** na barra de ferramentas não cria uma nova guia com uma sessão separada.</span><span class="sxs-lookup"><span data-stu-id="d77f6-116">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>
<span data-ttu-id="d77f6-117">Em vez disso, esses botões abrem um arquivo de script novo ou existente na guia ativa no momento com uma sessão.</span><span class="sxs-lookup"><span data-stu-id="d77f6-117">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span>
<span data-ttu-id="d77f6-118">Você pode deixar vários arquivos de script abertos com cada guia e a sessão.</span><span class="sxs-lookup"><span data-stu-id="d77f6-118">You can have multiple script files open with each tab and session.</span></span>
<span data-ttu-id="d77f6-119">As guias de script para uma sessão só aparecem abaixo das guias de sessão quando a sessão associada estiver ativa.</span><span class="sxs-lookup"><span data-stu-id="d77f6-119">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="d77f6-120">Para tornar uma guia do PowerShell ativa, clique nela. Para selecionar todas as guias do PowerShell que estão abertas no menu **Exibir**, clique na guia do PowerShell que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="d77f6-120">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="d77f6-121">Para criar e usar uma nova guia remota do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d77f6-121">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="d77f6-122">No menu **Arquivo**, clique em **Nova Guia Remota do PowerShell** para estabelecer uma sessão em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="d77f6-122">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span>
<span data-ttu-id="d77f6-123">Uma caixa de diálogo é exibida e solicita que você insira os detalhes necessários para estabelecer a conexão remota.</span><span class="sxs-lookup"><span data-stu-id="d77f6-123">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>
<span data-ttu-id="d77f6-124">A guia remota funciona como uma guia local do PowerShell, mas os comandos e os scripts são executados no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="d77f6-124">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="d77f6-125">Para fechar uma guia do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d77f6-125">To close a PowerShell Tab</span></span>

<span data-ttu-id="d77f6-126">Para fechar uma guia, você pode usar qualquer uma das seguintes técnicas:</span><span class="sxs-lookup"><span data-stu-id="d77f6-126">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="d77f6-127">Clique na guia que você deseja fechar.</span><span class="sxs-lookup"><span data-stu-id="d77f6-127">Click the tab that you want to close.</span></span>

- <span data-ttu-id="d77f6-128">No menu **Arquivo**, clique em **Fechar Guia do PowerShell** ou no botão Fechar (**X**) em uma guia para fechar a guia ativa.</span><span class="sxs-lookup"><span data-stu-id="d77f6-128">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="d77f6-129">Se tiver arquivos não salvos abertos na guia do PowerShell que você está fechando, será solicitado salvá-los ou descartá-los.</span><span class="sxs-lookup"><span data-stu-id="d77f6-129">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span>
<span data-ttu-id="d77f6-130">Para obter mais informações sobre como salvar um script, consulte [Como salvar um script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span><span class="sxs-lookup"><span data-stu-id="d77f6-130">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="d77f6-131">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="d77f6-131">See Also</span></span>

- [<span data-ttu-id="d77f6-132">Apresentando o ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d77f6-132">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="d77f6-133">Como usar o Painel de Console com o ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d77f6-133">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)