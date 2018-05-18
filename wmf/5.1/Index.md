---
ms.date: 08/12/2017
ms.topic: conceptual
keywords: wmf,powershell,instalação
title: Notas de versão do WMF 5.1
ms.openlocfilehash: 3512d2e80501a596e1fd6d7b33d4d75286cef1b9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="windows-management-framework-wmf-51"></a><span data-ttu-id="bdab7-103">Windows Management Framework (WMF) 5.1</span><span class="sxs-lookup"><span data-stu-id="bdab7-103">Windows Management Framework (WMF) 5.1</span></span> #

<span data-ttu-id="bdab7-104">O WMF fornece aos usuários a capacidade de atualizar os sistemas Windows existentes para as versões dos componentes PowerShell, WMI, WinRM e SIL (Log de Inventário de Software) que foram lançados com o Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="bdab7-104">WMF provides users with the ability to update existing Windows systems to the versions of PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>

<span data-ttu-id="bdab7-105">O WMF 5.1 pode ser instalado no Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 e 2012 R2 e fornece diversos aprimoramentos ao WMF 5.0 RTM, incluindo:</span><span class="sxs-lookup"><span data-stu-id="bdab7-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="bdab7-106">Novos cmdlets: usuários e grupos locais; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="bdab7-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="bdab7-107">Os aprimoramentos do PowerShellGet incluem a imposição de módulos assinados e a instalação de módulos JEA</span><span class="sxs-lookup"><span data-stu-id="bdab7-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="bdab7-108">Suporte acrescentado para o PackageManagement para Contêineres, Configuração de CBS, configuração baseada em EXE, pacotes CAB</span><span class="sxs-lookup"><span data-stu-id="bdab7-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="bdab7-109">Melhorias de depuração para classes DSC e PowerShell</span><span class="sxs-lookup"><span data-stu-id="bdab7-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="bdab7-110">Aprimoramentos de segurança, incluindo a imposição de módulos de catálogo assinado provenientes do Servidor de Recepção e ao usar cmdlets do PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="bdab7-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="bdab7-111">Respostas para diversos problemas e solicitações de usuários</span><span class="sxs-lookup"><span data-stu-id="bdab7-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="bdab7-112">Para saber mais sobre as novidades nesta versão, procure os tópicos listados em [Novos cenários e recursos](https://docs.microsoft.com/en-us/powershell/wmf/5.1/scenarios-features).</span><span class="sxs-lookup"><span data-stu-id="bdab7-112">To learn about what is new in this release, browse the topics listed under [New Scenarios and Features](https://docs.microsoft.com/en-us/powershell/wmf/5.1/scenarios-features).</span></span>

<span data-ttu-id="bdab7-113">O tópico [Instalar e configurar](https://docs.microsoft.com/en-us/powershell/wmf/5.1/install-configure) lista os requisitos e fornece instruções de instalação do WMF.</span><span class="sxs-lookup"><span data-stu-id="bdab7-113">The [Install and Configure](https://docs.microsoft.com/en-us/powershell/wmf/5.1/install-configure) topic lists the requirements and provides installation instructions for WMF.</span></span>

<span data-ttu-id="bdab7-114">O tópico [Compatibilidade](https://docs.microsoft.com/en-us/powershell/wmf/5.1/compatibility) lista quais versões do WMF podem ser instaladas em quais versões do Windows.</span><span class="sxs-lookup"><span data-stu-id="bdab7-114">The [Compatibility](https://docs.microsoft.com/en-us/powershell/wmf/5.1/compatibility) topic lists which versions of WMF may be installed on which Windows releases.</span></span>

<span data-ttu-id="bdab7-115">[Compatibilidade do produto](https://docs.microsoft.com/en-us/powershell/wmf/5.1/productincompat) lista os aplicativos da Microsoft que ainda não aprovaram o uso do WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="bdab7-115">[Product Compatibility](https://docs.microsoft.com/en-us/powershell/wmf/5.1/productincompat) lists the Microsoft applications that have not approved WMF 5.1 for use at this time.</span></span>

<span data-ttu-id="bdab7-116">Os detalhes dos componentes do WMF serão encontrados na documentação do MSDN:</span><span class="sxs-lookup"><span data-stu-id="bdab7-116">Details for the components of WMF will be found in MSDN documentation:</span></span>

- [<span data-ttu-id="bdab7-117">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="bdab7-117">PowerShell 5.1</span></span>](https://docs.microsoft.com/en-us/powershell/)
- <span data-ttu-id="bdab7-118">[WMI](https://msdn.microsoft.com/en-us/library/jj152383(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="bdab7-118">[WMI](https://msdn.microsoft.com/en-us/library/jj152383(v=vs.85).aspx)</span></span>
- <span data-ttu-id="bdab7-119">[WinRM](https://msdn.microsoft.com/en-us/library/aa384426(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="bdab7-119">[WinRM](https://msdn.microsoft.com/en-us/library/aa384426(v=vs.85).aspx)</span></span>
- <span data-ttu-id="bdab7-120">[Log de Inventário de Software](https://technet.microsoft.com/en-us/library/dn383584(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="bdab7-120">[Software Inventory Logging](https://technet.microsoft.com/en-us/library/dn383584(v=ws.11).aspx)</span></span>
