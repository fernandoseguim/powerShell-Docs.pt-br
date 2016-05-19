---
title: Como usar perfis no ISE do Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
---
# Como usar perfis no ISE do Windows PowerShell
Este tópico explica como usar perfis no ISE (Ambiente de Script Integrado) do Windows PowerShell. Recomendamos que antes de executar as tarefas nesta seção, você examine [about_Profiles [v4]](https://technet.microsoft.com/en-us/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054) ou, no painel de Console, digite, “get-help about_profiles” e pressione **ENTER**.

Um perfil é um script do ISE do Windows PowerShell executado automaticamente quando você inicia uma nova sessão.  Você pode criar um ou mais perfis do Windows PowerShell para o ISE do Windows PowerShell e usá-los para adicionar a configuração do Windows PowerShell ou o ambiente ISE do Windows PowerShell, preparando-o para seu uso, com variáveis, aliases, funções, cores e preferências de fonte que você quer disponíveis. Um perfil afeta cada sessão de ISE do Windows PowerShell que você começar.

> [!NOTE]
> A política de execução do Windows PowerShell determina se você pode executar scripts e carregar um perfil. A política de execução padrão, “Restricted”, impede a execução de todos os scripts, incluindo perfis. Se você usar a política “Restricted”, não será possível carregar o perfil. Para obter mais informações sobre a política de execução, consulte [about_Execution_Policies [v4]](https://technet.microsoft.com/en-us/library/347708dc-1515-4d74-978b-8334603472e6).

## Selecionar um perfil para usar com o ISE do Windows PowerShell
O ISE do Windows PowerShell dá suporte a perfis para o usuário atual e todos os usuários. Ele também dá suporte a perfis do Windows PowerShell que se aplicam a todos os hosts.

O perfil que você usa é determinado pela forma como você usa o Windows PowerShell e o ISE do Windows PowerShell.

-   Se você usar apenas o ISE do Windows PowerShell para executar o Windows PowerShell, salve todos os seus itens em um dos perfis específicos de ISE, como o perfil CurrentUserCurrentHost para o ISE do Windows PowerShell ou o perfil AllUsersCurrentHost para o ISE do Windows PowerShell.

-   Se você usar vários programas host para executar o Windows PowerShell, salve suas funções, aliases, variáveis e comandos em um perfil que afete todos os programas host, tais como o perfil CurrentUserAllHosts ou AllUsersAllHosts, e salve recursos específicos do ISE, como cor e personalização de fonte, no perfil CurrentUserCurrentHost do perfil do ISE do Windows PowerShell ou o perfil AllUsersCurrentHost do ISE do Windows PowerShell.

A seguir, os perfis que podem ser criados e usados no ISE do Windows PowerShell. Cada perfil é salvo em seu próprio caminho específico.

|Tipo de Perfil|Caminho do Perfil|
|----------------|----------------|
|"Usuário atual, ISE do PowerShell"|$profile.CurrentUserCurrentHost ou $profile|
|“Todos os usuários, ISE do PowerShell”|$profile.AllUsersCurrentHost|
|"Usuário atual, Todos os hosts"|$profile.CurrentUserAllHosts|
|"Todos os usuários, Todos os hosts"|$profile.AllUsersAllHosts|

## Para criar um novo perfil
Para criar um novo perfil de "Usuário atual, ISE do Windows PowerShell", execute este comando:

```
if (!(test-path $profile )) 
{new-item -type file -path $profile -force}
```

Para criar um novo perfil de "Todos os usuários, ISE do Windows PowerShell", execute este comando:

```
if (!(test-path $profile.AllUsersCurrentHost)) 
{new-item -type file -path $profile.AllUsersCurrentHost -force}
```

Para criar um novo perfil de "Usuário atual, Todos os Hosts", execute este comando:

```
if (!(test-path $profile.CurrentUserAllHosts)) 
{new-item -type file -path $profile.CurrentUserAllHosts -force}
```

Para criar um novo perfil de "Todos os usuários, Todos os Hosts", digite:

```
if (!(test-path $profile.AllUsersAllHosts)) 
{new-item -type file -path $profile.AllUsersAllHosts-force}
```

## Para editar um perfil

1.  Para abrir o perfil, execute o comando psedit com a variável que especifica o perfil que você deseja editar. Por exemplo, para abrir o perfil "Usuário atual, ISE do Windows PowerShell" digite: `psEdit $profile`

2.  Adicione alguns itens ao seu perfil. A seguir estão alguns exemplos para começar:

    -   Para alterar a cor da tela de fundo padrão do Painel de Console para azul, digite o seguinte no arquivo do perfil: `$psISE.Options.OutputPaneBackground = 'blue'` . Para mais informações sobre a variável psISE, consulte [Windows PowerShell ISE Object Model Reference](https://technet.microsoft.com/en-us/library/e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c) (Referência de modelo de objeto de ISE do Windows PowerShell).

    -   Para alterar o tamanho da fonte para 20, no arquivo de perfil digite: `$psISE.Options.FontSize =20`

3.  Para salvar esse arquivo de perfil, no menu **Arquivo**, clique em **Salvar**. Da próxima vez que você abrir o ISE do Windows PowerShell, as personalizações serão aplicadas.

## Consulte Também
[about_Profiles [v4]](https://technet.microsoft.com/en-us/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054)
[Usando o ISE do Windows PowerShell](Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=May16_HO2-->


