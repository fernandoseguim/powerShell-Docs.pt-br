---
title: Suporte à Ajuda Online | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857912"
---
# <a name="supporting-online-help"></a><span data-ttu-id="8f4c2-102">Suporte à ajuda online</span><span class="sxs-lookup"><span data-stu-id="8f4c2-102">Supporting Online Help</span></span>

<span data-ttu-id="8f4c2-103">Começando no Windows PowerShell 3.0, há duas maneiras para dar suporte a `Get-Help` recurso Online para comandos do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="8f4c2-104">Este tópico explica como implementar esse recurso para tipos diferentes de comando.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="8f4c2-105">Sobre a Ajuda Online</span><span class="sxs-lookup"><span data-stu-id="8f4c2-105">About Online Help</span></span>

<span data-ttu-id="8f4c2-106">A Ajuda online sempre foi uma parte essencial do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="8f4c2-107">Embora o `Get-Help` cmdlet exibirá tópicos da Ajuda no prompt de comando, muitos usuários preferem a experiência de leitura online, incluindo codificação por cores, hiperlinks e compartilhamento de ideias no conteúdo da comunidade e documentos com base em wiki.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="8f4c2-108">Mais importante é que, antes do advento do ajuda atualizável, a Ajuda online fornecida a versão mais atualizada dos arquivos de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="8f4c2-109">Com o advento da Ajuda atualizável no Windows PowerShell 3.0, a Ajuda online ainda desempenha um papel vital.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="8f4c2-110">Além da experiência de usuário flexível, a Ajuda online fornece ajuda para os usuários que não têm ou não é possível usar a Ajuda atualizável para baixar os tópicos da Ajuda.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="8f4c2-111">Como Get-Help-Online funciona</span><span class="sxs-lookup"><span data-stu-id="8f4c2-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="8f4c2-112">Para ajudar os usuários a localizar os tópicos da Ajuda online para comandos, o `Get-Help` command tem um parâmetro Online que abre a versão online do tópico da Ajuda para um comando no navegador de Internet padrão do usuário.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="8f4c2-113">Por exemplo, o comando a seguir abre o tópico de Ajuda online para o `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="8f4c2-114">Para implementar `Get-Help` -on-line, o `Get-Help` cmdlet procura para um identificador de URI (Uniform Resource) para o tópico da Ajuda on-line de versão nos seguintes locais.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="8f4c2-115">O primeiro link na seção Links relacionados do tópico da Ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="8f4c2-116">O tópico da Ajuda deve ser instalado no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="8f4c2-117">Esse recurso foi introduzido no Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="8f4c2-118">A propriedade HelpUri de qualquer comando.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-118">The HelpUri property of any command.</span></span> <span data-ttu-id="8f4c2-119">A propriedade HelpUri é acessível, mesmo quando o tópico da Ajuda para o comando não está instalado no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="8f4c2-120">Esse recurso foi introduzido no Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="8f4c2-121">`Get-Help` procura por um URI na primeira entrada na seção Links relacionados antes de obter o valor da propriedade HelpUri.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="8f4c2-122">Se o valor da propriedade estiver incorreto ou foi alterada, você pode substituí-la, inserindo um valor diferente no primeiro Link relacionado.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="8f4c2-123">No entanto, o primeiro Link relacionado funciona apenas quando os tópicos de ajuda são instalados no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="8f4c2-124">Adicionando um URI para o primeiro link relacionado de um tópico de ajuda de comando</span><span class="sxs-lookup"><span data-stu-id="8f4c2-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="8f4c2-125">Você pode dar suporte a `Get-Help` -on-line para qualquer comando, adicionando um URI válido para a primeira entrada na seção Links relacionados do tópico da Ajuda baseada em XML para o comando.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="8f4c2-126">Essa opção só é válida em tópicos de ajuda baseados em XML e funciona somente quando o tópico da Ajuda está instalado no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="8f4c2-127">Quando o tópico da Ajuda está instalado e o URI é preenchido, esse valor tem precedência sobre o **HelpUri** propriedade do comando.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span> <span data-ttu-id="8f4c2-128">Para obter informações sobre tópicos de ajuda baseados em XML para os comandos, consulte [Writing XML-Based tópicos da Ajuda para comandos](../help/writing-xml-based-help-topics-for-commands.md).</span><span class="sxs-lookup"><span data-stu-id="8f4c2-128">For information about XML-based help topics for commands, see [Writing XML-Based Help Topics for Commands](../help/writing-xml-based-help-topics-for-commands.md).</span></span>

