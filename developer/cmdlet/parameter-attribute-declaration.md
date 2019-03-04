---
title: Declaração de atributo de parâmetro | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: a3488d5fb3f7eb3df28d0242d6c39d07145a3c8d
ms.sourcegitcommit: 10c347a8c3dcbf8962295601834f5ba85342a87b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "56863612"
---
# <a name="parameter-attribute-declaration"></a>Declaração de atributo de parâmetro

O atributo de parâmetro identifica uma propriedade pública da classe cmdlet como um parâmetro de cmdlet.

## <a name="syntax"></a>Sintaxe

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>Parâmetros

`Mandatory` ([System. Boolean](/dotnet/api/System.Boolean)) parâmetro nomeado opcional. `True` Indica se que o parâmetro de cmdlet é obrigatório. Se um parâmetro obrigatório não for fornecido quando o cmdlet é invocado, o Windows PowerShell solicitará ao usuário para um valor de parâmetro. O padrão é `false`.

`ParameterSetName` ([System. String](/dotnet/api/System.String)) parâmetro nomeado opcional. Especifica que o parâmetro definido que esse parâmetro de cmdlet pertence. Se nenhum conjunto de parâmetro for especificado, o parâmetro pertence a todos os conjuntos de parâmetros.

`Position` ([System.Integer](/dotnet/api/System.Integer)) parâmetro nomeado opcional. Especifica a posição do parâmetro dentro de um comando do Windows PowerShell.

`ValueFromPipeline` ([System. Boolean](/dotnet/api/System.Boolean)) parâmetro nomeado opcional. `True` indica que o parâmetro de cmdlet obtém seu valor de um objeto de pipeline. Especifique essa palavra-chave se o cmdlet acessa o completo do objeto, não apenas uma propriedade do objeto. O padrão é `false`.

`ValueFromPipelineByPropertyName` ([System. Boolean](/dotnet/api/System.Boolean)) parâmetro nomeado opcional. `True` indica que o parâmetro de cmdlet obtém seu valor de uma propriedade de um objeto de pipeline que tem o mesmo nome ou o mesmo alias como este parâmetro. Por exemplo, se o cmdlet tem um `Name` parâmetro e o objeto de pipeline também tem uma `Name` propriedade, o valor da `Name` propriedade é atribuída ao `Name` parâmetro do cmdlet. O padrão é `false`.

`ValueFromRemainingArguments` ([System. Boolean](/dotnet/api/System.Boolean)) parâmetro nomeado opcional. `True` indica que o parâmetro de cmdlet aceita todos os argumentos restantes passados para o cmdlet. O padrão é `false`.

`HelpMessage` Parâmetro nomeado opcional. Especifica uma breve descrição do parâmetro. Windows PowerShell exibe esta mensagem quando um cmdlet é executado e um parâmetro obrigatório não for especificado.

`HelpMessageBaseName` Parâmetro nomeado opcional. Especifica o local onde residem os identificadores de recurso. Por exemplo, esse parâmetro pode especificar um assembly de recurso que contém mensagens de Ajuda que você deseja localizar.

`HelpMessageResourceId` Parâmetro nomeado opcional. Especifica o identificador de recurso para uma mensagem de Ajuda.

## <a name="remarks"></a>Comentários

- Para obter mais informações sobre como declarar esse atributo, consulte [como declarar parâmetros de Cmdlet](./how-to-declare-cmdlet-parameters.md).

- Um cmdlet pode ter qualquer número de parâmetros. No entanto, para uma melhor experiência de usuário, limite o número de parâmetros.

- Parâmetros devem ser declarados em campos de não estáticos públicos ou propriedades. Parâmetros devem ser declarados em Propriedades. A propriedade deve ter um acessador set públicos e se o `ValueFromPipeline` ou `ValueFromPipelineByPropertyName` palavra-chave for especificado, a propriedade deve ter um acessador get público.

- Quando você especificar parâmetros posicionais, limite o número de parâmetros posicionais em um parâmetro definido para menos de cinco. E, parâmetros posicionais não precisa ser contíguas. Posições 5, 100 e 250 funcionam da mesma maneira posições 0, 1 e 2.

- Quando o `Position` palavra-chave não for especificado, o parâmetro de cmdlet deve ser referenciado por seu nome.

- Quando você usa conjuntos de parâmetros, observe o seguinte:

    - Cada conjunto de parâmetro deve ter pelo menos um parâmetro exclusivo. Cmdlet bom design indica que esse parâmetro exclusivo também é necessário obrigatório se possível. Se seu cmdlet é projetado para ser executado sem parâmetros, o parâmetro unique não pode ser obrigatório.

    - Nenhum conjunto de parâmetros deve conter mais de um parâmetro posicional com a mesma posição.

    - Apenas um parâmetro em um conjunto de parâmetros deve declarar `ValueFromPipeline = true`. Vários parâmetros podem definir `ValueFromPipelineByPropertyName = true`.

    - Vários parâmetros podem definir `ValueFromPipelineByPropertyName = true`.

- Para obter mais informações sobre as diretrizes para nomes de parâmetro, consulte [nomes de parâmetro de Cmdlet](standard-cmdlet-parameter-names-and-types.md).

- O atributo de parâmetro é definido pela [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) classe.

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Nomes de parâmetro de cmdlet](standard-cmdlet-parameter-names-and-types.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
