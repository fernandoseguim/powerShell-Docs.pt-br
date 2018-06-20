---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso nxFileLine de DSC para Linux
ms.openlocfilehash: 6b927839c23478aa9916a5d23836b31fccc58484
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219626"
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="969eb-103">Recurso nxFileLine de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="969eb-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="969eb-104">O recurso **nxFileLine** na Configuração de Estado Desejado (DSC) do PowerShell fornece um mecanismo para gerenciar linhas dentro de um arquivo de configuração em um nó do Linux.</span><span class="sxs-lookup"><span data-stu-id="969eb-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="969eb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="969eb-105">Syntax</span></span>

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="969eb-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="969eb-106">Properties</span></span>

|  <span data-ttu-id="969eb-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="969eb-107">Property</span></span> |  <span data-ttu-id="969eb-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="969eb-108">Description</span></span> |
|---|---|
| <span data-ttu-id="969eb-109">FilePath</span><span class="sxs-lookup"><span data-stu-id="969eb-109">FilePath</span></span>| <span data-ttu-id="969eb-110">O caminho completo até o arquivo para gerenciar linhas no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="969eb-110">The full path to the file to manage lines in on the target node.</span></span>|
| <span data-ttu-id="969eb-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="969eb-111">ContainsLine</span></span>| <span data-ttu-id="969eb-112">Uma linha para garantir que exista no arquivo.</span><span class="sxs-lookup"><span data-stu-id="969eb-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="969eb-113">Essa linha será acrescentada ao arquivo caso não exista nele.</span><span class="sxs-lookup"><span data-stu-id="969eb-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="969eb-114">**ContainsLine** é obrigatório, mas poderá ser definido como uma cadeia de caracteres vazia (\`ContainsLine = ‘’\`\`) se não for necessário.</span><span class="sxs-lookup"><span data-stu-id="969eb-114">**ContainsLine** is mandatory, but can be set to an empty string (\`ContainsLine = ‘’\`\`) if it is not needed.</span></span>|
| <span data-ttu-id="969eb-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="969eb-115">DoesNotContainPattern</span></span>| <span data-ttu-id="969eb-116">Um padrão de expressão regular para linhas que não devem existir no arquivo.</span><span class="sxs-lookup"><span data-stu-id="969eb-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="969eb-117">Para todas as linhas existentes no arquivo que correspondem a essa expressão regular, a linha será removida do arquivo.</span><span class="sxs-lookup"><span data-stu-id="969eb-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span>|
| <span data-ttu-id="969eb-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="969eb-118">DependsOn</span></span> | <span data-ttu-id="969eb-119">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="969eb-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="969eb-120">Por exemplo, se a **ID** do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="969eb-120">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="969eb-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="969eb-121">Example</span></span>

<span data-ttu-id="969eb-122">Este exemplo demonstra como usar o recurso **nxFileLine** para configurar o arquivo `/etc/sudoers`, garantindo que o usuário: monuser esteja configurado como não requiretty.</span><span class="sxs-lookup"><span data-stu-id="969eb-122">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```
Import-DSCResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```