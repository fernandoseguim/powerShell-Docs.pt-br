---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
title: exemplo de modelo de um problema conhecido ou writeup de limitação
ms.openlocfilehash: cecf31127aaa1942471877a2056230ab592bd095
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
><span data-ttu-id="0c9ea-103">Observação: dê um título descritivo proposto e uma breve descrição</span><span class="sxs-lookup"><span data-stu-id="0c9ea-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="0c9ea-104">Exemplo: erros de ExecutionPolicy incorreta</span><span class="sxs-lookup"><span data-stu-id="0c9ea-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="0c9ea-105">No Windows 7, o uso de módulos PowerShell e recursos DSC pode fazer com que erros sobre ExecutionPolicy sejam relatados.</span><span class="sxs-lookup"><span data-stu-id="0c9ea-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="0c9ea-106">Resolução</span><span class="sxs-lookup"><span data-stu-id="0c9ea-106">Resolution</span></span>

<span data-ttu-id="0c9ea-107">Para resolver, defina **ExecutionPolicy** como **RemoteSigned** executando o seguinte comando em uma sessão do PowerShell com privilégios elevados (Executar como Administrador):</span><span class="sxs-lookup"><span data-stu-id="0c9ea-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```