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
Este tópico explica como usar Perfis no [!INCLUDE[ise_1](../Token/ise_1_md.md)]. Recomendamos que antes de executar as tarefas nesta seção, você examine [about_Profiles [v4]](https://technet.microsoft.com/en-us/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054) ou, no Painel de Console, digite "get-help about_profiles" e pressione **ENTER**.

Um perfil é um script do [!INCLUDE[ise_2](../Token/ise_2_md.md)] que é executado automaticamente quando você inicia uma nova sessão.  Você pode criar um ou mais perfis do [!INCLUDE[wps_2](../Token/wps_2_md.md)] para [!INCLUDE[ise_2](../Token/ise_2_md.md)] e usá-los para adicionar a configuração ao ambiente [!INCLUDE[wps_2](../Token/wps_2_md.md)] ou [!INCLUDE[ise_2](../Token/ise_2_md.md)], preparando-o para seu uso com variáveis, aliases, funções e as preferências de cor e de fonte que você deseja disponibilizar. Um perfil afeta cada sessão do [!INCLUDE[ise_2](../Token/ise_2_md.md)] que você iniciar.

> [!NOTE]
> A política de execução do [!INCLUDE[wps_2](../Token/wps_2_md.md)] determina se você pode executar scripts e carregar um perfil. A política de execução padrão, “Restricted”, impede a execução de todos os scripts, incluindo perfis. Se você usar a política “Restricted”, não será possível carregar o perfil. Para obter mais informações sobre as políticas, consulte [about_Execution_Policies [v4]](https://technet.microsoft.com/en-us/library/347708dc-1515-4d74-978b-8334603472e6).

## Selecionar um perfil para usar com o ISE do Windows PowerShell
O [!INCLUDE[ise_2](../Token/ise_2_md.md)] dá suporte a perfis para o usuário atual e todos os usuários. Ele também dá suporte a perfis do [!INCLUDE[wps_2](../Token/wps_2_md.md)] que se aplicam a todos os hosts.

O perfil que você usa é determinado por como você usa o [!INCLUDE[wps_2](../Token/wps_2_md.md)] e o [!INCLUDE[ise_2](../Token/ise_2_md.md)].

-   Se você usar apenas o [!INCLUDE[ise_2](../Token/ise_2_md.md)] para executar o Windows PowerShell, salve todos os itens em um dos perfis específicos de ISE, tais como o perfil CurrentUserCurrentHost para o [!INCLUDE[ise_2](../Token/ise_2_md.md)] ou o perfil AllUsersCurrentHost para [!INCLUDE[ise_2](../Token/ise_2_md.md)].

-   Se você usar vários programas de host para executar o Windows PowerShell, salve suas funções, aliases, variáveis, e comandos em um perfil que afeta todos os programas de host, como o perfil CurrentUserAllHosts ou o AllUsersAllHosts e salve os recursos específicos do ISE, como a personalização de fonte e de cor, no perfil CurrentUserCurrentHost para o perfil [!INCLUDE[ise_2](../Token/ise_2_md.md)] ou AllUsersCurrentHost para [!INCLUDE[ise_2](../Token/ise_2_md.md)].

A seguir estão os perfis que podem ser criados e usados no [!INCLUDE[ise_2](../Token/ise_2_md.md)]. Cada perfil é salvo em seu próprio caminho específico.

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

1.  Para abrir o perfil, execute o comando psedit com a variável que especifica o perfil que você deseja editar. Por exemplo, para abrir o perfil de "Usuário atual, ISE do Windows PowerShell", digite: `psEdit $profile`

2.  Adicione alguns itens ao seu perfil. A seguir estão alguns exemplos para começar:

    -   Para alterar a cor da tela de fundo padrão do Painel de Console para azul, digite o seguinte no arquivo do perfil: `$psISE.Options.OutputPaneBackground = 'blue'` . Para obter mais informações sobre a variável $psISE, consulte a [Referência de Modelo de Objeto do ISE do Windows PowerShell](https://technet.microsoft.com/en-us/library/e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c).

    -   Para alterar o tamanho da fonte para 20, digite o seguinte no tipo de arquivo do perfil: `$psISE.Options.FontSize =20`

3.  Para salvar esse arquivo de perfil, no menu **Arquivo**, clique em **Salvar**. Da próxima vez que você abrir o [!INCLUDE[ise_2](../Token/ise_2_md.md)], suas personalizações serão aplicadas.

## Consulte Também
[about_Profiles [v4]](https://technet.microsoft.com/en-us/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054)
[Usando o ISE do Windows PowerShell](../Topic/Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=Apr16_HO2-->


