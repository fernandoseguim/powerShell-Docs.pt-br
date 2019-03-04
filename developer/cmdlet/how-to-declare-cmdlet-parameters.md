---
title: Como declarar parâmetros de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: d6613889ebd2ba139ce0b3de1b8d24e4aec37d2a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861392"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="59f04-102">Como declarar parâmetros de cmdlet</span><span class="sxs-lookup"><span data-stu-id="59f04-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="59f04-103">Estes exemplos mostram como declarar nomeado, posicional, obrigatória, opcional e parâmetros de opção.</span><span class="sxs-lookup"><span data-stu-id="59f04-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="59f04-104">Esses exemplos também mostram como definir um alias de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="59f04-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="59f04-105">Como declarar um parâmetro nomeado</span><span class="sxs-lookup"><span data-stu-id="59f04-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="59f04-106">Defina uma propriedade pública, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="59f04-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="59f04-107">Quando você adiciona o atributo de parâmetro, omita o `Position` palavra-chave do atributo.</span><span class="sxs-lookup"><span data-stu-id="59f04-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="59f04-108">Para obter mais informações sobre o atributo de parâmetro, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="59f04-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="59f04-109">Como declarar um parâmetro posicional</span><span class="sxs-lookup"><span data-stu-id="59f04-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="59f04-110">Defina uma propriedade pública, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="59f04-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="59f04-111">Quando você adiciona o atributo de parâmetro, defina o `Position` palavra-chave para a posição do argumento.</span><span class="sxs-lookup"><span data-stu-id="59f04-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="59f04-112">Um valor de 0 indica a primeira posição.</span><span class="sxs-lookup"><span data-stu-id="59f04-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="59f04-113">Para obter mais informações sobre o atributo de parâmetro, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="59f04-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="59f04-114">Como declarar um parâmetro obrigatório</span><span class="sxs-lookup"><span data-stu-id="59f04-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="59f04-115">Defina uma propriedade pública, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="59f04-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="59f04-116">Quando você adiciona o atributo de parâmetro, defina as `Mandatory` palavra-chave para `true`.</span><span class="sxs-lookup"><span data-stu-id="59f04-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="59f04-117">Para obter mais informações sobre o atributo de parâmetro, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="59f04-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="59f04-118">Como declarar um parâmetro opcional</span><span class="sxs-lookup"><span data-stu-id="59f04-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="59f04-119">Defina uma propriedade pública, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="59f04-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="59f04-120">Quando você adiciona o atributo de parâmetro, omita o `Mandatory` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="59f04-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="59f04-121">Como declarar um parâmetro de opção</span><span class="sxs-lookup"><span data-stu-id="59f04-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="59f04-122">Definir uma propriedade pública como tipo [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter)e, em seguida, declarar o atributo de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="59f04-122">Define a public property as type [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="59f04-123">Para obter mais informações sobre o atributo de parâmetro, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="59f04-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="59f04-124">Como declarar um parâmetro com Aliases</span><span class="sxs-lookup"><span data-stu-id="59f04-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="59f04-125">Defina uma propriedade pública, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="59f04-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="59f04-126">Adicione um atributo de Alias que lista os aliases para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="59f04-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="59f04-127">Neste exemplo, três aliases são definidos para o mesmo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="59f04-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="59f04-128">O alias primeiro fornece um atalho.</span><span class="sxs-lookup"><span data-stu-id="59f04-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="59f04-129">Os aliases do segundo e terceiro fornecem nomes que podem ser usados para cenários diferentes.</span><span class="sxs-lookup"><span data-stu-id="59f04-129">The second and third aliases provide names you can use for different scenarios.</span></span>

    ```csharp
    [Alias("UN","Writer","Editor")]
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="59f04-130">Para obter mais informações sobre o atributo de Alias, consulte [declaração de atributo de Alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="59f04-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="59f04-131">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="59f04-131">See Also</span></span>

[<span data-ttu-id="59f04-132">System.Management.Automation.Switchparameter</span><span class="sxs-lookup"><span data-stu-id="59f04-132">System.Management.Automation.Switchparameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="59f04-133">Declaração de atributo de parâmetro</span><span class="sxs-lookup"><span data-stu-id="59f04-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="59f04-134">Declaração de atributo de alias</span><span class="sxs-lookup"><span data-stu-id="59f04-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

<span data-ttu-id="59f04-135">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="59f04-135">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
