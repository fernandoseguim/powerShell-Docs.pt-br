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
ms.openlocfilehash: 931383858c0b83f0a9a66026c215e16481b89e9e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862832"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>Tipos de arquivo permitidos em um arquivo CAB de ajuda atualizável

Este tópico lista e descreve os requisitos de conteúdo para os arquivos CAB de ajuda atualizável.

## <a name="updatable-help-cab-file-requirements"></a>Requisitos de arquivo CAB de ajuda atualizável

O conteúdo do arquivo CAB não compactado é limitado a 1 GB por padrão. Para ignorar esse limite, os usuários precisarão usar o **Force** parâmetro do [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.
O conteúdo do arquivo CAB não compactado é limitado a 1 GB por padrão. Para ignorar esse limite, os usuários precisarão usar o **Force** parâmetro do [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.

Para garantir a segurança dos arquivos de Ajuda que são baixados da Internet, um arquivo CAB de ajuda atualizável pode incluir somente os tipos de arquivo listados abaixo. O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet valida todos os arquivos em relação aos esquemas de tópico da Ajuda. Se o `Update-Help` cmdlet encontrar um arquivo que é inválido ou não é um tipo permitido, mas não instala o arquivo inválido e interrompe a instalação de arquivos CAB no computador do usuário.
Para garantir a segurança dos arquivos de Ajuda que são baixados da Internet, um arquivo CAB de ajuda atualizável pode incluir somente os tipos de arquivo listados abaixo. O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet valida todos os arquivos em relação aos esquemas de tópico da Ajuda. Se o `Update-Help` cmdlet encontrar um arquivo que é inválido ou não é um tipo permitido, mas não instala o arquivo inválido e interrompe a instalação de arquivos CAB no computador do usuário.

- Tópicos de ajuda baseados em XML para os cmdlets.

- Tópicos de ajuda baseados em XML, para scripts e funções.

- Tópicos de ajuda baseados em XML para provedores do Windows PowerShell.

- Com base em texto tópicos da Ajuda, como sobre tópicos.

O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifica o conteúdo do arquivo CAB, quando ele desempacota o CAB. Se `Update-Help` localiza os tipos de arquivo não compatível em um arquivo CAB de ajuda atualizável, ele gera um erro de terminação e interrompe a operação. Ele não instala os arquivos da Ajuda do CAB, mesmo aqueles dos tipos de arquivo em conformidade.
O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifica o conteúdo do arquivo CAB, quando ele desempacota o CAB. Se `Update-Help` localiza os tipos de arquivo não compatível em um arquivo CAB de ajuda atualizável, ele gera um erro de terminação e interrompe a operação. Ele não instala os arquivos da Ajuda do CAB, mesmo aqueles dos tipos de arquivo em conformidade.