---
title: Ciclo de vida de suporte do PowerShell Core
description: Políticas que regem o suporte ao PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 2e0ca1b9c133e6f316a40aff13365d0489059165
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400588"
---
# <a name="powershell-core-support-lifecycle"></a>Ciclo de vida de suporte do PowerShell Core

O PowerShell Core é um conjunto distinto de ferramentas e componentes que é enviado, instalado e configurado separadamente do Windows PowerShell.
Portanto, o PowerShell Core não está incluído nos contratos de licenciamento do Windows 7/8.1/10 ou Windows Server.

No entanto, o PowerShell Core é aceito pelos tradicionais contratos de suporte da Microsoft, incluindo [Premier][], [Microsoft Enterprise Agreement][enterprise-agreement] e [Microsoft Software Assurance][assurance].
Você também pode pagar por [suporte assistido][] do PowerShell Core preenchendo uma solicitação de suporte para o seu problema.

Oferecemos também [suporte da comunidade][] no GitHub, no qual você pode registrar um problema, um bug ou uma solicitação de recurso.
Como alternativa, você pode encontrar ajuda de outros membros da comunidade na [Microsoft Community][] geral ou na Microsoft [Comunidade tecnológica do PowerShell][].
Não oferecemos nenhuma garantia de que o problema será resolvido ou resolvido de maneira oportuna.
Se você tiver um problema que requer atenção imediata, use as opções tradicionais de suporte pago.

## <a name="lifecycle-of-powershell-core"></a>Ciclo de vida do PowerShell Core

O PowerShell Core está adotando a [política de ciclo de vida moderna da Microsoft][modern].
Esse ciclo de vida do suporte destina-se a manter os clientes atualizados com as versões mais recentes.

A ramificação da versão 6.x do PowerShell Core será atualizada aproximadamente a cada seis meses (por exemplo, 6.0, 6.1, 6.2 etc.)

> [!IMPORTANT]
> Você deve atualizar em seis meses após cada novo lançamento de versão secundária para continuar a receber suporte.

Por exemplo, se o PowerShell Core 6.1 for liberado em 1º de julho de 2018, espera-se que você atualize para o PowerShell Core 6.1 até 1º de janeiro de 2019 para manter o suporte.

![Ciclo de vida de ramificação do PowerShell Core][lifecycle-chart]

A política de ciclo de vida moderna também requer que a Microsoft forneça aos clientes um aviso 12 meses antes de interromper o suporte para um produto (ou seja, o PowerShell Core).

Por fim, esperamos que o PowerShell Core adotará a abordagem de "manutenção de longo prazo", na qual podemos exigir apenas atualizações de manutenção e segurança para manter o suporte em uma ramificação/versão específica do 6.x.

## <a name="supported-platforms"></a>Plataformas com suporte

Consulte a tabela a seguir para ver qual plataforma da versão do PowerShell Core que você está usando tem suporte oficial.

Nossa comunidade também contribuiu com pacotes para algumas plataformas, mas eles não têm suporte oficial.
Esses pacotes são marcados como `Community` na tabela.

As plataformas listadas como `Experimental` não têm suporte oficialmente, mas estão disponíveis para experimentação e comentários.

|                                                   | 6.0         | 6.1         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 e 10                            | Suportado   | Suportado   |
| Windows Server 2008 R2, 2012 R2, 2016             | Suportado   | Suportado   |
| [Windows Server Canal Semestral][semi-annual] | Suportado   | Suportado   |
| Ubuntu 14.04 e 16.04                           | Suportado   | Suportado   |
| Ubuntu 18.04                                      |             | Suportado   |
| Ubuntu 18.10 (por meio do pacote Snap)                   |             | Comunidade   |
| Debian 8.7+ e 9+                                | Suportado   | Suportado   |
| CentOS 7                                          | Suportado   | Suportado   |
| Red Hat Enterprise Linux 7                        | Suportado   | Suportado   |
| OpenSUSE 42.3                                     | Suportado   | Suportado   |
| Fedora 27                                         | Suportado   | Suportado   |
| Fedora 28                                         |             | Suportado   |
| macOS 10.12+                                      | Suportado   | Suportado   |
| Arch                                              | Comunidade   | Comunidade   |
| Raspbian                                          | Experimental| Comunidade   |
| Kali                                              | Comunidade   | Comunidade   |
| AppImage (funciona em várias plataformas Linux)     | Comunidade   | Comunidade   |
| [Pacote Snap](https://snapcraft.io/powershell)   | Consultar a observação    | Consultar a observação    |

> [!NOTE]
> Pacotes Snap estarão em fase experimental por um período.  Depois que estivermos confiantes de que não surgirão novos problemas de suporte para o Snap, o suporte seguirá a distribuição na qual você está executando o pacote.

## <a name="platform-which-are-out-of-support"></a>Plataforma sem suporte

Quando uma versão de plataforma atingir o final da vida, conforme definido pelo proprietário da plataforma, o PowerShell Core também deixará de dar suporte para essa versão de plataforma. Os pacotes liberados anteriormente continuarão disponíveis para clientes que precisam de acesso, mas suporte formal e atualizações de qualquer tipo não serão fornecidos.

Portanto, o suporte para as versões a seguir foi finalizado pelos proprietários de distribuição.

| SO       | Versão | Fim de vida                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 24      | [Agosto de 2017](https://fedoramagazine.org/fedora-24-eol/)                                    |
| Fedora   | 25      | [Dezembro de 2017](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 26      | [Maio de 2018](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| openSUSE | 42.1    | [Maio de 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| openSUSE | 42.2    | [Janeiro de 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| Ubuntu   | 16.10   | [Julho de 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| Ubuntu   | 17.04   | [Janeiro de 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 17.10   | [Julho de 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |

## <a name="notes-on-licensing"></a>Observações sobre o licenciamento

O PowerShell Core foi lançado sob a [licença MIT][].
Sob essa licença e na ausência de um contrato de suporte pago, os usuários estão limitados ao [suporte da comunidade][].
Com o suporte da comunidade, a Microsoft não faz nenhuma garantia de capacidade de resposta ou correções.

## <a name="windows-powershell-module"></a>Módulo do Windows PowerShell

O suporte para o PowerShell Core não se estende para outros módulos do produto, a menos que esses módulos deem suporte explicitamente ao PowerShell Core.
Por exemplo, usar o módulo `ActiveDirectory` fornecido como parte do Windows Server é um cenário sem suporte.

No entanto, os módulos que não dão suporte explicitamente ao PowerShell Core podem ser compatíveis em alguns casos.
Instalando o módulo [`WindowsPSModulePath`][], você pode acrescentar o Windows PowerShell `PSModulePath` ao PowerShell Core `PSModulePath`.

Primeiro, instale o módulo `WindowsPSModulePath` na Galeria do PowerShell:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Depois de instalar esse módulo, execute o cmdlet `Add-WindowsPSModulePath` para adicionar o Windows PowerShell `PSModulePath` ao PowerShell Core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[suporte da comunidade]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[Comunidade tecnológica do PowerShell]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[suporte assistido]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[licença MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
