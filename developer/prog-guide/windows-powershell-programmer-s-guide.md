---
title: O programador do Windows PowerShell&#39;guia de s | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell Programmer's Guide
ms.assetid: f3aaf667-af84-4ea8-a5ad-d454d0d700b8
caps.latest.revision: 9
ms.openlocfilehash: 1f7b5b60b202f4de0cf3d44b65057f5edd41f2b0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860042"
---
# <a name="windows-powershell-programmer39s-guide"></a>O programador do Windows PowerShell&#39;guia

Guia do programador, esta é destinado a desenvolvedores que estejam interessados no fornecimento de um ambiente de linha de comando de gerenciamento para administradores de sistema. Windows PowerShell fornece uma maneira simples para você criar comandos de gerenciamento que expõem os objetos .NET, enquanto permite que o Windows PowerShell fazer a maioria do trabalho para você.

No desenvolvimento de comando tradicionais, você deve escrever um analisador de parâmetro, um associador de parâmetro, filtros e todas as demais funcionalidades expostas por cada comando. Windows PowerShell oferece o seguinte para tornar mais fácil de escrever comandos:

- Um poderoso do Windows PowerShell em tempo de execução (mecanismo de execução) com seu próprio analisador e um mecanismo para associar automaticamente os parâmetros de comando.

- Utilitários para formatar e exibir os resultados do comando usando um interpretador de linha de comando (CLI).

- Suporte para altos níveis de funcionalidade (por meio de provedores do Windows PowerShell) que tornam fácil acessar dados armazenados.

  Baixo custo, você pode representar um objeto .NET por um comando avançado ou conjunto de comandos que oferecem uma experiência de linha de comando completa para o administrador.

  A próxima seção aborda os principais conceitos do Windows PowerShell e os termos. Familiarize-se com esses conceitos e termos antes de iniciar o desenvolvimento.

## <a name="about-windows-powershell"></a>Sobre o Windows PowerShell

Windows PowerShell define vários tipos de comandos que você pode usar no desenvolvimento. Esses comandos incluem: funções, filtros, scripts, aliases e executáveis (aplicativos). O tipo de comando principal abordado neste guia é um comando simple, pequeno, chamado "cmdlet". Windows PowerShell fornece um conjunto de cmdlets e dá suporte a personalização de cmdlet para se adequar ao seu ambiente. O tempo de execução do Windows PowerShell processa todos os tipos de comando, assim como acontece cmdlets, usando pipelines.

