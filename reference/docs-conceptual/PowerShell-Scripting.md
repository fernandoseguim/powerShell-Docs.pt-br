---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Scripts do PowerShell
ms.openlocfilehash: c6ba3abc2544834e2cbec16a524f79399a1d2599
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094044"
---
# <a name="powershell"></a>PowerShell

Desenvolvido na plataforma .NET Framework, o PowerShell é uma linguagem de scripts e um shell de linha de comando baseado em tarefas. Ele foi desenvolvido especificamente para administradores de sistema e usuários avançados, com a finalidade de automatizar rapidamente a administração de vários sistemas operacionais (Linux, macOS, Unix e Windows) e os processos relacionados aos aplicativos executados nesses sistemas operacionais.

## <a name="powershell-is-open-source"></a>O PowerShell é um software livre

O código-fonte base do PowerShell agora está disponível no GitHub e está aberto para contribuições da comunidade.
Confira a [Fonte do PowerShell no GitHub](https://github.com/powershell/powershell).

Você pode começar com as partes de que precisa em [Obter PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).
Ou, talvez, com um tour rápido em [Guia de Introdução](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)

## <a name="powershell-design-goals"></a>Metas de design do PowerShell
O PowerShell foi projetado para melhorar o ambiente de script e de linha de comando eliminando problemas antigos e adicionando novos recursos.

### <a name="discoverability"></a>Detectabilidade
O PowerShell facilita a descoberta dos seus recursos. Por exemplo, para localizar uma lista de cmdlets que exibem e alteram os serviços do Windows, digite:

```powershell
Get-Command *-Service
```

Depois de descobrir qual cmdlet realiza uma tarefa, você pode saber mais sobre ele usando o cmdlet `Get-Help`.
Por exemplo, para exibir a ajuda sobre o cmdlet `Get-Service`, digite:

```powershell
Get-Help Get-Service
```
A maioria dos cmdlets emite objetos que podem ser manipulados e renderizados no texto para exibição.
Para entender por completo a saída desse cmdlet, direcione a saída para o cmdlet `Get-Member`.
Por exemplo, o comando a seguir exibe informações sobre os membros da saída do objeto pelo cmdlet `Get-Service`.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Consistência
Gerenciar os sistemas pode ser um desafio complexo e as ferramentas que têm uma interface consistente ajudam a controlar a complexidade inerente.
Infelizmente, nem as ferramentas de linha de comando, nem objetos COM programáveis são conhecidos por sua consistência.

A consistência do PowerShell é um de seus principais ativos.
Por exemplo, se você aprender a usar o cmdlet `Sort-Object`, poderá usar esse conhecimento para classificar a saída de qualquer cmdlet.
Você não precisa apender as diferentes rotinas de classificação de cada cmdlet.

Além disso, os desenvolvedores do cmdlet não precisam criar recursos de classificação para os seus cmdlets.
O PowerShell oferece uma estrutura que fornece os recursos básicos e os força a ser consistentes em vários aspectos da interface.
A estrutura elimina algumas das escolhas que normalmente são deixadas para o desenvolvedor, porém, em troca, ela torna o desenvolvimento de cmdlets robustos e fáceis de usar em algo muito mais simples.

### <a name="interactive-and-scripting-environments"></a>Ambientes interativos e de scripts
O PowerShell é um ambiente interativo e de script combinado que fornece acesso a ferramentas de linha de comando e objetos COM, permitindo também que você use o poder da FCL (Biblioteca de Classes .NET Framework).

Esse ambiente aprimora o Prompt de Comando do Windows, que fornece um ambiente interativo com várias ferramentas de linha de comando.
Ele também aprimora scripts do WSH (Windows Script Host), que permitem usar várias ferramentas de linha de comando e objetos de automação COM, mas não fornecem um ambiente interativo.

Combinando o acesso a todos esses recursos, o PowerShell amplia a capacidade do usuário interativo e do gravador de script e facilita o gerenciamento de administração do sistema.

### <a name="object-orientation"></a>Orientação a objeto
Embora você interaja com o PowerShell digitando comandos de texto, o PowerShell se baseia em objetos, não em texto.
A saída de um comando é um objeto.
Você pode enviar o objeto de saída para outro comando como sua entrada.
Como resultado, o PowerShell fornece uma interface familiar para pessoas com experiência em outros shells, apresentando ao mesmo tempo um paradigma de linha de comando novo e poderoso.
Ele estende o conceito de enviar dados entre comandos, permitindo enviar objetos em vez de texto.

### <a name="easy-transition-to-scripting"></a>Transição fácil para scripts
O PowerShell facilita a transição de uma digitação interativa de comandos para a criação e execução de scripts.
Você pode digitar comandos no prompt de comando do PowerShell para descobrir os comandos que executam uma tarefa.
Em seguida, você pode salvar esses comandos em uma transcrição ou um histórico antes de copiá-los para um arquivo para usar como um script.
