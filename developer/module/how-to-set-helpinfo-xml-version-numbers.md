---
title: Como definir os números de versão XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: b98e6879bbfe0e3ec1a9ab37496dde44caf523a4
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054128"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="716b1-102">Como definir os números de versão do XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="716b1-102">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="716b1-103">Este tópico explica como definir e aumentar os números de versão em um arquivo de informações de ajuda atualizável, comumente conhecido como um "arquivo XML HelpInfo".</span><span class="sxs-lookup"><span data-stu-id="716b1-103">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="716b1-104">Como definir os números de versão do XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="716b1-104">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="716b1-105">Os números de versão em um arquivo XML HelpInfo são essenciais para a operação de ajuda atualizável.</span><span class="sxs-lookup"><span data-stu-id="716b1-105">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span>
<span data-ttu-id="716b1-106">O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets baixar novos arquivos de Ajuda somente quando o número de versão para uma cultura de interface do usuário no arquivo XML HelpInfo remoto é maior que o número de versão para aquela cultura de interface do usuário no XML HelpInfo local, ou não há nenhum arquivo XML HelpInfo local.</span><span class="sxs-lookup"><span data-stu-id="716b1-106">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="716b1-107">O arquivo XML HelpInfo usa o número de versão de 4 partes que é definido na **Version** classe do Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="716b1-107">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="716b1-108">O formato é `N1.N2.N3.N4`.</span><span class="sxs-lookup"><span data-stu-id="716b1-108">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="716b1-109">Os autores de módulo podem usar qualquer versão que é permitida pelo esquema de numeração a **Version** classe.</span><span class="sxs-lookup"><span data-stu-id="716b1-109">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="716b1-110">A Ajuda atualizável requer apenas que o número de versão para um aumento de cultura da interface do usuário quando uma nova versão do arquivo CAB para aquela cultura de interface do usuário for carregada para o local especificado pelo **HelpContentURI** elemento no arquivo XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="716b1-110">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="716b1-111">O exemplo a seguir mostra os elementos do arquivo XML HelpInfo para o alemão (de-DE) da interface do usuário quando a versão é 2.15.0.10 de cultura.</span><span class="sxs-lookup"><span data-stu-id="716b1-111">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="716b1-112">O número de versão para uma cultura de interface do usuário reflete a versão do arquivo CAB para aquela cultura de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="716b1-112">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="716b1-113">O número de versão se aplica a todo o arquivo CAB.</span><span class="sxs-lookup"><span data-stu-id="716b1-113">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="716b1-114">Números de versão diferentes para diferentes arquivos não pode ser definido no arquivo CAB.</span><span class="sxs-lookup"><span data-stu-id="716b1-114">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="716b1-115">O número de versão para cada cultura de interface do usuário é avaliado de maneira independente e não precisa estar relacionado aos números de versão para outras culturas de interface do usuário que suporta o módulo.</span><span class="sxs-lookup"><span data-stu-id="716b1-115">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>