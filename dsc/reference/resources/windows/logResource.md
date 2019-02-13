---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso Log de DSC
ms.openlocfilehash: 1f94a2d847a4ef63f81e2fb83d1a0f76f5677b09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675580"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="d02c9-103">Recurso Log de DSC</span><span class="sxs-lookup"><span data-stu-id="d02c9-103">DSC Log Resource</span></span>

> <span data-ttu-id="d02c9-104">_Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="d02c9-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="d02c9-105">O recurso __Log__ na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para escrever mensagens no log de eventos Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="d02c9-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="d02c9-106">Por padrão, somente os logs operacionais da DSC são habilitados.</span><span class="sxs-lookup"><span data-stu-id="d02c9-106">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="d02c9-107">Antes que o log Analítico esteja disponível ou visível, ele deve ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="d02c9-107">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="d02c9-108">Para obter mais informações, veja [Onde estão os logs de eventos da DSC?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="d02c9-108">For more information, see [Where are DSC Event Logs?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="d02c9-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d02c9-109">Properties</span></span>

| <span data-ttu-id="d02c9-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="d02c9-110">Property</span></span> | <span data-ttu-id="d02c9-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="d02c9-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="d02c9-112">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d02c9-112">Message</span></span>| <span data-ttu-id="d02c9-113">Indica a mensagem que você deseja escreve no log de eventos Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="d02c9-113">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="d02c9-114">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d02c9-114">DependsOn</span></span> | <span data-ttu-id="d02c9-115">Indica que a configuração de outro recurso deve ser executada antes de a mensagem do log ser escrita.</span><span class="sxs-lookup"><span data-stu-id="d02c9-115">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="d02c9-116">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="d02c9-116">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="d02c9-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d02c9-117">Example</span></span>

<span data-ttu-id="d02c9-118">O exemplo a seguir mostra como incluir uma mensagem no log de eventos Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="d02c9-118">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="d02c9-119">Se você executar [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) com esse recurso configurado, ele sempre retornará **$false**.</span><span class="sxs-lookup"><span data-stu-id="d02c9-119">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```
