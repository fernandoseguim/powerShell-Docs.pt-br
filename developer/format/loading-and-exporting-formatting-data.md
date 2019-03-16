---
title: Carregar e exportar dados de formatação | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 5c5168ffd74c15066b914ad1b39d9ead947c5e7f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054179"
---
# <a name="loading-and-exporting-formatting-data"></a>Carregar e exportar dados de formatação

Depois de criar seu arquivo de formatação, você precisará atualizar os dados de formato da sessão ao carregar seus arquivos para a sessão atual. (Os arquivos de formatação fornecidos pelo Windows PowerShell são carregados pelo snap-ins que são registrados quando a sessão atual é aberta.) Depois que os dados de formato da sessão atual for atualizados, o Windows PowerShell usa esses dados para exibir os objetos .NET associados com os modos de exibição definidos nos arquivos de formatação carregados. Não há nenhum limite para o número de arquivos de formatação que pode ser carregado para a sessão atual. Além de atualizar os dados de formatação, você pode exportar os dados de formatação na sessão atual para um arquivo de formatação.

## <a name="loading-format-data"></a>Carregamento de dados de formato

Arquivos de formatação podem ser carregados para a sessão atual usando os seguintes métodos:

- Você pode importar o arquivo de formatação para a sessão atual da linha de comando. Use o [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet conforme descrito no procedimento a seguir.

- Você pode criar um manifesto de módulo que faz referência a seu arquivo de formatação. Módulos permitem que você empacote você formatá-los para distribuição. Use o [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) para criar o manifesto e o [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet para carregar o módulo para a sessão atual. Para obter mais informações sobre os módulos, consulte [escrevendo um módulo do Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- Você pode criar um snap-in que faz referência a seu arquivo de formatação. Use o [System.Management.Automation.PSSnapIn.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) para fazer referência a arquivos de formatação. É altamente recomendável usar módulos para cmdlets do pacote e qualquer formatação associados e arquivos de tipos para distribuição. Para obter mais informações sobre os módulos, consulte [escrevendo um módulo do Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- Se você estiver chamando comandos por meio de programação, você pode adicionar uma entrada de arquivo de formatação para o estado de sessão inicial do runspace no qual os comandos são executados. Para obter mais informações sobre o tipo do .NET usado para adicionar o arquivo de formatação, consulte o [System.Management.Automation.Runspaces.Sessionstateformatentry? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) classe.

Quando um arquivo de formatação é carregado, ele é adicionado a uma lista interna que o Windows PowerShell usa para determinar qual exibição a ser usado ao exibir os objetos na linha de comando. Você pode colocar seu arquivo de formatação para o início da lista ou acrescente-ao final da lista. É importante se você estiver carregando um arquivo de formatação que define uma exibição para um objeto que tem uma exibição existente definida, como quando você deseja alterar como um objeto que é retornado por um cmdlet do Windows PowerShell core é saber onde seu arquivo de formatação é adicionado a esta lista  exibido. Se você estiver carregando um arquivo de formatação que define o modo de exibição único para um objeto, você pode usar qualquer um dos métodos descritos anteriormente.  Se você estiver carregando um arquivo de formatação que define outra exibição de um objeto, você deve usar o [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet e preceder seu arquivo para o início da lista.

## <a name="storing-your-formatting-file"></a>Armazenar o arquivo de formatação

Não há nenhum requisito para onde os arquivos de formatação são armazenados no disco. No entanto, é altamente recomendável que você armazene-os na seguinte pasta: `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>Carregar um arquivo de formato usando Import-FormatData

1. Store seu arquivo de formatação para o disco.

2. Execute o [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet usando um dos comandos a seguir.

   Para adicionar sua formatação de arquivo para a frente da lista de usar esse comando. Use este comando se você estiver alterando como um objeto é exibido.

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   Para adicionar sua formatação arquivo até o final da lista de usar esse comando.

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   Depois de adicionar um arquivo usando o [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet, você não pode remover o arquivo da lista durante uma sessão aberta. Você deve fechar a sessão para remover o arquivo de formatação da lista.

## <a name="exporting-format-data"></a>Exportando dados de formato

Insira o corpo da seção aqui.
