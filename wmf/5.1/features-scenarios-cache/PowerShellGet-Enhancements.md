---
title: "modelo de exemplo de um writeup de cenário ou recurso"
contributor: KeithB
translationtype: Human Translation
ms.sourcegitcommit: 8c55ca4b972c8d708a09b922f27eec585ddc33d0
ms.openlocfilehash: 025565404b60cebefac27e51c70d70edb5e47bc9

---

>Observação: dê um título descritivo proposto e uma breve descrição

## Aprimoramentos do PowerShellGet ##
Os cmdlets do módulo PowerShellGet foram atualizados consideravelmente no WMF 5.1. Agora, há suporte para os seguintes novos cenários:

- **Suporte para proxy:** agora, há suporte para usar os cmdlets do PowerShellGet com um proxy interno, com o acréscimo dos parâmetros Proxy e ProxyCredential a todos os cmdlets Find-, Install-, Save- e Publish- no módulo do PowerShellGet (por exemplo: Find-Module, Install-Module, Save-Module, Publish-Module). 
- **Imposição de assinatura de catálogo:** agora, todos os cmdlets do PowerShellGet verificam e impõem a atualização de módulos assinados. Módulos assinados usando os novos cmdlets de Catálogo serão verificados pelos cmdlets do PowerShellGet para garantir que o módulo não tenha sido modificado em trânsito e que as atualizações do módulo sejam provenientes apenas do editor original. Isso afeta os cmdlets Install-Module e Update-Module. 
- **Compartilhamento e aquisição de recursos de função:** recursos de função são as definições de ponto de extremidade usadas para configurar a "Administração Suficiente" para restringir e serão compartilhados por meio da Galeria do PowerShell em módulos do PowerShell. Os cmdlets incluem Find-RoleCapability e New-PSRoleCapabilityFile. 
- **Find-Command:** Find-Command permite que os usuários localizem um módulo na Galeria do PowerShell que contém um comando que estão procurando. 
- **Repositórios autenticados:** o feed do Gerenciador de Pacotes do Visual Studio requer autenticação, algo que agora tem suporte por meio dos cmdlets do PowerShellGet.

Comentários do usuário identificaram áreas adicionais para melhorias, que foram realizadas no 5.1, incluindo:

- **Alterações em Install-Script:** o local usado por Install-Script não é adicionado ao caminho de usuário automaticamente no 5.1. Essa alteração foi feita na versão autônoma do PowerShellGet e está agora no WMF 5.1.
- **Acréscimo de campos de metadados a scripts existentes:** Update-ScriptFileInfo pode ser usado em scripts existentes para adicionar os campos de metadados padrão necessários para publicar no PowerShellGallery. Anteriormente, os usuários precisavam mesclá-los manualmente em um script existente.
- **Publicação de um módulo com versão inferior na Galeria:** agora, é possível publicar um módulo com um número de versão menor do que a versão mais alta anterior na Galeria usando Publish-Module. Se um editor lançasse a versão 2.0.0 do seu módulo com alterações significativas com relação às versões 1.x, ele não poderia lançar facilmente uma correção da versão 1.5.0. Agora, ele pode publicar uma versão 1.5.1, o que melhora o suporte para a manutenção de módulos na Galeria do PowerShell. 
- **Verificação de substituição de comandos ao instalar módulos e scripts:** agora, Install-Module e Install-Script verificam se eles contêm comandos que já estão presentes no sistema e, por padrão, gerarão erros se isso acontecer. 
- **Inicialização de Nuget em cmdlets Publish-:** anteriormente, não era possível instalar automaticamente o provedor Nuget ao usar Publish-Module ou Publish-Script, o que dificultava muito algumas tarefas de automação. Agora, os usuários podem adicionar -Force a comandos Publish- para ignorar o aviso. 

>Observação: detalhes adicionais sobre os novos conceitos, implementação, exemplos, etc. devem ser vinculados à documentação técnica canônica

**Saiba mais sobre como usar o PowerShellGet**
- [About-CatalogSigning]()
- []()
- [Filtrar resultados de Get-Module por CompatiblePSEditions]()
- [Impedir a execução do script, a menos que execute em uma edição compatível do PowerShell]()






<!--HONumber=Aug16_HO3-->


