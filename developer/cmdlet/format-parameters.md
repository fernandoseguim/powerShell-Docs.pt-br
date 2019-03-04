---
title: Formatar parâmetros | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251176"
---
# <a name="format-parameters"></a><span data-ttu-id="745e5-102">Parâmetros de formato</span><span class="sxs-lookup"><span data-stu-id="745e5-102">Format Parameters</span></span>

<span data-ttu-id="745e5-103">A tabela a seguir lista nomes recomendados e funcionalidade para os parâmetros que são usadas para formatar ou para gerar dados.</span><span class="sxs-lookup"><span data-stu-id="745e5-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="745e5-104">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="745e5-104">Parameter</span></span>|<span data-ttu-id="745e5-105">Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="745e5-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="745e5-106">**como**</span><span class="sxs-lookup"><span data-stu-id="745e5-106">**As**</span></span><br><span data-ttu-id="745e5-107">Tipo de dados: Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="745e5-107">Data type: Keyword</span></span>|<span data-ttu-id="745e5-108">Implemente esse parâmetro para especificar o formato de saída do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="745e5-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="745e5-109">Por exemplo, os valores possíveis poderiam ser texto ou Script.</span><span class="sxs-lookup"><span data-stu-id="745e5-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="745e5-110">**binário**</span><span class="sxs-lookup"><span data-stu-id="745e5-110">**Binary**</span></span><br><span data-ttu-id="745e5-111">Tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="745e5-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="745e5-112">Implemente esse parâmetro para indicar que o cmdlet lida com valores binários.</span><span class="sxs-lookup"><span data-stu-id="745e5-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="745e5-113">**Encoding**</span><span class="sxs-lookup"><span data-stu-id="745e5-113">**Encoding**</span></span><br><span data-ttu-id="745e5-114">Tipo de dados: Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="745e5-114">Data type: Keyword</span></span>|<span data-ttu-id="745e5-115">Implemente esse parâmetro para especificar o tipo de codificação com suporte.</span><span class="sxs-lookup"><span data-stu-id="745e5-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="745e5-116">Por exemplo, os valores possíveis poderiam ser ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, bytes e cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="745e5-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="745e5-117">**NewLine**</span><span class="sxs-lookup"><span data-stu-id="745e5-117">**NewLine**</span></span><br><span data-ttu-id="745e5-118">Tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="745e5-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="745e5-119">Implemente esse parâmetro para que os caracteres de nova linha são suportados quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="745e5-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="745e5-120">**ShortName**</span><span class="sxs-lookup"><span data-stu-id="745e5-120">**ShortName**</span></span><br><span data-ttu-id="745e5-121">Tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="745e5-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="745e5-122">Implemente esse parâmetro para que nomes curtos têm suporte quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="745e5-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="745e5-123">**Width**</span><span class="sxs-lookup"><span data-stu-id="745e5-123">**Width**</span></span><br><span data-ttu-id="745e5-124">Tipo de dados: Int32</span><span class="sxs-lookup"><span data-stu-id="745e5-124">Data type: Int32</span></span>|<span data-ttu-id="745e5-125">Implemente esse parâmetro para que o usuário pode especificar a largura do dispositivo de saída.</span><span class="sxs-lookup"><span data-stu-id="745e5-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="745e5-126">**Quebra automática de linha**</span><span class="sxs-lookup"><span data-stu-id="745e5-126">**Wrap**</span></span><br><span data-ttu-id="745e5-127">Tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="745e5-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="745e5-128">Implemente esse parâmetro para que a quebra automática de texto tem suporte quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="745e5-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="745e5-129">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="745e5-129">See Also</span></span>

[<span data-ttu-id="745e5-130">Parâmetros do cmdlet</span><span class="sxs-lookup"><span data-stu-id="745e5-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

<span data-ttu-id="745e5-131">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="745e5-131">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

[<span data-ttu-id="745e5-132">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="745e5-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
