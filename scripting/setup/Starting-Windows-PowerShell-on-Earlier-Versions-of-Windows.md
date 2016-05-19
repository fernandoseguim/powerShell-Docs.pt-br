---
title: Iniciando o Windows PowerShell em versões anteriores do Windows
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
---
# Iniciando o Windows PowerShell em versões anteriores do Windows
Esta seção explica como iniciar o Windows PowerShell e o ISE (Ambiente de Script Integrado) do Windows PowerShell no Windows® 7, Windows Server® 2008 R2 e Windows Server 2008. Também explica como habilitar o recurso opcional para o ISE do Windows PowerShell no Windows PowerShell 2.0 no Windows Server® 2008 R2 e Windows Server 2008.

Para instalar o Windows PowerShell 4.0 em sistemas com suporte, baixe e instale o [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881). Para mais informações, consulte [Installing Windows PowerShel](Installing-Windows-PowerShell.md) (Instalando o Windows PowerShell).

Para instalar o Windows PowerShell 3.0 em sistemas com suporte, baixe e instale o [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290). Para mais informações, consulte [Installing Windows PowerShel](Installing-Windows-PowerShell.md) (Instalando o Windows PowerShell).

## Como iniciar o Windows PowerShell em versões anteriores do Windows
Use qualquer um dos seguintes métodos para iniciar a versão instalada do Windows PowerShell 3.0 ou o Windows PowerShell 4.0, quando aplicável.

#### Do menu Iniciar

-   Clique em **Iniciar**, digite **PowerShell** e clique em **Windows PowerShell**.

-   No menu **Iniciar** clique em **Iniciar**, Iniciar **Todos os Programas**, clique em **Acessórios**, clique na pasta **Windows PowerShell** e clique em **Windows PowerShell**.

#### No prompt de comando

-   No Cmd.exe, Windows PowerShell ou ISE do Windows PowerShell, para iniciar o Windows PowerShell, digite:

    ```
    PowerShell
    ```

    Você também pode usar os parâmetros do programa PowerShell.exe para personalizar a sessão. Para mais informações, consulte [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md) (Ajuda da linha de comando PowerShell.exe).

#### Com privilégios administrativos (“Executar como administrador”)

1.  Clique em **Iniciar**, digite **PowerShell**, clique com o botão direito do mouse em **Windows PowerShell** e depois clique em **Executar como administrador**.

## Como iniciar o ISE do Windows PowerShell em versões anteriores do Windows
Use qualquer um dos seguintes métodos para iniciar o ISE do Windows PowerShell.

#### Do menu Iniciar

-   Clique em **Iniciar**, digite **ISE** e depois clique em **ISE do Windows PowerShell**.

-   No menu **Iniciar**, clique em **Iniciar**, clique em **Todos os Programas**, clique em **Acessórios**, clique na pasta **Windows PowerShell** e clique em **ISE do Windows PowerShell**.

#### No prompt de comando

-   No Cmd.exe, Windows PowerShell ou ISE do Windows PowerShell, para iniciar o Windows PowerShell, digite:

    ```
    PowerShell_ISE
    ```

    ou

    ```
    ISE
    ```

#### Com privilégios administrativos (“Executar como administrador”)

1.  Clique em **Iniciar**, digite **ISE**, clique com o botão direito do mouse em **ISE do Windows PowerShell** e depois clique em **Executar como administrador**.

## Como habilitar o ISE do Windows PowerShell em versões anteriores do Windows
No Windows PowerShell 4.0 e Windows PowerShell 3.0, o ISE do Windows PowerShell é habilitado por padrão em todas as versões do Windows. Se ele ainda não estiver habilitado, o Windows Management Framework 4.0 ou Windows Management Framework 3.0 o habilitará.

No Windows PowerShell 2.0, o ISE do Windows PowerShell é habilitado por padrão no Windows 7. No entanto, no Windows Server 2008 R2 e Windows Server 2008, é um recurso opcional.

Para habilitar o ISE do Windows PowerShell no Windows PowerShell 2.0 no Windows Server 2008 R2 ou Windows Server 2008, use o seguinte procedimento.

#### Para habilitar o ISE (Ambiente de Script Integrado) do Windows PowerShell

1.  Inicie o Gerenciador do Servidor.

2.  Clique em **Recursos** e clique em **Adicionar Recursos**.

3.  Em Selecionar Recursos, clique em ISE (Ambiente de Script Integrado) do Windows PowerShell.



<!--HONumber=May16_HO2-->


