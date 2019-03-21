---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: galeria,powershell,cmdlet,psgallery
title: Pacotes com edições do PowerShell ou sistema operacional compatível
ms.openlocfilehash: 14038aa9b0453e1d06e6587e97da391b56297c75
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58057171"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>Pacotes com edições do PowerShell ou sistemas operacionais compatíveis

Da versão 5.1 em diante, o PowerShell está disponível em edições diferentes que denotam diversos conjuntos de recursos e compatibilidade de plataforma.

## <a name="searching-by-powershell-edition"></a>Pesquisar por edição do PowerShell

As duas edições do PowerShell são:
- **Desktop Edition:** criada no .NET Framework, fornece compatibilidade com scripts e módulos destinados a versões do PowerShell em execução em edições de volume completo do Windows, como Server Core e Windows Desktop.
- **Core Edition:** criada no .NET Core, oferece compatibilidade com scripts e módulos destinados a versões do PowerShell executadas em edições de volume reduzido do Windows, como o Nano Server e Windows IoT.

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>A Galeria do PowerShell permite filtrar pacotes compatíveis com edições específicas do PowerShell

Se um pacote tiver PSEditions compatíveis especificadas, elas serão listadas como parte das "Edições do PowerShell" na página de exibição do pacote e nos resultados de pacotes.
Você também pode pesquisar pacotes compatíveis usando o PowerShell.

![Página de exibição do item com PSEditions](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>Pesquisar pacotes na interface do usuário da galeria que funcionam no PowerShell Core

Use as marcas: "PSEdition_Desktop" e "PSEdition_Core" para filtrar os pacotes na Galeria do PowerShell.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Use as marcas: "PSEdition_Core" para pesquisar itens compatíveis com o PowerShell Core Edition.

![Resultados da pesquisa para itens compatíveis com o Core PSEdition](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Use as marcas: "PSEdition_Desktop" para pesquisar itens compatíveis com o PowerShell Desktop Edition.

![Resultados da pesquisa para itens compatíveis com o Desktop PSEdition](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>Pesquisar pacotes para encontrar edições compatíveis usando o PowerShell
Você pode especificar marcas para filtrar o sistema operacional e a edição do PowerShell.
Use o cmdlet `Find-Package` especificando o parâmetro `-Tag` para especificar a edição (e sistema operacional) de destino.
Dessa forma:

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>Pesquisando por sistema operacional

Uma vez que o PowerShell Core está disponível para Windows, Linux e MacOS, os pacotes na Galeria podem ter sido criados para qualquer combinação desses sistemas operacionais. Na interface do usuário da Galeria, use as seguintes marcas de pesquisa para encontrar pacotes marcados por sistema operacional:

- Marcações: “Windows”
- Marcações: “Linux”
- Marcações: “MacOS”

Você pode especificar essas marcas em `Find-Module` (e outros cmdlets no módulo PowerShellGet), da seguinte forma:

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>Pesquisando várias compatibilidades

Você pode pesquisar por um pacote que tem várias compatibilidades usando a sintaxe:

Marcações: "Compatibility1" "Compatibility2"

Por exemplo, se você estiver procurando por um pacote com compatibilidade com o PowerShell Core que é executado em computadores Windows e Linux, use as marcas de pesquisa:

Marcações: "PSEdition_Core" "Windows" "Linux"

Para pesquisar usando o PowerShell, você pode usar o `Find-Module` (e outros cmdlets no módulo do PowerShellGet), da seguinte forma:

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Mais detalhes sobre como criar e localizar os pacotes com as edições compatíveis do PowerShell

- [Módulos com PSEditions](../../concepts/module-psedition-support.md)
- [Scripts com PSEditions](../../concepts/script-psedition-support.md)
