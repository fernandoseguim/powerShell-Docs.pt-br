---
title: Como adicionar parâmetros dinâmicos para um tópico de Ajuda do provedor | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859872"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="31b42-102">Como adicionar parâmetros dinâmicos a um tópico de ajuda do provedor</span><span class="sxs-lookup"><span data-stu-id="31b42-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="31b42-103">Esta seção explica como popular o **parâmetros dinâmicos** seção de um tópico de Ajuda do provedor.</span><span class="sxs-lookup"><span data-stu-id="31b42-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="31b42-104">*Parâmetros dinâmicos* são parâmetros de um cmdlet ou função que estão disponíveis apenas em condições de especificadas.</span><span class="sxs-lookup"><span data-stu-id="31b42-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="31b42-105">Os parâmetros dinâmicos que estão documentados em um tópico de Ajuda do provedor são os parâmetros dinâmicos que adiciona o provedor para o cmdlet ou função quando o cmdlet ou função é usada na unidade de provedor.</span><span class="sxs-lookup"><span data-stu-id="31b42-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="31b42-106">Parâmetros dinâmicos também podem ser documentados na Ajuda do cmdlet personalizado para um provedor.</span><span class="sxs-lookup"><span data-stu-id="31b42-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="31b42-107">Ao escrever a Ajuda do provedor e a Ajuda do cmdlet personalizado para um provedor, inclua a documentação de parâmetro dinâmico em ambos os documentos.</span><span class="sxs-lookup"><span data-stu-id="31b42-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span> <span data-ttu-id="31b42-108">Para obter mais informações sobre a Ajuda do cmdlet personalizado, consulte [escrita Windows PowerShell Cmdlet ajuda personalizada para provedores de](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span><span class="sxs-lookup"><span data-stu-id="31b42-108">For more information about custom cmdlet help, see [Writing Windows PowerShell Custom Cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span></span>

