---
title: Invocar Cmdlets e Scripts dentro de um Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058871"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>Invocar cmdlets e scripts dentro de um cmdlet

Um cmdlet pode invocar outros cmdlets e scripts de dentro da método do cmdlet de processamento de entrada. Isso permite que você adicionar a funcionalidade de scripts e cmdlets existentes para o cmdlet sem reescrever o código.

## <a name="the-invoke-method"></a>A invocação de método

Todos os cmdlets podem invocar um cmdlet existente chamando o [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) método de dentro de uma entrada de processamento, como o método, [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), que é substituído pelo cmdlet. No entanto, você pode chamar apenas esses cmdlets que derivam diretamente de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe. Você não pode chamar um cmdlet que deriva de [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe.

O [System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) método tem as seguintes variantes.

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) essa variante invoca o objeto de cmdlet e retorna uma coleção de objetos do tipo "T".

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) essa variante invoca o objeto de cmdlet e retorna um emumerator com rigidez de tipos. Essa variante permite ao usuário usar os objetos na coleção para executar operações personalizadas.

## <a name="examples"></a>Exemplos

|Exemplo|Descrição|
|-------------|-----------------|
|[Invocar Cmdlets dentro de um Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|Este exemplo mostra como chamar um cmdlet de dentro de outro cmdlet.|
|[Invocando Scripts dentro de um Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md)|Este exemplo mostra como chamar um script que é fornecido para o cmdlet de dentro de outro cmdlet.|

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
