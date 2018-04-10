---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Recurso nxFileLine de DSC para Linux
ms.openlocfilehash: 798bfa4150996622c33c77d6a5aa3be4af342f1b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="0a365-103">Recurso nxFileLine de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="0a365-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="0a365-104">O recurso **nxFileLine** na Configuração de Estado Desejado (DSC) do PowerShell fornece um mecanismo para gerenciar linhas dentro de um arquivo de configuração em um nó do Linux.</span><span class="sxs-lookup"><span data-stu-id="0a365-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="0a365-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0a365-105">Syntax</span></span>

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="0a365-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="0a365-106">Properties</span></span>

|  <span data-ttu-id="0a365-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="0a365-107">Property</span></span> |  <span data-ttu-id="0a365-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a365-108">Description</span></span> |
|---|---|
| <span data-ttu-id="0a365-109">FilePath</span><span class="sxs-lookup"><span data-stu-id="0a365-109">FilePath</span></span>| <span data-ttu-id="0a365-110">O caminho completo até o arquivo para gerenciar linhas no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="0a365-110">The full path to the file to manage lines in on the target node.</span></span>|
| <span data-ttu-id="0a365-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="0a365-111">ContainsLine</span></span>| <span data-ttu-id="0a365-112">Uma linha para garantir que exista no arquivo.</span><span class="sxs-lookup"><span data-stu-id="0a365-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="0a365-113">Essa linha será acrescentada ao arquivo caso não exista nele.</span><span class="sxs-lookup"><span data-stu-id="0a365-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="0a365-114">**ContainsLine** é obrigatório, mas poderá ser definido como uma cadeia de caracteres vazia (\`ContainsLine = ‘’\`\`) se não for necessário.</span><span class="sxs-lookup"><span data-stu-id="0a365-114">**ContainsLine** is mandatory, but can be set to an empty string (\`ContainsLine = ‘’\`\`) if it is not needed.</span></span>|
| <span data-ttu-id="0a365-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="0a365-115">DoesNotContainPattern</span></span>| <span data-ttu-id="0a365-116">Um padrão de expressão regular para linhas que não devem existir no arquivo.</span><span class="sxs-lookup"><span data-stu-id="0a365-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="0a365-117">Para todas as linhas existentes no arquivo que correspondem a essa expressão regular, a linha será removida do arquivo.</span><span class="sxs-lookup"><span data-stu-id="0a365-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span>|
| <span data-ttu-id="0a365-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0a365-118">DependsOn</span></span> | <span data-ttu-id="0a365-119">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="0a365-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0a365-120">Por exemplo, se a **ID** do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0a365-120">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="0a365-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0a365-121">Example</span></span>

<span data-ttu-id="0a365-122">Este exemplo demonstra como usar o recurso **nxFileLine** para configurar o arquivo `/etc/sudoers`, garantindo que o usuário: monuser esteja configurado como não requiretty.</span><span class="sxs-lookup"><span data-stu-id="0a365-122">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```
Import-DSCResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```