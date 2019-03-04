---
title: Declaração de classe do cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 3e410087438ac99526049f99e5c768c017a29848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854442"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="a8212-102">Declaração de classe do cmdlet</span><span class="sxs-lookup"><span data-stu-id="a8212-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="a8212-103">Uma classe do Microsoft .NET Framework é declarada como um cmdlet, especificando o **Cmdlet** atributo como metadados para a classe.</span><span class="sxs-lookup"><span data-stu-id="a8212-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="a8212-104">(O **Cmdlet** é o único atributo necessário para todos os cmdlets).</span><span class="sxs-lookup"><span data-stu-id="a8212-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span> <span data-ttu-id="a8212-105">Quando você especifica o **Cmdlet** atributo, você deve especificar o par do verbo e substantivo que identifica o cmdlet para o usuário.</span><span class="sxs-lookup"><span data-stu-id="a8212-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="a8212-106">E, então, você deve descrever a funcionalidade do Windows PowerShell que o cmdlet oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="a8212-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="a8212-107">Para obter mais informações sobre a sintaxe de declaração que é usada para especificar o **Cmdlet** atributo, consulte [declaração de atributo do Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="a8212-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a8212-108">O **Cmdlet** atributo é definido pela [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="a8212-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="a8212-109">As propriedades dessa classe correspondem aos parâmetros de declaração que são usados quando você declara o atributo.</span><span class="sxs-lookup"><span data-stu-id="a8212-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="a8212-110">Substantivos</span><span class="sxs-lookup"><span data-stu-id="a8212-110">Nouns</span></span>

<span data-ttu-id="a8212-111">O substantivo do cmdlet especifica os recursos sobre os quais o cmdlet atua.</span><span class="sxs-lookup"><span data-stu-id="a8212-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="a8212-112">O substantivo diferencia seus cmdlets de outros cmdlets.</span><span class="sxs-lookup"><span data-stu-id="a8212-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="a8212-113">Substantivos nos nomes de cmdlet devem ser específico e, no caso de substantivos genéricos, como *server*, é melhor adicionar um prefixo curto que diferencia o recurso de outros recursos semelhantes.</span><span class="sxs-lookup"><span data-stu-id="a8212-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="a8212-114">Por exemplo, um nome de cmdlet que inclui um substantivo com um prefixo é `Get-SQLServer`.</span><span class="sxs-lookup"><span data-stu-id="a8212-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="a8212-115">A combinação de um substantivo específico com um verbo mais geral permite que o usuário localizar rapidamente o cmdlet por sua ação e, em seguida, identifique o cmdlet por seus recursos, evitando duplicação de nome de cmdlet desnecessários.</span><span class="sxs-lookup"><span data-stu-id="a8212-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="a8212-116">Para obter uma lista de caracteres especiais que não podem ser usados em nomes de cmdlet, consulte [diretrizes de desenvolvimento necessárias](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="a8212-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="a8212-117">Verbos</span><span class="sxs-lookup"><span data-stu-id="a8212-117">Verbs</span></span>

<span data-ttu-id="a8212-118">Quando você especifica um verbo, as diretrizes de desenvolvimento exigem que você use um dos verbos predefinidos fornecidos pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a8212-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="a8212-119">Usando um desses verbos predefinidos, você terá de garantir a consistência entre os cmdlets que você escreve e os cmdlets que são gravados pela Microsoft e por outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="a8212-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="a8212-120">Por exemplo, o verbo "Get" é usado para os cmdlets que recuperam dados.</span><span class="sxs-lookup"><span data-stu-id="a8212-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="a8212-121">Para obter mais informações sobre as diretrizes para verbos, consulte [nomes de verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="a8212-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="a8212-122">Para obter uma lista de caracteres especiais que não podem ser usados em nomes de cmdlet, consulte [diretrizes de desenvolvimento necessárias](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="a8212-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="a8212-123">Suporte à funcionalidade do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a8212-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="a8212-124">O **Cmdlet** atributo também permite que você especifique que seu cmdlet oferece suporte a algumas das funcionalidades comuns que é fornecida pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a8212-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="a8212-125">Isso inclui suporte para funcionalidades comuns como confirmação de comentários do usuário (conhecida como suporte para o recurso de ShouldProcess) e suporte para transações.</span><span class="sxs-lookup"><span data-stu-id="a8212-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="a8212-126">(O suporte para transações foi introduzido no Windows PowerShell 2.0).</span><span class="sxs-lookup"><span data-stu-id="a8212-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="a8212-127">Para obter mais informações sobre a sintaxe de declaração que é usada para especificar o **Cmdlet** atributo, consulte [declaração de atributo do Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="a8212-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="a8212-128">Definição de classe do cmdlet</span><span class="sxs-lookup"><span data-stu-id="a8212-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="a8212-129">O código a seguir é a definição de uma classe do cmdlet GetProc.</span><span class="sxs-lookup"><span data-stu-id="a8212-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="a8212-130">Observe que Pascal de maiusculas e minúsculas é usada e que o nome da classe inclui o verbo e substantivo do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a8212-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a><span data-ttu-id="a8212-131">Maiusculas e minúsculas de Pascal</span><span class="sxs-lookup"><span data-stu-id="a8212-131">Pascal Casing</span></span>

<span data-ttu-id="a8212-132">Ao nomear cmdlets, use o casing Pascal casing.</span><span class="sxs-lookup"><span data-stu-id="a8212-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="a8212-133">Por exemplo, o `Get-Item` e `Get-ItemProperty` cmdlets mostrar a maneira correta de usar maiusculas quando você está nomeando cmdlets.</span><span class="sxs-lookup"><span data-stu-id="a8212-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8212-134">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="a8212-134">See Also</span></span>

[<span data-ttu-id="a8212-135">System.Management.Automation.Cmdletattribute</span><span class="sxs-lookup"><span data-stu-id="a8212-135">System.Management.Automation.Cmdletattribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="a8212-136">Declaração CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="a8212-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="a8212-137">Nomes de verbos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="a8212-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

<span data-ttu-id="a8212-138">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="a8212-138">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

[<span data-ttu-id="a8212-139">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a8212-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
