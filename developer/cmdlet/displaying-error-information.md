---
title: Exibindo informações de erro | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858272"
---
# <a name="displaying-error-information"></a>Exibir informações de erro

Este tópico discute as maneiras em que os usuários podem exibir informações de erro.

Quando seu cmdlet encontra um erro, a apresentação das informações de erro serão, por padrão, se parecer com a seguinte saída de erro.

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

No entanto, os usuários podem exibir erros por categoria, definindo o `$ErrorView` variável para `"CategoryView"`. Modo de exibição de categoria exibe informações específicas do registro de erro em vez de uma descrição de texto livre do erro. Este modo de exibição pode ser útil se você tiver uma longa lista de erros de verificação. No modo de exibição de categoria, a mensagem de erro anterior é exibida da seguinte maneira.

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

Para obter mais informações sobre categorias de erro, consulte [registros de erros do Windows PowerShell](./windows-powershell-error-records.md).

## <a name="see-also"></a>Consulte Também

[Registros de erro do PowerShell do Windows](./windows-powershell-error-records.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
