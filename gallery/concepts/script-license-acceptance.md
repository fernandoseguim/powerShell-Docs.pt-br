---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Exigindo a aceitação da licença para scripts
ms.openlocfilehash: e7101eb6a480dd87965b7b9be9d49583042b603f
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002575"
---
# <a name="requiring-license-acceptance-for-scripts"></a>Exigindo a aceitação da licença para scripts

Não há suporte para a Aceitação de Licença para scripts. No entanto, há suporte para o cenário em que um script depende de um módulo que exige a aceitação da licença.

Os comandos de script (Install-Script/Save-Script/Update-Script) oferecem suporte a um novo parâmetro -AcceptLicense que se comporta como se o usuário tivesse visto a licença. Se -AcceptLicense não for especificado; o usuário verá o license.txt para o módulo dependente e receberá a solicitação para aceitar a licença.

## <a name="examples"></a>EXEMPLOS

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Exemplo 1: Instalar Script com dependências exigindo a aceitação da licença

O script 'ScriptRequireLicenseAcceptance' depende do módulo 'ModuleRequireLicenseAcceptance'. O usuário recebe a solicitação para aceitar licença.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance

License Acceptance
MIT License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Exemplo 2: Instalar o Script com dependências exigindo a aceitação da licença e -AcceptLicense

O script 'ScriptRequireLicenseAcceptance' depende do módulo 'ModuleRequireLicenseAcceptance'. O usuário não recebe a solicitação para aceitar a licença, pois - AcceptLicense é especificado.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>Mais detalhes

- [Suporte à exigência de aceitação da licença para Módulos](module-license-acceptance.md)
- [Suporte à exigência de aceitação da licença no PowerShellGallery](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [Exigir a aceitação da licença ao implantar na Automação do Azure](../how-to/working-with-packages/deploy-to-azure-automation.md)
