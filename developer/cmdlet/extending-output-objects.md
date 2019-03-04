---
title: Estendendo o objeto de saída | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861922"
---
# <a name="extending-output-objects"></a>Estender os objetos de saída

Você pode estender os objetos do .NET Framework que são retornados pelo cmdlets, funções e scripts por meio de tipos de arquivos (. ps1xml). Arquivos de tipos são arquivos baseados em XML que permitem adicionar propriedades e métodos em objetos existentes. Por exemplo, o Windows PowerShell fornece o arquivo Types.ps1xml, que adiciona elementos a vários objetos existentes do .NET Framework. O arquivo Types.ps1xml está localizado no diretório de instalação do Windows PowerShell (`$pshome`). Você pode criar seu próprio arquivo de tipos para ampliar ainda mais esses objetos ou estender a outros objetos. Quando você estende um objeto usando um arquivo de tipos, qualquer instância do objeto é estendida com os novos elementos.

## <a name="extending-the-systemarray-object"></a>Estendendo o objeto Array

O exemplo a seguir mostra como o Windows PowerShell estende o [System. array](/dotnet/api/System.Array) objeto no arquivo Types.ps1xml. Por padrão, [System. array](/dotnet/api/System.Array) objetos têm uma `Length` propriedade que lista o número de objetos na matriz. No entanto, como o "tamanho" do nome não descreve claramente a propriedade, Windows PowerShell adiciona a `Count` propriedade de alias, que exibe o mesmo valor que o `Length` propriedade. O XML a seguir adiciona o `Count` propriedade para o [System. array](/dotnet/api/System.Array) tipo.

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>

```

Para ver essa nova propriedade de alias, use uma [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) comando em qualquer matriz, conforme mostrado no exemplo a seguir.

```powershell
Get-Member -InputObject (1,2,3,4)
```

O comando retorna os resultados a seguir.
```output
Name           MemberType    Definition
----           ----------    ----------
Count          AliasProperty Count = Length
Address        Method        System.Object& Address(Int32 )
Clone          Method        System.Object Clone()
CopyTo         Method        System.Void CopyTo(Array array, Int32 index):
Equals         Method        System.Boolean Equals(Object obj)
Get            Method        System.Object Get(Int32 )
...
Length         Property      System.Int32 Length {get;}
```
Você pode usar o `Count` propriedade ou o `Length` propriedade para determinar quantos objetos estão em uma matriz. Por exemplo:

```powershell
PS> (1, 2, 3, 4).Count
```

```output
4
```

```powershell
PS> (1, 2, 3, 4).Length
```

```output
4
```

## <a name="custom-types-files"></a>Arquivos de tipos personalizados

Para criar um arquivo de tipos personalizados, comece copiando um arquivo de tipos existente. O novo arquivo pode ter qualquer nome, mas ele deve ter uma extensão de nome de arquivo. ps1xml. Quando você copiar o arquivo, você pode colocar o novo arquivo em qualquer diretório acessível ao Windows PowerShell, mas é útil colocar os arquivos no diretório de instalação do Windows PowerShell (`$pshome`) ou em um subdiretório do diretório de instalação.

Para adicionar seus próprios tipos estendidos para o arquivo, adicione um elemento de tipos para cada objeto que você deseja estender. Os tópicos a seguir fornecem exemplos.

- Para obter mais informações sobre como adicionar propriedades e conjuntos de propriedades, consulte [propriedades estendidas](./extending-properties-for-objects.md)

- Para obter mais informações sobre como adicionar métodos, consulte [métodos estendidos](./defining-default-methods-for-objects.md).

- Para obter mais informações sobre como adicionar conjuntos de membros, consulte [estendido membro define](./defining-default-member-sets-for-objects.md).

Depois de definir seus próprios tipos estendidos, use um dos seguintes métodos para disponibilizar seus objetos estendidos:

- Para disponibilizar seu arquivo de tipos estendidos para a sessão atual, use o [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet para adicionar o novo arquivo. Se você quiser que seus tipos para ter precedência sobre os tipos que são definidos em outros tipos de arquivos (incluindo o arquivo ps1xml), use o `PrependData` parâmetro do [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.
- Para disponibilizar seu arquivo de tipos estendidos para todas as futuras sessões, adicione o arquivo de tipos para um módulo, exportar a sessão atual ou adicionar o [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) comando ao seu perfil do Windows PowerShell.

## <a name="signing-types-files"></a>Tipos de arquivos de assinatura

Arquivos de tipos devem ser assinados digitalmente para evitar a violação porque o XML pode incluir os blocos de script. Para obter mais informações sobre como adicionar assinaturas digitais, consulte [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>Consulte Também

[Definir as propriedades padrão para objetos](./extending-properties-for-objects.md)

[Definindo os métodos padrão para objetos](./defining-default-methods-for-objects.md)

[Definindo conjuntos de membro padrão para objetos](./defining-default-member-sets-for-objects.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
