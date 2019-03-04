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
# <a name="adding-resources-to-a-management-odata-web-service"></a>Adicionar recursos a um serviço Web OData de gerenciamento

Este exemplo demonstra como adicionar um recurso a um serviço web de OData de gerenciamento existente usando o Designer de esquema de OData de gerenciamento. O [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exemplo cria um serviço web que expõe os recursos de processo e servidor. Neste exemplo, você irá adicionar um recurso de máquina Virtual (VM) para o serviço web.

## <a name="prerequisites"></a>Pré-requisitos

Este tópico pressupõe que você baixou e instalou o [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) de exemplo conforme descrito em [criando um serviço do Windows PowerShell Web](./creating-a-management-odata-web-service.md), e que você baixou e instalou o [Designer de esquema de OData de gerenciamento](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner). Este tópico também pressupõe que você tenha o módulo do PowerShell do Windows Hyper-V instalado no computador em que você configura o ponto de extremidade de Odata de gerenciamento.

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>Adicionar a VM como um recurso para o serviço Web

A primeira etapa é importar o esquema de ponto de extremidade de OData de gerenciamento existente para o designer de esquema. O procedimento a seguir descreve como fazer isso.

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>Importando um esquema existente para o designer de esquema

1. Abra o Designer de esquema de OData de gerenciamento.

2. Dos **arquivo** menu, selecione **arquivo** ; **Novo** ; **Arquivo**. O **novo arquivo** caixa de diálogo é exibida.

3. Clique em **modelo de OData de gerenciamento**e, em seguida, clique em **abrir**.

4. Clique com botão direito na janela principal e, em seguida, clique em **arquivo de esquema** ; **Importação**. O **abrir** caixa de diálogo é exibida.

5. Navegue até a pasta em que você configurar o serviço web de OData de gerenciamento para o [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exemplo. Se você usou o script do Windows PowerShell fornecido com esse exemplo para configurar o ponto de extremidade sem modificar o script, essa pasta está **C:\inetpub\wwwroot\Modata**. Selecione o MOF e, em seguida, clique em **aberto**.

   Neste ponto, abra os arquivos MOF e Schema. XML em um editor de texto e observe que eles contêm mapeamentos para os recursos de processo e pelo serviço. Usa o arquivo MOF [Distributed Management Task Force](https://www.dmtf.org/) standard (DTMF) MOF (Managed Object). O arquivo Schema. XML usa um esquema XML que é descrito em [esquema de mapeamento de recursos](./resource-mapping-schema.md).

   O procedimento a seguir descreve como importar os cmdlets do Hyper-V para o modelo de esquema.

#### <a name="importing-cmdlets-into-the-schema"></a>Importar os cmdlets para o esquema

1. Clique duas vezes em uma área em branco da janela do designer de esquema e, em seguida, clique em **importação Cmdlets**. O **Assistente de importação de Cmdlet** caixa de diálogo é exibida.

2. Certifique-se **computador Local** está selecionado e, em seguida, clique em **próxima**.

3. Certifique-se de que os módulos do Windows PowerShell instalados está selecionado e selecione o Hyper-V na lista suspensa. Clique em **próxima**. Clique em **Avançar**.

4. No **substantivo do Cmdlet** lista, selecione **VM**. Clique em **Avançar**

5. Neste exemplo, ligaremos somente os comandos Get e Delete com cmdlets. Limpar o **CREATE** e **atualização** caixas de seleção e certifique-se o **obter** e **excluir** caixas de seleção estão marcadas. Certifique-se de que o `Get-VM` cmdlet é selecionado para **Obtenha**e o `Remove-VM` cmdlet é selecionado para **excluir**.

6. Como os metadados para os cmdlets VM não especificam um tipo de saída, você precisará executar o cmdlet para especificar o tipo de saída. Selecione **tipo de saída forneça** e clique em **executar cmdlet**. O **execute o Cmdlet** caixa de diálogo é exibida. Clique em **executar**. O **tipo de CLR** caixa é preenchida com o `VirtualMachine` tipo. Clique em **Okey**, em seguida, clique em **próxima**.

7. Por padrão, todas as propriedades do objeto de máquina virtual são selecionadas. Você pode desmarcar quaisquer propriedades que você não deseja como parte dos dados retornados quando você solicitar esse recurso do serviço web. Clique em **Avançar**.

8. Você deve selecionar pelo menos uma propriedade a ser usado como uma chave. Selecione **nome** na lista e clique **próxima**.

9. A próxima janela permite que você mapeie propriedades do recurso OData de gerenciamento para as propriedades dos cmdlets subjacentes. O assistente mapeia as propriedades com nomes idênticos, por padrão. Por exemplo, o `ComputerName` propriedade do recurso é mapeada para o `ComputerName` propriedade dos cmdlets.  Isso permite que você especifique o `ComputerName` propriedade em uma solicitação para o serviço web e tem o valor especificado a ser passado para o `Get-VM` cmdlet. `Id` e `Name` também são mapeados por padrão.

   10. Clique em **próxima**, em seguida, clique em **concluir**.

       O recurso de máquina virtual agora aparece na janela do designer de esquema. Você pode examinar as propriedades e operações associadas ao recurso. Em seguida, você exportará os arquivos de esquema atualizado para o diretório virtual para o serviço web.

#### <a name="exporting-schema-files-from-the-schema-designer"></a>Exportando arquivos de esquema do designer de esquema

1. Clique duas vezes em uma área em branco da janela do designer de esquema e, em seguida, clique em **arquivo de esquema** ; **Exportar**. O **Salvar como** caixa de diálogo é exibida.

2. Navegar para o mesmo diretório de onde você importou o arquivo MOF. Nomeie o arquivo o mesmo que o arquivo MOF original (Schema por padrão) e, em seguida, clique em **salvar**. Confirme que você deseja substituir o arquivo existente.

   Embora ele não é explicitamente declarado na **Salvar como** caixa de diálogo, isso substitui os arquivos MOF tanto o Schema. XML.

## <a name="next-steps"></a>Próximas etapas

Antes de acessar o novo recurso VM do serviço web OData de gerenciamento, você deve atualizar o arquivo RbacConfiguration.xml para permitir o acesso para o módulo PowerShell do Hyper-V Windows conforme descrito em [autorização baseada em função configurando](./configuring-role-based-authorization.md), e você também precisará reiniciar o serviço web.