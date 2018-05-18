---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Cmdlets de solução de problemas
ms.openlocfilehash: 6295a5b99aa19db933569638d84e490ad81eedc7
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="3d1d8-103">Cmdlets de solução de problemas</span><span class="sxs-lookup"><span data-stu-id="3d1d8-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="3d1d8-104">Como resolver o problema “AVISO: falha ao baixar o Pacote 'nome do pacote'”?</span><span class="sxs-lookup"><span data-stu-id="3d1d8-104">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>

<span data-ttu-id="3d1d8-105">Foi relatado que Install-Module ou Update-Module às vezes falha em alguns computadores.</span><span class="sxs-lookup"><span data-stu-id="3d1d8-105">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="3d1d8-106">Com base em nossa investigação, isso está relacionado à conexão de rede.</span><span class="sxs-lookup"><span data-stu-id="3d1d8-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="3d1d8-107">Recentemente, atualizamos o provedor do NuGet para que ele possa baixar pacotes de forma confiável.</span><span class="sxs-lookup"><span data-stu-id="3d1d8-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="3d1d8-108">Siga as instruções abaixo para instalar o build mais recente do provedor do NuGet e instalar ou atualizar seu módulo.</span><span class="sxs-lookup"><span data-stu-id="3d1d8-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="3d1d8-109">Vamos usar o módulo “Azure” como o exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="3d1d8-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```