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
Esta seção explica como iniciar [!INCLUDE[wps_2](../Token/wps_2_md.md)] e [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)] em [!INCLUDE[win7_client_firstref](../Token/win7_client_firstref_md.md)], [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] e [!INCLUDE[lserver](../Token/lserver_md.md)]. Ela também explica como habilitar o recurso opcional para [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] no [!INCLUDE[psversion2](../Token/psversion2_md.md)] em [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] e [!INCLUDE[lserver](../Token/lserver_md.md)].

Para instalar o [!INCLUDE[psversion4](../Token/psversion4_md.md)] em sistemas com suporte, baixe e instale o [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881). Para saber mais, consulte [Instalar o Windows PowerShell](../Topic/Installing-Windows-PowerShell.md).

Para instalar o [!INCLUDE[psversion3](../Token/psversion3_md.md)] em sistemas com suporte, baixe e instale o [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290). Para saber mais, consulte [Instalar o Windows PowerShell](../Topic/Installing-Windows-PowerShell.md).

## Como iniciar o [!INCLUDE[mshshort](../Token/mshshort_md.md)] em versões anteriores do Windows
Use qualquer um dos métodos a seguir para iniciar a versão instalada do [!INCLUDE[psversion3](../Token/psversion3_md.md)] ou [!INCLUDE[psversion4](../Token/psversion4_md.md)], se aplicável.

#### Do menu Iniciar

-   Clique em **Iniciar**, digite **PowerShell** e clique em **Windows PowerShell**.

-   No menu **Iniciar**, clique em **Iniciar**, **Todos os Programas**, **Acessórios**, clique na pasta **Windows PowerShell** e clique em **Windows PowerShell**.

#### No prompt de comando

-   Para iniciar, digite o seguinte no Cmd.exe, [!INCLUDE[wps_2](../Token/wps_2_md.md)], ou o ISE do [!INCLUDE[wps_2](../Token/wps_2_md.md)]; para iniciar o [!INCLUDE[wps_2](../Token/wps_2_md.md)], digite:

    ```
    PowerShell
    ```

    Você também pode usar os parâmetros do programa PowerShell.exe para personalizar a sessão. Para obter mais informações, consulte [Ajuda de linha de comando do PowerShell.exe](../Topic/PowerShell.exe-Command-Line-Help.md).

#### Com privilégios administrativos (“Executar como administrador”)

1.  Clique em **Iniciar**, digite **PowerShell**, clique com o botão direito do mouse em **Windows PowerShell** e em **Executar como administrador**.

## Como iniciar o [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] em lançamentos anteriores do Windows
Use um dos seguintes métodos para iniciar o [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)].

#### Do menu Iniciar

-   Clique em **Iniciar**, digite **ISE** e clique em **ISE do Windows PowerShell**.

-   No menu **Iniciar**, clique em **Iniciar**, **Todos os Programas**, **Acessórios**, clique na pasta **Windows PowerShell** e clique em **ISE do Windows PowerShell**.

#### No prompt de comando

-   Para iniciar, digite o seguinte no Cmd.exe, [!INCLUDE[wps_2](../Token/wps_2_md.md)], ou o ISE do [!INCLUDE[wps_2](../Token/wps_2_md.md)]; para iniciar o [!INCLUDE[wps_2](../Token/wps_2_md.md)], digite:

    ```
    PowerShell_ISE
    ```

    ou

    ```
    ISE
    ```

#### Com privilégios administrativos (“Executar como administrador”)

1.  Clique em **Iniciar**, digite **ISE**, clique com o botão direito do mouse em **ISE do Windows PowerShell** e em **Executar como administrador**.

## Como habilitar o [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] em versões anteriores do Windows
No [!INCLUDE[psversion4](../Token/psversion4_md.md)] e [!INCLUDE[psversion3](../Token/psversion3_md.md)], o [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] é habilitado por padrão em todas as versões do Windows. Se ainda não estiver habilitado, o Windows Management Framework 4.0 ou [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] o habilitará.

No [!INCLUDE[psversion2](../Token/psversion2_md.md)], o [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] é habilitado por padrão no [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)]. No entanto, no [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] e [!INCLUDE[lserver](../Token/lserver_md.md)], ele é um recurso opcional.

Para habilitar o [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] no [!INCLUDE[psversion2](../Token/psversion2_md.md)] em [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] ou [!INCLUDE[lserver](../Token/lserver_md.md)], use o procedimento a seguir.

#### Para habilitar o [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]

1.  Inicie o Gerenciador do Servidor.

2.  Clique em **Recursos** e depois em **Adicionar Recursos**.

3.  Em Selecionar Recursos, clique em [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)].



<!--HONumber=Apr16_HO1-->


