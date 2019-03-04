---
title: Como validar uma contagem de argumento | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateCount attribute, example
ms.assetid: 4e6b6ac4-1003-4e7e-9d4a-9f1cf74fc4af
caps.latest.revision: 8
ms.openlocfilehash: b6ddb8185f21a65b2e3142ebb640962047e11763
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859132"
---
# <a name="how-to-validate-an-argument-count"></a>Como validar uma contagem de argumentos

Este exemplo mostra como especificar uma regra de validação que o tempo de execução do Windows PowerShell pode usar para verificar o número de argumentos (a contagem) que aceita um parâmetro antes que o cmdlet é executado. Você pode definir essa regra de validação ao declarar o atributo ValidateCount.

> [!NOTE]
> Para obter mais informações sobre a classe que define esse atributo, consulte [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).

## <a name="to-validate-an-argument-count"></a>Para validar uma contagem de argumento

- Adicione o atributo de validação, conforme mostrado no código a seguir. Este exemplo especifica que o parâmetro aceitará um argumento ou até três argumentos.

    ```csharp
    [ValidateCount(1, 3)]
    [Parameter(Position = 0, Mandatory = true)]
    public string[] UserNames
    {
      get { return userNames; }
      set { userNames = value; }
    }

    private string[] userNames;
    ```

Para obter mais informações sobre como declarar esse atributo, consulte [declaração de atributo ValidateCount](./validatecount-attribute-declaration.md).

## <a name="see-also"></a>Consulte Também

[Declaração de atributo ValidateCount](./validatecount-attribute-declaration.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
