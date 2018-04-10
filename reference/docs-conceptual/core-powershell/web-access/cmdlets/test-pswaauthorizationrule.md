---
description: ''
ms.topic: article
ms.prod: powershell
keywords: powershell, cmdlet
ms.date: 12/12/2016
title: test pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: ed6d56b2f3c4ee4ac410cdaadda312bffe506ee9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="test-pswaauthorizationrule"></a>Test-PswaAuthorizationRule

## <a name="synopsis"></a>SINOPSE

Verifica se existe uma regra para um usuário, computador ou ponto de extremidade especificado.

## <a name="syntax"></a>SINTAXE

### <a name="computername"></a>ComputerName
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a>ConnectionUri
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIÇÃO

O cmdlet **Test-PswaAuthorizationRule** verifica se existe uma regra para um usuário, computador ou ponto de extremidade especificado.
Esse cmdlet também pode ser usado para testa as regras de autorização a fim de validar se uma determinada solicitação de acesso de usuário, de computador ou de ponto de extremidade está autorizada.
Por padrão, esse cmdlet avalia todas as regras no arquivo de autorização.
No entanto, você pode especificar um subconjunto de regras a serem testadas.

Você pode usar este cmdlet para ajudar a solucionar problemas de falhas de autenticação.

Os parâmetros desse cmdlet correspondem aos campos na página de logon do Windows PowerShell® Web Access.

## <a name="parameters"></a>PARÂMETROS

### <a name="-computername-ltstringgt"></a>-ComputerName &lt;String&gt;

Especifica o nome do computador a ser testado.

|||
|-|-|
| Aliases                              | none                                 |
| Necessário?                            | verdadeiro                                 |
| Posição?                            | 2                                    |
| Valor padrão                        | none                                 |
| Aceitar entrada do pipeline?               | false                                |
| Aceitar caracteres curinga?          | false                                |

### <a name="-configurationname-ltstringgt"></a>-ConfigurationName &lt;String&gt;

Especifica o nome da configuração de sessão do Windows PowerShell, também conhecida como ponto de extremidade ou runspace, a ser testada.

|||
|-|-|
| Aliases                              | none                                 |
| Necessário?                            | false                                |
| Posição?                            | 3                                    |
| Valor padrão                        | none                                 |
| Aceitar entrada do pipeline?               | false                                |
| Aceitar caracteres curinga?          | false                                |

### <a name="-connectionuri-lturigt"></a>-ConnectionUri &lt;Uri&gt;

Especifica o URI de conexão a ser testado.

|||
|-|-|
| Aliases                              | none                                 |
| Necessário?                            | verdadeiro                                 |
| Posição?                            | 2                                    |
| Valor padrão                        | none                                 |
| Aceitar entrada do pipeline?               | false                                |
| Aceitar caracteres curinga?          | false                                |

### <a name="-credential-ltpscredentialgt"></a>-Credential &lt;PSCredential&gt;

Especifica um objeto **PSCredential** para uma conta de usuário que você deseja usar para testar as regras de autorização do Windows PowerShell Web Access. Se você não adicionar esse parâmetro, o cmdlet usará a conta do usuário conectado no momento. Para obter um objeto **PSCredential**, que é necessário para testar as regras de autorização remotamente, execute o cmdlet [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936).

|||
|-|-|
| Aliases                              | none                                 |
| Necessário?                            | false                                |
| Posição?                            | chamada                                |
| Valor padrão                        | none                                 |
| Aceitar entrada do pipeline?               | false                                |
| Aceitar caracteres curinga?          | false                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Rule &lt;PswaAuthorizationRule\[\]&gt;

Especifica um subconjunto de regras a serem testadas. Se esse parâmetro não for especificado, esse cmdlet testará todas as regras de autorização.

|||
|-|-|
| Aliases                              | none                                 |
| Necessário?                            | false                                |
| Posição?                            | chamada                                |
| Valor padrão                        | none                                 |
| Aceitar entrada do pipeline?               | True (ByValue)                       |
| Aceitar caracteres curinga?          | false                                |

### <a name="-username-ltstringgt"></a>-UserName &lt;String&gt;

Especifica o nome do usuário a ser testado.

|||
|-|-|
| Aliases                              | none                                 |
| Necessário?                            | verdadeiro                                 |
| Posição?                            | 1                                    |
| Valor padrão                        | none                                 |
| Aceitar entrada do pipeline?               | false                                |
| Aceitar caracteres curinga?          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Esse cmdlet oferece suporte aos parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.
Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>ENTRADAS

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Este cmdlet aceita uma matriz de objetos PswaAuthorizationRule como entrada.

## <a name="outputs"></a>SAÍDAS

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Esse cmdlet gera uma matriz de objetos PswaAuthorizationRule como saída.

## <a name="examples"></a>EXEMPLOS

### <a name="example-1"></a>EXEMPLO 1

Este exemplo testa todas as regras de autorização para exibir todas as regras que permitem que o usuário *contoso\\mhanson* se conecte ao computador *srv2* e use uma configuração de sessão do Windows PowerShell chamada *teste*.

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a>EXEMPLO 2

Este exemplo testa todas as regras de autorização para verificar quais regras de autorização se aplicam ao usuário *contoso\\mhanson*.

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a>Tópicos relacionados

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)