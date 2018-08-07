---
ms.topic: reference
keywords: powershell, cmdlet
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: bcf897730881551ec16ce970de6a1330961b67e6
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268258"
---
# <a name="add-pswaauthorizationrule"></a>Add-PswaAuthorizationRule

## <a name="synopsis"></a>SINOPSE

Adiciona uma nova regra de autorização ao conjunto de regras de autorização do Windows PowerShell Web Access.

## <a name="syntax"></a>Sintaxe

### <a name="usergroupnamecomputergroupname"></a>UserGroupNameComputerGroupName

```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a>UserGroupNameComputerName

```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a>UserNameComputerGroupName

```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a>UserNameComputerName

```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIÇÃO

O cmdlet **Add-PswaAuthorizationRule** adiciona uma nova regra de autorização ao conjunto de regras de autorização do Windows PowerShell(r) Web Access.

Você deve especificar os usuários, computadores e pontos de extremidade do Windows PowerShell para essa regra. Você pode especificar usuários e computadores por contas de usuário e nomes de computador individuais ou especificar grupos.

Para um computador ingressado em um domínio do Active Directory, o cmdlet usa o SID (identificador de segurança) do computador para criar a regra. Isso permite que você use um nome curto, um FQDN (nome de domínio totalmente qualificado) ou um endereço IP para o campo **Nome do Computador** na página de entrada.

Para um computador que não ingressou em um domínio do Active Directory, o cmdlet cria a regra usando o nome do computador fornecido pelo administrador. Para conectar-se com êxito a esse computador, o usuário final deve fornecer o nome do computador, exatamente como ele aparece na regra.

Se houver vários computadores com o mesmo nome na rede, o nome curto poderá ser resolvido para mais de um computador. Isso poderá causar ambiguidade ao estabelecer uma conexão. Por exemplo, se existir uma regra para o computador do grupo de trabalho chamado "*Server1*" e um novo computador chamado *server1.contoso.com* tiver ingressado na rede, a validação usando as regras de autorização será bem-sucedida e o Windows PowerShell Web Access tentará estabelecer uma conexão com o computador denominado "*Server1*". Não há garantia de que a conexão será estabelecida com o computador do grupo de trabalho especificado. Poderia ser feita uma tentativa no grupo de trabalho ou no computador de domínio chamado "*Server1*". Para reduzir a ambiguidade, é recomendável que você use o FQDN do computador de destino sempre que possível para criar uma regra de autorização.

As regras de autorização avaliam a credencial de logon principal dos usuários do Windows PowerShell Web Access, não as credenciais alternativas (o segundo conjunto de credenciais encontrado na seção **Configurações opcionais de conexão** da página de entrada). Para obter um exemplo disso, consulte o Exemplo 6.

## <a name="parameters"></a>Parâmetros

### <a name="-computergroupname-string"></a>-ComputerGroupName \<String\>

Especifica o nome de um grupo de computadores no AD DS (Active Directory Domain Services) ou de grupos locais aos quais essa regra concede acesso.

|||
|-|-|
| Aliases                     | none                  |
| Necessário?                   | verdadeiro                  |
| Posição?                   | chamada                 |
| Valor padrão               | none                  |
| Aceitar entrada do pipeline?      | True (ByPropertyName) |
| Aceitar caracteres curinga? | false                 |

### <a name="-computername-string"></a>-ComputerName \<String\>

Especifica o nome do computador ao qual esta regra concede acesso.

|||
|-|-|
| Aliases                     | none                  |
| Necessário?                   | verdadeiro                  |
| Posição?                   | chamada                 |
| Valor padrão               | none                  |
| Aceitar entrada do pipeline?      | True (ByPropertyName) |
| Aceitar caracteres curinga? | false                 |

### <a name="-configurationname-string"></a>-ConfigurationName \<String\>

Especifica o nome da configuração de sessão do Windows PowerShell, também conhecido como runspace, ao qual essa regra concede acesso.

|||
|-|-|
| Aliases                     | none                  |
| Necessário?                   | verdadeiro                  |
| Posição?                   | chamada                 |
| Valor padrão               | none                  |
| Aceitar entrada do pipeline?      | True (ByPropertyName) |
| Aceitar caracteres curinga? | false                 |

### <a name="-credential--pscredential"></a>-Credential \<PSCredential\>

Especifica um objeto **PSCredential** para uma conta de usuário que você deseja usar para alterar as regras de autorização do Windows PowerShell Web Access. Se você não adicionar esse parâmetro, o cmdlet usará a conta do usuário conectado no momento. Para obter um objeto **PSCredential**, que é necessário para adicionar regras de autorização remotamente, execute o cmdlet [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential).

|||
|-|-|
| Aliases                     | none  |
| Necessário?                   | false |
| Posição?                   | chamada |
| Valor padrão               | none  |
| Aceitar entrada do pipeline?      | false |
| Aceitar caracteres curinga? | false |

### <a name="-force"></a>-Force

Força o comando a ser executado sem solicitar a confirmação do usuário. Além disso, ele também solicita confirmação quando você insere um nome do computador curto ou simples (como um nome que não seja um nome de domínio ou não seja totalmente qualificado). A confirmação é solicitada por motivos de segurança, de modo que você apenas possa usar o nome simples para adicionar um computador se o computador estiver em um grupo de trabalho.

