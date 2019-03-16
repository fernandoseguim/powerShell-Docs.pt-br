---
title: Tipos de parâmetros do Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059568"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="84ccf-102">Tipos de parâmetros de cmdlet</span><span class="sxs-lookup"><span data-stu-id="84ccf-102">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="84ccf-103">Este tópico descreve os diferentes tipos de parâmetros que você pode declarar nos cmdlets.</span><span class="sxs-lookup"><span data-stu-id="84ccf-103">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="84ccf-104">Parâmetros do cmdlet podem ser posicional, nomeado, obrigatória, opcional ou parâmetros de opção.</span><span class="sxs-lookup"><span data-stu-id="84ccf-104">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="84ccf-105">Parâmetros posicionais e nomeados</span><span class="sxs-lookup"><span data-stu-id="84ccf-105">Positional and Named Parameters</span></span>

<span data-ttu-id="84ccf-106">Todos os parâmetros de cmdlet são parâmetros nomeados ou posicionais.</span><span class="sxs-lookup"><span data-stu-id="84ccf-106">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="84ccf-107">Um parâmetro nomeado exige que você digite o nome do parâmetro e o argumento ao chamar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="84ccf-107">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="84ccf-108">Um parâmetro posicional requer apenas que você digite os argumentos na ordem relativa.</span><span class="sxs-lookup"><span data-stu-id="84ccf-108">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="84ccf-109">O sistema, em seguida, mapeia o primeiro argumento sem nome para o primeiro parâmetro posicional.</span><span class="sxs-lookup"><span data-stu-id="84ccf-109">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="84ccf-110">O sistema mapeia o segundo argumento sem nome para o segundo parâmetro sem nome e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="84ccf-110">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="84ccf-111">Por padrão, todos os parâmetros de cmdlet são parâmetros nomeados.</span><span class="sxs-lookup"><span data-stu-id="84ccf-111">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="84ccf-112">Para definir um parâmetro nomeado, omita a `Position` palavra-chave em de **parâmetro** atributo de declaração, conforme mostrado na seguinte declaração de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="84ccf-112">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="84ccf-113">Para definir um parâmetro posicional, adicione o `Position` palavra-chave no parâmetro de declaração do atributo e, em seguida, especificar uma posição.</span><span class="sxs-lookup"><span data-stu-id="84ccf-113">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="84ccf-114">No exemplo a seguir, o `UserName` parâmetro é declarado como um parâmetro posicional com posição 0.</span><span class="sxs-lookup"><span data-stu-id="84ccf-114">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="84ccf-115">Isso significa que o primeiro argumento da chamada será automaticamente associado a esse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="84ccf-115">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> <span data-ttu-id="84ccf-116">Cmdlet bom design recomenda que os parâmetros usados com mais ser declarados como parâmetros posicionais para que o usuário não precisa digitar o nome de parâmetro quando o cmdlet é executado.</span><span class="sxs-lookup"><span data-stu-id="84ccf-116">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="84ccf-117">Parâmetros posicionais e nomeados aceitam argumentos únicos ou vários argumentos separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="84ccf-117">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="84ccf-118">São permitidos vários argumentos somente se o parâmetro aceita uma coleção, como uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="84ccf-118">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="84ccf-119">Você pode misturar os parâmetros posicionais e nomeados no mesmo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="84ccf-119">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="84ccf-120">Nesse caso, o sistema recupera os argumentos nomeados primeiro e, em seguida, tenta mapear o restante sem nome argumentos para os parâmetros posicionais.</span><span class="sxs-lookup"><span data-stu-id="84ccf-120">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="84ccf-121">Os comandos a seguir mostram as diferentes maneiras em que você pode especificar único e vários argumentos para os parâmetros do `Get-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="84ccf-121">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="84ccf-122">Observe que, nas últimas duas amostras **-nome** não precisa ser especificado porque o `Name` parâmetro é definido como um parâmetro posicional.</span><span class="sxs-lookup"><span data-stu-id="84ccf-122">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="84ccf-123">Parâmetros obrigatórios e opcionais</span><span class="sxs-lookup"><span data-stu-id="84ccf-123">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="84ccf-124">Você também pode definir parâmetros do cmdlet como parâmetros obrigatórios ou opcionais.</span><span class="sxs-lookup"><span data-stu-id="84ccf-124">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="84ccf-125">(Um parâmetro obrigatório deve ser especificado antes do tempo de execução do Windows PowerShell invoca o cmdlet.)  Por padrão, os parâmetros são definidos como opcionais.</span><span class="sxs-lookup"><span data-stu-id="84ccf-125">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="84ccf-126">Para definir um parâmetro obrigatório, adicione a `Mandatory` palavra-chave no parâmetro de declaração de atributo e defini-lo como `true`, conforme mostrado na seguinte declaração de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="84ccf-126">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="84ccf-127">Para definir um parâmetro opcional, omita a `Mandatory` palavra-chave em de **parâmetro** atributo de declaração, conforme mostrado na seguinte declaração de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="84ccf-127">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="84ccf-128">Parâmetros de opção</span><span class="sxs-lookup"><span data-stu-id="84ccf-128">Switch Parameters</span></span>

<span data-ttu-id="84ccf-129">O Windows PowerShell fornece um [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) tipo que permite que você definir um parâmetro cujo valor é definido automaticamente como `false` se o parâmetro não for especificado quando o cmdlet chamado.</span><span class="sxs-lookup"><span data-stu-id="84ccf-129">Windows PowerShell provides a [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="84ccf-130">Sempre que possível, use os parâmetros de opção no lugar de parâmetros booleanos.</span><span class="sxs-lookup"><span data-stu-id="84ccf-130">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="84ccf-131">Considere o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="84ccf-131">Consider the following sample.</span></span> <span data-ttu-id="84ccf-132">Por padrão, vários cmdlets do Windows PowerShell não passe um objeto de saída pelo pipeline.</span><span class="sxs-lookup"><span data-stu-id="84ccf-132">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="84ccf-133">No entanto, esses cmdlets têm um `PassThru` Troque o parâmetro que substitui o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="84ccf-133">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="84ccf-134">Se o `PassThru` parâmetro for especificado quando esses cmdlets são chamados, o cmdlet retorna um objeto de saída para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="84ccf-134">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="84ccf-135">Se você precisa que o parâmetro tenha um valor padrão de `true` quando o parâmetro não for especificado na chamada, considere reverter o sentido do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="84ccf-135">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="84ccf-136">Para obter exemplo, em vez de definir o atributo de parâmetro para um valor booleano `true`, declarar a propriedade como o [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) digite e, em seguida, defina o valor padrão do parâmetro para `false`.</span><span class="sxs-lookup"><span data-stu-id="84ccf-136">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="84ccf-137">Para definir um parâmetro de opção, declarar a propriedade como o [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) de tipo, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="84ccf-137">To define a switch parameter, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="84ccf-138">Para fazer com que o cmdlet agir sobre o parâmetro quando for especificado, use a seguinte estrutura dentro de uma entrada de métodos de processamento.</span><span class="sxs-lookup"><span data-stu-id="84ccf-138">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a><span data-ttu-id="84ccf-139">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="84ccf-139">See Also</span></span>

<span data-ttu-id="84ccf-140">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="84ccf-140">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
