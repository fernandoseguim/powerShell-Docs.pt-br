---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.topic: conceptual
title: exemplo de modelo de um problema conhecido ou writeup de limitação
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794478"
---
 ><span data-ttu-id="e1c9c-103">Observação: dê um título descritivo proposto e uma breve descrição</span><span class="sxs-lookup"><span data-stu-id="e1c9c-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="e1c9c-104">Exemplo: erros de ExecutionPolicy incorreta</span><span class="sxs-lookup"><span data-stu-id="e1c9c-104">Example: Erroneous ExecutionPolicy errors</span></span>
<span data-ttu-id="e1c9c-105">No Windows 7, o uso de módulos PowerShell e recursos DSC pode fazer com que erros sobre ExecutionPolicy sejam relatados.</span><span class="sxs-lookup"><span data-stu-id="e1c9c-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="e1c9c-106">Resolução</span><span class="sxs-lookup"><span data-stu-id="e1c9c-106">Resolution</span></span>

<span data-ttu-id="e1c9c-107">Para resolver, defina **ExecutionPolicy** como **RemoteSigned** executando o seguinte comando em uma sessão do PowerShell com privilégios elevados (Executar como Administrador):</span><span class="sxs-lookup"><span data-stu-id="e1c9c-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
