---
title: Usando o Visual Studio Code para edição e depuração remotas
description: Usando o Visual Studio Code para edição e depuração remotas
ms.date: 08/06/2018
ms.openlocfilehash: bab1a629a7e9dafd5957cf93025abb18b8a4f326
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655567"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Usando o Visual Studio Code para edição e depuração remotas

Para aqueles que estão familiarizados com o ISE, você deve se lembrar de que você pode executar `psedit file.ps1` do console integrado para abrir os arquivos - locais ou remotos - com o botão direito no ISE.

Na verdade, esse recurso também está disponível na extensão do PowerShell para VSCode. Este guia mostrará como fazê-lo.

## <a name="prerequisites"></a>Pré-requisitos

Este guia pressupõe que você tenha:

- um recurso remoto (ex: uma VM, um contêiner) que você tenha acesso a
- PowerShell em execução nele e o computador host
- VSCode e a extensão do PowerShell para VSCode

Esse recurso funciona no Windows PowerShell e o PowerShell Core.

Esse recurso também funciona ao se conectar a um computador remoto via WinRM, PowerShell Direct ou SSH. Se você quiser usar o SSH, mas estiver usando o Windows, confira a [versão Win32 do SSH](https://github.com/PowerShell/Win32-OpenSSH)!

## <a name="lets-go"></a>Vamos lá

Nesta seção, percorrerei remoto edição e depuração de meu MacBook Pro, para uma VM do Ubuntu em execução no Azure. Eu talvez não estejam usando o Windows, mas **o processo é idêntico**.

### <a name="local-file-editing-with-open-editorfile"></a>Edição com o Open EditorFile de arquivo local

Com a extensão do PowerShell para VSCode é iniciado e o Console integrado do PowerShell aberta, também podemos digitar `Open-EditorFile foo.ps1` ou `psedit foo.ps1` para abrir o arquivo de foo.ps1 local diretamente no editor.

![Abrir EditorFile foo.ps1 funciona localmente](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> foo.ps1 já deve existir.

A partir daí, podemos:

Adicionar pontos de interrupção a medianiz ![adicionando o ponto de interrupção para da medianiz](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)

e pressione F5 para depurar o script do PowerShell.
![o script do PowerShell local de depuração](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)

Durante a depuração, você pode interagir com o console de depuração, confira as variáveis no escopo à esquerda, e todos os outro padrão as ferramentas de depuração.

### <a name="remote-file-editing-with-open-editorfile"></a>Edição com o Open EditorFile de arquivo remoto

Agora, vejamos arquivo remoto, edição e depuração. As etapas são praticamente as mesmas, há apenas uma coisa que precisamos fazer primeiro – insira nossa sessão do PowerShell para o servidor remoto.

Há um cmdlet para fazer isso. Ele é chamado `Enter-PSSession`.

A explicação menos potente e para baixo do cmdlet é:

- `Enter-PSSession -ComputerName foo` inicia uma sessão por meio do WinRM
- `Enter-PSSession -ContainerId foo` e `Enter-PSSession -VmId foo` iniciar uma sessão por meio do PowerShell Direct
- `Enter-PSSession -HostName foo` inicia uma sessão por meio do SSH

Para obter mais informações sobre `Enter-PSSession`, confira os documentos [aqui](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).

Usarei SSH para a comunicação remota, pois vou do macOS para uma VM do Ubuntu no Azure.

Primeiro, no Console integrado, vamos executar nosso Enter-PSSession. Você saberá que você está na sessão porque `[something]` serão exibidos à esquerda do prompt de.

![A chamada para Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

A partir daí, podemos fazer as etapas exatas como se podemos estava editando um script local.

1. Execute `Open-EditorFile test.ps1` ou `psedit test.ps1` para abrir o controle remoto `test.ps1` arquivo ![EditorFile com a abrir o arquivo ps1](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)
2. Editar os arquivo/definir pontos de interrupção ![Editar e defina pontos de interrupção](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. Iniciar a depuração (F5) o arquivo remoto

![depurando o arquivo remoto](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

Isso é tudo para ele! Esperamos que este guia ajudou a esclarecer os alguma dúvida sobre a depuração remota e edição do PowerShell no VSCode.

Se você tiver problemas, fique à vontade para problemas em aberto [no repositório GitHub](http://github.com/powershell/vscode-powershell).
