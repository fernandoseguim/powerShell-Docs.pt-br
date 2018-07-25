---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso Log de DSC
ms.openlocfilehash: fade94efd8133ae0172737e4bb1aed89fc0f97d9
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093469"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="f8680-103">Recurso Log de DSC</span><span class="sxs-lookup"><span data-stu-id="f8680-103">DSC Log Resource</span></span>

> <span data-ttu-id="f8680-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f8680-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f8680-105">O recurso __Log__ na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para escrever mensagens no log de eventos Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="f8680-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="f8680-106">Por padrão, somente os logs operacionais da DSC são habilitados.</span><span class="sxs-lookup"><span data-stu-id="f8680-106">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="f8680-107">Antes que o log Analítico esteja disponível ou visível, ele deve ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="f8680-107">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="f8680-108">Para obter mais informações, veja [Onde estão os logs de eventos da DSC?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="f8680-108">For more information, see [Where are DSC Event Logs?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="f8680-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="f8680-109">Properties</span></span>

|  <span data-ttu-id="f8680-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f8680-110">Property</span></span>  |  <span data-ttu-id="f8680-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8680-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="f8680-112">Mensagem</span><span class="sxs-lookup"><span data-stu-id="f8680-112">Message</span></span>| <span data-ttu-id="f8680-113">Indica a mensagem que você deseja escreve no log de eventos Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="f8680-113">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="f8680-114">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f8680-114">DependsOn</span></span> | <span data-ttu-id="f8680-115">Indica que a configuração de outro recurso deve ser executada antes de a mensagem do log ser escrita.</span><span class="sxs-lookup"><span data-stu-id="f8680-115">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="f8680-116">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="f8680-116">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="f8680-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f8680-117">Example</span></span>

<span data-ttu-id="f8680-118">O exemplo a seguir mostra como incluir uma mensagem no log de eventos Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="f8680-118">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="f8680-119">Se você executar [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) com esse recurso configurado, ele sempre retornará **$false**.</span><span class="sxs-lookup"><span data-stu-id="f8680-119">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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