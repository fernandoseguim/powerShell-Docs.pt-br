---
title: Estado de sessão do Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059534"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="481fd-102">Estado de sessão do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="481fd-102">Windows PowerShell Session State</span></span>

<span data-ttu-id="481fd-103">Estado de sessão refere-se à configuração atual de uma sessão do Windows PowerShell ou o módulo.</span><span class="sxs-lookup"><span data-stu-id="481fd-103">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="481fd-104">Uma sessão do Windows PowerShell é o ambiente operacional que é usado interativamente pelo usuário de linha de comando ou por um aplicativo host de forma programática.</span><span class="sxs-lookup"><span data-stu-id="481fd-104">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="481fd-105">O estado de sessão para uma sessão é conhecido como o estado de sessão global.</span><span class="sxs-lookup"><span data-stu-id="481fd-105">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="481fd-106">Da perspectiva do desenvolvedor, uma sessão do Windows PowerShell refere-se para o tempo entre quando um aplicativo host é aberto em um espaço de execução do Windows PowerShell e quando ele fecha o espaço de execução.</span><span class="sxs-lookup"><span data-stu-id="481fd-106">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="481fd-107">Examinamos outra maneira, a sessão é o tempo de vida de uma instância do mecanismo do Windows PowerShell que é chamado enquanto o runspace existe.</span><span class="sxs-lookup"><span data-stu-id="481fd-107">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="481fd-108">Estado de sessão do módulo</span><span class="sxs-lookup"><span data-stu-id="481fd-108">Module Session State</span></span>

<span data-ttu-id="481fd-109">Estados de sessão do módulo são criados sempre que o módulo ou um de seus módulos aninhados é importado para a sessão.</span><span class="sxs-lookup"><span data-stu-id="481fd-109">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="481fd-110">Quando um módulo exporta um elemento como um cmdlet, função ou script, uma referência a esse elemento é adicionada para o estado de sessão global da sessão.</span><span class="sxs-lookup"><span data-stu-id="481fd-110">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="481fd-111">No entanto, quando o elemento é executado, ele é executado dentro do módulo, o estado de sessão.</span><span class="sxs-lookup"><span data-stu-id="481fd-111">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="481fd-112">Dados de estado de sessão</span><span class="sxs-lookup"><span data-stu-id="481fd-112">Session-State Data</span></span>

<span data-ttu-id="481fd-113">Dados de estado de sessão podem ser público ou privado.</span><span class="sxs-lookup"><span data-stu-id="481fd-113">Session state data can be public or private.</span></span> <span data-ttu-id="481fd-114">Dados públicos estão disponíveis para chamadas de fora o estado de sessão, enquanto dados particulares estão disponíveis somente para chamadas a partir de estado da sessão.</span><span class="sxs-lookup"><span data-stu-id="481fd-114">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="481fd-115">Por exemplo, um módulo pode ter uma função privada que pode ser chamada somente pelo módulo ou apenas internamente por um elemento público que foi exportado.</span><span class="sxs-lookup"><span data-stu-id="481fd-115">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="481fd-116">Isso é semelhante para os membros públicos e privados de um tipo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="481fd-116">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="481fd-117">Dados de estado de sessão são armazenados pela instância atual do mecanismo de execução dentro do contexto da sessão atual do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="481fd-117">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="481fd-118">Dados de estado de sessão consistem dos seguintes itens:</span><span class="sxs-lookup"><span data-stu-id="481fd-118">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="481fd-119">Informações de caminho</span><span class="sxs-lookup"><span data-stu-id="481fd-119">Path information</span></span>

- <span data-ttu-id="481fd-120">Informações da unidade</span><span class="sxs-lookup"><span data-stu-id="481fd-120">Drive information</span></span>

- <span data-ttu-id="481fd-121">Informações do provedor do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="481fd-121">Windows PowerShell provider information</span></span>

- <span data-ttu-id="481fd-122">Informações sobre os módulos importados e referências para os elementos de módulo (como cmdlets, funções e scripts) que são exportadas pelo módulo.</span><span class="sxs-lookup"><span data-stu-id="481fd-122">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="481fd-123">Essas informações e essas referências são para apenas o estado da sessão global.</span><span class="sxs-lookup"><span data-stu-id="481fd-123">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="481fd-124">Informações de variável de estado de sessão</span><span class="sxs-lookup"><span data-stu-id="481fd-124">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="481fd-125">Acessando dados de estado de sessão dentro de Cmdlets</span><span class="sxs-lookup"><span data-stu-id="481fd-125">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="481fd-126">Cmdlets podem acessar os dados de estado de sessão ou indiretamente por meio de [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) propriedade de classe do cmdlet ou diretamente por meio de [ System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) classe.</span><span class="sxs-lookup"><span data-stu-id="481fd-126">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="481fd-127">O [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) classe fornece propriedades que podem ser usadas para investigar os diferentes tipos de dados de estado de sessão.</span><span class="sxs-lookup"><span data-stu-id="481fd-127">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="481fd-128">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="481fd-128">See Also</span></span>

[<span data-ttu-id="481fd-129">System.Management.Automation.PSCmdlet.Sessionstate</span><span class="sxs-lookup"><span data-stu-id="481fd-129">System.Management.Automation.PSCmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="481fd-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="481fd-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="481fd-131">Cmdlets do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="481fd-131">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

<span data-ttu-id="481fd-132">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="481fd-132">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

[<span data-ttu-id="481fd-133">Shell do Windows PowerShell do SDK</span><span class="sxs-lookup"><span data-stu-id="481fd-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
