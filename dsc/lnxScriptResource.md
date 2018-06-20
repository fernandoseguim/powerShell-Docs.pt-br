---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso nxScript de DSC para Linux
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189322"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="a1499-103">Recurso nxScript de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="a1499-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="a1499-104">O recurso **nxScript** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para executar scripts do Linux em um nó do Linux.</span><span class="sxs-lookup"><span data-stu-id="a1499-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="a1499-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1499-105">Syntax</span></span>

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="a1499-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a1499-106">Properties</span></span>

|  <span data-ttu-id="a1499-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a1499-107">Property</span></span> |  <span data-ttu-id="a1499-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1499-108">Description</span></span> |
|---|---|
| <span data-ttu-id="a1499-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="a1499-109">GetScript</span></span>| <span data-ttu-id="a1499-110">Fornece um script que é executado quando você invoca o cmdlet [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx).</span><span class="sxs-lookup"><span data-stu-id="a1499-110">Provides a script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet.</span></span> <span data-ttu-id="a1499-111">O script precisa começar com um shebang, como #!/bin/bash.</span><span class="sxs-lookup"><span data-stu-id="a1499-111">The script must begin with a shebang, such as #!/bin/bash.</span></span>|
| <span data-ttu-id="a1499-112">SetScript</span><span class="sxs-lookup"><span data-stu-id="a1499-112">SetScript</span></span>| <span data-ttu-id="a1499-113">Fornece um script.</span><span class="sxs-lookup"><span data-stu-id="a1499-113">Provides a script.</span></span> <span data-ttu-id="a1499-114">Quando você invoca o cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), o **TestScript** é executado primeiro.</span><span class="sxs-lookup"><span data-stu-id="a1499-114">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** runs first.</span></span> <span data-ttu-id="a1499-115">Se o bloco **TestScript** gerar um código de saída diferente de 0, o bloco **SetScript** será executado.</span><span class="sxs-lookup"><span data-stu-id="a1499-115">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="a1499-116">Se o **TestScript** gerar um código de saída igual a 0, o **SetScript** não será executado.</span><span class="sxs-lookup"><span data-stu-id="a1499-116">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="a1499-117">O script precisa começar com um shebang, como `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="a1499-117">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>|
| <span data-ttu-id="a1499-118">TestScript</span><span class="sxs-lookup"><span data-stu-id="a1499-118">TestScript</span></span>| <span data-ttu-id="a1499-119">Fornece um script.</span><span class="sxs-lookup"><span data-stu-id="a1499-119">Provides a script.</span></span> <span data-ttu-id="a1499-120">Quando você invoca o cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), esse script é executado.</span><span class="sxs-lookup"><span data-stu-id="a1499-120">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this script runs.</span></span> <span data-ttu-id="a1499-121">Se gerar um código de saída diferente de 0, o SetScript será executado.</span><span class="sxs-lookup"><span data-stu-id="a1499-121">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="a1499-122">Se gerar um código de saída igual a 0, o **SetScript** não será executado.</span><span class="sxs-lookup"><span data-stu-id="a1499-122">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="a1499-123">O **TestScript** também é executado quando você invoca o cmdlet [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx).</span><span class="sxs-lookup"><span data-stu-id="a1499-123">The **TestScript** also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="a1499-124">No entanto, nesse caso, o **SetScript** não será executado, não importa qual código de saída é gerado pelo **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="a1499-124">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="a1499-125">O **TestScript** deverá gerar um código de saída igual a 0 se a configuração real corresponder à configuração atual de estado desejado e um código de saída diferente de 0 se não corresponder.</span><span class="sxs-lookup"><span data-stu-id="a1499-125">The **TestScript** must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="a1499-126">(A configuração atual de estado desejado é a última configuração aplicada no nó que está usando a DSC).</span><span class="sxs-lookup"><span data-stu-id="a1499-126">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="a1499-127">O script precisa começar com um shebang, como 1#!/bin/bash.1</span><span class="sxs-lookup"><span data-stu-id="a1499-127">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>|
| <span data-ttu-id="a1499-128">User</span><span class="sxs-lookup"><span data-stu-id="a1499-128">User</span></span>| <span data-ttu-id="a1499-129">O usuário com o qual o script será executado.</span><span class="sxs-lookup"><span data-stu-id="a1499-129">The user to run the script as.</span></span>|
| <span data-ttu-id="a1499-130">Grupo</span><span class="sxs-lookup"><span data-stu-id="a1499-130">Group</span></span>| <span data-ttu-id="a1499-131">O grupo com o qual o script será executado.</span><span class="sxs-lookup"><span data-stu-id="a1499-131">The group to run the script as.</span></span>|
| <span data-ttu-id="a1499-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a1499-132">DependsOn</span></span> | <span data-ttu-id="a1499-133">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="a1499-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a1499-134">Por exemplo, se a **ID** do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a1499-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="a1499-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a1499-135">Example</span></span>

<span data-ttu-id="a1499-136">O exemplo a seguir demonstra o uso do recurso **nxScript** para executar um gerenciamento de configuração adicional.</span><span class="sxs-lookup"><span data-stu-id="a1499-136">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxScript KeepDirEmpty{

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
}
}
```