---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: b839b476bb4ef7f8d73b158d61f0e8cbc1265e60
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a>Palavra-chave de Import-DscResource dá suporte ao parâmetro -ModuleVersion

Adicionamos um novo parâmetro à palavra-chave dinâmica `Import-DscResource`, disponível ao criar configurações DSC. Os autores da configuração agora podem especificar exatamente de qual versão do módulo os recursos DSC deverão ser carregados. A nova sintaxe da palavra-chave é:

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* **Nome**: nomes de um ou mais recursos a serem importados.
* **ModuleName**: nomes de módulo ou objetos ModuleSpecification de um ou mais módulos a ser importados.
* **ModuleVersion**: versão de módulo a ser importada. Se for usado, ModuleName deverá representar apenas um módulo por nome. 

No ISE do Windows PowerShell, ele é exibido com o IntelliSense:

![](../images/Import-DscResource-Modversion.jpg)

**Observação**: o parâmetro `–ModuleVersion` só pode ser usado em combinação com o parâmetro `–ModuleName`. Ele não pode ser usado com nomes de recurso que usam apenas o parâmetro `–Name`.

Antes disso, a única maneira de especificar a versão do módulo ao carregar recursos DSC era usar o objeto de especificação do Módulo, por exemplo: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`

