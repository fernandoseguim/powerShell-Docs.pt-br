---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Recurso nxSshAuthorizedKeys de DSC para Linux
ms.openlocfilehash: f48ecec39ffe24cee99ca08ad9d050b36c5e04bf
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="61303-103">Recurso nxSshAuthorizedKeys de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="61303-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="61303-104">O recurso **nxAuthorizedKeys** na Configuração de Estado Desejado (DSC) do PowerShell fornece um mecanismo para gerenciar chaves ssh autorizadas para um usuário especificado.</span><span class="sxs-lookup"><span data-stu-id="61303-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="61303-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61303-105">Syntax</span></span>

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="61303-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="61303-106">Properties</span></span>

|  <span data-ttu-id="61303-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="61303-107">Property</span></span> |  <span data-ttu-id="61303-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="61303-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="61303-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="61303-109">KeyComment</span></span>| <span data-ttu-id="61303-110">Um comentário exclusivo para a chave.</span><span class="sxs-lookup"><span data-stu-id="61303-110">A unique comment for the key.</span></span> <span data-ttu-id="61303-111">É usado para identificar as chaves com exclusividade.</span><span class="sxs-lookup"><span data-stu-id="61303-111">This is used to uniquely identify keys.</span></span>| 
| <span data-ttu-id="61303-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="61303-112">Ensure</span></span>| <span data-ttu-id="61303-113">Especifica se a chave foi definida.</span><span class="sxs-lookup"><span data-stu-id="61303-113">Specifies whether the key is defined.</span></span> <span data-ttu-id="61303-114">Defina essa propriedade como "Absent" para garantir que a chave não exista no arquivo de chaves autorizadas do usuário.</span><span class="sxs-lookup"><span data-stu-id="61303-114">Set this property to "Absent" to ensure the key does not exist in the user’s authorized keys file.</span></span> <span data-ttu-id="61303-115">Defina-a como "Present" para garantir que a chave seja definida no arquivo de chaves autorizadas do usuário.</span><span class="sxs-lookup"><span data-stu-id="61303-115">Set it to "Present" to ensure the key is defined in the user’s authorized key file.</span></span>| 
| <span data-ttu-id="61303-116">Nome de usuário</span><span class="sxs-lookup"><span data-stu-id="61303-116">Username</span></span>| <span data-ttu-id="61303-117">O nome de usuário para o qual as chaves ssh autorizadas serão gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="61303-117">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="61303-118">Se não for definido, o usuário padrão será "root".</span><span class="sxs-lookup"><span data-stu-id="61303-118">If not defined, the default user is "root".</span></span>| 
| <span data-ttu-id="61303-119">Chave</span><span class="sxs-lookup"><span data-stu-id="61303-119">Key</span></span>| <span data-ttu-id="61303-120">O conteúdo da chave.</span><span class="sxs-lookup"><span data-stu-id="61303-120">The contents of the key.</span></span> <span data-ttu-id="61303-121">Será obrigatório se **Ensure** for definido como "Present".</span><span class="sxs-lookup"><span data-stu-id="61303-121">This is required if **Ensure** is set to "Present".</span></span>| 
| <span data-ttu-id="61303-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="61303-122">DependsOn</span></span> | <span data-ttu-id="61303-123">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="61303-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="61303-124">Por exemplo, se a **ID** do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="61303-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="61303-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="61303-125">Example</span></span>

<span data-ttu-id="61303-126">O exemplo a seguir define uma chave ssh pública autorizada para o usuário "monuser".</span><span class="sxs-lookup"><span data-stu-id="61303-126">The following example defines a public ssh authorized key for the user "monuser".</span></span>

```
Import-DSCResource -Module nx 

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
} 
}
```

