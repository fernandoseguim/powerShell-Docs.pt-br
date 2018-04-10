---
description: ''
ms.topic: article
ms.prod: powershell
keywords: powershell, cmdlet
ms.date: 12/12/2016
title: remove pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 28dbfe84827d6ccb99dce1ebb520cae66dc8c50e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
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