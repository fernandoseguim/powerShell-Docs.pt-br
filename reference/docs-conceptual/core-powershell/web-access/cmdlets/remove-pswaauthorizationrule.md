---
ms.topic: reference
keywords: powershell, cmdlet
ms.date: 12/12/2016
title: Remove-PswaAuthorizationRule
ms.openlocfilehash: 6a3720bb9b8df3e1c6bb9f4a6196c9868b85b67d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="remove-pswaauthorizationrule"></a>Remove-PswaAuthorizationRule

## <a name="synopsis"></a>SINOPSE

Remove uma regra de autorização especificada do Windows PowerShell® Web Access.

## <a name="syntax"></a>SINTAXE

### <a name="id"></a>Id
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a>Regra
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIÇÃO

Remove uma regra de autorização especificada do Windows PowerShell Web Access.

## <a name="parameters"></a>PARÂMETROS

### <a name="-force"></a>-Force

Executa o cmdlet sem solicitar confirmação. Por padrão, o cmdlet solicita confirmação antes de continuar.

|||
|-|-|
| Aliases                              | none                                 |
| Necessário?                            | false                                |
| Posição?                            | chamada                                |
| Valor padrão                        | none                                 |
| Aceitar entrada do pipeline?               | false                                |
| Aceitar caracteres curinga?          | false                                |

### <a name="-id-ltint32gt"></a>-Id &lt;Int32\[\]&gt;

Especifica as IDs (identificadores) de uma ou mais regras a serem removidas.

|||
|-|-|
| Aliases                              | none                                 |
| Necessário?                            | verdadeiro                                 |
| Posição?                            | 2                                    |
| Valor padrão                        | none                                 |
| Aceitar entrada do pipeline?               | Verdadeiro (ByValue, ByPropertyName)       |
| Aceitar caracteres curinga?          | false                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Rule &lt;PswaAuthorizationRule\[\]&gt;

Especifica as regras a serem removidas.

|||
|-|-|
| Aliases                              | none                                 |
| Necessário?                            | verdadeiro                                 |
| Posição?                            | 2                                    |
| Valor padrão                        | none                                 |
| Aceitar entrada do pipeline?               | True (ByValue)                       |
| Aceitar caracteres curinga?          | false                                |

### <a name="-confirm"></a>-Confirm

Solicita que você confirme antes de executar o cmdlet.

|||
|-|-|
| Necessário?                            | false                                |
| Posição?                            | chamada                                |
| Valor padrão                        | false                                |
| Aceitar entrada do pipeline?               | false                                |
| Aceitar caracteres curinga?          | false                                |

### <a name="-whatif"></a>-WhatIf

Mostra o que aconteceria se o cmdlet fosse executado. O cmdlet não é executado.

|||
|-|-|
| Necessário?                            | false                                |
| Posição?                            | chamada                                |
| Valor padrão                        | false                                |
| Aceitar entrada do pipeline?               | false                                |
| Aceitar caracteres curinga?          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Esse cmdlet oferece suporte aos parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.
Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>ENTRADAS

### <a name="int"></a>int\[\]

Este cmdlet aceita uma matriz de inteiros ou uma matriz de objetos PswaAuthorizationRule.

### <a name="pswaauthorizationrule"></a>PswaAuthorizationRule\[\]

Este cmdlet aceita uma matriz de inteiros ou uma matriz de objetos PswaAuthorizationRule.

## <a name="outputs"></a>SAÍDAS

Este cmdlet não produz nenhuma saída.

## <a name="examples"></a>EXEMPLOS

### <a name="example-1"></a>EXEMPLO 1

Este exemplo remove a regra de autorização com a ID *2*.

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a>EXAMPLE 2 {#example-2 .subHeading}

Este exemplo remove todas as regras de autorização e também requer a confirmação do usuário.

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a>Tópicos relacionados

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)