---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso Registry de DSC
ms.openlocfilehash: b77710d7a6fc599949e78c17af309ad88a1a0872
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093578"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="51f10-103">Recurso Registry de DSC</span><span class="sxs-lookup"><span data-stu-id="51f10-103">DSC Registry Resource</span></span>

> <span data-ttu-id="51f10-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="51f10-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="51f10-105">O recurso **Registry** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para gerenciar chaves e valores do registro em um nó de destino.</span><span class="sxs-lookup"><span data-stu-id="51f10-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="51f10-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51f10-106">Syntax</span></span>

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a><span data-ttu-id="51f10-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="51f10-107">Properties</span></span>

|  <span data-ttu-id="51f10-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="51f10-108">Property</span></span>  |  <span data-ttu-id="51f10-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="51f10-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="51f10-110">Chave</span><span class="sxs-lookup"><span data-stu-id="51f10-110">Key</span></span>| <span data-ttu-id="51f10-111">Indica o caminho da chave do Registro para o qual você deseja garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="51f10-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="51f10-112">Esse caminho deve incluir o hive.</span><span class="sxs-lookup"><span data-stu-id="51f10-112">This path must include the hive.</span></span>|
| <span data-ttu-id="51f10-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="51f10-113">ValueName</span></span>| <span data-ttu-id="51f10-114">Indica o nome do valor de registro.</span><span class="sxs-lookup"><span data-stu-id="51f10-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="51f10-115">Para adicionar ou remover uma chave do Registro, especifique essa propriedade como uma cadeia de caracteres vazia sem especificar ValueType ou ValueData.</span><span class="sxs-lookup"><span data-stu-id="51f10-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="51f10-116">Para modificar ou remover o valor padrão de uma chave do Registro, especifica essa propriedade como uma cadeia de caracteres vazia e também especifique ValueType ou ValueData.</span><span class="sxs-lookup"><span data-stu-id="51f10-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>|
| <span data-ttu-id="51f10-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="51f10-117">Ensure</span></span>| <span data-ttu-id="51f10-118">Indica se a chave e o valor existem.</span><span class="sxs-lookup"><span data-stu-id="51f10-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="51f10-119">Para garantir que existam, defina essa propriedade como "Present".</span><span class="sxs-lookup"><span data-stu-id="51f10-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="51f10-120">Para garantir que não existam, defina a propriedade como "Absent".</span><span class="sxs-lookup"><span data-stu-id="51f10-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="51f10-121">O valor padrão é "Present".</span><span class="sxs-lookup"><span data-stu-id="51f10-121">The default value is "Present".</span></span>|
| <span data-ttu-id="51f10-122">Force</span><span class="sxs-lookup"><span data-stu-id="51f10-122">Force</span></span>| <span data-ttu-id="51f10-123">Se a chave do Registro especificada estiver presente, **Force** a substituirá pelo novo valor.</span><span class="sxs-lookup"><span data-stu-id="51f10-123">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="51f10-124">Para excluir uma chave do Registro com subchaves, isso deve ser **$true**</span><span class="sxs-lookup"><span data-stu-id="51f10-124">If deleting a registry key with subkeys, this needs to be **$true**</span></span> |
| <span data-ttu-id="51f10-125">Hex</span><span class="sxs-lookup"><span data-stu-id="51f10-125">Hex</span></span>| <span data-ttu-id="51f10-126">Indica se os dados serão expressos em formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="51f10-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="51f10-127">Se especificado, os dados do valor DWORD/QWORD são apresentados em formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="51f10-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="51f10-128">Não é válido para outros tipos.</span><span class="sxs-lookup"><span data-stu-id="51f10-128">Not valid for other types.</span></span> <span data-ttu-id="51f10-129">O valor padrão é **$false**.</span><span class="sxs-lookup"><span data-stu-id="51f10-129">The default value is **$false**.</span></span>|
| <span data-ttu-id="51f10-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="51f10-130">DependsOn</span></span>| <span data-ttu-id="51f10-131">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="51f10-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="51f10-132">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="51f10-132">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="51f10-133">ValueData</span><span class="sxs-lookup"><span data-stu-id="51f10-133">ValueData</span></span>| <span data-ttu-id="51f10-134">Os dados para o valor de registro.</span><span class="sxs-lookup"><span data-stu-id="51f10-134">The data for the registry value.</span></span>|
| <span data-ttu-id="51f10-135">ValueType</span><span class="sxs-lookup"><span data-stu-id="51f10-135">ValueType</span></span>| <span data-ttu-id="51f10-136">Indica o tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="51f10-136">Indicates the type of the value.</span></span> <span data-ttu-id="51f10-137">Os tipos com suporte são: cadeia de caracteres (REG_SZ), binário (REG-BINARY), Dword de 32 bits (REG_DWORD), Qword de 64 bits (REG_QWORD), cadeia de caracteres múltipla (REG_MULTI_SZ), cadeia de caracteres expansível (REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="51f10-137">The supported types are: String (REG_SZ), Binary (REG-BINARY), Dword 32-bit (REG_DWORD), Qword 64-bit (REG_QWORD), Multi-string (REG_MULTI_SZ), Expandable string (REG_EXPAND_SZ)</span></span> |

## <a name="example"></a><span data-ttu-id="51f10-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="51f10-138">Example</span></span>

<span data-ttu-id="51f10-139">Este exemplo assegura que uma chave chamada "ExampleKey" está presente no hive **HKEY\_LOCAL\_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="51f10-139">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> <span data-ttu-id="51f10-140">Alterar uma configuração do registro no hive **HKEY\_CURRENT\_USER** requer que a configuração seja executada com credenciais de usuário, em vez de como o sistema.</span><span class="sxs-lookup"><span data-stu-id="51f10-140">Changing a registry setting in the **HKEY\_CURRENT\_USER** hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="51f10-141">Você pode usar a propriedade **PsDscRunAsCredential** para especificar credenciais de usuário para a configuração.</span><span class="sxs-lookup"><span data-stu-id="51f10-141">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="51f10-142">Por exemplo, veja [Executar DSC com as credenciais do usuário](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="51f10-142">For an example, see [Running DSC with user credentials](runAsUser.md).</span></span>