<span data-ttu-id="8f4c2-129">Para dar suporte a esse recurso, o URI deve aparecer na `maml:uri` elemento sob o primeiro `maml:relatedLinks/maml:navigationLink` elemento o `maml:relatedLinks` elemento.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-129">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="8f4c2-130">O XML a seguir mostra a colocação correta do URI.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-130">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="8f4c2-131">A "versão Online:" texto no `maml:linkText` elemento é uma prática recomendada, mas não é necessária.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-131">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="8f4c2-132">Adição da propriedade HelpUri para um comando</span><span class="sxs-lookup"><span data-stu-id="8f4c2-132">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="8f4c2-133">Esta seção mostra como adicionar a propriedade HelpUri para comandos de tipos diferentes.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-133">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="8f4c2-134">Adicionando uma propriedade HelpUri para um Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8f4c2-134">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="8f4c2-135">Para cmdlets escritos em C#, adicione uma **HelpUri** atributo à classe do Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-135">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="8f4c2-136">O valor do atributo deve ser um URI que começa com "http" ou "https".</span><span class="sxs-lookup"><span data-stu-id="8f4c2-136">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="8f4c2-137">O código a seguir mostra o atributo HelpUri o `Get-History` classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-137">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="8f4c2-138">Adicionando uma propriedade HelpUri para uma função avançada</span><span class="sxs-lookup"><span data-stu-id="8f4c2-138">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="8f4c2-139">Para funções avançadas, adicione uma **HelpUri** propriedade para o **CmdletBinding** atributo.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-139">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="8f4c2-140">O valor da propriedade deve ser um URI que começa com "http" ou "https".</span><span class="sxs-lookup"><span data-stu-id="8f4c2-140">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="8f4c2-141">O código a seguir mostra o atributo HelpUri da função New-calendário</span><span class="sxs-lookup"><span data-stu-id="8f4c2-141">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="8f4c2-142">Adicionando um atributo HelpUri para um comando CIM</span><span class="sxs-lookup"><span data-stu-id="8f4c2-142">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="8f4c2-143">Para comandos CIM, adicione uma **HelpUri** atributo para o **CmdletMetadata** elemento no arquivo CDXML.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-143">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="8f4c2-144">O valor do atributo deve ser um URI que começa com "http" ou "https".</span><span class="sxs-lookup"><span data-stu-id="8f4c2-144">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="8f4c2-145">O código a seguir mostra o atributo HelpUri do comando Start-Debug CIM</span><span class="sxs-lookup"><span data-stu-id="8f4c2-145">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="8f4c2-146">Adicionando um atributo HelpUri para um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8f4c2-146">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="8f4c2-147">Para fluxos de trabalho que são escritos na linguagem do Windows PowerShell, adicione um **. ExternalHelp** diretiva de comentário para o código de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-147">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="8f4c2-148">O valor da diretiva deve ser um URI que começa com "http" ou "https".</span><span class="sxs-lookup"><span data-stu-id="8f4c2-148">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="8f4c2-149">Não há suporte para a propriedade HelpUri para fluxos de trabalho baseados em XAML no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-149">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="8f4c2-150">O seguinte código mostra o. Diretiva ExternalHelp em um arquivo de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8f4c2-150">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```