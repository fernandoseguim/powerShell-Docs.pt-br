---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: Como usar perfis no ISE do Windows PowerShell
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: 45d0187504ff2dc8f45824bf50aad39e55f7a224
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a>Como usar perfis no ISE do Windows PowerShell
Este tópico explica como usar perfis no ISE (Ambiente de Script Integrado) do Windows PowerShell®. Antes de executar as tarefas nesta seção, é recomendável que você examine [about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630)) ou que, no Painel de Console, digite `Get-Help about_Profiles` e pressione **ENTER**.

Um perfil é um script do ISE do Windows PowerShell executado automaticamente quando você inicia uma nova sessão.  Você pode criar um ou mais perfis do Windows PowerShell para o ISE do Windows PowerShell e usá-los para adicionar a configuração do Windows PowerShell ou o ambiente ISE do Windows PowerShell, preparando-o para seu uso, com variáveis, aliases, funções, cores e preferências de fonte que você quer disponíveis. Um perfil afeta cada sessão de ISE do Windows PowerShell que você começar.

> [!NOTE]
> A política de execução do Windows PowerShell determina se você pode executar scripts e carregar um perfil. A política de execução padrão, “Restricted”, impede a execução de todos os scripts, incluindo perfis. Se você usar a política “Restricted”, não será possível carregar o perfil. Para obter mais informações sobre as políticas, consulte [about_Execution_Policies [v4]](https://technet.microsoft.com/library/347708dc-1515-4d74-978b-8334603472e6(v=wps.630)).

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a>Selecionar um perfil para usar com o ISE do Windows PowerShell
O ISE do Windows PowerShell dá suporte a perfis para o usuário atual e todos os usuários. Ele também dá suporte a perfis do Windows PowerShell que se aplicam a todos os hosts.

O perfil que você usa é determinado pela forma como você usa o Windows PowerShell e o ISE do Windows PowerShell.

-   Se você usar apenas o ISE do Windows PowerShell para executar o Windows PowerShell, salve todos os seus itens em um dos perfis específicos do ISE, como o perfil CurrentUserCurrentHost ou o perfil AllUsersCurrentHost para o ISE do Windows PowerShell.

-   Se você usar vários programas host para executar o Windows PowerShell, salve funções, aliases, variáveis e comandos em um perfil que afete todos os programas host, como o perfil CurrentUserAllHosts ou AllUsersAllHosts, e salve recursos específicos do ISE, como cor e personalização de fonte, no perfil CurrentUserCurrentHost do perfil do ISE do Windows PowerShell ou o perfil AllUsersCurrentHost do ISE do Windows PowerShell.

A seguir, os perfis que podem ser criados e usados no ISE do Windows PowerShell. Cada perfil é salvo em seu próprio caminho específico.

| Tipo de Perfil | Caminho do Perfil |
| --- | --- |
| **Usuário atual, ISE do PowerShell**| `$PROFILE.CurrentUserCurrentHost` ou `$PROFILE` |
| **Todos os usuários, ISE do PowerShell**| `$PROFILE.AllUsersCurrentHost` |
| **Usuário atual, Todos os hosts**| `$PROFILE.CurrentUserAllHosts` |
| **Todos os usuários, Todos os hosts** | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a>Para criar um novo perfil
Para criar um novo perfil de "Usuário atual, ISE do Windows PowerShell", execute este comando:

```PowerShell
if (!(Test-Path -Path $PROFILE )) 
{ New-Item -Type File -Path $PROFILE -Force }
```

Para criar um novo perfil de "Todos os usuários, ISE do Windows PowerShell", execute este comando:

```PowerShell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost)) 
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

Para criar um novo perfil de "Usuário atual, Todos os Hosts", execute este comando:

```PowerShell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts)) 
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

Para criar um novo perfil de "Todos os usuários, Todos os Hosts", digite:

```PowerShell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts)) 
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a>Para editar um perfil

1.  Para abrir o perfil, execute o comando psedit com a variável que especifica o perfil que você deseja editar. Por exemplo, para abrir o perfil de "Usuário atual, ISE do Windows PowerShell", digite: `psEdit $PROFILE`

2.  Adicione alguns itens ao seu perfil. A seguir estão alguns exemplos para começar:

    -   Para alterar a cor da tela de fundo padrão do Painel de Console para azul, digite o seguinte no arquivo do perfil: `$psISE.Options.OutputPaneBackground = 'blue'` . Para obter mais informações sobre a variável $psISE, consulte a [Referência de Modelo de Objeto do ISE do Windows PowerShell](#windows-powershell-ise-object-model-reference).

    -   Para alterar o tamanho da fonte para 20, digite o seguinte no tipo de arquivo do perfil: `$psISE.Options.FontSize =20`

3.  Para salvar esse arquivo de perfil, no menu **Arquivo**, clique em **Salvar**. Da próxima vez que você abrir o ISE do Windows PowerShell, as personalizações serão aplicadas.

## <a name="see-also"></a>Consulte Também
- [about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630))
- [Usando o ISE do Windows PowerShell](Using-the-Windows-PowerShell-ISE.md)

