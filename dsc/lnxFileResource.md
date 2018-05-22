---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso nxFile de DSC para Linux
ms.openlocfilehash: f1eb98092049ae837d144ccf99a84fe5614144e0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="c8d17-103">Recurso nxFile de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="c8d17-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="c8d17-104">O recurso **nxFile** na Configuração de Estado Desejado (DSC) do PowerShell fornece um mecanismo para gerenciar arquivos e diretórios em um nó do Linux.</span><span class="sxs-lookup"><span data-stu-id="c8d17-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c8d17-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8d17-105">Syntax</span></span>

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="c8d17-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c8d17-106">Properties</span></span>

|  <span data-ttu-id="c8d17-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="c8d17-107">Property</span></span> |  <span data-ttu-id="c8d17-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="c8d17-108">Description</span></span> |
|---|---|
| <span data-ttu-id="c8d17-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="c8d17-109">DestinationPath</span></span>| <span data-ttu-id="c8d17-110">Especifica o local onde você deseja garantir o estado de um arquivo ou diretório.</span><span class="sxs-lookup"><span data-stu-id="c8d17-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="c8d17-111">SourcePath</span><span class="sxs-lookup"><span data-stu-id="c8d17-111">SourcePath</span></span>| <span data-ttu-id="c8d17-112">Especifica o caminho do qual o recurso de arquivo ou pasta deve ser copiado.</span><span class="sxs-lookup"><span data-stu-id="c8d17-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="c8d17-113">Esse caminho poderá ser um caminho local ou uma URL `http/https/ftp`.</span><span class="sxs-lookup"><span data-stu-id="c8d17-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="c8d17-114">Há suporte para URLs `http/https/ftp` remotas apenas quando o valor da propriedade **Type** é file.</span><span class="sxs-lookup"><span data-stu-id="c8d17-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is file.</span></span>|
| <span data-ttu-id="c8d17-115">Ensure</span><span class="sxs-lookup"><span data-stu-id="c8d17-115">Ensure</span></span>| <span data-ttu-id="c8d17-116">Determina se é necessário verificar se o arquivo existe.</span><span class="sxs-lookup"><span data-stu-id="c8d17-116">Determines whether to check if the file exists.</span></span> <span data-ttu-id="c8d17-117">Defina essa propriedade como "Present" para garantir que o arquivo exista.</span><span class="sxs-lookup"><span data-stu-id="c8d17-117">Set this property to "Present" to ensure the file exists.</span></span> <span data-ttu-id="c8d17-118">Defina-a como "Absent" para garantir que o arquivo não exista.</span><span class="sxs-lookup"><span data-stu-id="c8d17-118">Set it to "Absent" to ensure the file does not exist.</span></span> <span data-ttu-id="c8d17-119">O valor padrão é "Present".</span><span class="sxs-lookup"><span data-stu-id="c8d17-119">The default value is "Present".</span></span>|
| <span data-ttu-id="c8d17-120">Tipo</span><span class="sxs-lookup"><span data-stu-id="c8d17-120">Type</span></span>| <span data-ttu-id="c8d17-121">Especifica se o recurso que está sendo configurado é um diretório ou um arquivo.</span><span class="sxs-lookup"><span data-stu-id="c8d17-121">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="c8d17-122">Defina essa propriedade como "directory" para indicar que o recurso é um diretório.</span><span class="sxs-lookup"><span data-stu-id="c8d17-122">Set this property to "directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="c8d17-123">Defina-a como "file" para indicar que o recurso é um arquivo.</span><span class="sxs-lookup"><span data-stu-id="c8d17-123">Set it to "file" to indicate that the resource is a file.</span></span> <span data-ttu-id="c8d17-124">O valor padrão é "file"</span><span class="sxs-lookup"><span data-stu-id="c8d17-124">The default value is "file"</span></span>|
| <span data-ttu-id="c8d17-125">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="c8d17-125">Contents</span></span>| <span data-ttu-id="c8d17-126">Especifica o conteúdo de um arquivo, como uma cadeia de caracteres específica.</span><span class="sxs-lookup"><span data-stu-id="c8d17-126">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="c8d17-127">Soma de verificação</span><span class="sxs-lookup"><span data-stu-id="c8d17-127">Checksum</span></span>| <span data-ttu-id="c8d17-128">Define o tipo que deve ser usado para determinar se dois arquivos são iguais.</span><span class="sxs-lookup"><span data-stu-id="c8d17-128">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="c8d17-129">Se **Checksum** não for especificado, somente o nome de arquivo ou diretório será usado para comparação.</span><span class="sxs-lookup"><span data-stu-id="c8d17-129">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="c8d17-130">Os valores são: "ctime", "mtime" ou "md5".</span><span class="sxs-lookup"><span data-stu-id="c8d17-130">Values are: "ctime", "mtime", or "md5".</span></span>|
| <span data-ttu-id="c8d17-131">Recurse</span><span class="sxs-lookup"><span data-stu-id="c8d17-131">Recurse</span></span>| <span data-ttu-id="c8d17-132">Indica se subdiretórios são incluídos.</span><span class="sxs-lookup"><span data-stu-id="c8d17-132">Indicates if subdirectories are included.</span></span> <span data-ttu-id="c8d17-133">Defina essa propriedade como **$true** para indicar que você deseja que subdiretórios sejam incluídos.</span><span class="sxs-lookup"><span data-stu-id="c8d17-133">Set this property to **$true** to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="c8d17-134">O padrão é **$false**.</span><span class="sxs-lookup"><span data-stu-id="c8d17-134">The default is **$false**.</span></span> <span data-ttu-id="c8d17-135">**Observação:** essa propriedade é válida somente quando a propriedade **Type** é definida como directory.</span><span class="sxs-lookup"><span data-stu-id="c8d17-135">**Note:** This property is only valid when the **Type** property is set to directory.</span></span>|
| <span data-ttu-id="c8d17-136">Force</span><span class="sxs-lookup"><span data-stu-id="c8d17-136">Force</span></span>| <span data-ttu-id="c8d17-137">Determinadas operações de arquivo (como substituição de um arquivo ou exclusão de um diretório que não esteja vazio) resultarão em erro.</span><span class="sxs-lookup"><span data-stu-id="c8d17-137">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="c8d17-138">O uso da propriedade **Force** substitui esses erros.</span><span class="sxs-lookup"><span data-stu-id="c8d17-138">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="c8d17-139">O valor padrão é **$false**.</span><span class="sxs-lookup"><span data-stu-id="c8d17-139">The default value is **$false**.</span></span>|
| <span data-ttu-id="c8d17-140">Links</span><span class="sxs-lookup"><span data-stu-id="c8d17-140">Links</span></span>| <span data-ttu-id="c8d17-141">Especifica o comportamento desejado para links simbólicos.</span><span class="sxs-lookup"><span data-stu-id="c8d17-141">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="c8d17-142">Defina essa propriedade como "follow" para seguir links simbólicos e agir sobre o destino de links (por exemplo,</span><span class="sxs-lookup"><span data-stu-id="c8d17-142">Set this property to "follow" to follow symbolic links and act on the links target (for example.</span></span> <span data-ttu-id="c8d17-143">copiar o arquivo em vez do link).</span><span class="sxs-lookup"><span data-stu-id="c8d17-143">copy the file instead of the link).</span></span> <span data-ttu-id="c8d17-144">Defina essa propriedade como "manage" para agir sobre o link (por exemplo,</span><span class="sxs-lookup"><span data-stu-id="c8d17-144">Set this property to "manage" to act on the link (for example.</span></span> <span data-ttu-id="c8d17-145">copiar o próprio link).</span><span class="sxs-lookup"><span data-stu-id="c8d17-145">copy the link itself).</span></span> <span data-ttu-id="c8d17-146">Defina essa propriedade como "ignore" para ignorar links simbólicos.</span><span class="sxs-lookup"><span data-stu-id="c8d17-146">Set this property to "ignore" to ignore symbolic links.</span></span>|
| <span data-ttu-id="c8d17-147">Grupo</span><span class="sxs-lookup"><span data-stu-id="c8d17-147">Group</span></span>| <span data-ttu-id="c8d17-148">O nome do **Grupo** que será proprietário do arquivo ou diretório.</span><span class="sxs-lookup"><span data-stu-id="c8d17-148">The name of the **Group** to own the file or directory.</span></span>|
| <span data-ttu-id="c8d17-149">Modo</span><span class="sxs-lookup"><span data-stu-id="c8d17-149">Mode</span></span>| <span data-ttu-id="c8d17-150">Especifica as permissões desejadas para o recurso, na notação octal ou simbólica.</span><span class="sxs-lookup"><span data-stu-id="c8d17-150">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="c8d17-151">(por exemplo, 777 ou rwxrwxrwx).</span><span class="sxs-lookup"><span data-stu-id="c8d17-151">(for example, 777 or rwxrwxrwx).</span></span> <span data-ttu-id="c8d17-152">Se usar notação simbólica, não forneça o primeiro caractere que indica o diretório ou arquivo.</span><span class="sxs-lookup"><span data-stu-id="c8d17-152">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span>|
| <span data-ttu-id="c8d17-153">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c8d17-153">DependsOn</span></span> | <span data-ttu-id="c8d17-154">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="c8d17-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c8d17-155">Por exemplo, se a **ID** do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c8d17-155">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="c8d17-156">Informações adicionais</span><span class="sxs-lookup"><span data-stu-id="c8d17-156">Additional Information</span></span>


