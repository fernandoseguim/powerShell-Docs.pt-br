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
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="9245d-103">Ciclo de vida de suporte do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="9245d-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="9245d-104">O PowerShell Core é um conjunto distinto de ferramentas e componentes que é enviado, instalado e configurado separadamente do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9245d-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="9245d-105">Portanto, o PowerShell Core não está incluído nos contratos de licenciamento do Windows 7/8.1/10 ou Windows Server.</span><span class="sxs-lookup"><span data-stu-id="9245d-105">Therefore, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="9245d-106">No entanto, o PowerShell Core é aceito pelos tradicionais contratos de suporte da Microsoft, incluindo [Premier][], [Microsoft Enterprise Agreement][enterprise-agreement] e [Microsoft Software Assurance][assurance].</span><span class="sxs-lookup"><span data-stu-id="9245d-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="9245d-107">Você também pode pagar por [suporte assistido][] do PowerShell Core preenchendo uma solicitação de suporte para o seu problema.</span><span class="sxs-lookup"><span data-stu-id="9245d-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="9245d-108">Oferecemos também [suporte da comunidade][] no GitHub, no qual você pode registrar um problema, um bug ou uma solicitação de recurso.</span><span class="sxs-lookup"><span data-stu-id="9245d-108">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="9245d-109">Como alternativa, você pode encontrar ajuda de outros membros da comunidade na [Microsoft Community][] geral ou na Microsoft [Comunidade tecnológica do PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="9245d-109">Alternatively, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="9245d-110">Não oferecemos nenhuma garantia de que o problema será resolvido ou resolvido de maneira oportuna.</span><span class="sxs-lookup"><span data-stu-id="9245d-110">We offer no guarantee there that your issue will be addressed or resolved in a timely manner.</span></span>
<span data-ttu-id="9245d-111">Se você tiver um problema que requer atenção imediata, use as opções tradicionais de suporte pago.</span><span class="sxs-lookup"><span data-stu-id="9245d-111">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="9245d-112">Ciclo de vida do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="9245d-112">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="9245d-113">O PowerShell Core está adotando a [política de ciclo de vida moderna da Microsoft][modern].</span><span class="sxs-lookup"><span data-stu-id="9245d-113">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="9245d-114">Esse ciclo de vida do suporte destina-se a manter os clientes atualizados com as versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="9245d-114">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="9245d-115">A ramificação da versão 6.x do PowerShell Core será atualizada aproximadamente a cada seis meses (por exemplo, 6.0, 6.1, 6.2 etc.)</span><span class="sxs-lookup"><span data-stu-id="9245d-115">The version 6.x branch of PowerShell Core will be updated approximately once every six months (e.g. 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9245d-116">Você deve atualizar em seis meses após cada novo lançamento de versão secundária para continuar a receber suporte.</span><span class="sxs-lookup"><span data-stu-id="9245d-116">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="9245d-117">Por exemplo, se o PowerShell Core 6.1 for liberado em 1º de julho de 2018, espera-se que você atualize para o PowerShell Core 6.1 até 1º de janeiro de 2019 para manter o suporte.</span><span class="sxs-lookup"><span data-stu-id="9245d-117">For example, if PowerShell Core 6.1 is released on July 1st, 2018, you would be expected to update to PowerShell Core 6.1 by January 1st, 2019 to maintain support.</span></span>

![Ciclo de vida de ramificação do PowerShell Core][lifecycle-chart]

<span data-ttu-id="9245d-119">A política de ciclo de vida moderna também requer que a Microsoft forneça aos clientes um aviso 12 meses antes de interromper o suporte para um produto (ou seja, o PowerShell Core).</span><span class="sxs-lookup"><span data-stu-id="9245d-119">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (i.e. PowerShell Core).</span></span>

<span data-ttu-id="9245d-120">Por fim, esperamos que o PowerShell Core adotará a abordagem de "manutenção de longo prazo", na qual podemos exigir apenas atualizações de manutenção e segurança para manter o suporte em uma ramificação/versão específica do 6.x.</span><span class="sxs-lookup"><span data-stu-id="9245d-120">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach where we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="9245d-121">Plataformas com suporte</span><span class="sxs-lookup"><span data-stu-id="9245d-121">Supported platforms</span></span>

<span data-ttu-id="9245d-122">Consulte a tabela a seguir para ver qual plataforma da versão do PowerShell Core que você está usando tem suporte oficial.</span><span class="sxs-lookup"><span data-stu-id="9245d-122">Please see the following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="9245d-123">Nossa comunidade também contribuiu com pacotes para algumas plataformas, mas eles não têm suporte oficial.</span><span class="sxs-lookup"><span data-stu-id="9245d-123">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="9245d-124">Esses pacotes são marcados como `Community` na tabela.</span><span class="sxs-lookup"><span data-stu-id="9245d-124">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="9245d-125">As plataformas listadas como `Experimental` não têm suporte oficialmente, mas estão disponíveis para experimentação e comentários.</span><span class="sxs-lookup"><span data-stu-id="9245d-125">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="9245d-126">6.0</span><span class="sxs-lookup"><span data-stu-id="9245d-126">6.0</span></span>         | <span data-ttu-id="9245d-127">6.1</span><span class="sxs-lookup"><span data-stu-id="9245d-127">6.1</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="9245d-128">Windows 7, 8.1 e 10</span><span class="sxs-lookup"><span data-stu-id="9245d-128">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="9245d-129">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-129">Supported</span></span>   | <span data-ttu-id="9245d-130">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-130">Supported</span></span>   |
| <span data-ttu-id="9245d-131">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="9245d-131">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="9245d-132">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-132">Supported</span></span>   | <span data-ttu-id="9245d-133">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-133">Supported</span></span>   |
| <span data-ttu-id="9245d-134">[Windows Server Canal Semestral][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="9245d-134">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="9245d-135">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-135">Supported</span></span>   | <span data-ttu-id="9245d-136">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-136">Supported</span></span>   |
| <span data-ttu-id="9245d-137">Ubuntu 14.04 e 16.04</span><span class="sxs-lookup"><span data-stu-id="9245d-137">Ubuntu 14.04 and, 16.04</span></span>                           | <span data-ttu-id="9245d-138">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-138">Supported</span></span>   | <span data-ttu-id="9245d-139">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-139">Supported</span></span>   |
| <span data-ttu-id="9245d-140">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="9245d-140">Ubuntu 18.04</span></span>                                      |             | <span data-ttu-id="9245d-141">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-141">Supported</span></span>   |
| <span data-ttu-id="9245d-142">Ubuntu 18.10 (por meio do pacote Snap)</span><span class="sxs-lookup"><span data-stu-id="9245d-142">Ubuntu 18.10 (via Snap Package)</span></span>                   |             | <span data-ttu-id="9245d-143">Comunidade</span><span class="sxs-lookup"><span data-stu-id="9245d-143">Community</span></span>   |
| <span data-ttu-id="9245d-144">Debian 8.7+ e 9+</span><span class="sxs-lookup"><span data-stu-id="9245d-144">Debian 8.7+, and 9</span></span>                                | <span data-ttu-id="9245d-145">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-145">Supported</span></span>   | <span data-ttu-id="9245d-146">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-146">Supported</span></span>   |
| <span data-ttu-id="9245d-147">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="9245d-147">CentOS 7</span></span>                                          | <span data-ttu-id="9245d-148">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-148">Supported</span></span>   | <span data-ttu-id="9245d-149">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-149">Supported</span></span>   |
| <span data-ttu-id="9245d-150">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="9245d-150">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="9245d-151">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-151">Supported</span></span>   | <span data-ttu-id="9245d-152">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-152">Supported</span></span>   |
| <span data-ttu-id="9245d-153">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="9245d-153">OpenSUSE 42.3</span></span>                                     | <span data-ttu-id="9245d-154">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-154">Supported</span></span>   | <span data-ttu-id="9245d-155">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-155">Supported</span></span>   |
| <span data-ttu-id="9245d-156">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="9245d-156">Fedora 27</span></span>                                         | <span data-ttu-id="9245d-157">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-157">Supported</span></span>   | <span data-ttu-id="9245d-158">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-158">Supported</span></span>   |
| <span data-ttu-id="9245d-159">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="9245d-159">Fedora 28</span></span>                                         |             | <span data-ttu-id="9245d-160">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-160">Supported</span></span>   |
| <span data-ttu-id="9245d-161">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="9245d-161">macOS 10.12+</span></span>                                      | <span data-ttu-id="9245d-162">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-162">Supported</span></span>   | <span data-ttu-id="9245d-163">Suportado</span><span class="sxs-lookup"><span data-stu-id="9245d-163">Supported</span></span>   |
| <span data-ttu-id="9245d-164">Arch</span><span class="sxs-lookup"><span data-stu-id="9245d-164">Arch</span></span>                                              | <span data-ttu-id="9245d-165">Comunidade</span><span class="sxs-lookup"><span data-stu-id="9245d-165">Community</span></span>   | <span data-ttu-id="9245d-166">Comunidade</span><span class="sxs-lookup"><span data-stu-id="9245d-166">Community</span></span>   |
| <span data-ttu-id="9245d-167">Raspbian</span><span class="sxs-lookup"><span data-stu-id="9245d-167">Raspbian</span></span>                                          | <span data-ttu-id="9245d-168">Experimental</span><span class="sxs-lookup"><span data-stu-id="9245d-168">Experimental</span></span>| <span data-ttu-id="9245d-169">Comunidade</span><span class="sxs-lookup"><span data-stu-id="9245d-169">Community</span></span>   |
| <span data-ttu-id="9245d-170">Kali</span><span class="sxs-lookup"><span data-stu-id="9245d-170">Kali</span></span>                                              | <span data-ttu-id="9245d-171">Comunidade</span><span class="sxs-lookup"><span data-stu-id="9245d-171">Community</span></span>   | <span data-ttu-id="9245d-172">Comunidade</span><span class="sxs-lookup"><span data-stu-id="9245d-172">Community</span></span>   |
| <span data-ttu-id="9245d-173">AppImage (funciona em várias plataformas Linux)</span><span class="sxs-lookup"><span data-stu-id="9245d-173">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="9245d-174">Comunidade</span><span class="sxs-lookup"><span data-stu-id="9245d-174">Community</span></span>   | <span data-ttu-id="9245d-175">Comunidade</span><span class="sxs-lookup"><span data-stu-id="9245d-175">Community</span></span>   |
| [<span data-ttu-id="9245d-176">Pacote Snap</span><span class="sxs-lookup"><span data-stu-id="9245d-176">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="9245d-177">Consultar a observação</span><span class="sxs-lookup"><span data-stu-id="9245d-177">See note</span></span>    | <span data-ttu-id="9245d-178">Consultar a observação</span><span class="sxs-lookup"><span data-stu-id="9245d-178">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="9245d-179">Pacotes Snap estarão em fase experimental por um período.</span><span class="sxs-lookup"><span data-stu-id="9245d-179">Snap packages will be experimental for a period.</span></span>  <span data-ttu-id="9245d-180">Depois que estivermos confiantes de que não surgirão novos problemas de suporte para o Snap, o suporte seguirá a distribuição na qual você está executando o pacote.</span><span class="sxs-lookup"><span data-stu-id="9245d-180">After, we are confident that Snap does not introduce new support issues, the support will follow the distribution you are running the package on.</span></span>

## <a name="platform-which-are-out-of-support"></a><span data-ttu-id="9245d-181">Plataforma sem suporte</span><span class="sxs-lookup"><span data-stu-id="9245d-181">Platform which are out of support</span></span>

<span data-ttu-id="9245d-182">Quando uma versão de plataforma atingir o final da vida, conforme definido pelo proprietário da plataforma, o PowerShell Core também deixará de dar suporte para essa versão de plataforma.</span><span class="sxs-lookup"><span data-stu-id="9245d-182">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to provide support for that platform version.</span></span> <span data-ttu-id="9245d-183">Os pacotes liberados anteriormente continuarão disponíveis para clientes que precisam de acesso, mas suporte formal e atualizações de qualquer tipo não serão fornecidos.</span><span class="sxs-lookup"><span data-stu-id="9245d-183">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="9245d-184">Portanto, o suporte para as versões a seguir foi finalizado pelos proprietários de distribuição.</span><span class="sxs-lookup"><span data-stu-id="9245d-184">Therefore, support for the following versions was ended by the distribution owners and are not supported.</span></span>

| <span data-ttu-id="9245d-185">SO</span><span class="sxs-lookup"><span data-stu-id="9245d-185">OS</span></span>       | <span data-ttu-id="9245d-186">Versão</span><span class="sxs-lookup"><span data-stu-id="9245d-186">Version</span></span> | <span data-ttu-id="9245d-187">Fim de vida</span><span class="sxs-lookup"><span data-stu-id="9245d-187">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="9245d-188">Fedora</span><span class="sxs-lookup"><span data-stu-id="9245d-188">Fedora</span></span>   | <span data-ttu-id="9245d-189">24</span><span class="sxs-lookup"><span data-stu-id="9245d-189">24</span></span>      | [<span data-ttu-id="9245d-190">Agosto de 2017</span><span class="sxs-lookup"><span data-stu-id="9245d-190">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="9245d-191">Fedora</span><span class="sxs-lookup"><span data-stu-id="9245d-191">Fedora</span></span>   | <span data-ttu-id="9245d-192">25</span><span class="sxs-lookup"><span data-stu-id="9245d-192">25</span></span>      | [<span data-ttu-id="9245d-193">Dezembro de 2017</span><span class="sxs-lookup"><span data-stu-id="9245d-193">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="9245d-194">Fedora</span><span class="sxs-lookup"><span data-stu-id="9245d-194">Fedora</span></span>   | <span data-ttu-id="9245d-195">26</span><span class="sxs-lookup"><span data-stu-id="9245d-195">26</span></span>      | [<span data-ttu-id="9245d-196">Maio de 2018</span><span class="sxs-lookup"><span data-stu-id="9245d-196">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="9245d-197">openSUSE</span><span class="sxs-lookup"><span data-stu-id="9245d-197">openSUSE</span></span> | <span data-ttu-id="9245d-198">42.1</span><span class="sxs-lookup"><span data-stu-id="9245d-198">42.1</span></span>    | [<span data-ttu-id="9245d-199">Maio de 2017</span><span class="sxs-lookup"><span data-stu-id="9245d-199">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="9245d-200">openSUSE</span><span class="sxs-lookup"><span data-stu-id="9245d-200">openSUSE</span></span> | <span data-ttu-id="9245d-201">42.2</span><span class="sxs-lookup"><span data-stu-id="9245d-201">42.2</span></span>    | [<span data-ttu-id="9245d-202">Janeiro de 2018</span><span class="sxs-lookup"><span data-stu-id="9245d-202">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="9245d-203">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="9245d-203">Ubuntu</span></span>   | <span data-ttu-id="9245d-204">16.10</span><span class="sxs-lookup"><span data-stu-id="9245d-204">16.10</span></span>   | [<span data-ttu-id="9245d-205">Julho de 2017</span><span class="sxs-lookup"><span data-stu-id="9245d-205">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="9245d-206">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="9245d-206">Ubuntu</span></span>   | <span data-ttu-id="9245d-207">17.04</span><span class="sxs-lookup"><span data-stu-id="9245d-207">17.04</span></span>   | [<span data-ttu-id="9245d-208">Janeiro de 2018</span><span class="sxs-lookup"><span data-stu-id="9245d-208">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="9245d-209">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="9245d-209">Ubuntu</span></span>   | <span data-ttu-id="9245d-210">17.10</span><span class="sxs-lookup"><span data-stu-id="9245d-210">17.10</span></span>   | [<span data-ttu-id="9245d-211">Julho de 2018</span><span class="sxs-lookup"><span data-stu-id="9245d-211">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |

## <a name="notes-on-licensing"></a><span data-ttu-id="9245d-212">Observações sobre o licenciamento</span><span class="sxs-lookup"><span data-stu-id="9245d-212">Notes on licensing</span></span>

<span data-ttu-id="9245d-213">O PowerShell Core foi lançado sob a [licença MIT][].</span><span class="sxs-lookup"><span data-stu-id="9245d-213">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="9245d-214">Sob essa licença e na ausência de um contrato de suporte pago, os usuários estão limitados ao [suporte da comunidade][].</span><span class="sxs-lookup"><span data-stu-id="9245d-214">Under this license, and in the absence of a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="9245d-215">Com o suporte da comunidade, a Microsoft não faz nenhuma garantia de capacidade de resposta ou correções.</span><span class="sxs-lookup"><span data-stu-id="9245d-215">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="9245d-216">Módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9245d-216">Windows PowerShell Module</span></span>

<span data-ttu-id="9245d-217">O suporte para o PowerShell Core não se estende para outros módulos do produto, a menos que esses módulos deem suporte explicitamente ao PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="9245d-217">Support for PowerShell Core does not extend to other product modules unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="9245d-218">Por exemplo, usar o módulo `ActiveDirectory` fornecido como parte do Windows Server é um cenário sem suporte.</span><span class="sxs-lookup"><span data-stu-id="9245d-218">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="9245d-219">No entanto, os módulos que não dão suporte explicitamente ao PowerShell Core podem ser compatíveis em alguns casos.</span><span class="sxs-lookup"><span data-stu-id="9245d-219">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="9245d-220">Instalando o módulo [`WindowsPSModulePath`][], você pode acrescentar o Windows PowerShell `PSModulePath` ao PowerShell Core `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="9245d-220">By installing the [`WindowsPSModulePath`][] module, you can append the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="9245d-221">Primeiro, instale o módulo `WindowsPSModulePath` na Galeria do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9245d-221">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="9245d-222">Depois de instalar esse módulo, execute o cmdlet `Add-WindowsPSModulePath` para adicionar o Windows PowerShell `PSModulePath` ao PowerShell Core:</span><span class="sxs-lookup"><span data-stu-id="9245d-222">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[suporte da comunidade]: https://github.com/powershell/powershell/issues
[community support]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[Comunidade tecnológica do PowerShell]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[suporte assistido]: https://support.microsoft.com/assistedsupportproducts
[assisted support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[licença MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
