---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: O objeto ISEFile
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: a1fbd48e872684cc578adb03f52430eabdc54c2c
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefile-object"></a><span data-ttu-id="4f803-103">O objeto ISEFile</span><span class="sxs-lookup"><span data-stu-id="4f803-103">The ISEFile Object</span></span>
  <span data-ttu-id="4f803-104">Um objeto **ISEFile** representa um arquivo no ISE (Ambiente de Script Integrado) do Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="4f803-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="4f803-105">É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="4f803-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="4f803-106">Este tópico lista os métodos e as propriedades do membro.</span><span class="sxs-lookup"><span data-stu-id="4f803-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="4f803-107">O **$psISE.CurrentFile** e os arquivos da coleção de arquivos em uma guia do PowerShell são todas as instâncias da classe Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="4f803-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="4f803-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="4f803-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="4f803-109">Save\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="4f803-109">Save\( \[saveEncoding\] \)</span></span>
  <span data-ttu-id="4f803-110">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4f803-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4f803-111">Salva o arquivo no disco.</span><span class="sxs-lookup"><span data-stu-id="4f803-111">Saves the file to disk.</span></span>

 <span data-ttu-id="4f803-112">**\[saveEncoding\]** – [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) opcional Um parâmetro opcional de codificação de caracteres a ser usado para o arquivo salvo.</span><span class="sxs-lookup"><span data-stu-id="4f803-112">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="4f803-113">O valor padrão é **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="4f803-113">The default value is **UTF8**.</span></span>

 <span data-ttu-id="4f803-114">**Exceções**</span><span class="sxs-lookup"><span data-stu-id="4f803-114">**Exceptions**</span></span>
 -   <span data-ttu-id="4f803-115">**System.IO.IOException**: não foi possível salvar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="4f803-115">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="4f803-116">SaveAs\(filename, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="4f803-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>
  <span data-ttu-id="4f803-117">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4f803-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4f803-118">Salva o arquivo com o nome de arquivo e codificação especificados.</span><span class="sxs-lookup"><span data-stu-id="4f803-118">Saves the file with the specified file name and encoding.</span></span>

 <span data-ttu-id="4f803-119">**filename** – cadeia de caracteres, o nome a ser usado para salvar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="4f803-119">**filename** - String The name to be used to save the file.</span></span>

 <span data-ttu-id="4f803-120">**\[saveEncoding\]** – [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) opcional Um parâmetro opcional de codificação de caracteres a ser usado para o arquivo salvo.</span><span class="sxs-lookup"><span data-stu-id="4f803-120">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="4f803-121">O valor padrão é **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="4f803-121">The default value is **UTF8**.</span></span>

 <span data-ttu-id="4f803-122">**Exceções**</span><span class="sxs-lookup"><span data-stu-id="4f803-122">**Exceptions**</span></span>
 -   <span data-ttu-id="4f803-123">**System.ArgumentNullException**: o parâmetro **filename** é nulo.</span><span class="sxs-lookup"><span data-stu-id="4f803-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>

- <span data-ttu-id="4f803-124">**System.ArgumentException**: o parâmetro **filename** está vazio.</span><span class="sxs-lookup"><span data-stu-id="4f803-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>

- <span data-ttu-id="4f803-125">**System.IO.IOException**: não foi possível salvar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="4f803-125">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a><span data-ttu-id="4f803-126">Propriedades</span><span class="sxs-lookup"><span data-stu-id="4f803-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="4f803-127">DisplayName</span><span class="sxs-lookup"><span data-stu-id="4f803-127">DisplayName</span></span>
  <span data-ttu-id="4f803-128">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4f803-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="4f803-129">A propriedade somente leitura que obtém a cadeia que contém o nome de exibição deste arquivo.</span><span class="sxs-lookup"><span data-stu-id="4f803-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="4f803-130">O nome é mostrado na guia **Arquivo** na parte superior do editor.</span><span class="sxs-lookup"><span data-stu-id="4f803-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="4f803-131">A presença de um asterisco \(\*\) ao final do nome indica que o arquivo tem alterações que não foram salvas.</span><span class="sxs-lookup"><span data-stu-id="4f803-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

### <a name="editor"></a><span data-ttu-id="4f803-132">Editor</span><span class="sxs-lookup"><span data-stu-id="4f803-132">Editor</span></span>
  <span data-ttu-id="4f803-133">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4f803-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4f803-134">A propriedade somente leitura que obtém o [objeto editor](The-ISEEditor-Object.md) usado para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="4f803-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

### <a name="encoding"></a><span data-ttu-id="4f803-135">Codificando</span><span class="sxs-lookup"><span data-stu-id="4f803-135">Encoding</span></span>
  <span data-ttu-id="4f803-136">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4f803-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4f803-137">A propriedade somente leitura que obtém a codificação original do arquivo.</span><span class="sxs-lookup"><span data-stu-id="4f803-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="4f803-138">Este é um objeto **System.Text.Encoding**.</span><span class="sxs-lookup"><span data-stu-id="4f803-138">This is a **System.Text.Encoding** object.</span></span>

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

### <a name="fullpath"></a><span data-ttu-id="4f803-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="4f803-139">FullPath</span></span>
  <span data-ttu-id="4f803-140">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4f803-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4f803-141">A propriedade somente leitura que obtém a cadeia de caracteres que especifica o caminho completo do arquivo aberto.</span><span class="sxs-lookup"><span data-stu-id="4f803-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

### <a name="issaved"></a><span data-ttu-id="4f803-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="4f803-142">IsSaved</span></span>
  <span data-ttu-id="4f803-143">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4f803-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4f803-144">A propriedade Boolean somente leitura que retornará **$true** se o arquivo foi salvo depois de ter sido modificado pela última vez.</span><span class="sxs-lookup"><span data-stu-id="4f803-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

### <a name="isuntitled"></a><span data-ttu-id="4f803-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="4f803-145">IsUntitled</span></span>
  <span data-ttu-id="4f803-146">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4f803-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4f803-147">A propriedade somente leitura que retornará **$true** se o arquivo nunca recebeu um título.</span><span class="sxs-lookup"><span data-stu-id="4f803-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a><span data-ttu-id="4f803-148">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="4f803-148">See Also</span></span>
- [<span data-ttu-id="4f803-149">O ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="4f803-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md) 
- [<span data-ttu-id="4f803-150">O modelo de objeto de script do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4f803-150">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="4f803-151">Referência de modelo de objeto do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4f803-151">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="4f803-152">A hierarquia de modelo de objeto do ISE</span><span class="sxs-lookup"><span data-stu-id="4f803-152">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
