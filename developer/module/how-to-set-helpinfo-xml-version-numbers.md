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
# <a name="how-to-set-helpinfo-xml-version-numbers"></a>Como definir os números de versão do XML HelpInfo

Este tópico explica como definir e aumentar os números de versão em um arquivo de informações de ajuda atualizável, comumente conhecido como um "arquivo XML HelpInfo".

## <a name="how-to-set-helpinfo-xml-version-numbers"></a>Como definir os números de versão do XML HelpInfo

Os números de versão em um arquivo XML HelpInfo são essenciais para a operação de ajuda atualizável.
O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets baixar novos arquivos de Ajuda somente quando o número de versão para uma cultura de interface do usuário no arquivo XML HelpInfo remoto é maior que o número de versão para aquela cultura de interface do usuário no XML HelpInfo local, ou não há nenhum arquivo XML HelpInfo local.

O arquivo XML HelpInfo usa o número de versão de 4 partes que é definido na **Version** classe do Microsoft .NET Framework. O formato é `N1.N2.N3.N4`. Os autores de módulo podem usar qualquer versão que é permitida pelo esquema de numeração a **Version** classe. A Ajuda atualizável requer apenas que o número de versão para um aumento de cultura da interface do usuário quando uma nova versão do arquivo CAB para aquela cultura de interface do usuário for carregada para o local especificado pelo **HelpContentURI** elemento no arquivo XML HelpInfo.

O exemplo a seguir mostra os elementos do arquivo XML HelpInfo para o alemão (de-DE) da interface do usuário quando a versão é 2.15.0.10 de cultura.

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

O número de versão para uma cultura de interface do usuário reflete a versão do arquivo CAB para aquela cultura de interface do usuário. O número de versão se aplica a todo o arquivo CAB. Números de versão diferentes para diferentes arquivos não pode ser definido no arquivo CAB. O número de versão para cada cultura de interface do usuário é avaliado de maneira independente e não precisa estar relacionado aos números de versão para outras culturas de interface do usuário que suporta o módulo.