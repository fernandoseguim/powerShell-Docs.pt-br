---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Recurso Log de DSC
ms.openlocfilehash: f1a528767508d4a0e7f0ea2e58fd27a6a4d7ec75
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-log-resource"></a><span data-ttu-id="fb0ef-103">Recurso Log de DSC</span><span class="sxs-lookup"><span data-stu-id="fb0ef-103">DSC Log Resource</span></span>

> <span data-ttu-id="fb0ef-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fb0ef-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="fb0ef-105">O recurso __Log__ na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para escrever mensagens no log de eventos Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="fb0ef-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

<span data-ttu-id="fb0ef-106">OBSERVAÇÃO: por padrão, somente os logs Operacionais da DSC são habilitados.</span><span class="sxs-lookup"><span data-stu-id="fb0ef-106">NOTE: By default only the Operational logs for DSC are enabled.</span></span>
<span data-ttu-id="fb0ef-107">Antes que o log Analítico esteja disponível ou visível, ele deve ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="fb0ef-107">Before the Analytic log will be available or visible, it must be enabled.</span></span>
<span data-ttu-id="fb0ef-108">Veja o artigo a seguir.</span><span class="sxs-lookup"><span data-stu-id="fb0ef-108">See the following article.</span></span>

[<span data-ttu-id="fb0ef-109">Onde estão os logs de eventos de DSC?</span><span class="sxs-lookup"><span data-stu-id="fb0ef-109">Where are DSC Event Logs?</span></span>](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a><span data-ttu-id="fb0ef-110">Propriedades</span><span class="sxs-lookup"><span data-stu-id="fb0ef-110">Properties</span></span>
|  <span data-ttu-id="fb0ef-111">Propriedade</span><span class="sxs-lookup"><span data-stu-id="fb0ef-111">Property</span></span>  |  <span data-ttu-id="fb0ef-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb0ef-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="fb0ef-113">Mensagem</span><span class="sxs-lookup"><span data-stu-id="fb0ef-113">Message</span></span>| <span data-ttu-id="fb0ef-114">Indica a mensagem que você deseja escreve no log de eventos Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="fb0ef-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="fb0ef-115">DependsOn</span><span class="sxs-lookup"><span data-stu-id="fb0ef-115">DependsOn</span></span> | <span data-ttu-id="fb0ef-116">Indica que a configuração de outro recurso deve ser executada antes de a mensagem do log ser escrita.</span><span class="sxs-lookup"><span data-stu-id="fb0ef-116">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="fb0ef-117">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="fb0ef-117">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="fb0ef-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fb0ef-118">Example</span></span>

<span data-ttu-id="fb0ef-119">O exemplo a seguir mostra como incluir uma mensagem no log de eventos Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="fb0ef-119">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> <span data-ttu-id="fb0ef-120">**Observação**: se você executar [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) com esse recurso configurado, ele sempre gerará **$false**.</span><span class="sxs-lookup"><span data-stu-id="fb0ef-120">**Note**: if you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost

    {
        Log LogExample
        {
            Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
        }
    }
}
```