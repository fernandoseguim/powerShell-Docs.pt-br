---
title: Como declarar parâmetros de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059160"
---
# <a name="how-to-declare-cmdlet-parameters"></a>Como declarar parâmetros de cmdlet

Estes exemplos mostram como declarar nomeado, posicional, obrigatória, opcional e parâmetros de opção. Esses exemplos também mostram como definir um alias de parâmetro.

## <a name="how-to-declare-a-named-parameter"></a>Como declarar um parâmetro nomeado

- Defina uma propriedade pública, conforme mostrado no código a seguir. Quando você adiciona o atributo de parâmetro, omita o `Position` palavra-chave do atributo.

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Para obter mais informações sobre o atributo de parâmetro, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-positional-parameter"></a>Como declarar um parâmetro posicional

- Defina uma propriedade pública, conforme mostrado no código a seguir. Quando você adiciona o atributo de parâmetro, defina o `Position` palavra-chave para a posição do argumento. Um valor de 0 indica a primeira posição.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Para obter mais informações sobre o atributo de parâmetro, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-mandatory-parameter"></a>Como declarar um parâmetro obrigatório

- Defina uma propriedade pública, conforme mostrado no código a seguir. Quando você adiciona o atributo de parâmetro, defina as `Mandatory` palavra-chave para `true`.

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Para obter mais informações sobre o atributo de parâmetro, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).

## <a name="how-to-declare-an-optional-parameter"></a>Como declarar um parâmetro opcional

- Defina uma propriedade pública, conforme mostrado no código a seguir. Quando você adiciona o atributo de parâmetro, omita o `Mandatory` palavra-chave.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a>Como declarar um parâmetro de opção

- Definir uma propriedade pública como tipo [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)e, em seguida, declarar o atributo de parâmetro.

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

Para obter mais informações sobre o atributo de parâmetro, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-parameter-with-aliases"></a>Como declarar um parâmetro com Aliases

- Defina uma propriedade pública, conforme mostrado no código a seguir. Adicione um atributo de Alias que lista os aliases para o parâmetro. Neste exemplo, três aliases são definidos para o mesmo parâmetro. O alias primeiro fornece um atalho. Os aliases do segundo e terceiro fornecem nomes que podem ser usados para cenários diferentes.

    ```csharp
    [Alias("UN","Writer","Editor")]
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Para obter mais informações sobre o atributo de Alias, consulte [declaração de atributo de Alias](./alias-attribute-declaration.md).

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)

[Declaração de atributo de parâmetro](./parameter-attribute-declaration.md)

[Declaração de atributo de alias](./alias-attribute-declaration.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
