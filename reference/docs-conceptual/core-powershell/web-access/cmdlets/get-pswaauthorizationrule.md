---
description: ''
ms.topic: article
ms.prod: powershell
keywords: powershell, cmdlet
ms.date: 12/12/2016
title: get pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 74c044c329d8b6a305b86c9056a7041fb5fd046b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="get-pswaauthorizationrule"></a>Get-PswaAuthorizationRule

## <a name="synopsis"></a>SINOPSE

Retorna um conjunto de regras de autorização do Windows PowerShell® Web Access.

## <a name="syntax"></a>Sintaxe

### <a name="id"></a>ID
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a>Nome
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a>DESCRIÇÃO

O cmdlet **Get-PswaAuthorizationRule** retorna um conjunto de regras de autorização do Windows PowerShell® Web Access.
Se nem o parâmetro **Id** nem o parâmetro **RuleName** for especificado, esse cmdlet listará todas as regras. O parâmetro **Id** pode ser usado para filtrar os resultados.

## <a name="parameters"></a>PARÂMETROS

### <a name="-idltint32gt"></a>-Id&lt;Int32\[\]&gt;

Especifica as IDs (identificadores) das regras que este cmdlet deve obter. Se nenhuma ID for especificada, esse cmdlet retornará todas as regras de autorização.

|||
|-|-|
| Aliases                              | none                                 |
| Necessário?                            | false                                |
| Posição?                            | 2                                    |
| Valor padrão                        | none                                 |
| Aceitar entrada do pipeline?               | Verdadeiro (ByValue, ByPropertyName)       |
| Aceitar caracteres curinga?          | false                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;String\[\]&gt;

Especifica os nomes das regras de autorização a serem recuperadas. Este parâmetro retorna todas as regras que corresponderem exatamente aos nomes de regra das cadeias de caracteres nesta matriz.

|||
|-|-|
| Aliases                              | none                                 |
| Necessário?                            | verdadeiro                                 |
| Posição?                            | 2                                    |
| Valor padrão                        | none                                 |
| Aceitar entrada do pipeline?               | Verdadeiro (ByValue, ByPropertyName)       |
| Aceitar caracteres curinga?          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Esse cmdlet oferece suporte aos parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.
Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>ENTRADAS

### <a name="int"></a>int\[\]

Este cmdlet aceita uma matriz de inteiros ou uma matriz de valores de cadeia de caracteres como entrada.

### <a name="string"></a>String\[\]

Este cmdlet aceita uma matriz de inteiros ou uma matriz de valores de cadeia de caracteres como entrada.

## <a name="outputs"></a>SAÍDAS

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Este cmdlet gera um objeto PswaAuthorizationRule como saída.


## <a name="examples"></a>EXEMPLOS

### <a name="example-1"></a>EXEMPLO 1

Este exemplo obtém todas as regras.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a>EXEMPLO 2

Este exemplo obtém uma regra com uma ID igual a *2*.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a>EXEMPLO 3 {#example-3 .subHeading}

Este exemplo ilustra como o cmdlet aceita um valor do pipeline.
Uma ID de regra e um nome de regra são passados nesse cmdlet.

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a>Tópicos relacionados

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)