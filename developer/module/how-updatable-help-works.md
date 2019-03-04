---
title: Como Updatable Help funciona | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: 8874cc18416937c4d3cb30d801f2714410304c8c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860872"
---
# <a name="how-updatable-help-works"></a>Como a ajuda atualizável funciona

Este tópico explica como a Ajuda atualizável processos o arquivo XML HelpInfo CAB arquivos para cada módulo e instala atualizado ajuda para os usuários.

## <a name="the-update-help-process"></a>O processo de Update-Help

A lista a seguir descreve as ações do [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet quando um usuário executa um comando para atualizar os arquivos de ajuda para um módulo em uma determinada cultura da interface do usuário.
A lista a seguir descreve as ações do [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet quando um usuário executa um comando para atualizar os arquivos de ajuda para um módulo em uma determinada cultura da interface do usuário.

1. `Update-Help` Obtém o arquivo XML HelpInfo remoto do local especificado pelo valor de **HelpInfoURI** da chave no manifesto de módulo e valida o arquivo em relação ao esquema. (Para exibir o esquema, consulte [esquema de XML HelpInfo](./helpinfo-xml-schema.md).) Em seguida, `Update-Help` procurará um arquivo local de XML HelpInfo para o módulo no diretório do módulo no computador do usuário.

2. `Update-Help` compara o número de versão dos arquivos de ajuda para a cultura de interface do usuário especificada nos arquivos XML HelpInfo remotos e locais para o módulo. Se o número de versão no arquivo remoto é maior que o número de versão no arquivo local, ou não se houver nenhum arquivo XML HelpInfo local para o módulo, `Update-Help` prepara-se para baixar os novos arquivos de Ajuda.

3. `Update-Help` Seleciona o arquivo CAB para o módulo do local especificado o **HelpContentUri** elemento no arquivo XML HelpInfo remoto. Ele usa o nome do módulo, o GUID do módulo e a cultura de interface do usuário para identificar o arquivo CAB.

4. `Update-Help` baixa o arquivo CAB, descompacta-lo, valida os arquivos de conteúdo de Ajuda e salva a ajuda com arquivos de conteúdo no subdiretório específico do idioma do diretório do módulo no computador do usuário.

5. `Update-Help` cria um arquivo XML HelpInfo local copiando o arquivo XML HelpInfo remoto. Para que ele inclua elementos apenas para o arquivo CAB que ele instalado, ele edita o arquivo XML HelpInfo local. Em seguida, ele salva o arquivo XML HelpInfo local no diretório do módulo e conclui a atualização.

## <a name="the-save-help-process"></a>O processo de Save-Help

A lista a seguir descreve as ações do [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) e [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets quando um usuário executa comandos para atualizar os arquivos de Ajuda em um compartilhamento de arquivos e, em seguida, usá-los para atualizar os arquivos de ajuda sobre o computador do usuário.
A lista a seguir descreve as ações do [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) e [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets quando um usuário executa comandos para atualizar os arquivos de Ajuda em um compartilhamento de arquivos e, em seguida, usá-los para atualizar os arquivos de ajuda sobre o computador do usuário.

O `Save-Help` cmdlet executa as seguintes ações em resposta a um comando para salvar os arquivos de ajuda para um módulo em um compartilhamento de arquivos especificado pelo **DestinationPath** parâmetro.

1. `Save-Help` Obtém o arquivo XML HelpInfo remoto do local especificado pelo valor de **HelpInfoURI** da chave no manifesto de módulo e valida o arquivo em relação ao esquema. (Para exibir o esquema, consulte [esquema de XML HelpInfo](./helpinfo-xml-schema.md).) Em seguida, `Save-Help` procurará um arquivo XML HelpInfo local no diretório especificado pela **DestinationPath** parâmetro no `Save-Help` comando.

2. `Save-Help` compara o número de versão dos arquivos de ajuda para a cultura de interface do usuário especificada nos arquivos XML HelpInfo remotos e locais para o módulo. Se o número de versão no arquivo remoto é maior que o número de versão no arquivo local, ou não se houver nenhum arquivo XML HelpInfo local para o módulo na **DestinationPath** diretório, `Save-Help` prepara-se para baixar os novos arquivos de Ajuda.

3. `Save-Help` Seleciona o arquivo CAB para o módulo do local especificado o **HelpContentUri** elemento no arquivo XML HelpInfo remoto. Ele usa o nome do módulo, o GUID do módulo e a cultura de interface do usuário para identificar o arquivo CAB.

4. `Save-Help` baixa o arquivo CAB e salva-o na **DestinationPath** directory. (Ele não cria todos os subdiretórios específicos do idioma.)

5. `Save-Help` cria um arquivo XML HelpInfo local copiando o arquivo XML HelpInfo remoto. Ela edita o arquivo XML HelpInfo local para que ele inclua elementos apenas para o arquivo CAB que ele salvo. Em seguida, ele salva o arquivo XML HelpInfo local na **DestinationPath** diretório e conclui a atualização.

   O `Update-Help` cmdlet executa as seguintes ações em resposta a um comando para atualizar os arquivos de Ajuda no computador do usuário dos arquivos em um compartilhamento de arquivo que é especificado pelo **SourcePath** parâmetro.

1. `Update-Help` Obtém o arquivo XML HelpInfo remoto do **SourcePath** directory. Em seguida, ele procura por um arquivo XML HelpInfo local no diretório do módulo, no computador do usuário.

2. `Update-Help` compara o número de versão dos arquivos de ajuda para a cultura de interface do usuário especificada nos arquivos XML HelpInfo remotos e locais para o módulo. Se o número de versão no arquivo remoto é maior que o número de versão no arquivo local, ou se nenhum arquivo XML HelpInfo local, há `Update-Help` se prepara para instalar novos arquivos de Ajuda.

3. `Update-Help` Seleciona o arquivo CAB para o módulo da **SourcePath** directory. Ele usa o nome do módulo, o GUID do módulo e a cultura de interface do usuário para identificar o arquivo CAB.

4. `Update-Help` desempacota o arquivo CAB, valida os arquivos de conteúdo de Ajuda e salva a ajuda com arquivos de conteúdo no subdiretório específico do idioma do diretório do módulo no computador do usuário.

5. `Update-Help` cria um arquivo XML HelpInfo local copiando o arquivo XML HelpInfo remoto. Para que ele inclua elementos apenas para o arquivo CAB que ele instalado, ele edita o arquivo XML HelpInfo local. Em seguida, ele salva o arquivo XML HelpInfo local no diretório do módulo e conclui a atualização.