---
title: "FullyQuilifiedModuleName para o “uso de módulo”"
author: jaimeo
contributor: vors
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: e09cfe0994ac523fd10658955731a93b6c176c88

---

FullyQuilifiedModuleName para o “uso de módulo”
=========================

Agora `using module` comporta-se da mesma maneira que outras construções relacionadas ao módulo no PowerShell.

Problemas do WMF 5.0
----------

* Usuário não tem uma maneira de especificar a versão do módulo em `using module`.
* Se houver várias versões do módulo disponíveis no sistema, o usuário receberá um erro.

WMF 5.1
----------

* O usuário pode usar `ModuleSpecification` [tabela de hash](https://msdn.microsoft.com/en-us/library/jj136290(v=vs.85).aspx). Essa tabela de hash tem o mesmo formato que `Get-Module -FullyQualifiedName`

**Exemplo:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* Se houver várias versões do módulo, o PowerShell usará a **mesma lógica de resolução** que `Import-Module` e não sofrerá erro.

* Isso torna o `using module` alinhado a `Import-Module` e a `Import-DscResource`.



<!--HONumber=Jul16_HO3-->


