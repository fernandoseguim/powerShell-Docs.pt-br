---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Usando a expansão com Tab
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: 3d047bf0691c8a304d7637aa50fba6ae99709a82
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400594"
---
# <a name="using-tab-expansion"></a><span data-ttu-id="c8fb7-103">Usando a expansão com Tab</span><span class="sxs-lookup"><span data-stu-id="c8fb7-103">Using Tab Expansion</span></span>

<span data-ttu-id="c8fb7-104">Shells de linha de comando geralmente fornecem uma maneira de preencher os nomes de comandos ou arquivos longos automaticamente, acelerando a entrada de comando e fornecendo.</span><span class="sxs-lookup"><span data-stu-id="c8fb7-104">Command-line shells often provide a way to complete the names of long files or commands automatically, speeding up command entry and providing .</span></span> <span data-ttu-id="c8fb7-105">O Windows PowerShell permite preencher os nomes de arquivo e nomes de cmdlet pressionando a tecla **Tab**.</span><span class="sxs-lookup"><span data-stu-id="c8fb7-105">Windows PowerShell allows you to fill in file names and cmdlet names by pressing the **Tab** key.</span></span>

> [!NOTE]
> <span data-ttu-id="c8fb7-106">A expansão da guia é controlada pelas funções internas TabExpansion ou TabExpansion2.</span><span class="sxs-lookup"><span data-stu-id="c8fb7-106">Tab expansion is controlled by the internal function TabExpansion or TabExpansion2.</span></span> <span data-ttu-id="c8fb7-107">Como essa função pode ser modificada ou substituída, essa discussão é um guia para o comportamento da configuração padrão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8fb7-107">Since this function can be modified or overridden, this discussion is a guide to the behavior of the default PowerShell configuration.</span></span>

<span data-ttu-id="c8fb7-108">Para preencher automaticamente um nome de arquivo ou um caminho com as opções disponíveis automaticamente, digite parte do nome e pressione a tecla **Tab**.</span><span class="sxs-lookup"><span data-stu-id="c8fb7-108">To fill in a filename or path from the available choices automatically, type part of the name and press the **Tab** key.</span></span> <span data-ttu-id="c8fb7-109">O PowerShell expandirá automaticamente o nome para a primeira correspondência que encontrar.</span><span class="sxs-lookup"><span data-stu-id="c8fb7-109">PowerShell will automatically expand the name to the first match that it finds.</span></span> <span data-ttu-id="c8fb7-110">Pressionar a tecla **Tab** repetidamente percorrerá todas as opções disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c8fb7-110">Pressing the **Tab** key repeatedly will cycle through all of the available choices.</span></span>

<span data-ttu-id="c8fb7-111">A expansão com Tab de nomes de cmdlet é ligeiramente diferente.</span><span class="sxs-lookup"><span data-stu-id="c8fb7-111">The tab expansion of cmdlet names is slightly different.</span></span> <span data-ttu-id="c8fb7-112">Para usar a expansão com Tab em um nome de cmdlet, digite a primeira parte inteira do nome (o verbo) e o hífen que o segue.</span><span class="sxs-lookup"><span data-stu-id="c8fb7-112">To use tab expansion on a cmdlet name, type the entire first part of the name (the verb) and the hyphen that follows it.</span></span> <span data-ttu-id="c8fb7-113">Você pode preencher mais do mesmo nome de uma correspondência parcial.</span><span class="sxs-lookup"><span data-stu-id="c8fb7-113">You can fill in more of the name for a partial match.</span></span> <span data-ttu-id="c8fb7-114">Por exemplo, se você digitar **get-co** e pressionar a tecla **Tab**, o PowerShell o expandirá automaticamente para o cmdlet **Get-Command** (observe que ele também altera as letras maiúsculas e minúsculas para sua forma padrão).</span><span class="sxs-lookup"><span data-stu-id="c8fb7-114">For example, if you type **get-co** and then press the **Tab** key, PowerShell will automatically expand this to the **Get-Command** cmdlet (notice that it also changes the case of letters to their standard form).</span></span> <span data-ttu-id="c8fb7-115">Se você pressionar a tecla **Tab** novamente, o PowerShell substituirá isso pelo outro único nome de cmdlet correspondente, **Get-Content**.</span><span class="sxs-lookup"><span data-stu-id="c8fb7-115">If you press **Tab** key again, PowerShell replaces this with the only other matching cmdlet name, **Get-Content**.</span></span>

<span data-ttu-id="c8fb7-116">Você pode usar a expansão com Tab várias vezes na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="c8fb7-116">You can use tab expansion repeatedly on the same line.</span></span> <span data-ttu-id="c8fb7-117">Por exemplo, você pode usar a expansão da tabulação no nome do cmdlet **Get-Content** digitando:</span><span class="sxs-lookup"><span data-stu-id="c8fb7-117">For example, you can use tab expansion on the name of the **Get-Content** cmdlet by entering:</span></span>

```
PS> Get-Con<Tab>
```

<span data-ttu-id="c8fb7-118">Quando você pressiona a tecla **Tab**, o comando se expande para:</span><span class="sxs-lookup"><span data-stu-id="c8fb7-118">When you press the **Tab** key, the command expands to:</span></span>

```
PS> Get-Content
```

<span data-ttu-id="c8fb7-119">Você pode especificar parcialmente o caminho para o arquivo de log Active Setup e usar a expansão com Tab novamente:</span><span class="sxs-lookup"><span data-stu-id="c8fb7-119">You can then partially specify the path to the Active Setup log file and use tab expansion again:</span></span>

```
PS> Get-Content c:\windows\acts<Tab>
```

<span data-ttu-id="c8fb7-120">Quando você pressiona a tecla **Tab**, o comando se expande para:</span><span class="sxs-lookup"><span data-stu-id="c8fb7-120">When you press the **Tab** key, the command expands to:</span></span>

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> <span data-ttu-id="c8fb7-121">Uma limitação do processo de expansão de guia é que as guias são sempre interpretadas como tentativas de preencher uma palavra.</span><span class="sxs-lookup"><span data-stu-id="c8fb7-121">One limitation of the tab expansion process is that tabs are always interpreted as attempts to complete a word.</span></span> <span data-ttu-id="c8fb7-122">Se você copiar e colar os exemplos de comando em um console do PowerShell, verifique se o exemplo não contém guias; se contiver, os resultados serão imprevisíveis e certamente não serão o que você pretendia.</span><span class="sxs-lookup"><span data-stu-id="c8fb7-122">If you copy and paste command examples into a PowerShell console, make sure that the sample does not contain tabs; if it does, the results will be unpredictable and will almost certainly not be what you intended.</span></span>