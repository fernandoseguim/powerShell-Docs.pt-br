---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Criando e publicando um item
ms.openlocfilehash: c5027c5fb357bb187611880ba75610a8f33074e0
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522944"
---
# <a name="creating-and-publishing-an-item"></a>Criando e publicando um item

A Galeria do PowerShell é o local para publicar e compartilhar recursos de DSC, scripts e módulos do PowerShell estáveis com a comunidade mais ampla de usuários do PowerShell.

Este artigo aborda a mecânica e etapas importantes para preparar um script ou um módulo e publicá-lo na Galeria do PowerShell.
Recomendamos que você examine as [Diretrizes de publicação](https://msdn.microsoft.com/powershell/gallery/psgallery/psgallery-PublishingGuidelines) para entender como garantir que os itens publicados sejam mais aceitos pelos usuários da Galeria do PowerShell.

Os requisitos mínimos para publicar um item na Galeria do PowerShell são:

- Ter uma conta da Galeria do PowerShell e a chave de API associada
- Garantir que os metadados necessários estejam no item
- Usar as ferramentas de pré-validação para garantir que o item esteja pronto para ser publicado
- Publicar o item na Galeria do PowerShell usando os comandos Publish-Module e Publish-Script
- Responder a perguntas ou dúvidas sobre o item

A Galeria do PowerShell aceita módulos do PowerShell e scripts do PowerShell.
Quando nos referimos a scripts, queremos dizer um script do PowerShell que é um único arquivo e não faz parte de um módulo maior.

## <a name="powershell-gallery-account-and-api-key"></a>Conta da Galeria do PowerShell e chave de API

Consulte [Creating a PowerShell Gallery Account](https://msdn.microsoft.com/powershell/gallery/psgallery/psgallery_creating_an_account) (Criando uma conta da Galeria do PowerShell) para saber como configurar a sua conta da Galeria do PowerShell.

Depois de criar uma conta, você poderá obter a chave de API necessária para publicar um item.
Depois que você entrar usando a conta, seu nome de usuário será exibido na parte superior das páginas da Galeria do PowerShell em vez de Registrar.
Clicar em seu nome de usuário levará à página Minha conta, na qual você encontrará a chave de API.

Observação: a chave de API deve ser tratada com a mesma segurança que seu logon e sua senha.
Com essa chave você ou qualquer outra pessoa pode atualizar qualquer item que você possua na Galeria do PowerShell.
É recomendável atualizar a chave regularmente, o que pode ser feito usando Redefinir chave na página Minha conta.

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>Metadados necessários para itens publicados na Galeria do PowerShell

A Galeria do PowerShell fornece informações aos usuários da galeria que são extraídas dos campos de metadados incluídos no manifesto de módulo ou de script.
Para criar ou modificar itens para publicação na Galeria do PowerShell, há um pequeno conjunto de requisitos quanto às informações fornecidas no manifesto do item.
É altamente recomendado que você examine a seção de Metadados de item das [Diretrizes de publicação](https://msdn.microsoft.com/powershell/gallery/psgallery/psgallery-PublishingGuidelines) para saber como fornecer em seus itens as melhores informações para os usuários.

Os cmdlets [New-ModuleManifest](https://msdn.microsoft.com/powershell/gallery/psget/module/ModuleManifest-Reference) e [New-ScriptFileInfo](https://msdn.microsoft.com/powershell/gallery/psget/script/psget_new-scriptfileinfo) criarão o modelo de manifesto para você, com espaços reservados para todos os elementos do manifesto.

Ambos os manifestos têm duas seções importantes para a publicação, a área Dados de chave primária e PSData de PrivateData Os dados de chave primária em um manifesto de módulo do PowerShell correspondem a tudo que não está na seção PrivateData.
O conjunto de chaves primárias é vinculado à versão do PowerShell em uso e os indefinidos não têm suporte.
PrivateData dá suporte à adição de novas chaves, portanto, os elementos específicos da Galeria do PowerShell ficam no PSData.


Os elementos do manifesto mais importantes que devem ser preenchidos para o item publicado na Galeria do PowerShell são:

- Nome do script ou do módulo – são extraídos dos nomes do .PS1 para um script ou do .PSD1 para um módulo.
- Versão – é uma chave primária necessária e o formato deve seguir as diretrizes de SemVer (consulte as Práticas recomendadas para obter detalhes)
- Autor – é uma chave primária necessária e contém o nome a ser associado ao item (consulte Autores e Proprietários, abaixo)
- Descrição – é uma chave primária necessária, usada para explicar brevemente o que esse item faz e os requisitos para usá-lo
- ProjectURI – é um campo de URI altamente recomendado em PSData que fornece um link para um repositório Github ou local semelhante ao qual você pode fazer o desenvolvimento no item

Autores e Proprietários de itens da Galeria do PowerShell são conceitos relacionados, mas nem sempre correspondem.
Proprietários de item são usuários com contas da Galeria do PowerShell que têm permissão para manter o item. Pode haver vários Proprietários que podem atualizar um item.
O Proprietário só está disponível na Galeria do PowerShell e será perdido se o item for copiado de um sistema para outro.
Autor é uma cadeia de caracteres criada nos dados do manifesto, portanto, ele sempre faz parte do item.
As recomendações para itens de produtos da Microsoft são:

- Ter várias proprietários, com pelo menos um sendo o nome da equipe que produz o item;
- Ter o Autor como o nome de uma equipe conhecida (como a equipe do SDK do Azure) ou Microsoft Corporation.


## <a name="pre-validate-your-item"></a>Pré-validar o Item

Há algumas ferramentas que você precisa executar no código antes de publicar o item na Galeria do PowerShell:

- [Analisador de Script do PowerShell](https://www.powershellgallery.com/packages/PSScriptAnalyzer/), que fica na Galeria do PowerShell
- Para módulos, Test-ModuleManifest que faz parte do PowerShell
- Para scripts, Test-ScriptFileInfo que acompanha o PowerShell Get

[PowerShell Script Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) é uma ferramenta de análise de código estático que examina seu código para garantir que ele atenda às diretrizes de codificação básicas do PowerShell. Essa ferramenta identifica os problemas críticos e comuns no código e deve ser executada regularmente durante o desenvolvimento para ajudá-lo a preparar o item para ser publicado.
O PowerShell Script Analyzer fornecerá a lista dos problemas identificados como Erros, Aviso e Informações.
Todos os erros deverão ser resolvidos antes que você publique na Galeria do PowerShell. Os avisos precisam ser examinados e a maioria deles deve ser resolvida.
O PowerShell Script Analyzer é executado sempre que um item é publicado ou atualizado na Galeria do PowerShell.
A equipe de Operações de Galeria entrará em contato com os proprietários de item para resolver os erros encontrados.

Se as informações de manifesto no item não puderem ser lidas pela infraestrutura da Galeria do PowerShell, você não poderá publicar.
O [Test-ModuleManifest](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-modulemanifest) detectará problemas comuns que possam fazer com que o módulo fique inutilizável ao ser instalado. Ele deve ser executado para cada módulo antes de publicar na Galeria do PowerShell.

Da mesma forma, [Test-ScriptFileInfo](https://msdn.microsoft.com/powershell/gallery/psget/script/psget_test-scriptfileinfo) valida os metadados em um script e deve ser executado em cada script (publicado separado de um módulo) antes de publicar na Galeria do Powershell.


## <a name="publishing-items"></a>Publicando itens

Você deve usar o [Publish-Script](https://msdn.microsoft.com/powershell/gallery/psget/script/psget_publish-script) ou o [Publish-Module](https://msdn.microsoft.com/powershell/gallery/psget/module/psget_publish-module) para publicar itens na Galeria do PowerShell.
Esses dois comandos exigem

- O caminho para o item que você publicará. Para um módulo, use a pasta denominada para o seu módulo. Se você especificar uma pasta que contenha várias versões do mesmo módulo, você deverá especificar RequiredVersion.
- Uma chave de API do NuGet. Esta é a chave de API encontrada na página Minha conta na Galeria do PowerShell.

A maioria das outras opções na linha de comando deve estar nos dados de manifesto do item que você está publicando, portanto, você não precisa especificá-las no comando.

Para evitar erros, é altamente recomendado que você experimente os comandos usando -Whatif -Verbose, antes da publicação.
Isso poupará um tempo considerável, pois toda vez que você publica na Galeria do PowerShell, você deve atualizar o número de versão na seção de manifesto do item.

Exemplos seriam: 'Publish-Module -Path ".\MyModule" -RequiredVersion "0.0.1" -NugetAPIKey "GUID" -Whatif -Verbose' 'Publish-Script -Path ".\MyScriptFile.PS1" -NugetAPIKey "GUID" -Whatif -Verbose'

Examine a saída com cuidado e, se não aparecerem erros ou avisos, repita o comando sem o parâmetro -Whatif.

Todos os itens que são publicados na Galeria do PowerShell serão verificados em busca de vírus e serão analisados usando o PowerShell Script Analyzer.
Quaisquer problemas que surgirem no momento serão enviados ao publicador para resolução.

Depois de publicar um item na Galeria do PowerShell, você precisará observar os comentários sobre o item.

- Monitore o endereço de email associado à conta usada para publicar.
Os usuários e a equipe de operações da Galeria do PowerShell fornecem comentários por meio dessa conta, incluindo problemas do PSSA ou das verificações antivírus.
Se a conta de email for inválida ou se forem relatados problemas sérios à conta que ficarem muito tempo sem resolução, os itens poderão ser considerados abandonados e serão removidos da Galeria do PowerShell, conforme descrito em nossos [Termos de uso](https://www.powershellgallery.com/policies/Terms).
- Recomendamos que você assine os Comentários de cada item da Galeria do PowerShell que você publicar.
Isso permite que você seja notificado se alguém comentar sobre seus itens na Galeria do PowerShell.
Isso é opcional, pois requer a criação de uma conta do LiveFyre.