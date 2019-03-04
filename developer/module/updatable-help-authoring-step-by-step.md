---
title: 'Criação de ajuda atualizável: Passo a passo | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860312"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="ea7d1-102">Criação de ajuda atualizável: passo a passo</span><span class="sxs-lookup"><span data-stu-id="ea7d1-102">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="ea7d1-103">Este documenta lista as etapas no processo de criação de ajuda atualizável.</span><span class="sxs-lookup"><span data-stu-id="ea7d1-103">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="ea7d1-104">Criação de ajuda atualizável: passo a passo</span><span class="sxs-lookup"><span data-stu-id="ea7d1-104">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="ea7d1-105">Ajuda atualizável foi projetada para usuários finais, mas ele também oferece benefícios significativos para os autores de módulo e gravadores de Ajuda, incluindo a capacidade de adicionar conteúdo, corrigem os erros, entregar em várias culturas de interface do usuário e respondem aos comentários do usuário e solicitações, muito tempo após o módulo foi enviado.</span><span class="sxs-lookup"><span data-stu-id="ea7d1-105">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="ea7d1-106">Este tópico explica como você empacota e ajuda de carregamento de arquivos para que os usuários podem baixar e instalá-las usando o [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span><span class="sxs-lookup"><span data-stu-id="ea7d1-106">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="ea7d1-107">As etapas a seguir fornecem uma visão geral do processo de suporte à Ajuda atualizável.</span><span class="sxs-lookup"><span data-stu-id="ea7d1-107">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="ea7d1-108">Etapa 1: Encontrar um site da Internet para seus arquivos de ajuda</span><span class="sxs-lookup"><span data-stu-id="ea7d1-108">Step 1: Find an Internet site for your help files</span></span>

<span data-ttu-id="ea7d1-109">A primeira etapa na criação de ajuda atualizável é encontrar um local da Internet para os arquivos de Ajuda do seu módulo.</span><span class="sxs-lookup"><span data-stu-id="ea7d1-109">The first step in creating updatable help is to find an Internet location for your module's help files.</span></span> <span data-ttu-id="ea7d1-110">Na verdade, você pode usar dois locais diferentes.</span><span class="sxs-lookup"><span data-stu-id="ea7d1-110">Actually, you can use two different locations.</span></span> <span data-ttu-id="ea7d1-111">Você pode manter o arquivo de informações do seu módulo ajuda (HelpInfo XML - descritos abaixo) em um local de Internet e os arquivos CAB conteúdos de Ajuda em outro local de Internet.</span><span class="sxs-lookup"><span data-stu-id="ea7d1-111">You can keep your module's help information file (HelpInfo XML - described below) at one Internet location and the help content CAB files at another Internet location.</span></span> <span data-ttu-id="ea7d1-112">Todas as ajuda CAB arquivos de conteúdo para um módulo devem estar no mesmo local.</span><span class="sxs-lookup"><span data-stu-id="ea7d1-112">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="ea7d1-113">Você pode colocar os arquivos CAB de conteúdo da Ajuda para módulos diferentes no mesmo local.</span><span class="sxs-lookup"><span data-stu-id="ea7d1-113">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="ea7d1-114">Etapa 2: Adicionar uma chave de HelpInfoURI ao manifesto do módulo</span><span class="sxs-lookup"><span data-stu-id="ea7d1-114">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="ea7d1-115">Adicionar um **HelpInfoURI** chave ao manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="ea7d1-115">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="ea7d1-116">O valor da chave é o URI Uniform Resource Identifier () do local do arquivo XML HelpInfo informações para o seu módulo.</span><span class="sxs-lookup"><span data-stu-id="ea7d1-116">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="ea7d1-117">Para segurança, o endereço deve começar com "http" ou "https".</span><span class="sxs-lookup"><span data-stu-id="ea7d1-117">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="ea7d1-118">O URI deve especificar um local da Internet, mas não deve incluir o nome do arquivo XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="ea7d1-118">The URI should specify an Internet location, but must not include the HelpInfo XML file name.</span></span>

<span data-ttu-id="ea7d1-119">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ea7d1-119">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="ea7d1-120">Etapa 3: Crie um arquivo XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="ea7d1-120">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="ea7d1-121">O arquivo de informações XML HelpInfo contém o URI do local da Internet dos seus arquivos de Ajuda e os números de versão dos arquivos de ajuda mais recentes para o seu módulo em cada cultura de interface do usuário com suporte.</span><span class="sxs-lookup"><span data-stu-id="ea7d1-121">The HelpInfo XML information file contains the URI of the Internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="ea7d1-122">Cada módulo do Windows PowerShell tem um arquivo XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="ea7d1-122">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="ea7d1-123">Quando você atualiza seus arquivos de Ajuda, editar ou substituir o arquivo XML HelpInfo; Você não adicionar outro.</span><span class="sxs-lookup"><span data-stu-id="ea7d1-123">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="ea7d1-124">Para obter mais informações, consulte [como criar um arquivo de XML HelpInfo](./how-to-create-a-helpinfo-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="ea7d1-124">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-sign-your-help-files"></a><span data-ttu-id="ea7d1-125">Etapa 4: Assinar seus arquivos de ajuda</span><span class="sxs-lookup"><span data-stu-id="ea7d1-125">Step 4: Sign your help files</span></span>

<span data-ttu-id="ea7d1-126">Assinaturas digitais não são necessárias, mas eles são uma recomendação de melhores práticas, sempre que o compartilhamento de arquivos.</span><span class="sxs-lookup"><span data-stu-id="ea7d1-126">Digital signatures are not required, but they are a best-practice recommendation whenever you are sharing files.</span></span>

### <a name="step-5-create-cab-files"></a><span data-ttu-id="ea7d1-127">Etapa 5: Criar arquivos CAB</span><span class="sxs-lookup"><span data-stu-id="ea7d1-127">Step 5: Create CAB files</span></span>

<span data-ttu-id="ea7d1-128">Usar uma ferramenta que cria arquivos de gabinete (. cab), como MakeCab.exe, para criar um. Arquivo CAB que contém os arquivos de ajuda para o seu módulo.</span><span class="sxs-lookup"><span data-stu-id="ea7d1-128">Use a tool that creates cabinet (.cab) files, such as MakeCab.exe, to create a .CAB file that contains the help files for your module.</span></span> <span data-ttu-id="ea7d1-129">Crie um arquivo CAB separado para os arquivos de Ajuda em cada cultura de interface do usuário com suporte.</span><span class="sxs-lookup"><span data-stu-id="ea7d1-129">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="ea7d1-130">Para obter mais informações, consulte [como preparar atualizável ajuda arquivos CAB](./how-to-prepare-updatable-help-cab-files.md).</span><span class="sxs-lookup"><span data-stu-id="ea7d1-130">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-6-upload-your-files"></a><span data-ttu-id="ea7d1-131">Etapa 6: Carregar seus arquivos</span><span class="sxs-lookup"><span data-stu-id="ea7d1-131">Step 6: Upload your files</span></span>

<span data-ttu-id="ea7d1-132">Para publicar arquivos de ajuda novos ou atualizados, carregar os arquivos CAB para o local de Internet que é especificado pela **HelpContentUri** elemento no arquivo XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="ea7d1-132">To publish new or updated help files, upload the CAB files to the Internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="ea7d1-133">Em seguida, carregue o arquivo XML HelpInfo para o local de Internet que é especificado pelo valor da **HelpInfoUri** chave no manifesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="ea7d1-133">Then, upload the HelpInfo XML file to the Internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
