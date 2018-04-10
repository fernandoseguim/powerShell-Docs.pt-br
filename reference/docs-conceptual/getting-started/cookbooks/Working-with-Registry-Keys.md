---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Trabalhando com chaves do Registro
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: a9d08f2f6b5803980dec45a4e266ad66879c8c8d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="d454f-103">Trabalhando com chaves do Registro</span><span class="sxs-lookup"><span data-stu-id="d454f-103">Working with Registry Keys</span></span>

<span data-ttu-id="d454f-104">Como as chaves do Registro são itens em unidades do Windows PowerShell, trabalhar com elas é muito semelhante a trabalhar com arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="d454f-104">Because registry keys are items on Windows PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="d454f-105">Uma diferença fundamental é que cada item em uma unidade do Windows PowerShell com base no Registro é um contêiner, assim como uma pasta em uma unidade de sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="d454f-105">One critical difference is that every item on a registry-based Windows PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="d454f-106">No entanto, as entradas do Registro e seus valores associados são propriedades de itens, não itens distintos.</span><span class="sxs-lookup"><span data-stu-id="d454f-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

### <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="d454f-107">Listar todas as subchaves de uma chave do Registro</span><span class="sxs-lookup"><span data-stu-id="d454f-107">Listing All Subkeys of a Registry Key</span></span>

<span data-ttu-id="d454f-108">Você pode mostrar todos os itens dentro de uma chave do Registro usando **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="d454f-108">You can show all items directly within a registry key by using **Get-ChildItem**.</span></span> <span data-ttu-id="d454f-109">Adicione o parâmetro opcional **Force** para exibir itens ocultos ou do sistema.</span><span class="sxs-lookup"><span data-stu-id="d454f-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="d454f-110">Por exemplo, este comando exibe os itens diretamente na unidade do Windows PowerShell HKCU:, que corresponde ao hive do Registro HKEY_CURRENT_USER:</span><span class="sxs-lookup"><span data-stu-id="d454f-110">For example, this command displays the items directly within Windows PowerShell drive HKCU:, which corresponds to the HKEY_CURRENT_USER registry hive:</span></span>

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

<span data-ttu-id="d454f-111">Essas são as chaves de nível superior em HKEY_CURRENT_USER no Editor do Registro (Regedit.exe).</span><span class="sxs-lookup"><span data-stu-id="d454f-111">These are the top-level keys visible under HKEY_CURRENT_USER in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="d454f-112">Você também pode especificar esse caminho de Registro definindo o nome do provedor de Registro, seguido por "**::**".</span><span class="sxs-lookup"><span data-stu-id="d454f-112">You can also specify this registry path by specifying the registry provider's name, followed by "**::**".</span></span> <span data-ttu-id="d454f-113">O nome completo do provedor do Registro é **Microsoft.PowerShell.Core\\Registry**, mas isso pode ser reduzido para apenas **Registry**.</span><span class="sxs-lookup"><span data-stu-id="d454f-113">The registry provider's full name is **Microsoft.PowerShell.Core\\Registry**, but this can be shortened to just **Registry**.</span></span> <span data-ttu-id="d454f-114">Qualquer um dos comandos a seguir lista o conteúdo diretamente sob o HKCU:</span><span class="sxs-lookup"><span data-stu-id="d454f-114">Any of the following commands will list the contents directly under HKCU:</span></span>

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="d454f-115">Esses comandos listam apenas os itens contidos diretamente, similar ao uso do comando **DIR** do Cmd.exe ou do **ls** em um shell do UNIX.</span><span class="sxs-lookup"><span data-stu-id="d454f-115">These commands list only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="d454f-116">Para mostrar os itens contidos, você precisa especificar o parâmetro **Recurse**.</span><span class="sxs-lookup"><span data-stu-id="d454f-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="d454f-117">Para listar todas as chaves de Registro no HKCU, use o comando a seguir (esta operação pode demorar um muitíssimo tempo):</span><span class="sxs-lookup"><span data-stu-id="d454f-117">To list all registry keys in HKCU, use the following command (This operation can take an extremely long time.):</span></span>

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

<span data-ttu-id="d454f-118">**Get-ChildItem** pode executar os recursos de filtragem complexos por meio de seus parâmetros **Path**, **Filter**, **Include** e **Exclude**, mas esses parâmetros normalmente são baseados apenas no nome.</span><span class="sxs-lookup"><span data-stu-id="d454f-118">**Get-ChildItem** can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="d454f-119">É possível executar a filtragem complexa com base em outras propriedades de itens usando o cmdlet **Where-Object**.</span><span class="sxs-lookup"><span data-stu-id="d454f-119">You can perform complex filtering based on other properties of items by using the **Where-Object** cmdlet.</span></span> <span data-ttu-id="d454f-120">O comando a seguir encontra todas as chaves no HKCU:\\Software que têm, no máximo, uma subchave e que também têm exatamente quatro valores:</span><span class="sxs-lookup"><span data-stu-id="d454f-120">The following command finds all keys within HKCU:\\Software that have no more than one subkey and also have exactly four values:</span></span>

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a><span data-ttu-id="d454f-121">Copiar chaves</span><span class="sxs-lookup"><span data-stu-id="d454f-121">Copying Keys</span></span>

