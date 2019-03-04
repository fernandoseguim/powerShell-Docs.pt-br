---
title: Como declarar conjuntos de parâmetros | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859692"
---
# <a name="how-to-declare-parameter-sets"></a>Como declarar conjuntos de parâmetros

Este exemplo mostra como definir dois conjuntos de parâmetros quando você declara os parâmetros para um cmdlet. Cada conjunto de parâmetro tem um parâmetro exclusivo e um parâmetro compartilhado que é usado em ambos os conjuntos de parâmetro. Para obter mais informações sobre conjuntos de parâmetros, incluindo como especificar o conjunto de parâmetros padrão, consulte [conjuntos de parâmetros do Cmdlet](./cmdlet-parameter-sets.md).

> [!IMPORTANT]
> Sempre que possível, defina o parâmetro unique de um parâmetro definido como um parâmetro obrigatório. No entanto, se você quiser que seu cmdlet para executar sem especificar nenhum parâmetro, o parâmetro unique pode ser um parâmetro opcional. Por exemplo, o parâmetro unique do `Get-Command` cmdlet é opcional.

## <a name="how-to-define-two-parameter-sets"></a>Como definir dois conjuntos de parâmetros

1. Adicionar o `ParameterSet` palavra-chave para o atributo de parâmetro para o parâmetro unique do primeiro conjunto de parâmetros.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. Adicionar o `ParameterSet` palavra-chave para o atributo de parâmetro para o parâmetro unique do segundo conjunto de parâmetro.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. Para o parâmetro que pertence a ambos os conjuntos de parâmetros, adicione um atributo de parâmetro para cada conjunto de parâmetros e, em seguida, adicione o `ParameterSet` palavra-chave para cada conjunto. Em cada atributo de parâmetro, você pode especificar como esse parâmetro é definido. Um parâmetro pode ser opcional em um conjunto e obrigatórias em outro.

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a>Consulte Também

[Conjuntos de parâmetros do cmdlet](./cmdlet-parameter-sets.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
