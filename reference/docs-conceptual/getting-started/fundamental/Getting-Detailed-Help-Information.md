---
ms.date: 08/27/2018
keywords: powershell, cmdlet
title: Obtendo informações de ajuda detalhadas
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: d2578604ec7c01c0b2734bd180e1babaca58b153
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851265"
---
# <a name="getting-detailed-help-information"></a>Obtendo informações de ajuda detalhadas

O PowerShell inclui artigos detalhados de Ajuda que explicam os conceitos do PowerShell e a linguagem do PowerShell. Também há artigos de Ajuda para cada cmdlet e tópicos de provedor e para muitas funções e scripts.

Você pode exibir esses artigos de Ajuda no prompt de comando ou exibir as versões mais atualizadas dos seguintes artigos na documentação online do [PowerShell](/powershell/scripting/powershell-scripting).

## <a name="getting-help-for-cmdlets"></a>Obter ajuda para cmdlets

Para obter Ajuda sobre cmdlets do PowerShell, use o cmdlet [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help). Por exemplo, para obter Ajuda para o cmdlet `Get-ChildItem`, digite:

```powershell
Get-Help Get-ChildItem
```

ou

```powershell
Get-ChildItem -?
```

Você pode até mesmo obter ajuda para o cmdlet Get-Help. Por exemplo:

```powershell
Get-Help Get-Help
```

Para obter uma lista de todos os artigos de Ajuda de cmdlet em sua sessão, digite:

```powershell
Get-Help -Category Cmdlet
```

Para exibir uma página por vez de cada artigo de Ajuda, use a função `help` ou seu alias `man`.
Por exemplo, para exibir a Ajuda sobre o cmdlet `Get-ChildItem`, digite

```powershell
man Get-ChildItem
```

ou

```powershell
help Get-ChildItem
```

Para exibir informações detalhadas, use o parâmetro **Detailed** do cmdlet `Get-Help`. Por exemplo, para obter informações detalhadas sobre o cmdlet `Get-ChildItem`, digite:

```powershell
Get-Help Get-ChildItem -Detailed
```

Para exibir todo o conteúdo do artigo de Ajuda, use o parâmetro **Full** do cmdlet `Get-Help`. Por exemplo, para exibir todo o conteúdo do artigo de Ajuda do cmdlet `Get-ChildItem`, digite:

```powershell
Get-Help Get-ChildItem -Full
```

Para obter Ajuda detalhada para os parâmetros de um cmdlet, use o parâmetro **Parameter** do cmdlet `Get-Help`. Por exemplo, para obter Ajuda detalhada para todos os parâmetros do cmdlet `Get-ChildItem`, digite:

```powershell
Get-Help Get-ChildItem -Parameter *
```

Para exibir apenas os exemplos em um artigo de Ajuda, use o parâmetro **Examples** de `Get-Help`.
Por exemplo, para exibir apenas os exemplos no artigo de Ajuda para o cmdlet `Get-ChildItem `, digite:

```powershell
Get-Help Get-ChildItem -Examples
```

Para obter informações de como escrever artigos de Ajuda para os cmdlets que você escreve, confira [Como escrever a Ajuda do cmdlet](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).

## <a name="getting-conceptual-help"></a>Obter ajuda conceitual

O cmdlet `Get-Help` também exibe informações sobre artigos conceituais no PowerShell, incluindo artigos sobre a linguagem do PowerShell. Artigos de Ajuda conceituais começam com o prefixo "about_", como about_line_editing. (O nome do artigo conceitual deve ser inserido em inglês, mesmo em versões do PowerShell em idiomas diferentes do inglês).

Para exibir uma lista de artigos conceituais, digite:

```powershell
Get-Help about_*
```

Para exibir um artigo de Ajuda específico, digite o nome do tópico, por exemplo:

```powershell
Get-Help about_command_syntax
```

Os parâmetros de `Get-Help`, como **Detailed**, **Parameter** e **Examples** não têm efeito sobre a exibição dos artigos conceituais da Ajuda.

## <a name="getting-help-about-providers"></a>Obter ajuda sobre provedores

O cmdlet `Get-Help` exibe informações sobre provedores do PowerShell. Para obter Ajuda para um provedor, digite `Get-Help` seguido pelo nome do provedor. Por exemplo, para obter Ajuda para o provedor de Registro, digite:

```powershell
Get-Help registry
```

Para obter uma lista de todos os artigos de Ajuda de provedor em sua sessão, digite

```powershell
Get-Help -Category provider
```

Os parâmetros de `Get-Help`, como **Detailed**, **Parameter** e **Examples** não têm efeito sobre a exibição dos artigos de Ajuda referentes ao provedor.

## <a name="getting-help-about-scripts-and-functions"></a>Obter ajuda sobre scripts e funções

Muitos scripts e funções no PowerShell têm artigos de Ajuda. Use o cmdlet `Get-Help` para exibir os artigos de Ajuda para scripts e funções.

Para exibir a Ajuda para uma função, digite `Get-Help` seguido pelo nome da função. Por exemplo, para obter Ajuda para a função `Disable-PSRemoting`, digite:

```powershell
Get-Help Disable-PSRemoting
```

Para exibir a Ajuda para um script, digite o caminho até o arquivo de script. Se o script não estiver em um caminho listado na variável de ambiente Path, será necessário usar o caminho totalmente qualificado.

Por exemplo, se você tiver um script chamado "TestScript.ps1" no diretório C:\\PS-Test, para exibir o artigo de Ajuda do script, digite:

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

Os parâmetros projetados para exibir a Ajuda do cmdlet também funcionam para a Ajuda de script e de função. No entanto, a ajuda para funções e scripts não é exibida quando você executa `Get-Help *`.

Para saber mais sobre como escrever artigos de Ajuda para suas funções e scripts, consulte os artigos a seguir:

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a>Obter ajuda online

Exibir artigos de Ajuda online é uma das melhores maneiras de obter ajuda. Os artigos online são mais fáceis de atualizar e fornecem o conteúdo mais atual.

Para obter Ajuda online, use o parâmetro **Online** do cmdlet `Get-Help`. Todos os artigos de Ajuda que acompanham o PowerShell, incluindo a Ajuda do provedor e artigos conceituais de Ajuda (Sobre), estão disponíveis online na documentação do [PowerShell](/powershell/scripting/powershell-scripting).

> [!NOTE]
> Não é possível usar o parâmetro **Online** com artigos de Ajuda do provedor ou conceituais (about_\*).
> A ajuda online é opcional, portanto não funciona para todos os cmdlets, funções ou scripts.

Por exemplo, para obter a versão online do artigo de Ajuda sobre o cmdlet `Get-ChildItem`, digite:

```powershell
Get-Help Get-ChildItem -Online
```

O PowerShell abre o artigo em seu navegador padrão. Se a Ajuda online tiver suporte para um artigo de Ajuda, você também poderá exibir a URL do artigo de Ajuda. A URL aparece na seção Links Relacionados de um artigo de Ajuda.

Por exemplo, para ver a URL da versão online do cmdlet Add-Computer, digite:

```powershell
Get-Help Add-Computer
```

A primeira linha na seção Links Relacionados do artigo é mostrada abaixo.

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

Para saber mais sobre como fornecer suporte online dos artigos de Ajuda, confira [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

## <a name="see-also"></a>Consulte também

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [Get-Help](/powershell/module/microsoft.powershell.core/get-help)
