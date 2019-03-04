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
# <a name="extending-output-objects"></a><span data-ttu-id="02057-102">Estender os objetos de saída</span><span class="sxs-lookup"><span data-stu-id="02057-102">Extending Output Objects</span></span>

<span data-ttu-id="02057-103">Você pode estender os objetos do .NET Framework que são retornados pelo cmdlets, funções e scripts por meio de tipos de arquivos (. ps1xml).</span><span class="sxs-lookup"><span data-stu-id="02057-103">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="02057-104">Arquivos de tipos são arquivos baseados em XML que permitem adicionar propriedades e métodos em objetos existentes.</span><span class="sxs-lookup"><span data-stu-id="02057-104">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="02057-105">Por exemplo, o Windows PowerShell fornece o arquivo Types.ps1xml, que adiciona elementos a vários objetos existentes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="02057-105">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="02057-106">O arquivo Types.ps1xml está localizado no diretório de instalação do Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="02057-106">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="02057-107">Você pode criar seu próprio arquivo de tipos para ampliar ainda mais esses objetos ou estender a outros objetos.</span><span class="sxs-lookup"><span data-stu-id="02057-107">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="02057-108">Quando você estende um objeto usando um arquivo de tipos, qualquer instância do objeto é estendida com os novos elementos.</span><span class="sxs-lookup"><span data-stu-id="02057-108">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="02057-109">Estendendo o objeto Array</span><span class="sxs-lookup"><span data-stu-id="02057-109">Extending the System.Array Object</span></span>

<span data-ttu-id="02057-110">O exemplo a seguir mostra como o Windows PowerShell estende o [System. array](/dotnet/api/System.Array) objeto no arquivo Types.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="02057-110">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="02057-111">Por padrão, [System. array](/dotnet/api/System.Array) objetos têm uma `Length` propriedade que lista o número de objetos na matriz.</span><span class="sxs-lookup"><span data-stu-id="02057-111">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="02057-112">No entanto, como o "tamanho" do nome não descreve claramente a propriedade, Windows PowerShell adiciona a `Count` propriedade de alias, que exibe o mesmo valor que o `Length` propriedade.</span><span class="sxs-lookup"><span data-stu-id="02057-112">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="02057-113">O XML a seguir adiciona o `Count` propriedade para o [System. array](/dotnet/api/System.Array) tipo.</span><span class="sxs-lookup"><span data-stu-id="02057-113">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

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

<span data-ttu-id="02057-114">Para ver essa nova propriedade de alias, use uma [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) comando em qualquer matriz, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="02057-114">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="02057-115">O comando retorna os resultados a seguir.</span><span class="sxs-lookup"><span data-stu-id="02057-115">The command returns the following results.</span></span>
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
<span data-ttu-id="02057-116">Você pode usar o `Count` propriedade ou o `Length` propriedade para determinar quantos objetos estão em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="02057-116">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="02057-117">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="02057-117">For example:</span></span>

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

## <a name="custom-types-files"></a><span data-ttu-id="02057-118">Arquivos de tipos personalizados</span><span class="sxs-lookup"><span data-stu-id="02057-118">Custom Types Files</span></span>

<span data-ttu-id="02057-119">Para criar um arquivo de tipos personalizados, comece copiando um arquivo de tipos existente.</span><span class="sxs-lookup"><span data-stu-id="02057-119">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="02057-120">O novo arquivo pode ter qualquer nome, mas ele deve ter uma extensão de nome de arquivo. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="02057-120">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="02057-121">Quando você copiar o arquivo, você pode colocar o novo arquivo em qualquer diretório acessível ao Windows PowerShell, mas é útil colocar os arquivos no diretório de instalação do Windows PowerShell (`$pshome`) ou em um subdiretório do diretório de instalação.</span><span class="sxs-lookup"><span data-stu-id="02057-121">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="02057-122">Para adicionar seus próprios tipos estendidos para o arquivo, adicione um elemento de tipos para cada objeto que você deseja estender.</span><span class="sxs-lookup"><span data-stu-id="02057-122">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="02057-123">Os tópicos a seguir fornecem exemplos.</span><span class="sxs-lookup"><span data-stu-id="02057-123">The following topics provide examples.</span></span>

- <span data-ttu-id="02057-124">Para obter mais informações sobre como adicionar propriedades e conjuntos de propriedades, consulte [propriedades estendidas](./extending-properties-for-objects.md)</span><span class="sxs-lookup"><span data-stu-id="02057-124">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="02057-125">Para obter mais informações sobre como adicionar métodos, consulte [métodos estendidos](./defining-default-methods-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="02057-125">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="02057-126">Para obter mais informações sobre como adicionar conjuntos de membros, consulte [estendido membro define](./defining-default-member-sets-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="02057-126">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="02057-127">Depois de definir seus próprios tipos estendidos, use um dos seguintes métodos para disponibilizar seus objetos estendidos:</span><span class="sxs-lookup"><span data-stu-id="02057-127">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="02057-128">Para disponibilizar seu arquivo de tipos estendidos para a sessão atual, use o [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet para adicionar o novo arquivo.</span><span class="sxs-lookup"><span data-stu-id="02057-128">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="02057-129">Se você quiser que seus tipos para ter precedência sobre os tipos que são definidos em outros tipos de arquivos (incluindo o arquivo ps1xml), use o `PrependData` parâmetro do [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="02057-129">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="02057-130">Para disponibilizar seu arquivo de tipos estendidos para todas as futuras sessões, adicione o arquivo de tipos para um módulo, exportar a sessão atual ou adicionar o [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) comando ao seu perfil do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="02057-130">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="02057-131">Tipos de arquivos de assinatura</span><span class="sxs-lookup"><span data-stu-id="02057-131">Signing Types Files</span></span>

<span data-ttu-id="02057-132">Arquivos de tipos devem ser assinados digitalmente para evitar a violação porque o XML pode incluir os blocos de script.</span><span class="sxs-lookup"><span data-stu-id="02057-132">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="02057-133">Para obter mais informações sobre como adicionar assinaturas digitais, consulte [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span><span class="sxs-lookup"><span data-stu-id="02057-133">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="02057-134">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="02057-134">See Also</span></span>

[<span data-ttu-id="02057-135">Definir as propriedades padrão para objetos</span><span class="sxs-lookup"><span data-stu-id="02057-135">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="02057-136">Definindo os métodos padrão para objetos</span><span class="sxs-lookup"><span data-stu-id="02057-136">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="02057-137">Definindo conjuntos de membro padrão para objetos</span><span class="sxs-lookup"><span data-stu-id="02057-137">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

<span data-ttu-id="02057-138">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="02057-138">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
