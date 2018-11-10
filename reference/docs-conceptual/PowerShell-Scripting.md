---
ms.date: 08/27/2018
keywords: powershell, cmdlet
title: Scripts do PowerShell
ms.openlocfilehash: 07925ce8dcafd33970a703c9b241bf6f76f88d10
ms.sourcegitcommit: 47becf2823ece251a7264db2387bb503cf3abaa9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49451023"
---
# <a name="powershell"></a>PowerShell

O PowerShell é um shell de linha de comando baseado em tarefas e linguagem de script desenvolvido no .NET.
O PowerShell ajuda os administradores do sistema e os usuários avançados a automatizar rapidamente as tarefas que gerenciam processos e sistemas operacionais (Linux, macOS e Windows).

Os comandos do PowerShell permitem que você gerencie os computadores da linha de comando. Os provedores do PowerShell permitem o acesso a repositórios de dados, como o Registro e o repositório de certificados, de forma tão fácil quanto acessar o sistema de arquivos. O PowerShell inclui um valioso analisador de expressões e uma linguagem de scripts totalmente desenvolvida.

## <a name="powershell-is-open-source"></a>O PowerShell é um software livre

O código-fonte base do PowerShell agora está disponível no GitHub e está aberto para contribuições da comunidade.
Confira a [Fonte do PowerShell no GitHub](https://github.com/powershell/powershell).

Você pode começar com as partes de que precisa em [Obter PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).
Ou, talvez, com um tour rápido em [Guia de Introdução](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).

## <a name="powershell-design-goals"></a>Metas de design do PowerShell

O PowerShell foi projetado para melhorar o ambiente de script e de linha de comando eliminando problemas antigos e adicionando novos recursos.

### <a name="discoverability"></a>Detectabilidade

O PowerShell facilita a descoberta dos seus recursos. Por exemplo, para localizar uma lista de cmdlets que exibem e alteram os serviços do Windows, digite:

```powershell
Get-Command *-Service
```

Depois de descobrir qual cmdlet realiza uma tarefa, você pode saber mais sobre ele usando o cmdlet `Get-Help`. Por exemplo, para exibir a ajuda sobre o cmdlet `Get-Service`, digite:

```powershell
Get-Help Get-Service
```

A maioria dos cmdlets retorna objetos que podem ser manipulados e renderizados como texto para exibição. Para entender por completo a saída desse cmdlet, direcione a saída para o cmdlet `Get-Member`. Por exemplo, o comando a seguir exibe informações sobre os membros da saída do objeto pelo cmdlet `Get-Service`.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Consistência

O gerenciamento de sistemas pode ser uma tarefa complexa. As ferramentas que têm uma interface consistente ajudam a controlar a complexidade inerente. Infelizmente, as ferramentas de linha de comando e objetos COM programáveis em script não são conhecidos por sua consistência.

A consistência do PowerShell é um de seus principais ativos. Por exemplo, se você aprender a usar o cmdlet `Sort-Object`, poderá usar esse conhecimento para classificar a saída de qualquer cmdlet. Você não precisa apender as diferentes rotinas de classificação de cada cmdlet.

Além disso, os desenvolvedores de cmdlet não precisam criar recursos de classificação para os seus cmdlets. O PowerShell fornece uma estrutura com os recursos básicos que forçam a consistência. A estrutura elimina algumas opções que são deixadas para o desenvolvedor. Mas, em troca, ela torna o desenvolvimento de cmdlets muito mais simples.

### <a name="interactive-and-scripting-environments"></a>Ambientes interativos e de scripts

O Prompt de Comando do Windows fornece um shell interativo com o acesso a ferramentas de linha de comando e scripts básicos. O WSH (Windows Script Host) tem ferramentas de linha de comando programáveis por script e objetos de automação COM, mas não fornece um shell interativo.

O PowerShell combina um shell interativo e um ambiente de geração de script. O PowerShell pode acessar as ferramentas de linha de comando, objetos COM e bibliotecas de classes do .NET. Essa combinação de funcionalidades estende os recursos do usuário interativo, o produtor de script e o administrador do sistema.

### <a name="object-orientation"></a>Orientação do objeto

O PowerShell tem base no objeto, não no texto. A saída de um comando é um objeto. Você pode enviar o objeto de saída, pelo pipeline, para outro comando como entrada.

Esse pipeline fornece uma interface familiar para pessoas com experiência com outros shells. O PowerShell expande esse conceito, enviando objetos em vez de texto.

### <a name="easy-transition-to-scripting"></a>Transição fácil para scripts

A descoberta de comando do PowerShell facilita a transição de uma digitação interativa de comandos para a criação e execução de scripts. O histórico e as transcrições do PowerShell facilitam a cópia de comandos em um arquivo para uso como script.
