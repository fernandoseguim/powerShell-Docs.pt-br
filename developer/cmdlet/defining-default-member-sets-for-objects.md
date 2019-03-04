---
title: Definindo o membro padrão define objetos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: e8185eb7221a3be0445eddc537dbca89478c74f2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859792"
---
# <a name="defining-default-member-sets-for-objects"></a>Definir os conjuntos de membro padrão para objetos

O conjunto de membros PSStandardMembers é usado pelo Windows PowerShell para definir os conjuntos de propriedades padrão para um objeto. Os conjuntos de propriedades padrão podem ser usados por comandos, como os cmdlets de formatação para exibir somente as propriedades que são definidas pelo conjunto de propriedades. Os conjuntos de propriedades padrão incluem DefaultDisplayProperty, DefaultDisplayPropertySet e DefaultKeyPropertySet. Windows PowerShell ignora todos os outros conjuntos de membros e outros conjuntos de propriedades adicionados ao conjunto de membros PSStandardMembers.

## <a name="member-set-for-systemdiagnosticsprocess"></a>Conjunto de membros para Diagnostics

No exemplo a seguir, o conjunto de membros PSStandardMembers define a propriedade DefaultDisplayPropertySet definida para [Diagnostics](/dotnet/api/System.Diagnostics.Process) objetos. Essa propriedade definida é usada pelas [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.
No exemplo a seguir, o conjunto de membros PSStandardMembers define a propriedade DefaultDisplayPropertySet definida para [Diagnostics](/dotnet/api/System.Diagnostics.Process) objetos. Essa propriedade definida é usada pelas [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.

```xml
<Type>
  <Name>System.Diagnostics.Process</Name>
  <Members>
    <MemberSet>
     <Name>PSStandardMembers</Name>
     <Members>
       <PropertySet>
         <Name>DefaultDisplayPropertySet</Name>
         <ReferencedProperties>
           <Name>Id</Name>
           <Name>Handles</Name>
           <Name>CPU</Name>
           <Name>Name</Name>
         </ReferencedProperties>
      </PropertySet>
    </Members>
  </MemberSet>
```

A saída a seguir mostra as propriedades padrão retornadas pela [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet. Somente o `Id`, `Handles`, `CPU`, e `Name` propriedades são retornadas para cada objeto de processo.
A saída a seguir mostra as propriedades padrão retornadas pela [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet. Somente o `Id`, `Handles`, `CPU`, e `Name` propriedades são retornadas para cada objeto de processo.

```powershell
Get-Process | format-list
```

```output
Id      : 2036
Handles : 27
CPU     :
Name    : AEADISRV

Id      : 272
Handles : 38
CPU     :
Name    : agrsmsvc
...
```

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
