---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: ce5afc2f90f78433b64bf5b41946fc7506c43504
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219643"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a><span data-ttu-id="76282-102">Palavra-chave de Import-DscResource dá suporte ao parâmetro -ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="76282-102">Import-DscResource keyword supports -ModuleVersion parameter</span></span>

<span data-ttu-id="76282-103">Adicionamos um novo parâmetro à palavra-chave dinâmica `Import-DscResource`, disponível ao criar configurações DSC.</span><span class="sxs-lookup"><span data-stu-id="76282-103">We have added a new parameter to the `Import-DscResource` dynamic keyword available when authoring DSC configurations.</span></span> <span data-ttu-id="76282-104">Os autores da configuração agora podem especificar exatamente de qual versão do módulo os recursos DSC deverão ser carregados.</span><span class="sxs-lookup"><span data-stu-id="76282-104">Configuration authors can now specify exactly which module version to load the DSC resources from.</span></span> <span data-ttu-id="76282-105">A nova sintaxe da palavra-chave é:</span><span class="sxs-lookup"><span data-stu-id="76282-105">The new syntax of the keyword is:</span></span>

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* <span data-ttu-id="76282-106">**Nome**: nomes de um ou mais recursos a serem importados.</span><span class="sxs-lookup"><span data-stu-id="76282-106">**Name**: Names of one or more resources to import.</span></span>
* <span data-ttu-id="76282-107">**ModuleName**: nomes de módulo ou objetos ModuleSpecification de um ou mais módulos a ser importados.</span><span class="sxs-lookup"><span data-stu-id="76282-107">**ModuleName**: Module names or ModuleSpecification objects of one or more modules to import.</span></span>
* <span data-ttu-id="76282-108">**ModuleVersion**: versão de módulo a ser importada.</span><span class="sxs-lookup"><span data-stu-id="76282-108">**ModuleVersion**: Version of module ot import.</span></span> <span data-ttu-id="76282-109">Se for usado, ModuleName deverá representar apenas um módulo por nome.</span><span class="sxs-lookup"><span data-stu-id="76282-109">If used, ModuleName must represent only one module by name.</span></span>

<span data-ttu-id="76282-110">No ISE do Windows PowerShell, ele é exibido com o IntelliSense:</span><span class="sxs-lookup"><span data-stu-id="76282-110">In the Windows PowerShell ISE, it shows up with IntelliSense:</span></span>

![](../images/Import-DscResource-Modversion.jpg)

<span data-ttu-id="76282-111">**Observação**: o parâmetro `–ModuleVersion` só pode ser usado em combinação com o parâmetro `–ModuleName`.</span><span class="sxs-lookup"><span data-stu-id="76282-111">**Note**: the `–ModuleVersion` parameter can only be used in combination with the `–ModuleName` parameter.</span></span> <span data-ttu-id="76282-112">Ele não pode ser usado com nomes de recurso que usam apenas o parâmetro `–Name`.</span><span class="sxs-lookup"><span data-stu-id="76282-112">It cannot be used with resource names using only the `–Name` parameter.</span></span>

<span data-ttu-id="76282-113">Antes disso, a única maneira de especificar a versão do módulo ao carregar recursos DSC era usar o objeto de especificação do Módulo, por exemplo: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span><span class="sxs-lookup"><span data-stu-id="76282-113">Before this, the only way to specify the module version when loading DSC resources was by using the Module specification object e.g.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span></span>
