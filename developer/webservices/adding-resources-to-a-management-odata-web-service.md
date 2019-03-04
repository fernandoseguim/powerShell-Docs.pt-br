---
title: Adicionar recursos a um serviço Web OData de gerenciamento | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e620bf6d-76be-47b0-a7a8-f43418f30c60
caps.latest.revision: 6
ms.openlocfilehash: b81a32b867795ae51c3f5308c2f82c31ed2747fa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858362"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a><span data-ttu-id="10e92-102">Adicionar recursos a um serviço Web OData de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="10e92-102">Adding Resources to a Management OData Web Service</span></span>

<span data-ttu-id="10e92-103">Este exemplo demonstra como adicionar um recurso a um serviço web de OData de gerenciamento existente usando o Designer de esquema de OData de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="10e92-103">This example demonstrates how to add a resource to an existing Management OData web service by using the Management OData Schema Designer.</span></span> <span data-ttu-id="10e92-104">O [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exemplo cria um serviço web que expõe os recursos de processo e servidor.</span><span class="sxs-lookup"><span data-stu-id="10e92-104">The [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample creates a web service that exposes the Process and Server resources.</span></span> <span data-ttu-id="10e92-105">Neste exemplo, você irá adicionar um recurso de máquina Virtual (VM) para o serviço web.</span><span class="sxs-lookup"><span data-stu-id="10e92-105">In this example, you will add a Virtual Machine (VM) resource to the web service.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="10e92-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="10e92-106">Prerequisites</span></span>

<span data-ttu-id="10e92-107">Este tópico pressupõe que você baixou e instalou o [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) de exemplo conforme descrito em [criando um serviço do Windows PowerShell Web](./creating-a-management-odata-web-service.md), e que você baixou e instalou o [Designer de esquema de OData de gerenciamento](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner).</span><span class="sxs-lookup"><span data-stu-id="10e92-107">This topic assumes that you have downloaded and installed the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample as described in [Creating a Windows PowerShell Web Service](./creating-a-management-odata-web-service.md), and that you have downloaded and installed the [Management OData Schema Designer](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner).</span></span> <span data-ttu-id="10e92-108">Este tópico também pressupõe que você tenha o módulo do PowerShell do Windows Hyper-V instalado no computador em que você configura o ponto de extremidade de Odata de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="10e92-108">This topic also assumes that you have the Hyper-V Windows PowerShell module installed on the computer where you set up the Management Odata endpoint.</span></span>

## <a name="adding-vm-as-a-resource-to-the-web-service"></a><span data-ttu-id="10e92-109">Adicionar a VM como um recurso para o serviço Web</span><span class="sxs-lookup"><span data-stu-id="10e92-109">Adding VM as a Resource to the Web Service</span></span>

<span data-ttu-id="10e92-110">A primeira etapa é importar o esquema de ponto de extremidade de OData de gerenciamento existente para o designer de esquema.</span><span class="sxs-lookup"><span data-stu-id="10e92-110">The first step is to import the schema from the existing Management OData endpoint into the schema designer.</span></span> <span data-ttu-id="10e92-111">O procedimento a seguir descreve como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="10e92-111">The following procedure describes how to do that.</span></span>

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a><span data-ttu-id="10e92-112">Importando um esquema existente para o designer de esquema</span><span class="sxs-lookup"><span data-stu-id="10e92-112">Importing an existing schema into the schema designer</span></span>

1. <span data-ttu-id="10e92-113">Abra o Designer de esquema de OData de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="10e92-113">Open the Management OData Schema Designer.</span></span>

2. <span data-ttu-id="10e92-114">Dos **arquivo** menu, selecione **arquivo** ; **Novo** ; **Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="10e92-114">From the **File** menu, select **File** ; **New** ; **File**.</span></span> <span data-ttu-id="10e92-115">O **novo arquivo** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="10e92-115">The **New File** dialog appears.</span></span>

3. <span data-ttu-id="10e92-116">Clique em **modelo de OData de gerenciamento**e, em seguida, clique em **abrir**.</span><span class="sxs-lookup"><span data-stu-id="10e92-116">Click **Management OData Model**, and then click **Open**.</span></span>

4. <span data-ttu-id="10e92-117">Clique com botão direito na janela principal e, em seguida, clique em **arquivo de esquema** ; **Importação**.</span><span class="sxs-lookup"><span data-stu-id="10e92-117">Right-click in the main window, and click **Schema file** ; **Import**.</span></span> <span data-ttu-id="10e92-118">O **abrir** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="10e92-118">The **Open** dialog appears.</span></span>

5. <span data-ttu-id="10e92-119">Navegue até a pasta em que você configurar o serviço web de OData de gerenciamento para o [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exemplo.</span><span class="sxs-lookup"><span data-stu-id="10e92-119">Navigate to the folder where you set up the Management OData web service for the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="10e92-120">Se você usou o script do Windows PowerShell fornecido com esse exemplo para configurar o ponto de extremidade sem modificar o script, essa pasta está **C:\inetpub\wwwroot\Modata**.</span><span class="sxs-lookup"><span data-stu-id="10e92-120">If you used the Windows PowerShell script provided with that sample to set up the endpoint without modifying the script, that folder is **C:\inetpub\wwwroot\Modata**.</span></span> <span data-ttu-id="10e92-121">Selecione o MOF e, em seguida, clique em **aberto**.</span><span class="sxs-lookup"><span data-stu-id="10e92-121">Select Schema.mof, and click **Open**.</span></span>

   <span data-ttu-id="10e92-122">Neste ponto, abra os arquivos MOF e Schema. XML em um editor de texto e observe que eles contêm mapeamentos para os recursos de processo e pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="10e92-122">At this point, open the Schema.mof and Schema.xml files in a text editor, and notice that they contain mappings for the Process and Service resources.</span></span> <span data-ttu-id="10e92-123">Usa o arquivo MOF [Distributed Management Task Force](https://www.dmtf.org/) standard (DTMF) MOF (Managed Object).</span><span class="sxs-lookup"><span data-stu-id="10e92-123">The Schema.mof file uses [Distributed Management  Task Force](https://www.dmtf.org/) (DTMF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="10e92-124">O arquivo Schema. XML usa um esquema XML que é descrito em [esquema de mapeamento de recursos](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="10e92-124">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

   <span data-ttu-id="10e92-125">O procedimento a seguir descreve como importar os cmdlets do Hyper-V para o modelo de esquema.</span><span class="sxs-lookup"><span data-stu-id="10e92-125">The following procedure describes how to import Hyper-V cmdlets in to the schema model.</span></span>

#### <a name="importing-cmdlets-into-the-schema"></a><span data-ttu-id="10e92-126">Importar os cmdlets para o esquema</span><span class="sxs-lookup"><span data-stu-id="10e92-126">Importing cmdlets into the schema</span></span>

1. <span data-ttu-id="10e92-127">Clique duas vezes em uma área em branco da janela do designer de esquema e, em seguida, clique em **importação Cmdlets**.</span><span class="sxs-lookup"><span data-stu-id="10e92-127">Right-click on a blank area of the schema designer window, and click **Import Cmdlets**.</span></span> <span data-ttu-id="10e92-128">O **Assistente de importação de Cmdlet** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="10e92-128">The **Cmdlet Import Wizard** dialog appears.</span></span>

2. <span data-ttu-id="10e92-129">Certifique-se **computador Local** está selecionado e, em seguida, clique em **próxima**.</span><span class="sxs-lookup"><span data-stu-id="10e92-129">Make sure **Local Computer** is selected, and click **Next**.</span></span>

3. <span data-ttu-id="10e92-130">Certifique-se de que os módulos do Windows PowerShell instalados está selecionado e selecione o Hyper-V na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="10e92-130">Make sure that Installed Windows PowerShell Modules is selected, and select Hyper-V from the drop-down list.</span></span> <span data-ttu-id="10e92-131">Clique em **próxima**.</span><span class="sxs-lookup"><span data-stu-id="10e92-131">click **Next**.</span></span> <span data-ttu-id="10e92-132">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="10e92-132">Click **Next**.</span></span>

4. <span data-ttu-id="10e92-133">No **substantivo do Cmdlet** lista, selecione **VM**.</span><span class="sxs-lookup"><span data-stu-id="10e92-133">In the **Cmdlet Noun** list, select **VM**.</span></span> <span data-ttu-id="10e92-134">Clique em **Avançar**</span><span class="sxs-lookup"><span data-stu-id="10e92-134">Click **Next**</span></span>

5. <span data-ttu-id="10e92-135">Neste exemplo, ligaremos somente os comandos Get e Delete com cmdlets.</span><span class="sxs-lookup"><span data-stu-id="10e92-135">For this example, we will bind only the Get and Delete commands with cmdlets.</span></span> <span data-ttu-id="10e92-136">Limpar o **CREATE** e **atualização** caixas de seleção e certifique-se o **obter** e **excluir** caixas de seleção estão marcadas.</span><span class="sxs-lookup"><span data-stu-id="10e92-136">Clear the **CREATE** and **UPDATE** checkboxes, and make sure the **GET** and **DELETE** checkboxes are checked.</span></span> <span data-ttu-id="10e92-137">Certifique-se de que o `Get-VM` cmdlet é selecionado para **Obtenha**e o `Remove-VM` cmdlet é selecionado para **excluir**.</span><span class="sxs-lookup"><span data-stu-id="10e92-137">Make sure that the `Get-VM` cmdlet is selected for **GET**, and the `Remove-VM` cmdlet is selected for **DELETE**.</span></span>

6. <span data-ttu-id="10e92-138">Como os metadados para os cmdlets VM não especificam um tipo de saída, você precisará executar o cmdlet para especificar o tipo de saída.</span><span class="sxs-lookup"><span data-stu-id="10e92-138">Because the metadata for the VM cmdlets does not specify an output type, you will need to run the cmdlet to specify the output type.</span></span> <span data-ttu-id="10e92-139">Selecione **tipo de saída forneça** e clique em **executar cmdlet**.</span><span class="sxs-lookup"><span data-stu-id="10e92-139">Select **Provide output type** and click **Run cmdlet**.</span></span> <span data-ttu-id="10e92-140">O **execute o Cmdlet** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="10e92-140">The **Run Cmdlet** dialog appears.</span></span> <span data-ttu-id="10e92-141">Clique em **executar**.</span><span class="sxs-lookup"><span data-stu-id="10e92-141">Click **Run**.</span></span> <span data-ttu-id="10e92-142">O **tipo de CLR** caixa é preenchida com o `VirtualMachine` tipo.</span><span class="sxs-lookup"><span data-stu-id="10e92-142">The **CLR Type** box is populated with the `VirtualMachine` type.</span></span> <span data-ttu-id="10e92-143">Clique em **Okey**, em seguida, clique em **próxima**.</span><span class="sxs-lookup"><span data-stu-id="10e92-143">Click **OK**, then click **Next**.</span></span>

7. <span data-ttu-id="10e92-144">Por padrão, todas as propriedades do objeto de máquina virtual são selecionadas.</span><span class="sxs-lookup"><span data-stu-id="10e92-144">By default, all of the properties of the VirtualMachine object are selected.</span></span> <span data-ttu-id="10e92-145">Você pode desmarcar quaisquer propriedades que você não deseja como parte dos dados retornados quando você solicitar esse recurso do serviço web.</span><span class="sxs-lookup"><span data-stu-id="10e92-145">You can clear any properties that you do not want as part of the data returned when you request this resource from the web service.</span></span> <span data-ttu-id="10e92-146">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="10e92-146">Click **Next**.</span></span>

8. <span data-ttu-id="10e92-147">Você deve selecionar pelo menos uma propriedade a ser usado como uma chave.</span><span class="sxs-lookup"><span data-stu-id="10e92-147">You must select at least one property to be used as a key.</span></span> <span data-ttu-id="10e92-148">Selecione **nome** na lista e clique **próxima**.</span><span class="sxs-lookup"><span data-stu-id="10e92-148">Select **Name** in the list, and click **Next**.</span></span>

9. <span data-ttu-id="10e92-149">A próxima janela permite que você mapeie propriedades do recurso OData de gerenciamento para as propriedades dos cmdlets subjacentes.</span><span class="sxs-lookup"><span data-stu-id="10e92-149">The next window allows you to map properties of the Management OData resource to properties of the underlying cmdlets.</span></span> <span data-ttu-id="10e92-150">O assistente mapeia as propriedades com nomes idênticos, por padrão.</span><span class="sxs-lookup"><span data-stu-id="10e92-150">The wizard maps properties with identical names by default.</span></span> <span data-ttu-id="10e92-151">Por exemplo, o `ComputerName` propriedade do recurso é mapeada para o `ComputerName` propriedade dos cmdlets.</span><span class="sxs-lookup"><span data-stu-id="10e92-151">For example, the `ComputerName` property of the resource is mapped to the `ComputerName` property of the cmdlets.</span></span>  <span data-ttu-id="10e92-152">Isso permite que você especifique o `ComputerName` propriedade em uma solicitação para o serviço web e tem o valor especificado a ser passado para o `Get-VM` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="10e92-152">This allows you to specify the `ComputerName` property in a request to the web service, and have the value you specify be passed to the `Get-VM` cmdlet.</span></span> <span data-ttu-id="10e92-153">`Id` e `Name` também são mapeados por padrão.</span><span class="sxs-lookup"><span data-stu-id="10e92-153">`Id` and `Name` are also mapped by default.</span></span>

   10. <span data-ttu-id="10e92-154">Clique em **próxima**, em seguida, clique em **concluir**.</span><span class="sxs-lookup"><span data-stu-id="10e92-154">Click **Next**, then click **Finish**.</span></span>

       <span data-ttu-id="10e92-155">O recurso de máquina virtual agora aparece na janela do designer de esquema.</span><span class="sxs-lookup"><span data-stu-id="10e92-155">The VM resource now appears in the schema designer window.</span></span> <span data-ttu-id="10e92-156">Você pode examinar as propriedades e operações associadas ao recurso.</span><span class="sxs-lookup"><span data-stu-id="10e92-156">You can examine the properties and operations associated with the resource.</span></span> <span data-ttu-id="10e92-157">Em seguida, você exportará os arquivos de esquema atualizado para o diretório virtual para o serviço web.</span><span class="sxs-lookup"><span data-stu-id="10e92-157">Next, you will export the updated schema files into the virtual directory for the web service.</span></span>

#### <a name="exporting-schema-files-from-the-schema-designer"></a><span data-ttu-id="10e92-158">Exportando arquivos de esquema do designer de esquema</span><span class="sxs-lookup"><span data-stu-id="10e92-158">Exporting schema files from the schema designer</span></span>

1. <span data-ttu-id="10e92-159">Clique duas vezes em uma área em branco da janela do designer de esquema e, em seguida, clique em **arquivo de esquema** ; **Exportar**.</span><span class="sxs-lookup"><span data-stu-id="10e92-159">Right-click on a blank area of the schema designer window, and click **Schema file** ; **Export**.</span></span> <span data-ttu-id="10e92-160">O **Salvar como** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="10e92-160">The **Save As** dialog appears.</span></span>

2. <span data-ttu-id="10e92-161">Navegar para o mesmo diretório de onde você importou o arquivo MOF.</span><span class="sxs-lookup"><span data-stu-id="10e92-161">Navigate to the same directory from where you imported the MOF file.</span></span> <span data-ttu-id="10e92-162">Nomeie o arquivo o mesmo que o arquivo MOF original (Schema por padrão) e, em seguida, clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="10e92-162">Name the file the same as the original MOF file (Schema.mof by default), and click **Save**.</span></span> <span data-ttu-id="10e92-163">Confirme que você deseja substituir o arquivo existente.</span><span class="sxs-lookup"><span data-stu-id="10e92-163">Confirm that you want to overwrite the existing file.</span></span>

   <span data-ttu-id="10e92-164">Embora ele não é explicitamente declarado na **Salvar como** caixa de diálogo, isso substitui os arquivos MOF tanto o Schema. XML.</span><span class="sxs-lookup"><span data-stu-id="10e92-164">Although it is not explicitly stated in the **Save As** dialog, this replaces both the Schema.mof and Schema.xml files.</span></span>

## <a name="next-steps"></a><span data-ttu-id="10e92-165">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="10e92-165">Next Steps</span></span>

<span data-ttu-id="10e92-166">Antes de acessar o novo recurso VM do serviço web OData de gerenciamento, você deve atualizar o arquivo RbacConfiguration.xml para permitir o acesso para o módulo PowerShell do Hyper-V Windows conforme descrito em [autorização baseada em função configurando](./configuring-role-based-authorization.md), e você também precisará reiniciar o serviço web.</span><span class="sxs-lookup"><span data-stu-id="10e92-166">Before you access the new VM resource from the Management OData web service, you must update the RbacConfiguration.xml file to allow access to the Hyper-V Windows PowerShell module as described in [Configuring Role-based Authorization](./configuring-role-based-authorization.md), and you will also need to restart the web service.</span></span>