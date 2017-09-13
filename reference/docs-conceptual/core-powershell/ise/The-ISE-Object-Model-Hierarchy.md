---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: A hierarquia de modelo do objeto do ISE
ms.openlocfilehash: 2df6d40f39dbe14bd3f46a6400cde4a6e91052ef
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2017
---
# <a name="the-ise-object-model-hierarchy"></a>A hierarquia de modelo do objeto do ISE
Este tópico mostra a hierarquia de objetos que fazem parte do ISE (Ambiente de Script Integrado) do Windows PowerShell. O ISE do Windows PowerShell está incluído no Windows PowerShell 3.0 e no Windows PowerShell 4.0. Clique um objeto para levá-lo até a documentação de referência da classe que define o objeto.

## <a name="psise-object"></a>Objeto $psISE

O objeto **$psISE** é o [objeto raiz](The-ObjectModelRoot-Object.md) da hierarquia de objeto ISE do Windows PowerShell.
Localizado no nível superior, disponibiliza os seguintes objetos para script:

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE.CurrentFile](The-ISEFile-Object.md)

O objeto **$psISE.CurrentFile** é uma instância da classe [ISEFile](The-ISEFile-Object.md).

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)

O objeto **$psISE.CurrentPowerShellTab** é uma instância da classe [PowerShellTab](The-PowerShellTab-Object.md).

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE.CurrentVisibleHorizontalTool

O objeto **$psISE.CurrentVisibleHorizontalTool** é uma instância da classe [ISEAddOnTool](The-ISEAddOnTool-Object.md).
Ele representa a ferramenta complementar instalada que está encaixada atualmente na borda superior da janela do ISE do Windows PowerShell.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE.CurrentVisibleVerticalTool

O objeto **$psISE.CurrentVisibleHorizontalTool** é uma instância da classe [ISEAddOnTool](The-ISEAddOnTool-Object.md).
Ele representa a ferramenta complementar instalada que está encaixada atualmente na borda superior direita da janela do ISE do Windows PowerShell.

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE.Options](The-ISEOptions-Object.md)

O objeto **$psISE.Options** é uma instância da classe [ISEOptions](The-ISEOptions-Object.md).
O objeto ISEOptions representa várias configurações para o ISE do Windows PowerShell.
Ele é uma instância da classe Microsoft.PowerShell.Host.ISE.ISEOptions.

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)

O objeto **$psISE.PowerShellTabs** é uma instância da classe [PowerShellTabCollection](The-PowerShellTabCollection-Object.md).
É uma coleção de todas as guias do PowerShell abertas no momento que representam os ambientes de execução disponíveis do Windows PowerShell no computador local ou em computadores remotos conectados. Cada membro da coleção é uma instância da classe [PowerShellTab](The-PowerShellTab-Object.md).

## <a name="see-also"></a>Consulte Também
- [O modelo de objeto de script do ISE do Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Referência de modelo de objeto do ISE do Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md)