<span data-ttu-id="c8d17-157">Linux e Windows usam diferentes caracteres de quebra de linha em arquivos de texto por padrão; isso pode causar resultados inesperados ao configurar alguns arquivos em um computador Linux com __nxFile__.</span><span class="sxs-lookup"><span data-stu-id="c8d17-157">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with __nxFile__.</span></span> <span data-ttu-id="c8d17-158">Há várias maneiras de gerenciar o conteúdo de um arquivo do Linux e, ao mesmo tempo, evitar problemas causados por caracteres de quebra de linha inesperada:</span><span class="sxs-lookup"><span data-stu-id="c8d17-158">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

<span data-ttu-id="c8d17-159">Etapa 1: copie o arquivo de uma origem remota (http, https ou ftp): crie um arquivo em Linux com o conteúdo desejado e prepare-o em m servidor da web ou ftp acessível com o(s) nó(s) que vai configurar.</span><span class="sxs-lookup"><span data-stu-id="c8d17-159">Step 1: Copy the file from a remote source (http, https, or ftp): create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="c8d17-160">Defina a propriedade __SourcePath__ no recurso __nxFile__ com a URL da web ou do ftp para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="c8d17-160">Define the __SourcePath__ property in the __nxFile__ resource with the web or ftp URL to the file.</span></span>

