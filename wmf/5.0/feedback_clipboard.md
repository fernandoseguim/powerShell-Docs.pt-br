---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: d34a267bae7e48afe4442256d7f112da3a97eb7d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="clipboard-cmdlets"></a><span data-ttu-id="6f241-102">Área de transferência de Cmdlets</span><span class="sxs-lookup"><span data-stu-id="6f241-102">Clipboard cmdlets</span></span>
<span data-ttu-id="6f241-103">**Get-Clipboard** e **Set-Clipboard** facilitam a transferência do conteúdo de e para uma sessão do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6f241-103">**Get-Clipboard** and **Set-Clipboard** make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="6f241-104">Por exemplo, se você usar o Windows Explorer para copiar três arquivos na área de transferência (selecionando-os e pressionando `ctrl-c`, por exemplo), poderá facilmente acessar o conteúdo da área de transferência como uma lista de arquivos:</span><span class="sxs-lookup"><span data-stu-id="6f241-104">For example, if you use Windows Explorer to copy three files to the clipboard (by selecting them and pressing `ctrl-c`, for example), you can then easily access the contents of the clipboard as a list of files:</span></span>

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


<span data-ttu-id="6f241-105">Os cmdlets Clipboard dão suporte a imagens, arquivos de áudio, listas de arquivo e texto.</span><span class="sxs-lookup"><span data-stu-id="6f241-105">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>