---
title: Escrevendo um módulo do Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 3c6d8e410427d6cfaa1c15db421b3fe935f7d322
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857932"
---
# <a name="writing-a-windows-powershell-module"></a>Escrever um módulo do Windows PowerShell

Este documento foi escrito para administradores, desenvolvedores de script e os desenvolvedores de cmdlet que precisam empacotar e distribuir seus cmdlets do Windows PowerShell. Usando módulos do Windows PowerShell, você pode empacotar e distribuir suas soluções do Windows PowerShell sem usar uma linguagem compilada.

Módulos do Windows PowerShell permitem que você a partição, organizam e abstraem o código do Windows PowerShell em unidades independentes e reutilizáveis. Com essas unidades reutilizáveis, você pode compartilhar facilmente seus módulos diretamente com outras pessoas. Se você for um desenvolvedor de script, você também pode reempacotar os módulos de terceiros para criar aplicativos personalizados baseados em script. Soluções de script pronta para produção que usam componentes reutilizáveis e redistribuíveis, com o benefício adicional de permitindo que você empacote e abstrair os vários componentes para habilitar a módulos, semelhantes aos módulos em outras linguagens de script como Perl e Python, Crie soluções personalizadas.

Em sua forma mais básica, Windows PowerShell tratará qualquer código de script do Windows PowerShell válido salvo em um arquivo. psm1 como um módulo. PowerShell tratará automaticamente qualquer assembly do cmdlet binário como um módulo. No entanto, você também pode usar um módulo (ou mais especificamente, um manifesto de módulo) para agrupar uma solução inteira. Os cenários a seguir descrevem os usos comuns para módulos do Windows PowerShell.

### <a name="libraries"></a>Bibliotecas

Módulos podem ser usados para empacotar e distribuir as bibliotecas coesas de funções que executam tarefas comuns. Normalmente, os nomes dessas funções compartilham um ou mais substantivos que refletem a tarefa comum que elas são usadas. Essas funções também podem ser semelhantes a classes do .NET Framework em que eles podem ter membros públicos e privados. Por exemplo, uma biblioteca pode conter um conjunto de funções para transferências de arquivos. Nesse caso, o substantivo refletindo a tarefa comum pode ser "arquivo".

### <a name="configuration"></a>Configuração

Módulos podem ser usados para personalizar seu ambiente com a adição de variáveis, provedores, funções e cmdlets específicos.

### <a name="compiled-code-development-and-distribution"></a>Desenvolvimento de código compilado e distribuição

Os desenvolvedores de cmdlet e o provedor podem usar módulos para testar e distribuir seu código compilado sem a necessidade de criar snap-ins. Eles podem importar o assembly que contém o código compilado como um módulo (um módulo binário) sem a necessidade de criar e registrar o snap-ins.

## <a name="see-also"></a>Consulte Também

[Noções básicas sobre um módulo do Windows PowerShell](./understanding-a-windows-powershell-module.md)

[Como escrever um módulo de Script do PowerShell](./how-to-write-a-powershell-script-module.md)

[Como escrever um módulo binário do PowerShell](./how-to-write-a-powershell-binary-module.md)

[Como escrever um manifesto de módulo do PowerShell](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)

[Modificando o caminho de instalação do PSModulePath](./modifying-the-psmodulepath-installation-path.md)

[Importando um módulo do PowerShell](./importing-a-powershell-module.md)

[Instalando um módulo do PowerShell](./installing-a-powershell-module.md)
