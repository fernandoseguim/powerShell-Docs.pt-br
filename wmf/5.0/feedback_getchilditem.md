---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: 62cccabd7c63c6ba928fc2bf8addd3d11483e90f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="104e1-102">Get-ChildItem contém o parâmetro -Depth</span><span class="sxs-lookup"><span data-stu-id="104e1-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="104e1-103">**Get-ChildItem** agora tem um parâmetro **–Depth** que é usado com **–Recurse** para limitar a recursão:</span><span class="sxs-lookup"><span data-stu-id="104e1-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="104e1-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span><span class="sxs-lookup"><span data-stu-id="104e1-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="104e1-105">Diretório: C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="104e1-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="104e1-106">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="104e1-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="104e1-107">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="104e1-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="104e1-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="104e1-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="104e1-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="104e1-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="104e1-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="104e1-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="104e1-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span><span class="sxs-lookup"><span data-stu-id="104e1-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="104e1-112">Diretório: C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="104e1-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="104e1-113">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="104e1-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="104e1-114">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="104e1-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="104e1-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="104e1-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="104e1-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="104e1-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="104e1-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="104e1-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="104e1-118">Diretório: C:\\Users\\slee\\Downloads\\Example\\Depth0</span><span class="sxs-lookup"><span data-stu-id="104e1-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="104e1-119">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="104e1-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="104e1-120">d----- 4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="104e1-120">d----- 4/14/2015 5:33 PM Depth1</span></span>