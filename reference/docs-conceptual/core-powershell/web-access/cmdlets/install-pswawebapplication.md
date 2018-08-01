---
ms.topic: reference
keywords: powershell, cmdlet
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 29e074b75eeb387640831229c63142e6dd5e991a
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268292"
---
# <a name="install-pswawebapplication"></a>Install-PswaWebApplication

## <a name="synopsis"></a>SINOPSE

Configura o aplicativo Web Windows PowerShell Web Access no IIS.

## <a name="syntax"></a>SINTAXE

### <a name="default"></a>Padrão
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIÇÃO

O cmdlet **Install-PswaWebApplication** configura o aplicativo Web Windows PowerShell Web Access.
Este cmdlet instala o aplicativo Web, associa-o a um site e, opcionalmente, cria um certificado SSL de teste usando o parâmetro **useTestCertificate**. Por motivo de segurança, os administradores da Web não devem usar um certificado de teste para ambientes de produção.

## <a name="parameters"></a>PARÂMETROS

### <a name="-usetestcertificate"></a>-UseTestCertificate

Especifica que um certificado de teste é criado. Se esse parâmetro for definido como true, esse cmdlet criará um certificado de teste e configurará o aplicativo Web Windows PowerShell Web Access para usar o certificado para solicitações HTTPS. Se esse parâmetro for definido como false, não serão criados certificados nem associações. Defina esse valor como false se outro certificado for usado para o Windows PowerShell Web Access.

|||
|-|-|
| Aliases                              | none                                 |
| Necessário?                            | false                                |
| Posição?                            | chamada                                |
| Valor padrão                        | verdadeiro                                 |
| Aceitar entrada do pipeline?               | false                                |
| Aceitar caracteres curinga?          | false                                |

### <a name="-webapplicationname"></a>-WebApplicationName

Especifica o nome do seu aplicativo Web. Essa opção é exibida como a última parte da URL do Windows PowerShell Web Access.

|||
|-|-|
| Aliases                              | none                                 |
| Necessário?                            | false                                |
| Posição?                            | 1                                    |
| Valor padrão                        | pswa                                 |
| Aceitar entrada do pipeline?               | false                                |
| Aceitar caracteres curinga?          | false                                |

### <a name="-websitename"></a>-WebSiteName

Especifica o nome do site do Servidor Web (IIS) no qual este aplicativo Web Windows PowerShell Web Access será instalado.

|||
|-|-|
| Aliases                              | none                                 |
| Necessário?                            | false                                |
| Posição?                            | chamada                                |
| Valor padrão                        | Site padrão                     |
| Aceitar entrada do pipeline?               | false                                |
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

Mostra o que aconteceria se o cmdlet fosse executado.
O cmdlet não é executado.

|||
|-|-|
| Necessário?                            | false                                |
| Posição?                            | chamada                                |
| Valor padrão                        | false                                |
| Aceitar entrada do pipeline?               | false                                |
| Aceitar caracteres curinga?          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Esse cmdlet oferece suporte aos parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable. Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>ENTRADAS

Este cmdlet não aceita nenhuma entrada.

## <a name="outputs"></a>SAÍDAS

Este cmdlet não produz nenhuma saída.

## <a name="examples"></a>EXEMPLOS

### <a name="example-1"></a>EXEMPLO 1

Este exemplo instala o aplicativo Web PSWA usando os valores padrão para os parâmetros **WebApplicationName** (*pswa*) e **WebSiteName** (*Site Padrão*).

```
Install-PswaWebApplication
```

### <a name="example-2"></a>EXEMPLO 2

Este exemplo instala o aplicativo Web PSWA com um certificado de teste e usando os valores padrão para os parâmetros **WebApplicationName** e **WebSiteName**.

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a>Tópicos relacionados

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)