```
Import-DSCResource -Module nx
Node $Node
{
nxFile resolvConf
{
    SourcePath = "http://10.185.85.11/conf/resolv.conf"
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"

}

}
```


<span data-ttu-id="c8d17-161">Etapa 2: leia o conteúdo do arquivo no script do PowerShell com [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) depois de definir a propriedade __$OFS__ para usar o caractere de quebra de linha do Linux.</span><span class="sxs-lookup"><span data-stu-id="c8d17-161">Step 2: Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the __$OFS__ property to use the Linux line-break character.</span></span>


```
Import-DSCResource -Module nx
Node $Node
{
$OFS = "`n"
$Contents = Get-Content C:\temp\resolv.conf

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = "$Contents"
}

}
```


<span data-ttu-id="c8d17-162">Etapa 3: use uma função do PowerShell para substituir as quebras de linha do Windows com caracteres de quebra de linha do Linux.</span><span class="sxs-lookup"><span data-stu-id="c8d17-162">Step 3: Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
    Return $outputStr
}

Import-DSCResource -Module nx
Node $Node
{

$Contents = @'
search contoso.com
domain contoso.com
nameserver 10.185.85.11
'@

$Contents = LinuxString $Contents

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = $Contents

}
}
```

## <a name="example"></a><span data-ttu-id="c8d17-163">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c8d17-163">Example</span></span>

<span data-ttu-id="c8d17-164">O exemplo a seguir garante que o diretório `/opt/mydir` exista e que um arquivo com conteúdo especificado exista nesse diretório.</span><span class="sxs-lookup"><span data-stu-id="c8d17-164">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxFile DirectoryExample
{
   Ensure = "Present"
   DestinationPath = "/opt/mydir"
   Type = "Directory"
}

nxFile FileExample
{
    Ensure = "Present"
    Destinationpath = "/opt/mydir/myfile"
    Contents=@"
#!/bin/bash`necho "hello world"`n
"@
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
}
}
```