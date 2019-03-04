---
title: Referência do Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell SDK
ms.assetid: cbba4879-bcac-484a-9906-4bbe2cd1eb33
caps.latest.revision: 11
ms.openlocfilehash: dfda6cb68b089a30a156760345420ee80d1d3ae9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862102"
---
# <a name="windows-powershell-reference"></a>Referência do Windows PowerShell

Windows PowerShell é um ambiente de conectados ao .NET Framework do Microsoft criado para a automação administrativa. Windows PowerShell fornece uma nova abordagem para compilar comandos, composição de soluções e criação gráfica do usuário de ferramentas de gerenciamento baseado em interface.

Windows PowerShell permite que um administrador de sistema automatizem a administração de recursos do sistema pela execução de comandos diretamente ou por meio de scripts.

## <a name="developer-audience"></a>Público de desenvolvedores

O Software Development Kit (SDK) do Windows PowerShell foi criado para desenvolvedores de comando que exigem informações de referência sobre as APIs fornecidas pelo Windows PowerShell. Os desenvolvedores do comando usam Windows PowerShell para criar comandos e provedores que estendem as tarefas que podem ser executadas pelo Windows PowerShell.

## <a name="windows-powershell-resources"></a>Recursos do Windows PowerShell

Além do SDK do Windows PowerShell, os recursos a seguir fornecem mais informações.

[Introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) fornece uma introdução ao Windows PowerShell: o idioma, os cmdlets, provedores e o uso de objetos.

[Escrevendo um módulo do Windows PowerShell](./module/writing-a-windows-powershell-module.md) fornece informações e exemplos para administradores, desenvolvedores de script e os desenvolvedores de cmdlet que precisam empacotar e distribuir suas soluções do Windows PowerShell usando módulos do Windows PowerShell.

[Escrevendo um Cmdlet do Windows PowerShell](./cmdlet/writing-a-windows-powershell-cmdlet.md) fornece informações e exemplos de código para gerentes de programa que estão criando cmdlets e para os desenvolvedores que estão implementando o código do cmdlet.

[Blog da equipe do Windows PowerShell](https://blogs.msdn.microsoft.com/PowerShell/) o melhor recurso para aprender e colaborar com outros usuários do Windows PowerShell. Leia o blog da equipe do Windows PowerShell e, em seguida, ingressar o fórum de usuários do Windows PowerShell (PowerShell). Use o Windows Live Search para encontrar outros blogs do Windows PowerShell e recursos. Em seguida, à medida que você desenvolve sua experiência, livremente contribuir com suas ideias.

[Navegador de módulo do PowerShell](/powershell/module/) fornece as versões mais recentes dos tópicos da Ajuda de linha de comando.

## <a name="class-libraries"></a>Bibliotecas de classes

[Automation](/dotnet/api/System.Management.Automation) esse é o namespace raiz para o Windows PowerShell. Ele contém as classes, enumerações e interfaces necessárias para implementar cmdlets personalizados. Em particular, o [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) é a classe base da qual cmdlet todas as classes devem ser derivadas. Para obter mais informações sobre os cmdlets, consulte.

[System.Management.Automation.Provider](/dotnet/api/System.Management.Automation.Provider) este namespace contém as classes, enumerações e interfaces necessárias para implementar um provedor do Windows PowerShell. Em particular, o [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) é a classe base da qual PowerShell Windows todas as classes de provedor devem ser derivadas.

[Microsoft.Powershell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) este namespace contém classes para os cmdlets e provedores implementados pelo Windows PowerShell. Da mesma forma, é recomendável que você crie uma *YourName*. Os comandos de namespace para os cmdlets que você implementar.

[System.Management.Automation.Host](/dotnet/api/System.Management.Automation.Host) este namespace contém as classes, enumerações e interfaces que o cmdlet usa para definir a interação entre o usuário e o Windows PowerShell.

[System.Management.Automation.Internal](/dotnet/api/System.Management.Automation.Internal) este namespace contém as classes base usadas por outras classes do namespace. Por exemplo, o [System.Management.Automation.Internal.Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute) é a classe base para o [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) classe.

[System.Management.Automation.Runspaces](/dotnet/api/System.Management.Automation.Runspaces) este namespace contém as classes, enumerações e interfaces usadas para criar um espaço de execução do Windows PowerShell. Nesse contexto, o espaço de execução do Windows PowerShell é o contexto no qual um ou mais pipelines de Windows PowerShell invocar cmdlets. Ou seja, os cmdlets funcionam dentro do contexto de um espaço de execução do Windows PowerShell. Para obter mais informações aboutWindows runspaces do PowerShell, consulte [espaços de execução do Windows PowerShell](http://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9).
