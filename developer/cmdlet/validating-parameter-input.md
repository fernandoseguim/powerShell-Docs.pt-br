---
title: Validação de parâmetro de entrada | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429832"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="e50a8-102">Validação de entrada de parâmetro</span><span class="sxs-lookup"><span data-stu-id="e50a8-102">Validating Parameter Input</span></span>

<span data-ttu-id="e50a8-103">PowerShell pode validar os argumentos passados para os parâmetros de cmdlet de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="e50a8-103">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="e50a8-104">PowerShell pode validar o comprimento, intervalo e o padrão de caracteres do argumento.</span><span class="sxs-lookup"><span data-stu-id="e50a8-104">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="e50a8-105">Ele pode validar o número de argumentos disponíveis (a contagem).</span><span class="sxs-lookup"><span data-stu-id="e50a8-105">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="e50a8-106">Essas regras de validação são definidas por atributos de validação que são declarados com o atributo de parâmetro em propriedades públicas da classe do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e50a8-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="e50a8-107">Para validar um argumento de parâmetro, o tempo de execução do PowerShell usa as informações fornecidas pelos atributos de validação para confirmar se o valor do parâmetro antes que o cmdlet é executado.</span><span class="sxs-lookup"><span data-stu-id="e50a8-107">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="e50a8-108">Se a entrada de parâmetro não for válida, o usuário recebe uma mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="e50a8-108">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="e50a8-109">Cada parâmetro de validação define uma regra de validação que é imposta pelo PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e50a8-109">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="e50a8-110">PowerShell impõe as regras de validação com base nos seguintes atributos.</span><span class="sxs-lookup"><span data-stu-id="e50a8-110">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="e50a8-111">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="e50a8-111">ValidateCount</span></span>

<span data-ttu-id="e50a8-112">Especifica o número mínimo e máximo de argumentos que aceite um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e50a8-112">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="e50a8-113">Para obter mais informações, consulte [declaração de atributo ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e50a8-113">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="e50a8-114">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="e50a8-114">ValidateLength</span></span>

<span data-ttu-id="e50a8-115">Especifica o número mínimo e máximo de caracteres no argumento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e50a8-115">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="e50a8-116">Para obter mais informações, consulte [declaração de atributo ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e50a8-116">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="e50a8-117">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="e50a8-117">ValidatePattern</span></span>

<span data-ttu-id="e50a8-118">Especifica uma expressão regular que valida o argumento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e50a8-118">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="e50a8-119">Para obter mais informações, consulte [declaração de atributo ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e50a8-119">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="e50a8-120">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="e50a8-120">ValidateRange</span></span>

<span data-ttu-id="e50a8-121">Especifica os valores mínimos e máximo do argumento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e50a8-121">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="e50a8-122">Para obter mais informações, consulte [declaração de atributo ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e50a8-122">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="e50a8-123">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="e50a8-123">ValidateSet</span></span>

<span data-ttu-id="e50a8-124">Especifica os valores válidos para o argumento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e50a8-124">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="e50a8-125">Para obter mais informações, consulte [declaração de atributo ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e50a8-125">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e50a8-126">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="e50a8-126">See Also</span></span>

[<span data-ttu-id="e50a8-127">Como validar a entrada de parâmetro</span><span class="sxs-lookup"><span data-stu-id="e50a8-127">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

<span data-ttu-id="e50a8-128">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="e50a8-128">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
