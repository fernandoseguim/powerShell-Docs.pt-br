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
Esta seção explica como iniciar o Mecanismo Windows PowerShell 2.0 no Windows 8.1, Windows Server 2012 R2, Windows 8 e Windows Server 2012, que inclui o Mecanismo Windows PowerShell 2.0 e em outros sistemas em que o Windows PowerShell 2.0, Windows PowerShell 3.0 e Windows PowerShell 4.0 são instalados.

Windows PowerShell 4.0 e Windows PowerShell 3.0 são projetados para serem compatíveis com o Windows PowerShell 2.0. Cmdlets, provedores, snap-ins, módulos e scripts escritos para o Windows PowerShell 2.0 são executados sem alteração no Windows PowerShell 4.0 e Windows PowerShell 3.0. No entanto, devido a uma mudança na política de ativação de tempo de execução no Microsoft .NET Framework 4, programas host do Windows PowerShell escritos para Windows PowerShell 2.0 e compilados com CLR (Common Language Runtime) 2.0 não podem ser executados sem modificação no Windows PowerShell 3.0 ou o Windows PowerShell 4.0, que são compilados com CLR 4.0. O Mecanismo Windows PowerShell 2.0 deve ser usado somente quando um programa de script ou host existente não puder ser executado porque é incompatível com o Windows PowerShell 4.0, Windows PowerShell 3.0 ou Microsoft .NET Framework 4. Tais casos devem ser raros.

Muitos programas que exigem o Mecanismo Windows PowerShell 2.0 o inicia automaticamente. Essas instruções são incluídas para as raras situações em que você precisa iniciar o mecanismo manualmente.

## Instalar e habilitar os programas necessários
Antes de iniciar o Mecanismo Windows PowerShell 2.0, habilite o Mecanismo Windows PowerShell 2.0 e o Microsoft .NET Framework 3.5 com o Service Pack 1. Para obter instruções, consulte [Installing Windows PowerShell](Installing-Windows-PowerShell.md) (Instalando o Windows PowerShell).

Sistemas nos quais o [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) ou Windows Management Framework 3.0 estão instalados têm todos os componentes necessários. Nenhuma outra configuração é necessária. Para obter informações sobre como instalar o [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) ou Windows Management Framework 3.0, consulte [Installing Windows PowerShell](Installing-Windows-PowerShell.md) (Instalando o Windows PowerShell).

## Como iniciar o Mecanismo Windows PowerShell 2.0
Ao iniciar o Windows PowerShell a versão mais recente é iniciada por padrão. Para iniciar o Windows PowerShell com o Mecanismo Windows PowerShell 2.0, use o parâmetro de Versão do PowerShell.exe. Você pode executar o comando no prompt de comando, incluindo o Windows PowerShell e Cmd.exe.

```
PowerShell.exe -Version 2
```

## Como iniciar uma sessão remota com o Mecanismo Windows PowerShell 2.0
Para executar o Mecanismo Windows PowerShell 2.0 em uma sessão remota, crie uma configuração de sessão (também conhecida como "ponto de extremidade") no computador remoto que carrega o Mecanismo Windows PowerShell 2.0. A configuração da sessão é salva no computador remoto e pode ser usada por um usuário autorizado para criar sessões que utilizam o Mecanismo Windows PowerShell 2.0.

Essa é uma tarefa avançada que normalmente é executada por um administrador do sistema.

O procedimento a seguir usa o parâmetro **PSVersion** do cmdlet [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) para criar uma Mecanismo Windows PowerShell 2.0. Você também pode usar o parâmetro **PowerShellVersion** do cmdlet [New-PSSessionConfigurationFile](https://technet.microsoft.com/en-us/library/5f3e3633-6e90-479c-aea9-ba45a1954866) para criar um arquivo de configuração de sessão para uma sessão que carrega o Mecanismo Windows PowerShell 2.0 e você pode usar o parâmetro **PSVersion** do parâmetro [Set-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) para alterar uma configuração de sessão para usar o Mecanismo Windows PowerShell 2.0.

Para mais informações sobre arquivos de configuração de sessão, consulte [about_Session_Configuration_Files](https://technet.microsoft.com/en-us/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8). Para obter informações sobre configurações de sessão, incluindo configuração e segurança, consulte [about_Session_Configurations [v4]](https://technet.microsoft.com/en-us/library/a2fbe12a-350c-4d04-be50-24102824e3ab).

#### Para iniciar uma sessão remota do Windows PowerShell 2.0

1.  Para criar uma configuração de sessão que requer o Mecanismo Windows PowerShell 2.0, use o parâmetro **PSVersion** do cmdlet [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) com um valor de "2.0". Execute este comando no computador no “lado do servidor” ou na extremidade de recebimento de uma conexão.

    O comando de exemplo a seguir cria a configuração de sessão PS2 no computador Server01. Para executar esse comando, inicie o Windows PowerShell 4.0 ou o Windows PowerShell 3.0 com a opção **Executar como administrador**.

    ```
    Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
    ```

2.  Para criar uma sessão no computador Server01 que usa a configuração de sessão PS2, use o parâmetro **ConfigurationName** de cmdlets que criam uma sessão remota, como o cmdlet [New-PSSession](https://technet.microsoft.com/en-us/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f).

    Quando uma sessão que usa a configuração de sessão é iniciada, o Mecanismo Windows PowerShell 2.0 é automaticamente carregado na sessão.

    O comando a seguir inicia uma sessão no computador Server01 que usa a configuração de sessão PS2. O comando salva a sessão na variável $s.

    ```
    $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
    ```

## Como iniciar um trabalho em segundo plano com o Mecanismo Windows PowerShell 2.0
Para iniciar um trabalho em segundo plano com o Mecanismo Windows PowerShell 2.0, use o parâmetro **PSVersion** do cmdlet [Start-Job](https://technet.microsoft.com/en-us/library/2bc04935-0deb-4ec0-b856-d7290cca6442).

O comando a seguir inicia um trabalho em segundo plano com o Mecanismo Windows PowerShell 2.0

```
Start-Job {Get-Process} -PSVersion 2.0
```

Para obter mais informações sobre trabalhos em segundo plano, consulte [about_Jobs [v4]](https://technet.microsoft.com/en-us/library/7362512a-8a4e-4575-b2ea-a740e5c4f002).



<!--HONumber=May16_HO2-->


