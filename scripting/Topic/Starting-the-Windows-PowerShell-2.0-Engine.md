---
title: Iniciando o Mecanismo do Windows PowerShell 2.0
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: edafc2fa-7576-49c2-bbba-9336f4bcfc28
---
# Iniciando o Mecanismo do Windows PowerShell 2.0
Esta seção explica como iniciar o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)] em [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)] e [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)], que incluem o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)] e em outros sistemas em que o [!INCLUDE[psversion2](../Token/psversion2_md.md)], [!INCLUDE[psversion3](../Token/psversion3_md.md)] e [!INCLUDE[psversion4](../Token/psversion4_md.md)] estão instalados.

[!INCLUDE[psversion4](../Token/psversion4_md.md)] e [!INCLUDE[psversion3](../Token/psversion3_md.md)] são projetados para serem compatíveis com versões anteriores com o [!INCLUDE[psversion2](../Token/psversion2_md.md)]. Cmdlets, provedores, snap-ins, módulos e scripts desenvolvidos para o [!INCLUDE[psversion2](../Token/psversion2_md.md)] são executados sem alterações no [!INCLUDE[psversion4](../Token/psversion4_md.md)] e [!INCLUDE[psversion3](../Token/psversion3_md.md)]. No entanto, devido a uma alteração na política de ativação do tempo de execução no Microsoft .NET Framework 4, programas de host do [!INCLUDE[wps_2](../Token/wps_2_md.md)] que foram desenvolvidos para [!INCLUDE[psversion2](../Token/psversion2_md.md)] e compilados com o CLR (Common Language Runtime) 2.0 não podem ser executado sem modificação no [!INCLUDE[psversion3](../Token/psversion3_md.md)] ou [!INCLUDE[psversion4](../Token/psversion4_md.md)], que são compilados com o CLR 4.0. O Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)] se destina a ser usado somente quando um programa de host ou um script existente não puder ser executado porque ele é incompatível com [!INCLUDE[psversion4](../Token/psversion4_md.md)], [!INCLUDE[psversion3](../Token/psversion3_md.md)] ou Microsoft .NET Framework 4. Tais casos devem ser raros.

Muitos programas que exigem o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)] o iniciam automaticamente. Essas instruções são incluídas para as raras situações em que você precisa iniciar o mecanismo manualmente.

## Instalar e habilitar os programas necessários
Antes de iniciar o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)], habilite o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)] e o Microsoft .NET Framework 3.5 com Service Pack 1. Para ver as instruções, consulte [Instalar o Windows PowerShell](../Topic/Installing-Windows-PowerShell.md).

Sistemas em que o [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) ou o [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] estão instalados têm todos os componentes necessários. Nenhuma outra configuração é necessária. Para obter informações sobre como instalar o [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) ou o [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)], consulte [Instalar o Windows PowerShell](../Topic/Installing-Windows-PowerShell.md).

## Como iniciar o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)]
Quando você iniciar o [!INCLUDE[mshshort](../Token/mshshort_md.md)], a versão mais recente é iniciada por padrão. Para iniciar o [!INCLUDE[mshshort](../Token/mshshort_md.md)] com o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)], use o parâmetro Version do PowerShell.exe. Você pode executar o comando no prompt de comando, incluindo o Windows PowerShell e Cmd.exe.

```
PowerShell.exe -Version 2
```

## Como iniciar uma sessão remota com o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)]
Para executar o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)] em uma sessão remota, crie uma configuração de sessão (também conhecida como um "ponto de extremidade") no computador remoto que carrega o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)]. A configuração de sessão é salvo no computador remoto e pode ser usada por qualquer usuário autorizado para criar sessões que usam o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)].

Essa é uma tarefa avançada que normalmente é executada por um administrador do sistema.

O procedimento a seguir usa o parâmetro **PSVersion** do cmdlet [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) para criar uma configuração de sessão que usa o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)]. Você também pode usar o parâmetro **PowerShellVersion** do cmdlet [New-PSSessionConfigurationFile](https://technet.microsoft.com/en-us/library/5f3e3633-6e90-479c-aea9-ba45a1954866) para criar um arquivo de configuração de sessão para uma sessão que carrega o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)], bem como usar o parâmetro **PSVersion** do parâmetro [Set-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) para alterar uma configuração de sessão para usar o Mecanismo [!INCLUDE[psversion2](../Token/psversion2_md.md)].

Para obter mais informações sobre os arquivos de configuração de sessão, consulte [about_Session_Configuration_Files](https://technet.microsoft.com/en-us/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8). Para obter mais informações sobre as configurações de sessão, incluindo instalação e segurança, consulte [about_Session_Configurations [v4]](https://technet.microsoft.com/en-us/library/a2fbe12a-350c-4d04-be50-24102824e3ab).

#### Para iniciar uma sessão remota do [!INCLUDE[psversion2](../Token/psversion2_md.md)]

1.  Para criar uma configuração de sessão que requer o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)], use o parâmetro **PSVersion** do cmdlet [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) com um valor de "2.0". Execute este comando no computador no “lado do servidor” ou na extremidade de recebimento de uma conexão.

    O comando de exemplo a seguir cria a configuração de sessão PS2 no computador Server01. Para executar esse comando, inicie o [!INCLUDE[psversion4](../Token/psversion4_md.md)] ou [!INCLUDE[psversion3](../Token/psversion3_md.md)] com a opção **Executar como administrador**.

    ```
    Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
    ```

2.  Para criar uma sessão no computador Server01 que usa a configuração de sessão PS2, use o parâmetro **ConfigurationName** de cmdlets que criam uma sessão remota, como o cmdlet [New-PSSession](https://technet.microsoft.com/en-us/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f).

    Quando uma sessão que usa a configuração de sessão é iniciada, o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)] é carregado automaticamente para a sessão.

    O comando a seguir inicia uma sessão no computador Server01 que usa a configuração de sessão PS2. O comando salva a sessão na variável $s.

    ```
    $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
    ```

## Como iniciar um trabalho em segundo plano com o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)]
Para iniciar um trabalho em segundo plano com o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)], use o parâmetro **PSVersion** do cmdlet [Start-Job](https://technet.microsoft.com/en-us/library/2bc04935-0deb-4ec0-b856-d7290cca6442).

O comando a seguir inicia um trabalho em segundo plano com o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)]

```
Start-Job {Get-Process} -PSVersion 2.0
```

Para obter mais informações sobre trabalhos em segundo plano, consulte [about_Jobs [v4]](https://technet.microsoft.com/en-us/library/7362512a-8a4e-4575-b2ea-a740e5c4f002).



<!--HONumber=Apr16_HO2-->


