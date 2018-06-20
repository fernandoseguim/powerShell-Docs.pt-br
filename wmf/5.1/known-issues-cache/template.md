---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.topic: conceptual
title: exemplo de modelo de um problema conhecido ou writeup de limitação
ms.openlocfilehash: 453d4e40b906ebcab7314f04e138ded271338846
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221928"
---
><span data-ttu-id="0bd13-103">Observação: dê um título descritivo proposto e uma breve descrição</span><span class="sxs-lookup"><span data-stu-id="0bd13-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="0bd13-104">Exemplo: erros de ExecutionPolicy incorreta</span><span class="sxs-lookup"><span data-stu-id="0bd13-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="0bd13-105">No Windows 7, o uso de módulos PowerShell e recursos DSC pode fazer com que erros sobre ExecutionPolicy sejam relatados.</span><span class="sxs-lookup"><span data-stu-id="0bd13-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="0bd13-106">Resolução</span><span class="sxs-lookup"><span data-stu-id="0bd13-106">Resolution</span></span>

<span data-ttu-id="0bd13-107">Para resolver, defina **ExecutionPolicy** como **RemoteSigned** executando o seguinte comando em uma sessão do PowerShell com privilégios elevados (Executar como Administrador):</span><span class="sxs-lookup"><span data-stu-id="0bd13-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
