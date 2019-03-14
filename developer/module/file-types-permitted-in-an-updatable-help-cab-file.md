---
title: Tipos de arquivo permitidos em um atualizável ajudam a arquivo CAB | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 3562804157ebdfca561445a8671d726b55cc4efd
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794239"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="fef7a-102">Tipos de arquivo permitidos em um arquivo CAB de ajuda atualizável</span><span class="sxs-lookup"><span data-stu-id="fef7a-102">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="fef7a-103">Este tópico lista e descreve os requisitos de conteúdo para os arquivos CAB de ajuda atualizável.</span><span class="sxs-lookup"><span data-stu-id="fef7a-103">This topics lists and describes the content requirements for Updatable Help CAB files.</span></span>

## <a name="updatable-help-cab-file-requirements"></a><span data-ttu-id="fef7a-104">Requisitos de arquivo CAB de ajuda atualizável</span><span class="sxs-lookup"><span data-stu-id="fef7a-104">Updatable Help CAB File Requirements</span></span>

<span data-ttu-id="fef7a-105">O conteúdo do arquivo CAB não compactado é limitado a 1 GB por padrão.</span><span class="sxs-lookup"><span data-stu-id="fef7a-105">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="fef7a-106">Para ignorar esse limite, os usuários precisarão usar o **Force** parâmetro do [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span><span class="sxs-lookup"><span data-stu-id="fef7a-106">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="fef7a-107">Para garantir a segurança dos arquivos de Ajuda que são baixados da Internet, um arquivo CAB de ajuda atualizável pode incluir somente os tipos de arquivo listados abaixo.</span><span class="sxs-lookup"><span data-stu-id="fef7a-107">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="fef7a-108">O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet valida todos os arquivos em relação aos esquemas de tópico da Ajuda.</span><span class="sxs-lookup"><span data-stu-id="fef7a-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="fef7a-109">Se o `Update-Help` cmdlet encontrar um arquivo que é inválido ou não é um tipo permitido, mas não instala o arquivo inválido e interrompe a instalação de arquivos CAB no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="fef7a-109">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="fef7a-110">Tópicos de ajuda baseados em XML para os cmdlets.</span><span class="sxs-lookup"><span data-stu-id="fef7a-110">XML-based help topics for cmdlets.</span></span>

- <span data-ttu-id="fef7a-111">Tópicos de ajuda baseados em XML, para scripts e funções.</span><span class="sxs-lookup"><span data-stu-id="fef7a-111">XML-based help topics for scripts and functions.</span></span>

- <span data-ttu-id="fef7a-112">Tópicos de ajuda baseados em XML para provedores do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fef7a-112">XML-based help topics for Windows PowerShell providers.</span></span>

- <span data-ttu-id="fef7a-113">Com base em texto tópicos da Ajuda, como sobre tópicos.</span><span class="sxs-lookup"><span data-stu-id="fef7a-113">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="fef7a-114">O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifica o conteúdo do arquivo CAB, quando ele desempacota o CAB.</span><span class="sxs-lookup"><span data-stu-id="fef7a-114">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="fef7a-115">Se `Update-Help` localiza os tipos de arquivo não compatível em um arquivo CAB de ajuda atualizável, ele gera um erro de terminação e interrompe a operação.</span><span class="sxs-lookup"><span data-stu-id="fef7a-115">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="fef7a-116">Ele não instala os arquivos da Ajuda do CAB, mesmo aqueles dos tipos de arquivo em conformidade.</span><span class="sxs-lookup"><span data-stu-id="fef7a-116">It does not install any help files from the CAB, even those of compliant file types.</span></span>