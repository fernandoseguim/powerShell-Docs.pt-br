---
ms.date: 06/12/2017
contributor: manikb
keywords: galeria,powershell,cmdlet,psget
title: Cmdlets de solução de problemas
ms.openlocfilehash: c0a1fbcafd8c4443dc9d628c54c4c525d9701861
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892467"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="d0faa-103">Cmdlets de solução de problemas</span><span class="sxs-lookup"><span data-stu-id="d0faa-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="d0faa-104">Como resolver o problema “AVISO: falha ao fazer o download do Pacote 'nome do pacote'”</span><span class="sxs-lookup"><span data-stu-id="d0faa-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="d0faa-105">Há relatos de que `Install-Module` ou `Update-Module` às vezes falha em alguns computadores.</span><span class="sxs-lookup"><span data-stu-id="d0faa-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span>
<span data-ttu-id="d0faa-106">Com base em nossa investigação, isso está relacionado à conexão de rede.</span><span class="sxs-lookup"><span data-stu-id="d0faa-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="d0faa-107">Recentemente, atualizamos o provedor do NuGet para que ele possa baixar pacotes de forma confiável.</span><span class="sxs-lookup"><span data-stu-id="d0faa-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="d0faa-108">Siga as instruções abaixo para instalar o build mais recente do provedor do NuGet e instalar ou atualizar seu módulo.</span><span class="sxs-lookup"><span data-stu-id="d0faa-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="d0faa-109">Vamos usar o módulo “Azure” como o exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="d0faa-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```