Além de comandos, o Windows PowerShell dá suporte a vários provedores do Windows PowerShell personalizáveis que tornam disponíveis conjuntos de cmdlets específicos. O shell deve operar dentro do aplicativo de host fornecidos pelo Windows PowerShell (Windows PowerShell.exe), mas é igualmente acessível a partir de um aplicativo de host personalizado que você pode desenvolver para atender às necessidades específicas. Para obter mais informações, consulte [como o Windows PowerShell funciona](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="windows-powershell-cmdlets"></a>Cmdlets do Windows PowerShell

Um cmdlet é um comando simples que é usado no ambiente do Windows PowerShell. O tempo de execução do Windows PowerShell invoca esses cmdlets dentro do contexto de scripts de automação que são fornecidos na linha de comando, e o tempo de execução do Windows PowerShell também invoca-los programaticamente por meio de APIs do Windows PowerShell.

Para obter mais informações sobre os cmdlets, consulte [escrevendo um Cmdlet do Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).

### <a name="windows-powershell-providers"></a>Provedores do Windows PowerShell

Na execução de tarefas administrativas, o usuário talvez precise examinar os dados armazenados em um repositório de dados (por exemplo, o sistema de arquivos, o registro do Windows ou um repositório de certificados). Para facilitar essas operações, o Windows PowerShell define um módulo chamado de provedor do Windows PowerShell que pode ser usado para acessar um repositório de dados específicos, como o registro do Windows. Cada provedor dá suporte a um conjunto de cmdlets relacionados para dar ao usuário uma exibição simétrica dos dados no repositório.

Windows PowerShell fornece vários padrão provedores do Windows PowerShell. Por exemplo, o provedor Registry dá suporte à navegação e manipulação de registro do Windows. Chaves do registro são representadas como itens, e valores do registro são tratadas como propriedades.

Se você expõe um armazenamento de dados que o usuário precisar de acesso, você talvez precise escrever seu próprio provedor do Windows PowerShell, conforme descrito em [criação de provedores do Windows PowerShell](./how-to-create-a-windows-powershell-provider.md). Para obter mais informações aboutWindows provedores do PowerShell, consulte [como o Windows PowerShell funciona](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="host-application"></a>Aplicativo de host

Windows PowerShell inclui o padrão host aplicativo powershell.exe, que é um aplicativo de console que interage com o usuário e hospeda o tempo de execução do Windows PowerShell usando uma janela do console.

Raramente você precisará escrever seu próprio aplicativo de host para o Windows PowerShell, embora haja suporte para a personalização. Um caso em que o seu próprio aplicativo pode ser necessário é quando você tem um requisito para uma interface GUI que é mais sofisticada do que a interface fornecida pelo aplicativo host padrão. Você também poderá um aplicativo personalizado quando você estiver baseando sua GUI na linha de comando. Para obter mais informações, consulte[como criar um aplicativo de Host do Windows PowerShell](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07).

### <a name="windows-powershell-runtime"></a>O tempo de execução do Windows PowerShell

O tempo de execução do Windows PowerShell é o mecanismo de execução que implementa o processamento do comando. Ele inclui as classes que fornecem a interface entre o aplicativo host e os comandos do Windows PowerShell e os provedores. O tempo de execução do Windows PowerShell é implementado como um objeto de espaço de execução para a sessão atual do Windows PowerShell, que é o ambiente operacional em que o shell e os comandos a executam. Para obter detalhes operacionais, consulte [como o Windows PowerShell funciona](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="windows-powershell-language"></a>Idioma do Windows PowerShell

A linguagem do Windows PowerShell fornece funções de script e mecanismos para invocar comandos. Para obter informações completas de script, consulte que a referência de linguagem do Windows PowerShell acompanham o Windows PowerShell.

### <a name="extended-type-system-ets"></a>Sistema de tipo estendido (ETS)

Windows PowerShell fornece acesso a uma variedade de diferentes objetos, como .NET e XML. Como consequência, para apresentar uma abstração comum para todos os tipos de objeto, o shell usa seu sistema de tipo estendido (ETS). A maioria das funcionalidades ETS são transparente para o usuário, mas o script ou o desenvolvedor de .NET usa as seguintes finalidades:

- Exibindo um subconjunto de membros de objetos específicos. Windows PowerShell fornece uma exibição "adaptada" dos vários tipos de objeto específico.

- Adicionando membros a objetos existentes.

- Acesso serializado objetos.

- Gravação personalizadas de objetos.

  Usando ETS, você pode criar novos flexíveis "tipos" que são compatíveis com a linguagem do Windows PowerShell. Se você for um desenvolvedor .NET, será possível trabalhar com objetos usando a mesma semântica como a linguagem do Windows PowerShell se aplica ao script, por exemplo, para determinar se um objeto for avaliada como `true`.

  Para obter mais informações sobre o ETS e como o Windows PowerShell usa objetos, consulte [conceitos de objeto do Windows PowerShell](http://msdn.microsoft.com/en-us/12700631-be23-4e6b-9bf0-81ea0d166353).

## <a name="programming-for-windows-powershell"></a>Programação para o Windows PowerShell

Windows PowerShell define seu código para comandos, provedores e outros módulos do programa usando o .NET Framework. Você não se restringe o uso do Microsoft Visual Studio na criação de módulos personalizados para o Windows PowerShell, embora os exemplos fornecidos neste guia são conhecidos para executar nessa ferramenta. Você pode usar qualquer linguagem .NET que oferece suporte a herança de classe e o uso de atributos. Em alguns casos, as APIs do Windows PowerShell exigem a linguagem de programação para ser capaz de acessar tipos genéricos.

## <a name="programmers-reference"></a>Referência do programador

Para obter a referência ao desenvolver para o Windows PowerShell, consulte o [SDK do Windows PowerShell](../windows-powershell-reference.md).

## <a name="getting-started-using-windows-powershell"></a>Guia de Introdução usando o Windows PowerShell

Para obter mais informações sobre como começar a usar o shell do Windows PowerShell, consulte o [Introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) acompanham o Windows PowerShell. Um documento de três dobras de referência rápida também é fornecido como um livro de instruções para uso do cmdlet.

## <a name="contents-of-this-guide"></a>Conteúdo deste guia

|Tópico|Definição|
|-----------|----------------|
|[Como criar um provedor do Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)|Esta seção descreve como criar um provedor do Windows PowerShell para o Windows PowerShell.|
|[Como criar um aplicativo de Host do PowerShell do Windows](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07)|Esta seção descreve como escrever um aplicativo host que manipula um runspace e como escrever um aplicativo host que implementa seu próprio host personalizado.|
|[Como criar um Snap-in do PowerShell do Windows](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|Esta seção descreve como criar um snap-in que é usado para registrar todos os cmdlets e provedores em um assembly e como criar um snap-in personalizado.|
|[Como criar um Shell do Console](./how-to-create-a-console-shell.md)|Esta seção descreve como criar um shell de console que não é extensível.|
|[Conceitos do Windows PowerShell](./windows-powershell-concepts.md)|Esta seção contém informações conceituais que ajudarão você a entender o Windows PowerShell do ponto de vista de um desenvolvedor.|

## <a name="see-also"></a>Consulte Também

[SDK do Windows PowerShell](../windows-powershell-reference.md)