<span data-ttu-id="d454f-122">A cópia é feita com **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="d454f-122">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="d454f-123">O comando a seguir copia HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion e todas as suas propriedades em HKCU:\\, criando uma nova chave chamada “CurrentVersion”:</span><span class="sxs-lookup"><span data-stu-id="d454f-123">The following command copies HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion and all of its properties to HKCU:\\, creating a new key named "CurrentVersion":</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

<span data-ttu-id="d454f-124">Ao examinar essa nova chave no editor do Registro ou usando **Get-ChildItem**, você observará que não há cópias das subchaves contidas no novo local.</span><span class="sxs-lookup"><span data-stu-id="d454f-124">If you examine this new key in the registry editor or by using **Get-ChildItem**, you will notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="d454f-125">Para copiar todo o conteúdo de um contêiner, você precisa especificar o parâmetro **Recurse**.</span><span class="sxs-lookup"><span data-stu-id="d454f-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="d454f-126">Para tornar o comando de cópia anterior recursivo, você usaria este comando:</span><span class="sxs-lookup"><span data-stu-id="d454f-126">To make the preceding copy command recursive, you would use this command:</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

<span data-ttu-id="d454f-127">Você ainda pode usar outras ferramentas que já estão disponíveis para executar cópias do sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="d454f-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="d454f-128">Quaisquer ferramentas de edição de Registro, incluindo reg.exe, regini.exe e regedit.exe, e objetos COM que dão suporte à edição do Registro (como o WScript.Shell e a classe StdRegProv do WMI) podem ser usados de dentro do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d454f-128">Any registry editing tools—including reg.exe, regini.exe, and regedit.exe—and COM objects that support registry editing (such as WScript.Shell and WMI's StdRegProv class) can be used from within Windows PowerShell.</span></span>

### <a name="creating-keys"></a><span data-ttu-id="d454f-129">Criar chaves</span><span class="sxs-lookup"><span data-stu-id="d454f-129">Creating Keys</span></span>

<span data-ttu-id="d454f-130">Criar novas chaves no Registro é mais simples do que criar um novo item em um sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="d454f-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="d454f-131">Como todas as chaves do Registro são contêineres, você não precisa especificar o tipo de item; basta fornecer um caminho explícito, como:</span><span class="sxs-lookup"><span data-stu-id="d454f-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

<span data-ttu-id="d454f-132">Você também pode usar um caminho de provedor para especificar uma chave:</span><span class="sxs-lookup"><span data-stu-id="d454f-132">You can also use a provider-based path to specify a key:</span></span>

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a><span data-ttu-id="d454f-133">Excluir chaves</span><span class="sxs-lookup"><span data-stu-id="d454f-133">Deleting Keys</span></span>

<span data-ttu-id="d454f-134">Excluir itens é essencialmente o mesmo para todos os provedores.</span><span class="sxs-lookup"><span data-stu-id="d454f-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="d454f-135">Os comandos a seguir removerão itens silenciosamente:</span><span class="sxs-lookup"><span data-stu-id="d454f-135">The following commands will silently remove items:</span></span>

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="d454f-136">Remover todas as chaves sob uma chave específica</span><span class="sxs-lookup"><span data-stu-id="d454f-136">Removing All Keys Under a Specific Key</span></span>

<span data-ttu-id="d454f-137">Você pode remover os itens contidos usando **Remove-Item**, mas será solicitado que confirme a remoção se o item contiver qualquer outra coisa.</span><span class="sxs-lookup"><span data-stu-id="d454f-137">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="d454f-138">Por exemplo, se tentarmos excluir a subchave HKCU:\\CurrentVersion que criamos, veremos isto:</span><span class="sxs-lookup"><span data-stu-id="d454f-138">For example, if we attempt to delete the HKCU:\\CurrentVersion subkey we created, we see this:</span></span>

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="d454f-139">Para excluir os itens contidos sem nenhuma solicitação, especifique o parâmetro **-Recurse**:</span><span class="sxs-lookup"><span data-stu-id="d454f-139">To delete contained items without prompting, specify the **-Recurse** parameter:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="d454f-140">Se desejar remover todos os itens dentro de HKCU:\\CurrentVersion, mas não o HKCU:\\CurrentVersion em si, você poderá usar:</span><span class="sxs-lookup"><span data-stu-id="d454f-140">If you wanted to remove all items within HKCU:\\CurrentVersion but not HKCU:\\CurrentVersion itself, you could instead use:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```