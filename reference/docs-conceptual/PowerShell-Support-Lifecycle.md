---
title: Ciclo de vida de suporte do PowerShell Core
description: Políticas que regem o suporte ao PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 178e5c43520f9a392ca219b9f785eb18b1ec5436
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623851"
---
# <a name="powershell-core-support-lifecycle"></a>Ciclo de vida de suporte do PowerShell Core

O PowerShell Core é um conjunto distinto de ferramentas e componentes que é enviado, instalado e configurado separadamente do Windows PowerShell.
Portanto, o PowerShell Core não está incluído nos contratos de licenciamento do Windows 7/8.1/10 ou Windows Server.

No entanto, o PowerShell Core é aceito pelos tradicionais contratos de suporte da Microsoft, incluindo [Premier][], [Microsoft Enterprise Agreement][enterprise-agreement] e [Microsoft Software Assurance][assurance].
Você também pode pagar por [suporte assistido][] do PowerShell Core preenchendo uma solicitação de suporte para o seu problema.

## <a name="community-support"></a>Suporte da comunidade

Oferecemos também [suporte da comunidade][] no GitHub, no qual você pode registrar um problema, um bug ou uma solicitação de recurso.
Além disso, você pode encontrar ajuda de outros membros da comunidade na [Microsoft Community][] geral ou na Microsoft [Comunidade tecnológica do PowerShell][].
Não oferecemos nenhuma garantia de que a comunidade atenderá ou resolverá seu problema de maneira oportuna.
Se você tiver um problema que requer atenção imediata, use as opções tradicionais de suporte pago.

## <a name="lifecycle-of-powershell-core"></a>Ciclo de vida do PowerShell Core

O PowerShell Core está adotando a [política de ciclo de vida moderna da Microsoft][modern].
Esse ciclo de vida do suporte destina-se a manter os clientes atualizados com as versões mais recentes.

A ramificação da versão 6.x do PowerShell Core será atualizada aproximadamente a cada seis meses (por exemplo: 6.0, 6.1, 6.2 etc.)

> [!IMPORTANT]
> Você deve atualizar em seis meses após cada novo lançamento de versão secundária para continuar a receber suporte.

Por exemplo, se o PowerShell Core 6.1 for liberado em 1º de julho de 2018, espera-se que você atualize para o PowerShell Core 6.1 até 1º de janeiro de 2019 para manter o suporte.

> [!IMPORTANT]
> Você deve atualizar em 30 dias após cada novo lançamento de versão de patch para continuar a receber suporte.

Por exemplo, se você estiver executando o PowerShell Core 6.1 e o 6.1.3 foi lançado em 19 de fevereiro de 2019, é esperado que você atualize para o PowerShell Core 6.1.3 até 21 de março de 2019, que é 30 dias após o lançamento para manter o suporte.
Se qualquer correção for considerada necessária, ela será lançada na nossa próxima atualização cumulativa.

![Ciclo de vida de ramificação do PowerShell Core][lifecycle-chart]

A política de ciclo de vida moderna também requer que a Microsoft forneça aos clientes um aviso 12 meses antes de interromper o suporte para um produto (ou seja, o PowerShell Core).

Por fim, esperamos que o PowerShell Core adote a abordagem de "manutenção de longo prazo".
Nessa abordagem de manutenção, exigiríamos apenas que as atualizações de serviço e segurança permanecessem em suporte em um branch/versão específica do 6.x.

## <a name="supported-platforms"></a>Plataformas com suporte

Na tabela a seguir, veja qual plataforma da versão do PowerShell Core que você está usando tem suporte oficial.

Nossa comunidade também contribuiu com pacotes para algumas plataformas, mas eles não têm suporte oficial.
Esses pacotes são marcados como `Community` na tabela.

As plataformas listadas como `Experimental` não têm suporte oficialmente, mas estão disponíveis para experimentação e comentários.

|                                                   | 6.1         | 6.2         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 e 10                            | Suportado   | Suportado   |
| Windows Server 2008 R2, 2012 R2, 2016             | Suportado   | Suportado   |
| [Windows Server Canal Semestral][semi-annual] | Suportado   | Suportado   |
| Ubuntu 16.04 e 18.04                            | Suportado   | Suportado   |
| Ubuntu 18.10 (por meio do pacote Snap)                   | Comunidade   | Comunidade   |
| Debian 9                                          | Suportado   | Suportado   |
| CentOS 7                                          | Suportado   | Suportado   |
| Red Hat Enterprise Linux 7                        | Suportado   | Suportado   |
| OpenSUSE 42.3                                     | Suportado   | Suportado   |
| Fedora 28                                         | Suportado   | Suportado   |
| macOS 10.12+                                      | Suportado   | Suportado   |
| Arch                                              | Comunidade   | Comunidade   |
| Raspbian                                          | Comunidade   | Comunidade   |
| Kali                                              | Comunidade   | Comunidade   |
| AppImage (funciona em várias plataformas Linux)     | Comunidade   | Comunidade   |
| [Pacote Snap](https://snapcraft.io/powershell)   | Consultar a observação    | Consultar a observação    |

> [!NOTE]
> Os pacotes de ajustes tem suporte da mesma forma que a distribuição na qual você está executando o pacote.

## <a name="powershell-release-end-of-life"></a>Fim da vida útil da versão do PowerShell

Com base no [Ciclo de vida do PowerShell Core](#lifecycle-of-powershell-core), a tabela a seguir lista as datas em que várias versões não terão mais suporte.

| Versão | Fim da vida útil                   |
|---------|-------------------------------|
| 6.0     | 13 de fevereiro de 2019             |
| 6.1     | 28 de setembro de 2019            |
| 6.2     | 6 meses após o lançamento do 6.3   |

## <a name="platforms-which-are-out-of-support"></a>Plataformas que estão sem suporte

Quando uma versão de plataforma atingir o final da vida, conforme definido pelo proprietário da plataforma, o PowerShell Core também encerrará o suporte dessa versão de plataforma.
Os pacotes liberados anteriormente continuarão disponíveis para clientes que precisam de acesso, mas suporte formal e atualizações de qualquer tipo não serão fornecidos.

Portanto, os proprietários de distribuição finalizaram o suporte para as versões a seguir e não são suportadas.

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
| Debian   | 8       | [Junho de 2018](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| Fedora   | 27      | [Novembro de 2018](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| Ubuntu   | 14.04   | [Abril de 2019](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a>Observações sobre o licenciamento

O PowerShell Core foi lançado sob a [licença MIT][].
Sob essa licença e sem um contrato de suporte pago, os usuários estão limitados ao [suporte da comunidade][].
Com o suporte da comunidade, a Microsoft não faz nenhuma garantia de capacidade de resposta ou correções.

## <a name="windows-powershell-module"></a>Módulo do Windows PowerShell

O suporte para o PowerShell Core não inclui módulos do produto, a menos que esses módulos deem suporte explicitamente ao PowerShell Core.
Por exemplo, usar o módulo `ActiveDirectory` fornecido como parte do Windows Server é um cenário sem suporte.

No entanto, os módulos que não dão suporte explicitamente ao PowerShell Core podem ser compatíveis em alguns casos.
Instalando o módulo [`WindowsPSModulePath`][], você pode adicionar o Windows PowerShell `PSModulePath` ao PowerShell Core `PSModulePath`.

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

## <a name="experimental-features"></a>Recursos experimentais

Os [recursos experimentais][] estão limitados ao [suporte da comunidade](#community-support).

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
[Recursos experimentais]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
