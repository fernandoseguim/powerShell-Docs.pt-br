# <a name="powershell-core-support-lifecycle"></a>Ciclo de vida de suporte do PowerShell Core

O PowerShell Core é um conjunto distinto de ferramentas e componentes que é enviado, instalado e configurado separadamente do Windows PowerShell.
Portanto, o PowerShell Core não está incluído nos contratos de licenciamento do Windows 7/8.1/10 ou Windows Server.

No entanto, o PowerShell Core é aceito pelos tradicionais contratos de suporte da Microsoft, incluindo [Premier][], [Microsoft Enterprise Agreement][enterprise-agreement] e [Microsoft Software Assurance][assurance].
Você também pode pagar por [suporte assistido][] do PowerShell Core preenchendo uma solicitação de suporte para o seu problema.

Oferecemos também [suporte da comunidade][] no GitHub, no qual você pode registrar um problema, um bug ou uma solicitação de recurso.
Como alternativa, você pode encontrar ajuda de outros membros da comunidade na [Microsoft Community][] geral ou na Microsoft [PowerShell Tech Community][].
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

O PowerShell Core é oficialmente compatível com as seguintes plataformas:

* Windows 7, 8.1 e 10
* Windows Server 2008 R2, 2012 R2, 2016
* [Windows Server Canal Semestral][semi-annual]
* Ubuntu 14.04, 16.04 e 17.04
* Debian 8.7+ e 9+
* CentOS 7
* Red Hat Enterprise Linux 7
* OpenSUSE 42.2
* Fedora 25, 26
* macOS 10.12+

Nossa comunidade também contribuiu com pacotes para as seguintes plataformas, mas eles não têm suporte oficialmente:

* Arch Linux
* Kali Linux
* AppImage (funciona em várias plataformas Linux)

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
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[suporte assistido]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[licença MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