|||
|-|-|
| Aliases                              | none                                 |
| Necessário?                            | false                                |
| Posição?                            | chamada                                |
| Valor padrão                        | none                                 |
| Aceitar entrada do pipeline?               | false                                |
| Aceitar caracteres curinga?          | false                                |

### <a name="-rulename-string"></a>-RuleName \<String\>

Especifica o nome amigável dessa regra.

|||
|-|-|
| Aliases                              | none                                 |
| Necessário?                            | false                                |
| Posição?                            | chamada                                |
| Valor padrão                        | none                                 |
| Aceitar entrada do pipeline?               | True (ByPropertyName)                |
| Aceitar caracteres curinga?          | false                                |

### <a name="-usergroupname-string"></a>-UserGroupName \<String\[\]\>

Especifica o nome de um ou mais grupos de usuários no AD DS ou grupos locais aos quais essa regra concede acesso.

|||
|-|-|
| Aliases                              | none                                 |
| Necessário?                            | verdadeiro                                 |
| Posição?                            | chamada                                |
| Valor padrão                        | none                                 |
| Aceitar entrada do pipeline?               | True (ByPropertyName)                |
| Aceitar caracteres curinga?          | false                                |

### <a name="-username-string"></a>-UserName \<String\[\]\>

Especifica um ou mais usuários aos quais essa regra concede acesso. O nome de usuário pode ser uma conta de usuário local no computador do gateway ou um usuário no AD DS. O formato é `domain\user` ou `computer\user`.

|||
|-|-|
| Aliases                              | none                                 |
| Necessário?                            | verdadeiro                                 |
| Posição?                            | 1                                    |
| Valor padrão                        | none                                 |
| Aceitar entrada do pipeline?               | Verdadeiro (ByValue, ByPropertyName)       |
| Aceitar caracteres curinga?          | false                                |

###  <a name="commonparameters"></a>\<CommonParameters\>

Esse cmdlet oferece suporte aos parâmetros comuns:

-Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.
Para obter mais informações, consulte [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).

## <a name="inputs"></a>ENTRADAS

### <a name="string"></a>Cadeia de caracteres

Este cmdlet aceita uma cadeia de caracteres ou uma matriz de cadeias de caracteres como entrada.

### <a name="string"></a>String\[\]

Este cmdlet aceita uma cadeia de caracteres ou uma matriz de cadeias de caracteres como entrada.

## <a name="outputs"></a>Saídas

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule

Este cmdlet retorna o objeto de regra de autorização.

## <a name="examples"></a>EXEMPLOS

### <a name="example-1"></a>EXEMPLO 1

Este exemplo concede acesso à configuração de sessão _PSWAEndpoint_, um runspace restrito no _srv2_ para os usuários no grupo _SMAdmins_.

> [!NOTE]
> O nome do computador deve ser um FQDN (nome de domínio totalmente qualificado). Os administradores definem uma configuração de sessão restrita ou um runspace, que é um intervalo limitado de cmdlets e tarefas que os usuários finais podem executar. A definição de um runspace restrito pode evitar que usuários acessem outros computadores que não estejam no runspace permitido do Windows PowerShell(r), oferecendo assim uma conexão mais segura. Para saber mais sobre as configurações de sessão, confira [about_Session_Configurations](/powershell/module/microsoft.powershell.core/about/about_session_configurations) ou [Instalar e usar o Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).

```powershell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a>EXEMPLO 2

Este exemplo concede acesso à configuração de sessão padrão do Windows PowerShell, `Microsoft.PowerShell`, no *srv2* para os usuários chamados `contoso\user1`, `contoso\user2` e `contoso\user3`. Esse cmdlet cria três regras (uma por pessoa).

```powershell
Add-PswaAuthorizationRule -UserName contoso\user1, contoso\user2, contoso\user3 -ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a>EXEMPLO 3

Este exemplo ilustra como inserir valores de nome de usuário por meio do pipeline.

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule -ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a>EXEMPLO 4

Este exemplo ilustra como todos os parâmetros obtêm os valores do pipeline pelo nome da propriedade.

````powershell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" -PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a>EXEMPLO 5

Este exemplo adiciona uma regra para permitir que o usuário local chamado `PswaServer\ChrisLocal` acesse um servidor chamado **srv1.contoso.com**.

Este exemplo ilustra um cenário em que o gateway está em um grupo de trabalho e o computador de destino está em um domínio. A regra de autorização aplica-se aos usuários locais no gateway. Na página de logon do Windows PowerShell Web Access, para autenticar-se com êxito, o usuário deve fornecer um segundo conjunto de credenciais na área **Configurações opcionais de conexão**. O servidor de gateway usa o conjunto adicional de credenciais para autenticar o usuário no computador de destino, um servidor chamado *srv1.contoso.com*.

````powershell
Add-PswaAuthorizationRule -UserName PswaServer\ChrisLocal -ComputerName srv1.contoso.com -ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a>EXEMPLO 6

Este exemplo permite que todos os usuários acessem todos os pontos de extremidade em todos os computadores. Essa opção basicamente desativa as regras de autorização.

> [!NOTE]
> O uso do caractere curinga `*` não é recomendado para implantações que exigem um alto nível de segurança e só deve ser considerado para ambientes de teste ou usado em implantações nas quais a segurança possa ser reduzida.

````powershell
Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a>Consulte Também

[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)

[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)

[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)

[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)

[Add-Member](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936)