---
ms.date: 2017-06-05
keywords: powershell, cmdlet
title: Iniciando o Windows PowerShell
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: 90f6992f47e62c1775cae216b4012f630e07558f
ms.sourcegitcommit: 755d7bc0740573d73613cedcf79981ca3dc81c5e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="starting-windows-powershell"></a>Iniciando o Windows PowerShell
O PowerShell é uma dll de mecanismo de script que é inserida em vários hosts.  Os hosts que você iniciará com mais frequência são a linha de comando interativa do PowerShell.exe e o Ambiente de Script Integrado do PowerShell_ISE.exe.

Para iniciar o Windows PowerShell® no Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 e Windows 8, consulte [Common Management Tasks and Navigation (Tarefas comuns de gerenciamento e navegação)](http://technet.microsoft.com/library/hh831491.aspx).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Como iniciar o Windows PowerShell em versões anteriores do Windows

Esta seção explica como iniciar o Windows PowerShell e o ISE (Ambiente de Script Integrado) do Windows PowerShell no Windows® 7, Windows Server® 2008 R2 e Windows Server® 2008. Também explica como habilitar o recurso opcional para o ISE do Windows PowerShell no Windows PowerShell 2.0 no Windows Server® 2008 R2 e Windows Server 2008.

Use qualquer um dos seguintes métodos para iniciar a versão instalada do Windows PowerShell 3.0 ou o Windows PowerShell 4.0, quando aplicável.

#### <a name="from-the-start-menu"></a>Do menu Iniciar

- Clique em **Iniciar**, digite **PowerShell** e clique em **Windows PowerShell**.
- No menu **Iniciar**, clique em **Iniciar**, **Todos os Programas**, **Acessórios**, clique na pasta **Windows PowerShell** e clique em **Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>No prompt de comando

No Cmd.exe, Windows PowerShell ou ISE do Windows PowerShell, para iniciar o Windows PowerShell, digite:

```
PowerShell
```

Você também pode usar os parâmetros do programa PowerShell.exe para personalizar a sessão. Para obter mais informações, consulte [Ajuda de linha de comando do PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>Com privilégios administrativos (“Executar como administrador”)

Clique em **Iniciar**, digite **PowerShell**, clique com o botão direito do mouse em **Windows PowerShell** e depois clique em **Executar como administrador**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Como iniciar o ISE do Windows PowerShell em versões anteriores do Windows

Use qualquer um dos seguintes métodos para iniciar o ISE do Windows PowerShell.

#### <a name="from-the-start-menu"></a>Do menu Iniciar

- Clique em **Iniciar**, digite **ISE** e clique em **ISE do Windows PowerShell**.
- No menu **Iniciar**, clique em **Iniciar**, **Todos os Programas**, **Acessórios**, clique na pasta **Windows PowerShell** e clique em **ISE do Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>No prompt de comando

No Cmd.exe, Windows PowerShell ou ISE do Windows PowerShell, para iniciar o Windows PowerShell, digite:

```
PowerShell_ISE
```

ou

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a>Com privilégios administrativos (“Executar como administrador”)

Clique em **Iniciar**, digite **ISE**, clique com o botão direito do mouse em **ISE do Windows PowerShell** e depois clique em **Executar como administrador**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Como habilitar o ISE do Windows PowerShell em versões anteriores do Windows

No Windows PowerShell 4.0 e Windows PowerShell 3.0, o ISE do Windows PowerShell é habilitado por padrão em todas as versões do Windows. Se ele ainda não estiver habilitado, o Windows Management Framework 4.0 ou Windows Management Framework 3.0 o habilitará.

No Windows PowerShell 2.0, o ISE do Windows PowerShell é habilitado por padrão no Windows 7. No entanto, no Windows Server 2008 R2 e Windows Server 2008, é um recurso opcional.

Para habilitar o ISE do Windows PowerShell no Windows PowerShell 2.0 no Windows Server 2008 R2 ou Windows Server 2008, use o seguinte procedimento.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Para habilitar o ISE (Ambiente de Script Integrado) do Windows PowerShell

1. Inicie o Gerenciador do Servidor.
2. Clique em **Recursos** e depois em **Adicionar Recursos**.
3. Em Selecionar Recursos, clique em ISE (Ambiente de Script Integrado) do Windows PowerShell.

## <a name="starting-the-32-bit-version-of-windows-powershell"></a>Iniciando a versão de 32 bits do Windows PowerShell

Quando você instala o Windows PowerShell em um computador de 64 bits, o **Windows PowerShell (x86)**, uma versão de 32 bits do Windows PowerShell é instalada com a versão de 64 bits. Quando você executa o Windows PowerShell, a versão de 64 bits é executada por padrão.

No entanto, ocasionalmente pode ser necessário executar o **Windows PowerShell (x86)**, como quando você estiver usando um módulo que requer a versão de 32 bits ou quando você quiser se conectar remotamente a um computador de 32 bits.

Para iniciar uma versão de 32 bits do Windows PowerShell, use qualquer um dos procedimentos a seguir.

#### <a name="in-windows-server-2012-r2"></a>No Windows Server® 2012 R2

- Na tela **Iniciar**, clique em **Windows PowerShell (x86)**. Clique no bloco **Windows PowerShell x86**.
- Em **Gerenciador do Servidor**, no menu **Ferramentas**, selecione **Windows PowerShell (x86)**.
- Na área de trabalho, mova o cursor para o canto superior direito, clique em **Pesquisar**, digite **PowerShell x86** e clique em **Windows PowerShell (x86)**.
- Por meio da linha de comando, digite: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>No Windows Server® 2012

- Na tela **Iniciar**, digite **PowerShell** e clique em **Windows PowerShell (x86)**.
- Em **Gerenciador do Servidor**, no menu **Ferramentas**, selecione **Windows PowerShell (x86)**.
- Na área de trabalho, mova o cursor para o canto superior direito, clique em **Pesquisar**, digite **PowerShell** e clique em **Windows PowerShell (x86)**.
- Por meio da linha de comando, digite: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>No Windows® 8.1

- Na tela **Iniciar**, clique em **Windows PowerShell (x86)**. Clique no bloco **Windows PowerShell x86**.
- Se estiver executando as [Ferramentas de Administração de Servidor Remoto](http://go.microsoft.com/fwlink/?LinkID=304145) para o Windows 8.1, você também poderá abrir o Windows PowerShell x86 no menu **Ferramentas do Gerenciador do Servidor**.
  Selecione **Windows PowerShell (x86)**.
- Na área de trabalho, mova o cursor para o canto superior direito, clique em **Pesquisar**, digite **PowerShell x86** e clique em **Windows PowerShell (x86)**.
- Por meio da linha de comando, digite: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>No Windows® 8

- Na tela **Iniciar**, mova o cursor para o canto superior direito, clique em **Configurações**, **Blocos** e mova o controle deslizante **Mostrar Ferramentas Administrativas** para Sim. Em seguida, digite **PowerShell** e clique em **Windows PowerShell (x86)**.
- Se estiver executando as [Ferramentas de Administração de Servidor Remoto](http://www.microsoft.com/download/details.aspx?id=28972) para o Windows 8, você também poderá abrir o Windows PowerShell x86 no menu **Ferramentas do Gerenciador do Servidor**. Selecione **Windows PowerShell (x86)**.
- Na tela **Iniciar** ou na área de trabalho, digite **PowerShell (x86)** e clique em **Windows PowerShell (x86)**.
- Por meio da linha de comando, digite: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`
