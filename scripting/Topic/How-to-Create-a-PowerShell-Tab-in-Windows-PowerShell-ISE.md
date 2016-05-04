---
title: Como criar uma guia do PowerShell no ISE do Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
---
# Como criar uma guia do PowerShell no ISE do Windows PowerShell
As guias no [!INCLUDE[ise_1](../Token/ise_1_md.md)] permitem criar e usar simultaneamente vários ambientes de execução dentro do mesmo aplicativo. Cada guia do PowerShell corresponde a uma sessão ou ambiente de execução separado.

> [!NOTE]
> Variáveis, funções e aliases que você criar em uma guia não serão transferidos para outra. Eles são sessões diferentes do Windows PowerShell.

Use as etapas a seguir para abrir ou fechar uma guia no [!INCLUDE[wps_2](../Token/wps_2_md.md)]. Para renomear uma guia, defina a propriedade [DisplayName](assetId:///a9b58556-951b-4f48-b3ae-b351b7564360#Displayname) no objeto de script de guia do [!INCLUDE[wps_2](../Token/wps_2_md.md)].

## Para criar e usar uma nova guia do PowerShell
No menu **Arquivo**, clique em **Nova Guia do PowerShell**. A nova guia do PowerShell sempre é aberta como a janela ativa. Guias do PowerShell são numeradas incrementalmente na ordem em que são abertas. Cada guia é associada à sua própria janela de console do Windows PowerShell. Você pode ter até 32 guias do PowerShell com sua própria sessão aberta por vez (isso fica limitado a 8 no [!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0.)

Observe que clicar nos ícones **Novo** ou **Abrir** na barra de ferramentas não cria uma nova guia com uma sessão separada.  Em vez disso, esses botões abrem um arquivo de script novo ou existente na guia ativa no momento com uma sessão. Você pode deixar vários arquivos de script abertos com cada guia e a sessão. As guias de script para uma sessão só aparecem abaixo das guias de sessão quando a sessão associada estiver ativa.

Para tornar uma guia do PowerShell ativa, clique nela. Para selecionar todas as guias do PowerShell que estão abertas no menu **Exibir**, clique na guia do PowerShell que você deseja usar.

## Para criar e usar uma nova guia remota do PowerShell
No menu **Arquivo**, clique em **Nova Guia Remota do PowerShell** para estabelecer uma sessão em um computador remoto. Uma caixa de diálogo é exibida e solicita que você insira os detalhes necessários para estabelecer a conexão remota. A guia remota funciona como uma guia local do PowerShell, mas os comandos e os scripts são executados no computador remoto.

## Para fechar uma guia do PowerShell
Para fechar uma guia, você pode usar qualquer uma das seguintes técnicas:

-   Clique na guia que você deseja fechar.

-   No menu **Arquivo**, clique em **Fechar Guia do PowerShell** ou no botão Fechar (**X**) em uma guia para fechar a guia ativa.

Se tiver arquivos não salvos abertos na guia do PowerShell que você está fechando, será solicitado salvá-los ou descartá-los. Para obter mais informações sobre como salvar um script, consulte [Como salvar um script](assetId:///162f594d-efd3-4234-9960-45e56e6eadc8).

## Consulte Também
[Usando o ISE do Windows PowerShell](../Topic/Using-the-Windows-PowerShell-ISE.md)
[Como usar o Painel de Console com o ISE do Windows PowerShell](../Topic/How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)



<!--HONumber=Apr16_HO1-->


