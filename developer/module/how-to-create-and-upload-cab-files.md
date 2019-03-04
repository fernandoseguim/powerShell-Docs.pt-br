---
title: Como criar e carregar arquivos CAB | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 9928a0b31a57d42eb39cea1af0509613c483caf7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858642"
---
# <a name="how-to-create-and-upload-cab-files"></a>Como criar e carregar arquivos CAB

Este tópico explica como criar arquivos CAB de ajuda atualizável e carregá-los para o local em que os cmdlets de ajuda atualizável pode encontrá-los.

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>Como criar e carregar os arquivos CAB a Ajuda atualizável

Você pode usar o recurso de ajuda atualizável para distribuir arquivos de ajuda novos ou atualizados para um módulo em vários idiomas e culturas. Um pacote com a Ajuda atualizável para um módulo consiste em um arquivo XML HelpInfo e um ou mais de gabinete (. Arquivos CAB). Cada arquivo CAB contém arquivos de ajuda para o módulo em uma cultura de interface do usuário. Use o procedimento a seguir para criar arquivos CAB para ajuda atualizável.

1. Organize os arquivos de ajuda para o módulo com a cultura de interface do usuário. Cada arquivo CAB de ajuda atualizável contém os arquivos de ajuda para um módulo em uma cultura de interface do usuário. Você pode fornecer ajuda de vários arquivos CAB para o módulo, cada um para uma cultura de interface do usuário diferente.

2. Verifique se que arquivos de Ajuda incluem somente os tipos de arquivo permitidos para a Ajuda atualizável e validá-los em um esquema de arquivo de Ajuda. Se o `Update-Help` cmdlet encontrar um arquivo que é inválido ou não é um tipo permitido, mas não instala o arquivo inválido e interrompe a instalação de arquivos do CAB. Para obter uma lista dos tipos de arquivo permitidos, consulte [tipos de arquivo permitidos em um arquivo de CAB de ajuda atualizável](./file-types-permitted-in-an-updatable-help-cab-file.md).

3. Assine digitalmente os arquivos de Ajuda. Assinaturas digitais não são necessárias, mas eles são uma prática recomendada.

4. Inclua todos os arquivos para o módulo na interface do usuário de cultura, não apenas os arquivos que são novos ou foram alterados de Ajuda. Se o arquivo CAB estiver incompleto, os usuários que baixam arquivos de ajuda pela primeira vez ou não baixar todas as atualizações, não terá todos os arquivos de Ajuda do módulo.

5. Use um utilitário que cria arquivos de gabinete, como MakeCab.exe. Windows PowerShell não inclui cmdlets que criam arquivos CAB.

6. Nomeie os arquivos CAB. Para obter mais informações, consulte [como nomear um arquivo de CAB de ajuda atualizável](./how-to-name-an-updatable-help-cab-file.md).

7. Carregar os arquivos CAB para o módulo para o local especificado pelo **HelpContentUri** elemento no arquivo XML HelpInfo para o módulo. Em seguida, carregar o arquivo XML HelpInfo para o local especificado pelo **HelpInfoUri** chave do manifesto do módulo. O **HelpContentUri** e **HelpInfoUri** pode apontar para o mesmo local.

> [!CAUTION]
> O valor da **HelpInfoUri** chave e o **HelpContentUri** elemento deve começar com "http" ou "https". O valor deve indicar um local da Internet e não deve incluir um nome de arquivo.