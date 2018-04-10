---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: ada4fcc0beb3eb74b099f221762341abbf2c3b4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="new-temporaryfile"></a><span data-ttu-id="bb5e4-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="bb5e4-102">New-TemporaryFile</span></span>
<span data-ttu-id="bb5e4-103">Às vezes, em seus scripts, é necessário criar um arquivo temporário.</span><span class="sxs-lookup"><span data-stu-id="bb5e4-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="bb5e4-104">Você pode isso com facilidade com o cmdlet **New-TemporaryFile**:</span><span class="sxs-lookup"><span data-stu-id="bb5e4-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="bb5e4-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="bb5e4-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="bb5e4-106">PS C:\\&gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="bb5e4-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="bb5e4-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="bb5e4-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>