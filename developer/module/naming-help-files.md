---
title: Arquivos de ajuda de nomenclatura | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795344"
---
# <a name="naming-help-files"></a>Nomear arquivos de ajuda

Este tópico explica como nomear um arquivo de ajuda baseados em XML, de modo que o [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet pode encontrá-lo. Os requisitos de nome são diferentes para cada tipo de comando.

## <a name="cmdlet-help-files"></a>Arquivos de Ajuda do cmdlet

O arquivo de ajuda para um C# cmdlet deve ser nomeado para o assembly no qual o cmdlet é definido. Use o seguinte formato de nome de arquivo:

```
<AssemblyName>.dll-help.xml
```

O formato de nome do assembly é necessário, mesmo quando o assembly é um módulo aninhado.

Por exemplo, o [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet é definida no assembly Microsoft.PowerShell.Diagnostics.dll. O `Get-Help` cmdlet procura por um tópico da Ajuda para o `Get-WinEvent` cmdlet apenas no arquivo Microsoft.PowerShell.Diagnostics.dll help.xml no diretório do módulo.

## <a name="provider-help-files"></a>Arquivos de Ajuda do provedor

O arquivo de ajuda para um provedor do Windows PowerShell deve ser nomeado para o assembly no qual o provedor é definido. Use o seguinte formato de nome de arquivo:

```
<AssemblyName>.dll-help.xml
```

O formato de nome do assembly é necessário, mesmo quando o assembly é um módulo aninhado.

Por exemplo, o provedor de certificado é definido no assembly Microsoft.PowerShell.Security.dll. O `Get-Help` cmdlet procura um tópico da Ajuda para o provedor de certificado apenas no arquivo Microsoft.PowerShell.Security.dll help.xml no diretório do módulo.

## <a name="function-help-files"></a>Arquivos de ajuda de função

Funções podem ser documentadas usando [a Ajuda baseada em comentário](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) ou documentados em um arquivo de Ajuda do XML. Quando a função está documentada em um arquivo XML, a função deve ter um `.ExternalHelp` comentar a palavra-chave que associa a função com o arquivo XML. Caso contrário, o `Get-Help` cmdlet não é possível localizar o arquivo de Ajuda.

Não há nenhum requisitos técnicos para o nome de um arquivo de ajuda de função. No entanto, é uma prática recomendada nomear o arquivo de ajuda para o módulo de script no qual a função é definida. Por exemplo, a função a seguir é definida no arquivo MyModule.psm1.

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>Arquivos de ajuda de comando do CIM

O arquivo de ajuda para um comando CIM deve ser nomeado para o arquivo CDXML no qual o comando CIM é definido. Use o seguinte formato de nome de arquivo:

```
<FileName>.cdxml-help.xml
```

Comandos CIM são definidos em arquivos CDXML que podem ser incluídos nos módulos, como módulos aninhados. Quando o comando CIM é importado para a sessão como uma função, o Windows PowerShell adiciona um `.ExternalHelp` comentário palavra-chave para a definição da função que associa a função com uma ajuda XML do arquivo que é nomeado para o arquivo CDXML no qual o comando CIM é definido.

## <a name="script-workflow-help-files"></a>Arquivos de Ajuda do fluxo de trabalho de script

Fluxos de trabalho de script que estão incluídos nos módulos podem ser documentados nos arquivos de ajuda baseados em XML. Não há nenhum requisitos técnicos para o nome do arquivo de Ajuda. No entanto, é uma prática recomendada nomear o arquivo de ajuda para o módulo de script no qual o fluxo de trabalho de script é definido. Por exemplo:

```
<ScriptModule>.psm1-help.xml
```

Ao contrário de outros comandos em script, fluxos de trabalho de script não exigem um `.ExternalHelp` comentar a palavra-chave para associá-los a um arquivo de Ajuda. Em vez disso, o Windows PowerShell pesquisa os subdiretórios específicos da cultura de interface do usuário do diretório do módulo para arquivos de ajuda baseados em XML e procura ajuda para o fluxo de trabalho de script em todos os arquivos. `.ExternalHelp` Comente a palavra-chave são ignorados.

Porque o `.ExternalHelp` palavra-chave do comentário é ignorado, a `Get-Help` cmdlet pode encontrar ajuda para fluxos de trabalho de script apenas quando eles são incluídos nos módulos.