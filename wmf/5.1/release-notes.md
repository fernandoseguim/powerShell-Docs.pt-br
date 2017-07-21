---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
title: "Notas de versão do WMF 5.1"
ms.openlocfilehash: f80c1ec5886578e3e43f2c96981f40152db000d1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="windows-management-framework-wmf-51-release-notes"></a><span data-ttu-id="595f5-103">Notas de versão do Windows Management Framework (WMF) 5.1</span><span class="sxs-lookup"><span data-stu-id="595f5-103">Windows Management Framework (WMF) 5.1 Release Notes</span></span> #

<span data-ttu-id="595f5-104">O WMF 5.1 inclui os componentes do PowerShell, WMI, do WinRM e do SIL (Inventário de Software e Licenciamento), que foram lançados com o Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="595f5-104">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory and Licensing (SIL) components that were released with Windows Server 2016.</span></span>
<span data-ttu-id="595f5-105">O WMF 5.1 pode ser instalado no Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 e 2012 R2 e fornece diversos aprimoramentos ao WMF 5.0 RTM, incluindo:</span><span class="sxs-lookup"><span data-stu-id="595f5-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="595f5-106">Novos cmdlets: usuários e grupos locais; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="595f5-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="595f5-107">Os aprimoramentos do PowerShellGet incluem a imposição de módulos assinados e a instalação de módulos JEA</span><span class="sxs-lookup"><span data-stu-id="595f5-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="595f5-108">Suporte acrescentado para o PackageManagement para Contêineres, Configuração de CBS, configuração baseada em EXE, pacotes CAB</span><span class="sxs-lookup"><span data-stu-id="595f5-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="595f5-109">Melhorias de depuração para classes DSC e PowerShell</span><span class="sxs-lookup"><span data-stu-id="595f5-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="595f5-110">Aprimoramentos de segurança, incluindo a imposição de módulos de catálogo assinado provenientes do Servidor de Recepção e ao usar cmdlets do PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="595f5-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="595f5-111">Respostas para diversos problemas e solicitações de usuários</span><span class="sxs-lookup"><span data-stu-id="595f5-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="595f5-112">**Observações importantes:**</span><span class="sxs-lookup"><span data-stu-id="595f5-112">**Important notes:**</span></span>

- <span data-ttu-id="595f5-113">**O WMF 5.1 exige o .NET Framework 4.5.2**.</span><span class="sxs-lookup"><span data-stu-id="595f5-113">**WMF 5.1 requires the .NET Framework 4.5.2**.</span></span> <span data-ttu-id="595f5-114">A instalação terá êxito, mas ocorrerá falha nos principais recursos se o .NET 4.5.2 não estiver instalado.</span><span class="sxs-lookup"><span data-stu-id="595f5-114">Installation will succeed, but key features will fail if .NET 4.5.2 is not installed.</span></span> <span data-ttu-id="595f5-115">As instruções estão disponíveis no tópico [Instalar e Configurar WMF 5.1](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure).</span><span class="sxs-lookup"><span data-stu-id="595f5-115">Instructions are available in the [Install and Configure WMF 5.1 ](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure) topic.</span></span>
- <span data-ttu-id="595f5-116">A visualização do WMF 5.1 deve ser desinstalada antes de instalar a versão RTM do WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="595f5-116">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="595f5-117">O WMF 5.1 pode ser instalado diretamente sobre o WMF 5.0 ou o WMF 4.0.</span><span class="sxs-lookup"><span data-stu-id="595f5-117">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="595f5-118">Não é __necessário__ instalar o WMF 4.0 antes de instalar o WMF 5.1 no Windows 7 e no Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="595f5-118">It is __not required__ to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="595f5-119">Este era um problema na versão de visualização do WMF 5.1 e ele foi resolvido.</span><span class="sxs-lookup"><span data-stu-id="595f5-119">That was an issue for the WMF 5.1 Preview release, and has been resolved.</span></span>  


