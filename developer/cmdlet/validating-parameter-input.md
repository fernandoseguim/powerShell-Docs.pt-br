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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858842"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="4be1b-102">Validação de entrada de parâmetro</span><span class="sxs-lookup"><span data-stu-id="4be1b-102">Validating Parameter Input</span></span>

<span data-ttu-id="4be1b-103">Windows PowerShell pode validar os argumentos passados para os parâmetros de cmdlet de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="4be1b-103">Windows PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span> <span data-ttu-id="4be1b-104">Windows PowerShell pode validar o comprimento, intervalo e o padrão de caracteres do argumento.</span><span class="sxs-lookup"><span data-stu-id="4be1b-104">Windows PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span> <span data-ttu-id="4be1b-105">Ele pode validar o número de argumentos disponíveis (a contagem).</span><span class="sxs-lookup"><span data-stu-id="4be1b-105">It can validate the number of arguments available (the count).</span></span> <span data-ttu-id="4be1b-106">Essas regras de validação são definidas por atributos de validação que são declarados com o atributo de parâmetro em propriedades públicas da classe do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4be1b-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="4be1b-107">Para validar um argumento de parâmetro, o tempo de execução do Windows PowerShell usa as informações fornecidas pelos atributos de validação para confirmar se o valor do parâmetro antes que o cmdlet é executado.</span><span class="sxs-lookup"><span data-stu-id="4be1b-107">To validate a parameter argument, the Windows PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span> <span data-ttu-id="4be1b-108">Se a entrada de parâmetro não for válida, o usuário recebe uma mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="4be1b-108">If the parameter input is not valid, the user receives an error message.</span></span> <span data-ttu-id="4be1b-109">Cada parâmetro de validação define uma regra de validação que é imposta pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4be1b-109">Each validation parameter defines a validation rule that is enforced by Windows PowerShell.</span></span>

<span data-ttu-id="4be1b-110">Windows PowerShell impõe as regras de validação com base nos seguintes atributos.</span><span class="sxs-lookup"><span data-stu-id="4be1b-110">Windows PowerShell enforces the validation rules based on the following attributes.</span></span>

<span data-ttu-id="4be1b-111">ValidateCount Especifica o número mínimo e máximo de argumentos que aceite um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4be1b-111">ValidateCount Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span> <span data-ttu-id="4be1b-112">Para obter mais informações sobre a sintaxe usada para declarar esse atributo, consulte [declaração de atributo ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="4be1b-112">For more information about the syntax used to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

<span data-ttu-id="4be1b-113">ValidateLength Especifica o número mínimo e máximo de caracteres no argumento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4be1b-113">ValidateLength Specifies the minimum and maximum number of characters in the parameter argument.</span></span> <span data-ttu-id="4be1b-114">Para obter mais informações sobre a sintaxe usada para declarar esse atributo, consulte [declaração de atributo ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="4be1b-114">For more information about the syntax used to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

<span data-ttu-id="4be1b-115">ValidatePattern Especifica uma expressão regular que valida o argumento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4be1b-115">ValidatePattern Specifies a regular expression that validates the parameter argument.</span></span> <span data-ttu-id="4be1b-116">Para obter mais informações sobre a sintaxe usada para declarar esse atributo, consulte [declaração de atributo ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="4be1b-116">For more information about the syntax used to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

<span data-ttu-id="4be1b-117">ValidateRange Especifica os valores mínimos e máximo do argumento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4be1b-117">ValidateRange Specifies the minimum and maximum values of the parameter argument.</span></span> <span data-ttu-id="4be1b-118">Para obter mais informações sobre a sintaxe usada para declarar esse atributo, consulte [declaração de atributo ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="4be1b-118">For more information about the syntax used to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

<span data-ttu-id="4be1b-119">ValidateSet Especifica os valores válidos para o argumento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4be1b-119">ValidateSet Specifies the valid values for the parameter argument.</span></span> <span data-ttu-id="4be1b-120">Para obter mais informações sobre a sintaxe usada para declarar esse atributo, consulte [declaração de atributo ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="4be1b-120">For more information about the syntax used to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4be1b-121">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="4be1b-121">See Also</span></span>

[<span data-ttu-id="4be1b-122">Como validar a entrada de parâmetro</span><span class="sxs-lookup"><span data-stu-id="4be1b-122">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

<span data-ttu-id="4be1b-123">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="4be1b-123">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
