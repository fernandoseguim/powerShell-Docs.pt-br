---
description: ''
ms.topic: article
ms.prod: powershell
keywords: powershell, cmdlet
ms.date: 12/12/2016
title: uninstall pswawebapplication
ms.technology: powershell
ms.openlocfilehash: 139c8358a24e54dec630f8c78737728330ba4aa2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="uninstall-pswawebapplication"></a>Uninstall-PswaWebApplication

## <a name="synopsis"></a>SINOPSE

Desinstala o aplicativo Web Windows PowerShell®.

## <a name="syntax"></a>SINTAXE

### <a name="default"></a>Padrão
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIÇÃO

O cmdlet **Uninstall-PswaWebApplication** desinstala o aplicativo Web Windows PowerShell e remove o site do IIS. O cmdlet não desinstala o IIS nem nenhum outro recurso que foi instalado porque era necessário para a execução do Windows PowerShell.

## <a name="parameters"></a>PARÂMETROS

### <a name="-deletetestcertificate"></a>-DeleteTestCertificate

Indica que os certificados de teste criados pelo cmdlet **Install\_PswaWebApplication** (com o parâmetro **UseTestCertificate**) são excluídos.
Somente é removido o certificado de teste com o mesmo nome que aquele criado pelo cmdlet **Install-PswaWebApplication**.

|||
|-|-|
| Aliases                              | none                                 |
| Necessário?                            | false                                |
| Posição?                            | chamada                                |
| Valor padrão                        | verdadeiro                                 |
| Aceitar entrada do pipeline?               | false                                |
| Aceitar caracteres curinga?          | false                                |

### <a name="-webapplicationname-ltstringgt"></a>-WebApplicationName &lt;String&gt;

Especifica o nome do aplicativo Web a ser desinstalado.

|||
|-|-|
| Aliases                              | none                                 |
| Necessário?                            | false                                |
| Posição?                            | 1                                    |
| Valor padrão                        | pswa                                 |
| Aceitar entrada do pipeline?               | false                                |
| Aceitar caracteres curinga?          | false                                |

### <a name="-websitename-ltstringgt"></a>-WebSiteName &lt;String&gt;

Especifica o nome do site em que o aplicativo Web está instalado.

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

Esse cmdlet oferece suporte aos parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.
Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>ENTRADAS

Este cmdlet não aceita nenhuma entrada.

## <a name="outputs"></a>SAÍDAS

Esse cmdlet não retorna nenhuma saída.

## <a name="examples"></a>EXEMPLOS

### <a name="example-1"></a>EXEMPLO 1

Este comando desinstala o aplicativo Web Windows PowerShell.
Você poderá usar este cmdlet para desinstalar o aplicativo Web Windows PowerShell se ele tiver sido instalado usando os valores padrão.

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a>EXEMPLO 2

Esse comando desinstala o aplicativo Web Windows PowerShell e exclui o certificado de teste associado ao aplicativo.
Você poderá usar este cmdlet para desinstalar o aplicativo Web Windows PowerShell se o tiver instalado usando os valores padrão e tiver criado um certificado de teste.

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a>EXAMPLE 3 {#example-3 .subHeading}

Este comando desinstala o aplicativo Web Windows PowerShell quando um aplicativo e um site personalizados foram especificados durante a instalação.
O comando remove o site chamado *MySite* e o aplicativo chamado *TestApplication* e especifica que os certificados de teste associados ao aplicativo também são excluídos.

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a>Tópicos relacionados

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)