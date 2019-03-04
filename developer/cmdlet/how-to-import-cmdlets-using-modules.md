---
title: Como importar os Cmdlets que usam módulos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859142"
---
# <a name="how-to-import-cmdlets-using-modules"></a>Como importar cmdlets por meio de módulos

Este tópico descreve como importar os cmdlets para uma sessão do Windows PowerShell usando um módulo binário.

> [!NOTE]
> Os membros de módulos podem incluir cmdlets, provedores, funções, variáveis, aliases e muito mais. Snap-ins pode conter apenas os cmdlets e provedores.

## <a name="how-to-load-cmdlets-using-a-module"></a>Como carregar os cmdlets usando um módulo

1. Crie uma pasta de módulo que tem o mesmo nome que o arquivo do assembly no qual os cmdlets são implementados. Neste procedimento, a pasta de módulo é criada no `system32` pasta.

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. Certifique-se de que o `PSModulePath` variável de ambiente inclui o caminho para a nova pasta de módulo. Por padrão, a pasta do sistema já foi adicionada para o `PSModulePath` variável de ambiente.

3. Copie o assembly de cmdlet para a pasta de módulo.

4. Execute o seguinte comando para adicionar os cmdlets para a sessão:

   `import-module [Module_Name]`

   Esse procedimento pode ser usado para testar seus cmdlets. Ele adiciona todos os cmdlets no assembly para a sessão. Para obter mais informações sobre os módulos, os diferentes tipos de módulos, as diferentes maneiras de carregar módulos e como restringir os elementos de um módulo são exportados, consulte [escrevendo um módulo do Windows PowerShell](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)

[Instalar os módulos](../module/installing-a-powershell-module.md)