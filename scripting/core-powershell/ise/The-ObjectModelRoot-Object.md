---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet
ms.date: 2016-12-12
title: O objeto ObjectModelRoot
ms.technology: powershell
ms.assetid: 13fcf7ee-b18f-4499-a2b4-ccfc4484cd88
ms.openlocfilehash: f25dfea23ba865d98f09ae9b1604ade8b1c4f72a
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="the-objectmodelroot-object"></a>O objeto ObjectModelRoot
  O objeto **$psISE**, que é o objeto raiz da entidade de segurança no ISE (Ambiente de Script Integrado) do Windows PowerShell®, é uma instância da classe Microsoft.PowerShell.Host.ISE.ObjectModelRoot. Este tópico descreve as propriedades do objeto **ObjectModelRoot**.

## <a name="properties"></a>Propriedades

### <a name="currentfile"></a>CurrentFile
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém o arquivo, que é associada ao objeto host que atualmente tem o foco.

### <a name="currentpowershelltab"></a>CurrentPowerShellTab
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém a guia do PowerShell que tem o foco.

### <a name="currentvisiblehorizontaltool"></a>CurrentVisibleHorizontalTool
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém a ferramenta complementar do ISE do Windows PowerShell visível no momento que está localizada no painel de ferramentas horizontal na parte inferior do editor.

### <a name="currentvisibleverticaltool"></a>CurrentVisibleVerticalTool
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém a ferramenta complementar do ISE do Windows PowerShell visível no momento que está localizada no painel de ferramentas vertical no lado direito do editor.

### <a name="options"></a>Opções
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém as várias opções que podem alterar as configurações no ISE do Windows PowerShell.

### <a name="powershelltabs"></a>PowerShellTabs
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém a coleção de guias do PowerShell, que está aberta no ISE do Windows PowerShell. Por padrão, esse objeto contém uma guia do PowerShell. No entanto, é possível adicionar mais guias do PowerShell a esse objeto usando scripts ou usando os menus no ISE do Windows PowerShell.

## <a name="see-also"></a>Consulte Também
- [O modelo de objeto de script do ISE do Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referência de modelo de objeto do ISE do Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [A hierarquia de modelo de objeto do ISE](The-ISE-Object-Model-Hierarchy.md)

  
