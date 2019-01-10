---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: galeria,powershell,cmdlet,psgallery
title: Pacotes com as edições do PowerShell ou do sistema operacional compatível
ms.openlocfilehash: 8230866561d3021379a48cc2c83fb4104a4058c1
ms.sourcegitcommit: d396d0e4cfe3d279f399c17e7337380a31d373ac
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747697"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>Pacotes com as edições do PowerShell ou em sistemas operacionais compatíveis

Da versão 5.1 em diante, o PowerShell está disponível em edições diferentes que denotam diversos conjuntos de recursos e compatibilidade de plataforma.

## <a name="searching-by-powershell-edition"></a>Pesquisar por edição do PowerShell 
As duas edições do Powershell são:
- Desktop Edition Baseado no .NET Framework e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell em execução em edições de superfície completa do Windows como núcleo de servidor e área de trabalho do Windows.
- **Core Edition:** Baseada no .NET Core e fornece compatibilidade com scripts e módulos destinados a versões do PowerShell em execução em edições de volume reduzido do Windows, como o Nano Server e Windows IoT.

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>Galeria do PowerShell lhe permite filtrar os pacotes compatíveis para edições específicas do PowerShell

Se um pacote tem compatível PSEditions especificado, eles são listados como parte das edições do PowerShell na página de exibição do pacote e também nos resultados de pacotes.
Você também pode procurar pacotes compatíveis usando o PowerShell.

![Página de exibição do item com PSEditions](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>Procurar pacotes na Galeria de interface do usuário que funcionam no PowerShell Core

Use as marcas: "PSEdition_Desktop" e "PSEdition_Core" para filtrar os pacotes na Galeria do PowerShell.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Use as marcas: "PSEdition_Core" para pesquisar itens compatíveis com o PowerShell Core Edition.

![Resultados da pesquisa para itens compatíveis com o Core PSEdition](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Use as marcas: "PSEdition_Desktop" para pesquisar itens compatíveis com o PowerShell Desktop Edition.

![Resultados da pesquisa para itens compatíveis com o Desktop PSEdition](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>Procurar pacotes encontrar as edições compatíveis usando o PowerShell
Você pode especificar marcas para filtrar para a edição do PowerShell e o sistema operacional. Você usa o `Find-Package` cmdlet especificando o `-Tag` parâmetro para especificar a edição (e o sistema operacional) destinados.
Assim:

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>Pesquisar pelo sistema operacional 

Uma vez que o PowerShell Core está disponível para Windows, Linux e MacOS, pacotes na galeria podem ser projetados para qualquer combinação desses sistemas operacionais. Na Galeria de interface do usuário, use as seguintes marcas searchs encontrar pacotes marcados pelo sistema operacional:

- Marcações: “Windows”
- Marcações: “Linux”
- Marcações: “MacOS” 

Você pode especificar essas marcas em `Find-Module` (e outros cmdlets no módulo do PowerShellGet), semelhante a esta:

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>Pesquisando vários compatibilidades

Você pode procurar por um pacote que tem vários compatibilidades usando a sintaxe: 

Marcas "Compatibility1" "Compatibility2" 

Por exemplo, se você estiver procurando por um pacote com o PowerShell Core compatibilidade que é executado em computadores meu Windows e Linux, use as marcas de pesquisa:

Marcas "PSEdition_Core" "Windows" "Linux" 

Para pesquisar usando o PowerShell, você pode usar o `Find-Module` (e outros cmdlets no módulo do PowerShellGet), semelhante a esta:

```powewrshell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Mais detalhes sobre como criar e localizar os pacotes com as edições compatíveis do PowerShell

- [Módulos com PSEditions](../../concepts/module-psedition-support.md)
- [Scripts com PSEditions](../../concepts/script-psedition-support.md)
