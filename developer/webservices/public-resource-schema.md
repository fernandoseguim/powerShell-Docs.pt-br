---
title: Esquema de recurso público | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: c7e20ff0f36e8cab2d414ff2e5924b3359ad9c60
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057234"
---
# <a name="public-resource-schema"></a>Esquema de recursos públicos

OData de gerenciamento usa o MOF para definir recursos e suas propriedades. As propriedades de uma entidade OData de gerenciamento correspondem diretamente às propriedades do tipo gerenciado retornado pelo cmdlet subjacente.

## <a name="defining-a-resource"></a>Definição de um recurso

Cada recurso corresponde a um objeto retornado por um cmdlet do Windows PowerShell. O arquivo MOF de recurso público, você define um recurso, declarando uma classe. A classe consiste em propriedades que correspondem às propriedades do objeto. Por exemplo, no exemplo a seguir, o [Diagnostics](/dotnet/api/System.Diagnostics.Process) classe é representado pela seguinte MOF.

```csharp
class PswsTest_Process
{
    [Key] SInt32 Id;
    [Required] SInt32 BasePriority;
    [Required] SInt32 HandleCount;
    [Required] string MachineName;
    [Required] SInt32 MainWindowHandle;

    ...
};
```

Cada nome de propriedade é precedido por um tipo de dados. Neste exemplo, os tipos de dados correspondem aos tipos de dados primitivos do CLR no .NET Framework, mas propriedades também podem ser referências a outros recursos ou tipos complexos, ambos descritos posteriormente.

O `Key` qualificador indica que uma propriedade é usada para identificar exclusivamente uma instância do recurso. Um recurso pode ter mais de uma chave.

O `Required` qualificador indica que a propriedade é necessária. Se uma propriedade é rotulada com o `Key` qualificador, ele é considerado necessário e o `Required` qualificador não é necessário.

### <a name="complex-data-types"></a>Tipos de dados complexos

Propriedades de entidades podem ter tipos de dados complexos. Tipos de dados complexos são tipos que são compostos de outros tipos, semelhantes a structs na linguagem de programação C. Um tipo complexo é declarado no arquivo MOF como uma classe com o `ComplexType` qualificador, como no exemplo a seguir.

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

Para declarar uma propriedade de entidade como um tipo complexo, declare-o como uma `string` tipo com o `EmbeddedInstance` qualificador, incluindo o nome do tipo complexo. O exemplo a seguir mostra a declaração de uma propriedade do `PswsTest_ProcessModule` tipo declarado no exemplo anterior.

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>Associação de entidades

Você pode associar duas entidades usando os qualificadores de associação e AssociationClass. Para obter mais informações, consulte [associando entidades de OData de gerenciamento](./associating-management-odata-entities.md).

### <a name="derived-types"></a>Tipos derivados

Você pode derivar um tipo de outro tipo. O tipo derivado herda todas as propriedades do tipo do qual ela deriva além de quaisquer propriedades derivadas explicitamente. O exemplo a seguir mostra uma declaração de tipo e, em seguida, uma declaração de dois tipos derivados desse tipo.

```csharp
Class Product {

    [Key] String ProductName;

};

Class DairyProduct : Product {

    Uint16 PercentFat;
};
Class POPProduct : Product {

    Boolean IsCarbonated;
};
```