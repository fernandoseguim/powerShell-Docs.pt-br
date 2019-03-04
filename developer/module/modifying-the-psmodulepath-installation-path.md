---
title: Modificando o caminho de instalação do PSModulePath | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855562"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Modificar o caminho de instalação PSModulePath

O `PSModulePath` variável de ambiente armazena os caminhos para os locais dos módulos que estão instalados no disco. Windows PowerShell usa essa variável para localizar os módulos quando o usuário não especifica o caminho completo para um módulo. Os caminhos nessa variável são pesquisados na ordem em que aparecem.

Quando o Windows PowerShell é iniciado, `PSModulePath` é criado como uma variável de ambiente do sistema com o valor padrão: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.

## <a name="to-view-the-psmodulepath-variable"></a>Para exibir a variável PSModulePath

Para exibir os caminhos que são especificados no `PSModulePath` variável, digite o seguinte comando:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Para adicionar locais para a variável PSModulePath

Para adicionar caminhos a essa variável, use um dos seguintes métodos:

- Para adicionar um valor temporário que está disponível somente para a sessão atual, execute o seguinte comando na linha de comando:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- Para adicionar um valor persistente que está disponível sempre que uma sessão é aberta, adicione o seguinte comando para um perfil do Windows PowerShell:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  Para obter mais informações sobre perfis, consulte [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) na biblioteca do Microsoft TechNet.

- Para adicionar uma variável persistente no registro, crie uma nova variável de ambiente de usuário chamada `PSModulePath` usando o Editor de variáveis de ambiente na **propriedades do sistema** caixa de diálogo.

- Para adicionar uma variável persistente usando um script, use o **SetEnvironmentVariable** método na classe de ambiente. Por exemplo, o script a seguir adiciona o "C:\Program Files\Fabrikam\Module caminho para o valor da variável de ambiente PSModulePath para o computador. Para adicionar o caminho à variável de ambiente PSModulePath usuário, defina o destino para "Usuário".

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>Para remover locais de PSModulePath

Você pode remover caminhos da variável usando métodos semelhantes: por exemplo, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` removerá o **c:\ModulePath** caminho da sessão atual.

## <a name="see-also"></a>Consulte Também

[Escrevendo um módulo do Windows PowerShell](./writing-a-windows-powershell-module.md)
