---
title: Preparando-se para usar o Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6dc7052d-cc5a-4220-950f-98f963a2b587
---
# Preparando-se para usar o Windows PowerShell
Quando o [!INCLUDE[wps_2](../Token/wps_2_md.md)] estiver instalado e iniciado, considere as seguintes opções de configuração. Você pode executar essas tarefas a qualquer momento.

-   **Instale os arquivos de Ajuda.** Os cmdlets que estão incluídos no [!INCLUDE[psversion3](../Token/psversion3_md.md)] não vem com arquivos de Ajuda. No entanto, você pode usar o cmdlet [Update-Help](assetId:///93e1d870-ace6-432b-8778-8920291d7545) para baixar e instalar os arquivos de ajuda mais recentes no seu computador. Depois de os arquivos serem instalados, você pode usar o cmdlet [Get-Help](assetId:///1f46eeb4-49d7-4bec-bb29-395d9b42f54a) para exibi-los diretamente na linha de comando. Para obter mais informações, consulte [about_Updatable_Help](assetId:///10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe).

    Se você decidir não instalar os arquivos de Ajuda, ainda poderá ler os tópicos da Ajuda online. Para abrir a versão online de qualquer tópico de Ajuda de cmdlet, digite: `Get-Help <CmdletName> -Online`. Para procurar os tópicos de Ajuda do [!INCLUDE[wps_2](../Token/wps_2_md.md)] na Biblioteca do TechNet, comece por [http://go.microsoft.com/fwlink/?LinkID=107116](http://go.microsoft.com/fwlink/?LinkID=107116).

-   **Execute os Scripts.** Para manter o [!INCLUDE[mshshort](../Token/mshshort_md.md)] seguro, a política de execução padrão no [!INCLUDE[mshshort](../Token/mshshort_md.md)] é **Restricted**. Essa política permite executar os cmdlets, mas não em scripts. Para executar scripts, use o cmdlet [Set-ExecutionPolicy [PSITPro5_Security]](assetId:///5690a0e1-495b-4e63-8280-65ead7bf01ab) para alterar a política de execução para **AllSigned** ou **RemoteSigned**. Somente os membros do grupo Administradores no computador podem executar este cmdlet. Para obter mais informações, consulte [about_Execution_Policies [v4]](assetId:///347708dc-1515-4d74-978b-8334603472e6).

-   **Habilite a comunicação remota.** O sistema já está configurado para executar comandos remotos em outros computadores. No [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] e [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)], o sistema também está configurado para receber comandos remotos, ou seja, para permitir que outros computadores executem comandos remotos no computador local. Para permitir que os computadores que executam outras versões do Windows recebam comandos remotos, execute o cmdlet [Enable-PSRemoting](assetId:///19437c28-33b8-4ac1-9113-8439cc8beffb) no computador que você deseja gerenciar remotamente. Somente os membros do grupo Administradores no computador podem executar este cmdlet. Para obter mais informações, consulte [about_Remote](assetId:///9b4a5c87-9162-4adf-bdfe-fbc80b9b8970).

    OBSERVAÇÃO: se a comunicação remota estiver habilitada em um computador que executa o [!INCLUDE[psversion2](../Token/psversion2_md.md)], a comunicação remota ainda estará habilitada após a instalação do [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]. No entanto, no [!INCLUDE[lserver](../Token/lserver_md.md)] (não no [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)]), você deve habilitar novamente a comunicação remota após a instalação do [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)].

## Consulte Também
[Instalar o Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)
[Iniciando o Windows PowerShell [ps]](assetId:///8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=Apr16_HO1-->


