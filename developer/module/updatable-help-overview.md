---
title: Visão geral de ajuda atualizável | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: 3f7388a9-9fa8-42bc-b294-538c9a01e30a
caps.latest.revision: 12
ms.openlocfilehash: f2dfb9642ba2dde38124142b659b425bbbb00f37
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057596"
---
# <a name="updatable-help-overview"></a>Visão geral da ajuda atualizável

Este documento fornece uma introdução básica sobre o design e a operação do recurso de ajuda atualizável do Windows PowerShell. Ele é projetado para autores de módulo e de outras pessoas que fornecer tópicos da Ajuda do Windows PowerShell para usuários.

## <a name="introduction"></a>Introdução

Tópicos de Ajuda do Windows PowerShell são parte integrante da experiência do Windows PowerShell. Como módulos do Windows PowerShell, tópicos de ajuda são continuamente atualizados e aprimorados por autores e as contribuições da comunidade de usuários do Windows PowerShell.

O *Updatable Help* recurso, introduzido no Windows PowerShell 3.0, garante que os usuários tenham as versões mais recentes dos tópicos de Ajuda no prompt de comando, mesmo para comandos internos do Windows PowerShell, sem baixar novos módulos ou executando o Windows Update. A Ajuda atualizável facilita a atualização simples, fornecendo cmdlets que baixar as versões mais recentes dos tópicos de Ajuda da Internet e instalá-los nos subdiretórios corretos no computador local do usuário. Mesmo os usuários que estão atrás de firewalls podem usar os novos cmdlets para obter ajuda atualizada de um compartilhamento de arquivos internos.

A Ajuda atualizável é totalmente suportada por todos os módulos do Windows PowerShell no Windows® 8 e Windows Server® 2012 e seus recursos estão disponíveis para todos os autores de módulo do Windows PowerShell. A Ajuda atualizável dá suporte a apenas os arquivos de ajuda baseados em XML. Ele não oferece suporte a Ajuda baseada em comentário.

A Ajuda atualizável inclui os seguintes recursos.

- O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet, que determina se os usuários têm a Ajuda mais recentes de arquivos para um módulo e, se não estiver, baixa os arquivos de ajuda mais recentes da Internet, descompacta-os e instala-os nos subdiretórios de módulo correto no computador do usuário.
  Os usuários podem usar o [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet para exibir os tópicos da Ajuda recém-instalado imediatamente.
  Eles não precisam reiniciar o PowerShell.

- O [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet, que baixa a Ajuda mais recentes da Internet e os salva em um diretório de sistema de arquivos. Os usuários podem usar o `Update-Help` cmdlet para obter os arquivos de Ajuda do diretório do sistema de arquivos e descompactar e instalá-los nos subdiretórios de módulo no computador do usuário. O `Save-Help` cmdlet é projetado para os usuários que têm limitado ou sem acesso à Internet e para as empresas que preferem limitar o acesso à Internet.

- **Ajuda para um módulo**. Arquivos de ajuda para um módulo são gerenciados e fornecidos como uma unidade, para que os usuários podem obter todos os arquivos de ajuda para os módulos que eles usam. A Ajuda atualizável só tem suporte para módulos, não para o snap-ins do Windows PowerShell.

- **Suporte à versão**. A Ajuda atualizável usa o padrão quatro posição (N1. N2. N3. Números de versão N4). A Ajuda atualizável baixa arquivos de ajuda quando o número de versão da Ajuda de arquivos no computador do usuário (ou no `Save-Help` directory) é menor do que o número de versão dos arquivos de Ajuda no local da Internet.

- **Suporte a vários idiomas**. A Ajuda atualizável dá suporte a arquivos de Ajuda do módulo em várias culturas de interface do usuário. A Ajuda atualizável nomes de arquivo incluem os códigos de idioma padrão, como "en-US" e "ja-JP" e o `Update-Help` e `Save-Help` cmdlets colocar os arquivos de Ajuda em subdiretórios específicos do idioma do diretório do módulo.

- **A Ajuda gerada automaticamente**. O [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet exibe a Ajuda básica para os comandos que não tem arquivos de Ajuda. A Ajuda gerada automaticamente inclui a sintaxe de comando e aliases e instruções sobre como usar a Ajuda online e ajuda atualizável.

- **Aprimorada a Ajuda Online**. Acesso fácil a Ajuda on-line não requer mais arquivos de Ajuda. O **Online** parâmetro do `Get-Help` agora obtém a URL de um tópico da Ajuda online do valor da **HelpUri** propriedade de qualquer comando, se ele não é possível localizar a URL de Ajuda online em um arquivo de Ajuda. Você pode preencher a **HelpUri** propriedade com a adição de uma **HelpUri** de atributo para o código de cmdlets, funções e comandos CIM, ou usando o **. Link** diretiva ajuda baseada em comentário em fluxos de trabalho e scripts.

  Para tornar nossos arquivos de ajuda atualizável, os módulos do Windows PowerShell no Windows 8 e Windows Server vNext não vêm com arquivos de Ajuda. Os usuários podem usar a Ajuda atualizável para instalar arquivos de Ajuda e atualizá-los. Os autores de outros módulos podem incluir arquivos de Ajuda em módulos ou omiti-los. Suporte para ajuda atualizável é opcional, mas recomendado.
