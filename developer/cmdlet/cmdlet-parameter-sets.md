---
title: Define um parâmetro de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857262"
---
# <a name="cmdlet-parameter-sets"></a>Conjuntos de parâmetros do cmdlet

Windows PowerShell usa conjuntos de parâmetros para que você possa escrever um único cmdlet que pode executar ações diferentes para diferentes cenários. Conjuntos de parâmetros permitem que você exponha diferentes parâmetros para o usuário e para retornar informações diferentes com base nos parâmetros especificados pelo usuário.

## <a name="examples-of-parameter-sets"></a>Exemplos de conjuntos de parâmetros

Por exemplo, o `Get-EventLog` cmdlet (fornecido pelo Windows PowerShell) retorna informações diferentes dependendo se o usuário Especifica a `List` ou `LogName` parâmetro. Se o `List` parâmetro for especificado, o cmdlet retorna informações sobre os arquivos de log em si, mas não as informações de evento que eles contêm. Se o `LogName` parâmetro for especificado, o cmdlet retorna informações sobre os eventos em um log de eventos específico. O `List` e `LogName` parâmetros identificam dois conjuntos de parâmetros separado.

## <a name="unique-parameter"></a>Parâmetro exclusivo

Cada conjunto de parâmetros deve ter um parâmetro exclusivo que o tempo de execução do Windows PowerShell pode usar para expor o conjunto de parâmetros apropriado. Se possível, o parâmetro unique deve ser um parâmetro obrigatório. Quando um parâmetro é obrigatório, o usuário é forçado para especificar o parâmetro e o tempo de execução do Windows PowerShell pode usar esse parâmetro para identificar o parâmetro definido para usar. O parâmetro unique não pode ser obrigatório se o cmdlet foi projetado para ser executado sem especificar nenhum parâmetro.

## <a name="multiple-parameter-sets"></a>Vários conjuntos de parâmetros

Na ilustração a seguir, a coluna esquerda mostra três conjuntos de parâmetro válido. Parâmetro um é exclusivo para o primeiro conjunto de parâmetros, parâmetro B é exclusivo para o segundo parâmetro definido e parâmetro C é exclusivo para o terceiro conjunto de parâmetros. No entanto, na coluna à direita, os conjuntos de parâmetros não tem um parâmetro exclusivo.

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>Requisitos do conjunto de parâmetros

Os seguintes requisitos se aplicam a todos os conjuntos de parâmetros.

- Cada conjunto de parâmetro deve ter pelo menos um parâmetro exclusivo. Se possível, torne este parâmetro um parâmetro obrigatório.

- Um conjunto de parâmetros que contém vários parâmetros posicionais deve definir posições exclusivas para cada parâmetro. Não há dois parâmetros posicionais podem especificar a mesma posição.

- Apenas um parâmetro em um conjunto pode declarar o `ValueFromPipeline` palavra-chave com um valor de `true`. Vários parâmetros podem definir a `ValueFromPipelineByPropertyName` palavra-chave com um valor de `true`.

- Se nenhum conjunto de parâmetro for especificado para um parâmetro, o parâmetro pertence a todos os conjuntos de parâmetros.

## <a name="default-parameter-sets"></a>Conjuntos de parâmetros padrão

Quando vários conjuntos de parâmetros são definidos, você pode usar o `DefaultParameterSetName` palavra-chave do atributo Cmdlet para especificar o conjunto de parâmetros padrão. Windows PowerShell usa o parâmetro padrão definido se não é possível determinar o parâmetro definido para usar com base nas informações fornecidas pelo comando. Para obter mais informações sobre o atributo de Cmdlet, consulte [declaração de atributo do Cmdlet](./cmdlet-attribute-declaration.md).

## <a name="declaring-parameter-sets"></a>Declarando conjuntos de parâmetros

Para criar um conjunto de parâmetros, você deve especificar o `ParameterSetName` palavra-chave quando você declara o atributo de parâmetro para cada parâmetro no conjunto de parâmetros. Para parâmetros que pertencem a vários conjuntos de parâmetros, adicione um atributo de parâmetro para cada conjunto de parâmetros. Isso permite que você defina o parâmetro de modo diferente para cada conjunto de parâmetros. Por exemplo, você pode definir um parâmetro como opcional em outra e obrigatória em um conjunto. No entanto, cada conjunto de parâmetros deve conter um parâmetro exclusivo.

No exemplo a seguir, o `UserName` parâmetro é o parâmetro unique do conjunto de parâmetros Test01 e o `ComputerName` parâmetro é o parâmetro unique de conjunto de parâmetros Test02. O `SharedParam` parâmetro pertence aos dois conjuntos e é obrigatório para o parâmetro de Test01 definido, mas opcional para o conjunto de parâmetros Test02.

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```