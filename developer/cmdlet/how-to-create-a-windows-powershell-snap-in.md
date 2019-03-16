---
title: Como criar um Snap-in do PowerShell do Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 43199544dc02ccae4b61053c30d6ed36576adfcf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055930"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a>Como criar um snap-in do Windows PowerShell

Um snap-in do Windows PowerShell fornece um mecanismo para registrar os conjuntos de cmdlets e outro provedor do Windows PowerShell com o shell, estendendo a funcionalidade do shell. Um snap-in do Windows PowerShell pode registrar todos os cmdlets e provedores em um único assembly, ou ele pode registrar uma lista específica de cmdlets e provedores.

Assemblies de snap-in devem ser instalados em um diretório protegido, assim como com outros sistemas operacionais em que eles seriam. Caso contrário, usuários mal-intencionados podem substituir um assembly com código não seguro.

## <a name="windows-powershell-snap-in-classes"></a>Classes de Snap-in do PowerShell do Windows

Todos os Windows PowerShell snap-in de classes derivam a [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) ou [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.

## <a name="examples"></a>Exemplos

[Escrevendo um Snap-in do PowerShell do Windows](./writing-a-windows-powershell-snap-in.md): Este exemplo mostra como criar um snap-in que é usado para registrar todos os cmdlets e provedores em um assembly.

[Escrevendo um Snap-in do PowerShell do Windows personalizado](./writing-a-custom-windows-powershell-snap-in.md): Este exemplo mostra como criar um snap-in padrão que é usado para registrar um conjunto específico de cmdlets e provedores que podem ou não existir em um único assembly.

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)

[System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[Registrar Cmdlets](./registering-cmdlets.md)

[Shell do Windows PowerShell do SDK](../windows-powershell-reference.md)
