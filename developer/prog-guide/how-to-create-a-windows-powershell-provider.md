---
title: Como criar um provedor do Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide]
- providers [PowerShellProgrammer's Guide], creating
- Windows PowerShell Programmer's Guide, providers
ms.assetid: 863e48e9-7206-4c6a-a59a-2ab2d30396bc
caps.latest.revision: 5
ms.openlocfilehash: 06910f32752668f13400f9be0767a2179133df04
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623816"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>Como criar um provedor do Windows PowerShell

Esta seção descreve como criar um provedor do Windows PowerShell. Um provedor do Windows PowerShell pode ser considerado de duas maneiras. Para o usuário, o provedor representa um conjunto de dados armazenados. Por exemplo, os dados armazenados podem ser a Metabase do serviços de informações da Internet (IIS), o registro do Microsoft Windows, o sistema de arquivos do Windows, Active Directory e os dados de alias e variável armazenados pelo Windows PowerShell.

Para o desenvolvedor, o provedor do Windows PowerShell é a interface entre o usuário e os dados que o usuário precisa acessar. Sob essa perspectiva, cada tipo de provedor descrito nesta seção, dá suporte a um conjunto de classes específicas de base e interfaces que permitem que o tempo de execução do Windows PowerShell para expor determinados cmdlets para o usuário de uma maneira comum.

## <a name="providers-provided-by-windows-powershell"></a>Provedores fornecidos pelo Windows PowerShell

Windows PowerShell fornece vários provedores (por exemplo, o provedor FileSystem, o provedor de registro e o provedor Alias) que são usados para acessar armazenamentos de dados conhecidos. Para obter mais informações sobre os provedores fornecidos pelo Windows PowerShell, use o comando a seguir para acessar a Ajuda online:

**PS > get-help about_providers**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>Acessando os dados armazenados usando os caminhos do Windows PowerShell

Provedores do Windows PowerShell são acessíveis para o tempo de execução do Windows PowerShell e comandos de forma programática com o uso de caminhos do Windows PowerShell. Na maioria das vezes, esses caminhos são usados para acessar diretamente os dados por meio do provedor. No entanto, alguns caminhos podem ser resolvidos para caminhos de provedor interno que permitem que um cmdlet para usar as interfaces de programação de aplicativo (APIs) do não sejam do Windows PowerShell para acessar os dados. Para obter mais informações sobre como os provedores do Windows PowerShell funcionam dentro do Windows PowerShell, consulte [como o Windows PowerShell funciona](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>Unidades de expor Cmdlets do provedor usando o Windows PowerShell

Um provedor do Windows PowerShell expõe seus cmdlets com suporte usando unidades virtuais do Windows PowerShell. Windows PowerShell aplica as seguintes regras para uma unidade do Windows PowerShell:

- O nome de uma unidade pode ser qualquer sequência de alfanumérica.

- Uma unidade pode ser especificada em qualquer ponto válido em um caminho, chamado "root".

- Uma unidade pode ser implementada para todos os dados armazenados, não apenas o sistema de arquivos.

- Cada unidade mantém seu próprio local de trabalho atual, permitindo que o usuário manter o contexto ao deslocar entre unidades.

## <a name="in-this-section"></a>Nesta seção

A tabela a seguir lista os tópicos que incluem exemplos de código que se baseiam uns nos outros. Começando com o segundo tópico, o provedor básico do Windows PowerShell pode ser inicializado e não inicializado pelo tempo de execução do Windows PowerShell, o próximo tópico adiciona funcionalidade para acessar os dados, o próximo tópico adiciona funcionalidade para manipulação de dados ( os itens nos dados armazenados), e assim por diante.

|Tópico|Definição|
|-----------|----------------|
|[Criando o provedor do Windows PowerShell](./designing-your-windows-powershell-provider.md)|Este tópico aborda as coisas que você deve considerar antes de implementar um provedor do Windows PowerShell. Ela resume as classes base do provedor do Windows PowerShell e interfaces que são usados.|
|[Criar um provedor de PowerShell do Windows básico](./creating-a-basic-windows-powershell-provider.md)|Este tópico mostra como criar um provedor do Windows PowerShell que permite que o tempo de execução do Windows PowerShell inicializar e inicializar o provedor.|
|[Criar um provedor de unidade do PowerShell do Windows](./creating-a-windows-powershell-drive-provider.md)|Este tópico mostra como criar um provedor do Windows PowerShell que permite ao usuário acessar um armazenamento de dados por meio de uma unidade do Windows PowerShell.|
|[Criar um provedor de Item do PowerShell do Windows](./creating-a-windows-powershell-item-provider.md)|Este tópico mostra como criar um provedor do Windows PowerShell que permite ao usuário manipular os itens em um repositório de dados.|
|[Criar um provedor de contêiner do Windows PowerShell](./creating-a-windows-powershell-container-provider.md)|Este tópico mostra como criar um provedor do Windows PowerShell que permite ao usuário trabalhar em armazenamentos de dados de várias camadas.|
|[Criar um provedor de navegação do Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md)|Este tópico mostra como criar um provedor do Windows PowerShell que permite que o usuário navegue os itens de um armazenamento de dados de forma hierárquica.|
|[Criar um provedor de conteúdo do PowerShell do Windows](./creating-a-windows-powershell-content-provider.md)|Este tópico mostra como criar um provedor do Windows PowerShell que permite ao usuário manipular o conteúdo dos itens em um repositório de dados.|
|[Criar um provedor de propriedade PowerShell do Windows](./creating-a-windows-powershell-property-provider.md)|Este tópico mostra como criar um provedor do Windows PowerShell que permite ao usuário manipular as propriedades dos itens em um repositório de dados.|

## <a name="see-also"></a>Consulte Também

[Como funciona o Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[SDK do Windows PowerShell](../windows-powershell-reference.md)

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)