<span data-ttu-id="31b42-109">Se um provedor não implementa nenhum parâmetro dinâmico, o tópico de Ajuda do provedor contém um vazio `DynamicParameters` elemento.</span><span class="sxs-lookup"><span data-stu-id="31b42-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="31b42-110">Para adicionar parâmetros dinâmicos</span><span class="sxs-lookup"><span data-stu-id="31b42-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="31b42-111">No *AssemblyName*help.xml. dll do arquivo, dentro de `providerHelp` elemento, adicionar um `DynamicParameters` elemento.</span><span class="sxs-lookup"><span data-stu-id="31b42-111">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="31b42-112">O `DynamicParameters` elemento deve aparecer após o `Tasks` elemento e antes do `RelatedLinks` elemento.</span><span class="sxs-lookup"><span data-stu-id="31b42-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="31b42-113">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="31b42-113">For example:</span></span>

    ```xml
    <providerHelp>
        <Tasks>
        </Tasks>
        <DynamicParameters>
        </DynamicParameters>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

   <span data-ttu-id="31b42-114">Se o provedor não implementa nenhum parâmetro dinâmico, o `DynamicParameters` elemento pode estar vazio.</span><span class="sxs-lookup"><span data-stu-id="31b42-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="31b42-115">Dentro de `DynamicParameters` elemento para cada parâmetro dinâmico, adicione um `DynamicParameter` elemento.</span><span class="sxs-lookup"><span data-stu-id="31b42-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="31b42-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="31b42-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="31b42-117">Em cada `DynamicParameter` elemento, adicione uma `Name` e `CmdletSupported` elemento.</span><span class="sxs-lookup"><span data-stu-id="31b42-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="31b42-118">Nome do elemento</span><span class="sxs-lookup"><span data-stu-id="31b42-118">Element Name</span></span>|<span data-ttu-id="31b42-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="31b42-119">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="31b42-120">Nome</span><span class="sxs-lookup"><span data-stu-id="31b42-120">Name</span></span>|<span data-ttu-id="31b42-121">Especifica o nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="31b42-121">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="31b42-122">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="31b42-122">CmdletSupported</span></span>|<span data-ttu-id="31b42-123">Especifica os cmdlets no qual o parâmetro é válido.</span><span class="sxs-lookup"><span data-stu-id="31b42-123">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="31b42-124">Digite uma lista separada por vírgulas de nomes de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="31b42-124">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="31b42-125">Por exemplo, os documentos XML a seguir a `Encoding` parâmetro dinâmico que adiciona o provedor de sistema de arquivos do Windows PowerShell para o `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="31b42-125">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="31b42-126">Em cada `DynamicParameter` elemento, adicionar um `Type` elemento.</span><span class="sxs-lookup"><span data-stu-id="31b42-126">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="31b42-127">O `Type` elemento é um contêiner para o `Name` elemento que contém o tipo de .NET do valor do parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="31b42-127">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="31b42-128">Por exemplo, o XML a seguir mostra que o tipo de .NET do `Encoding` parâmetro dinâmico é o [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeração.</span><span class="sxs-lookup"><span data-stu-id="31b42-128">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
    ...
    </DynamicParameters>
    ```

5. <span data-ttu-id="31b42-129">Adicionar o `Description` elemento, que contém uma breve descrição do parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="31b42-129">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="31b42-130">Ao redigir a descrição, use as diretrizes prescritas para todos os parâmetros de cmdlet na [como adicionar informações de parâmetro](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="31b42-130">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="31b42-131">Por exemplo, o XML a seguir inclui a descrição do `Encoding` parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="31b42-131">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
            <Description> Specifies the encoding of the output file that contains the content. </Description>
    ...
    </DynamicParameters>
    ```

6. <span data-ttu-id="31b42-132">Adicionar o `PossibleValues` elemento e seus elementos filho.</span><span class="sxs-lookup"><span data-stu-id="31b42-132">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="31b42-133">Juntos, esses elementos descrevem os valores do parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="31b42-133">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="31b42-134">Esse elemento foi projetado para valores enumerados.</span><span class="sxs-lookup"><span data-stu-id="31b42-134">This element is designed for enumerated values.</span></span> <span data-ttu-id="31b42-135">Se o parâmetro dinâmico não aceita um valor, tal como acontece com um parâmetro de opção ou os valores não podem ser enumerados, adicione um vazio `PossibleValues` elemento.</span><span class="sxs-lookup"><span data-stu-id="31b42-135">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="31b42-136">A tabela a seguir lista e descreve o `PossibleValues` elemento e seus elementos filho.</span><span class="sxs-lookup"><span data-stu-id="31b42-136">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="31b42-137">Nome do elemento</span><span class="sxs-lookup"><span data-stu-id="31b42-137">Element Name</span></span>|<span data-ttu-id="31b42-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="31b42-138">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="31b42-139">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="31b42-139">PossibleValues</span></span>|<span data-ttu-id="31b42-140">Esse elemento é um contêiner.</span><span class="sxs-lookup"><span data-stu-id="31b42-140">This element is a container.</span></span> <span data-ttu-id="31b42-141">Seus elementos filho são descritos abaixo.</span><span class="sxs-lookup"><span data-stu-id="31b42-141">Its child elements are described below.</span></span> <span data-ttu-id="31b42-142">Adicione um `PossibleValues` elemento para cada tópico de Ajuda do provedor.</span><span class="sxs-lookup"><span data-stu-id="31b42-142">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="31b42-143">O elemento pode estar vazio.</span><span class="sxs-lookup"><span data-stu-id="31b42-143">The element can be empty.</span></span>|
   |<span data-ttu-id="31b42-144">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="31b42-144">PossibleValue</span></span>|<span data-ttu-id="31b42-145">Esse elemento é um contêiner.</span><span class="sxs-lookup"><span data-stu-id="31b42-145">This element is a container.</span></span> <span data-ttu-id="31b42-146">Seus elementos filho são descritos abaixo.</span><span class="sxs-lookup"><span data-stu-id="31b42-146">Its child elements are described below.</span></span> <span data-ttu-id="31b42-147">Adicione um `PossibleValue` elemento para cada valor do parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="31b42-147">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="31b42-148">Valor</span><span class="sxs-lookup"><span data-stu-id="31b42-148">Value</span></span>|<span data-ttu-id="31b42-149">Especifica o nome do valor.</span><span class="sxs-lookup"><span data-stu-id="31b42-149">Specifies the value name.</span></span>|
   |<span data-ttu-id="31b42-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="31b42-150">Description</span></span>|<span data-ttu-id="31b42-151">Esse elemento contém um `Para` elemento.</span><span class="sxs-lookup"><span data-stu-id="31b42-151">This element contains a `Para` element.</span></span> <span data-ttu-id="31b42-152">O texto a `Para` elemento descreve o valor que é nomeado no `Value` elemento.</span><span class="sxs-lookup"><span data-stu-id="31b42-152">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="31b42-153">Por exemplo, o XML a seguir mostra uma `PossibleValue` elemento o `Encoding` parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="31b42-153">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
    ...
            <Description> Specifies the encoding of the output file that contains the content. </Description>
            <PossibleValues>
                <PossibleValue>
                    <Value> ASCII </Value>
                    <Description>
                        <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                    </Description>
                </PossibleValue>
    ...
            </PossibleValues>
    </DynamicParameters>
    ```

## <a name="example"></a><span data-ttu-id="31b42-154">Exemplo</span><span class="sxs-lookup"><span data-stu-id="31b42-154">Example</span></span>

<span data-ttu-id="31b42-155">A exemplo a seguir mostra a `DynamicParameters` elemento o `Encoding` parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="31b42-155">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

```xml
<DynamicParameters/>
    <DynamicParameter>
        <Name> Encoding </Name>
        <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
        <Type>
            <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
        <Type>
        <Description> Specifies the encoding of the output file that contains the content. </Description>
        <PossibleValues>
            <PossibleValue>
                <Value> ASCII </Value>
                <Description>
                    <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                </Description>
            </PossibleValue>
            <PossibleValue>
                <Value> Unicode </Value>
                <Description>
                    <para> Encodes in UTF-16 format using the little-endian byte order. </para>
                </Description>
            </PossibleValue>
        </PossibleValues>
</DynamicParameters>
```