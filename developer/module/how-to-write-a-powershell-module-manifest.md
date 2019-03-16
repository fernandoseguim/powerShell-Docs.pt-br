---
title: Como escrever um manifesto de módulo do PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: eaa927ec90df6053843f5c942357fed4c7dee966
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059483"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>Como escrever um manifesto de módulo do Windows PowerShell

Quando você tiver gravado seu módulo do Windows PowerShell, você pode opcionalmente adicionar um manifesto de módulo. Um manifesto de módulo é um arquivo de script do PowerShell que você pode usar para incluir informações sobre o módulo. Por exemplo, você pode descrever o autor, especificar arquivos de módulo (como módulos aninhados), executados scripts para personalizar o ambiente do usuário, carregar arquivos de formatação e tipo, definem requisitos de sistema e limitam os membros que o módulo exporta.

## <a name="creating-a-module-manifest"></a>Criar um manifesto de módulo

Um *manifesto de módulo* é um arquivo de dados do Windows PowerShell (. psd1) que descreve o conteúdo de um módulo e determina como um módulo é processado. O arquivo de manifesto é um arquivo de texto que contém uma tabela de hash de chaves e valores. Você pode vincular um arquivo de manifesto para um módulo nomeando-o mesmo que o módulo, e colocando-o na raiz do diretório do módulo.

Para módulos simples que contêm somente um. psm1 único ou um assembly binário, um manifesto de módulo é opcional. No entanto, é recomendável que você use um manifesto de módulo sempre que possível, pois eles são úteis para ajudá-lo a organizar seu código e para manter informações de controle de versão. Além disso, um manifesto de módulo é necessário para exportar um assembly que está instalado no cache de assembly global. Um manifesto de módulo também é necessário para os módulos que suportam o recurso de ajuda atualizável. Ou seja, a Ajuda atualizável usa o **HelpInfoUri** chave no manifesto de módulo para encontrar o arquivo de informações (HelpInfo XML) de Ajuda que contém o local dos arquivos de Ajuda atualizados para o módulo. Para obter mais informações sobre a Ajuda atualizável, consulte [suporte à Ajuda atualizável](./supporting-updatable-help.md).

### <a name="to-create-and-use-a-module-manifest"></a>Criar e usar um manifesto de módulo

1. Para criar um manifesto de módulo, você tem várias opções:

   1. Diretamente criar a tabela de hash com as informações mínimas necessárias e salve-o em um arquivo. psd1 que tem o mesmo nome que seu módulo. Assim que tiver feito isso, você pode abrir o arquivo e adicionar manualmente os valores apropriados.

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. Ou, chame o [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet, com um ou mais dos valores padrão passados como parâmetros. (Observe que o somente o nome do arquivo é necessário para gerar um manifesto, no entanto.) Isso criará um manifesto de módulo com todos os os manifestos valores que você forneceu explicitamente declarados e com o resto que contém o valor padrão adequado.

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. Por fim, você pode também criar um arquivo. psd1 vazia, copie o modelo na parte inferior deste tópico para o arquivo e preencha os valores relevantes. O único requisito real nesse caso seria garantir que o arquivo foi o mesmo nome que o módulo.

2. Adicione todos os elementos adicionais a que você deseja ter no arquivo de manifesto.

   Em termos gerais, isso provavelmente será feito em qualquer editor de texto que você prefere, como o bloco de notas. No entanto, isso é tecnicamente um arquivo de script que contém o código, portanto, talvez você queira editá-lo em um ambiente real de desenvolvimento ou script, como o ISE do PowerShell. Novamente, observe que todos os elementos de um arquivo de manifesto são opcionais, exceto para o número de ModuleVersion.

   Para obter descrições das chaves e valores que você pode ter em um manifesto de módulo, consulte a **elementos do manifesto de módulo** abaixo. Para obter mais informações, consulte as descrições de parâmetro na [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet.

3. Opcionalmente, você pode optar por adicionar mais código ao manifesto do módulo, para lidar com quaisquer cenários que não devem ser cobertos pelos elementos do manifesto de módulo básico.

   Devido a questões de segurança, o PowerShell será executado somente um pequeno subconjunto de operações disponíveis em um arquivo de manifesto de módulo. Em geral, você pode usar o **se** instrução, operadores aritméticos e de comparação e os tipos de dados básicos do PowerShell.

4. Depois de ter criado seu manifesto de módulo, você pode testá-lo (para confirmar que todos os caminhos descritos no manifesto estão corretos) com uma chamada para [Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest).

   `Test-ModuleManifest myModuleName.psd1`

5. Certifique-se de que seu manifesto de módulo está localizado no nível superior do diretório que contém seu módulo.

   Quando você copia seu módulo em um sistema e importá-lo, o PowerShell usará o manifesto de módulo para importar o módulo.

6. Opcionalmente, você pode testar diretamente seu manifesto de módulo com uma chamada para [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) por dot sourcing o manifesto em si.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Elementos do manifesto de módulo

A tabela a seguir descreve os elementos que você pode ter em um manifesto de módulo

|Elemento|Padrão|Descrição|
|-------------|-------------|-----------------|
|RootModule<br /><br /> Type: string|' '|Módulo ou binário módulo arquivo de script associado com esse manifesto. Versões anteriores do PowerShell chamado neste elemento o ModuleToProcess.<br /><br /> Os tipos possíveis para o módulo raiz podem estar vazios (que tornará isso um **manifesto** módulo), o nome de um módulo de script (. psm1, o que torna isso um **Script** módulo), ou o nome de um módulo binário (DLL ou. .exe, que o torna uma **binário** módulo). Colocar o nome de um manifesto de módulo (. psd1) ou um arquivo de script (. ps1) neste elemento fará com que ocorra um erro.|
|ModuleVersion<br /><br /> Type: string|1.0|Número de versão do módulo. A cadeia de caracteres deve ser capaz de converter para [Version]. Ou seja, ' #. #. #. #. #'. `Import-Module` carregará o primeiro módulo encontradas na **$psModulePath** que corresponde ao nome e que tem pelo menos tão alto ModuleVersion, como o `-MinimumVersion` parâmetro. Para importar uma versão específica, use o`-RequiredVersion` parâmetro, em vez disso.<br /><br /> Exemplo: `ModuleVersion = '1.0'`|
|GUID<br /><br /> Type: string|GUID gerado automaticamente|ID usada para identificar com exclusividade este módulo. Observe que no momento, você não é possível importar um módulo por GUID.<br /><br /> Exemplo: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|Autor<br /><br /> Type: string|Não|Autor deste módulo.<br /><br /> Exemplo: `Author = 'AuthorNameHere'`|
|CompanyName<br /><br /> Type: string|Unknown|Da empresa ou fornecedor deste módulo.<br /><br /> Exemplo: `CompanyName = 'Fabrikam'`|
|Direitos autorais<br /><br /> Type: string|(c) [currentYear] [criar]. Todos os direitos reservados.|Declaração de direitos autorais para esse módulo.<br /><br /> Exemplo: `Copyright = '2016 AuthorName. All rights reserved.'`|
|Descrição<br /><br /> Type: string|' '|Descrição da funcionalidade fornecida por esse módulo.<br /><br /> Exemplo: `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> Type: string|' '|Versão mínima do mecanismo do Windows PowerShell necessário para esse módulo. Valores válidos no momento são 1.0, 2.0, 3.0, 4.0 e 5.0.<br /><br /> Exemplo: `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> Type: string|' '|Especifica o nome do host do Windows PowerShell que é exigido pelo módulo. Esse nome é fornecido pelo Windows PowerShell. Para localizar o nome de um programa de host, no programa, digite: `$host.name` .<br /><br /> Exemplo: `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> Type: string|' '|Versão mínima do host do Windows PowerShell necessário para esse módulo.<br /><br /> Exemplo: `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> Type: string|' '|Versão mínima do Microsoft .NET Framework necessária por esse módulo.<br /><br /> Exemplo: `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> Type: string|' '|Versão mínima do common language runtime (CLR) exigido por esse módulo.<br /><br /> Exemplo: `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> Type: string|' '|Arquitetura do processador (nenhum, X86, Amd64) exigida por esse módulo. Os valores válidos são x86, AMD64 IA64 e Nenhum (desconhecido ou não especificado).<br /><br /> Exemplo: `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> Type: [string[]]|@()|Módulos que devem ser importados para o ambiente global antes de importar esse módulo. Isso carregará todos os módulos listados, a menos que já foram carregados. (Por exemplo, alguns módulos podem já ser carregados por um módulo diferente.). Também é possível especificar uma versão específica para carregar usando `RequiredVersion` em vez de `ModuleVersion`. Ao usar `ModuleVersion` ele carregará a versão mais recente disponível com no mínimo a versão especificada.<br /><br /> Exemplo: `RequiredModules = @(@{ModuleName="myDependentModule", ModuleVersion="2.0",Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> Exemplo: `RequiredModules = @(@{ModuleName="myDependentModule", RequiredVersion="1.5",Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> Type: [string[]]|@()|Assemblies que devem ser carregados antes de importar esse módulo.<br /><br /> Observe que, ao contrário de RequiredModules, o PowerShell carregará o RequiredAssemblies se eles não tiverem sido carregados.|
|ScriptsToProcess<br /><br /> Type: [string[]]|@()|Arquivos de script (. ps1) que são executados no estado de sessão do chamador, quando o módulo é importado. Isso pode ser a sessão global, estada ou, para módulos aninhados, o estado da sessão de outro módulo. Você pode usar esses scripts para preparar um ambiente, assim como você pode usar um script de logon.<br /><br /> Esses scripts são executados antes que qualquer um dos módulos listados no manifesto sejam carregados.|
|TypesToProcess<br /><br /> Type: [Object[]]|@()|Tipo de arquivos (. ps1xml) a ser carregado ao importar esse módulo.|
|FormatsToProcess<br /><br /> Type: [Object[]]|@()|Formatos de arquivo (. ps1xml) a ser carregado ao importar esse módulo.|
|NestedModules<br /><br /> Type: [Object[]]|@()|Módulos para importar como módulos aninhados do módulo especificado na RootModule/ModuleToProcess.<br /><br /> Adicionar um nome de módulo para esse elemento é semelhante a chamar `Import-Module` de dentro de seu código de script ou assembly. A principal diferença é que ele é mais fácil de ver o que você está carregando aqui no arquivo de manifesto. Além disso, se um módulo falhar ao carregar aqui, você será não ainda tiver carregado seu módulo real.<br /><br /> Além de outros módulos, você também pode carregar arquivos de script (. ps1) aqui. Esses arquivos serão executadas no contexto do módulo raiz. (Isso é equivalente a dot sourcing o script em seu módulo raiz.)|
|FunctionsToExport<br /><br /> Tipo: Cadeia de caracteres|'*'|Especifica as funções que o módulo exporta (os caracteres são permitidos curingas) para o estado de sessão do chamador. Por padrão, todas as funções são exportadas. Você pode usar essa chave para restringir as funções que são exportadas pelo módulo.<br /><br /> Estado de sessão do chamador pode ser a sessão global, estada ou, para módulos aninhados, o estado da sessão de outro módulo. Ao encadear módulos aninhados, todas as funções que são exportadas por um módulo aninhado serão exportadas para o estado de sessão global, a menos que um módulo na cadeia restringe a função usando a chave FunctionsToExport.<br /><br /> Se o manifesto também exporta os aliases para as funções, essa chave pode remover funções cujos aliases são listados na chave AliasesToExport, mas essa chave não pode adicionar aliases de função à lista.|
|CmdletsToExport<br /><br /> Tipo: Cadeia de caracteres|'*'|Especifica os cmdlets que o módulo exporta (os caracteres são permitidos curingas). Por padrão, todos os cmdlets são exportados. Você pode usar essa chave para restringir os cmdlets que são exportados pelo módulo.<br /><br /> Estado de sessão do chamador pode ser a sessão global, estada ou, para módulos aninhados, o estado da sessão de outro módulo. Quando encadeamento de módulos aninhados, todos os cmdlets que são exportados por um módulo aninhado será, por fim, exportados para o estado de sessão global, a menos que um módulo na cadeia restringe o cmdlet por meio da chave CmdletsToExport.<br /><br /> Se o manifesto também exporta os aliases para os cmdlets, essa chave pode remover cmdlets cujos aliases são listados na chave AliasesToExport, mas essa chave não pode adicionar aliases de cmdlet à lista.|
|VariablesToExport<br /><br /> Tipo: Cadeia de caracteres|'*'|Especifica as variáveis que o módulo exporta (os caracteres são permitidos curingas) para o estado de sessão do chamador. Por padrão, todas as variáveis são exportadas. Você pode usar essa chave para restringir as variáveis que são exportadas pelo módulo.<br /><br /> Estado de sessão do chamador pode ser a sessão global, estada ou, para módulos aninhados, o estado da sessão de outro módulo. Quando encadeamento de módulos aninhados, todas as variáveis que são exportadas por um módulo aninhado serão exportadas para o estado de sessão global, a menos que um módulo na cadeia restringe a variável usando a chave VariablesToExport.<br /><br /> Se o manifesto também exporta os aliases para as variáveis, essa chave pode remover variáveis cujos aliases são listados na chave AliasesToExport, mas essa chave não pode adicionar aliases variável à lista.|
|AliasesToExport<br /><br /> Tipo: Cadeia de caracteres|'*'|Especifica os aliases que o módulo exporta (os caracteres são permitidos curingas) para o estado de sessão do chamador. Por padrão, todos os aliases são exportados. Você pode usar essa chave para restringir os aliases exportados pelo módulo.<br /><br /> Estado de sessão do chamador pode ser a sessão global, estada ou, para módulos aninhados, o estado da sessão de outro módulo. Quando encadeamento de módulos aninhados, todos os aliases exportados por um módulo aninhado serão, por fim, exportados para o estado de sessão global, a menos que um módulo na cadeia restringe o alias, usando a chave AliasesToExport.|
|ModuleList<br /><br /> Type: [string[]]|@()|Especifica todos os módulos que são empacotados com este módulo. Esses módulos podem ser inseridos por nome (uma cadeia de caracteres separada por vírgulas) ou como uma tabela de hash com as chaves ModuleName e GUID. A tabela de hash também pode ter uma chave ModuleVersion opcional. A chave ModuleList foi projetada para atuar como um inventário do módulo. Esses módulos não são processados automaticamente.|
|Lista de arquivos<br /><br /> Type: [string[]]|@()|Lista de todos os arquivos compactados com esse módulo. Como com ModuleList, FileList é ajudá-lo como uma lista de inventário e caso contrário, não será processada.|
|PrivateData<br /><br /> Tipo: [objeto]|' '|Especifica todos os dados privados que devem ser passados para o módulo raiz especificado pela chave RootModule/ModuleToProcess.|
|HelpInfoURI<br /><br /> Type: string|' '|URI HelpInfo deste módulo.|
|DefaultCommandPrefix<br /><br /> Type: string|' '|O prefixo padrão para comandos exportados a partir deste módulo. Substituir o prefixo padrão usando `Import-Module` -prefixo.|

## <a name="sample-module-manifest"></a>Exemplo de manifesto de módulo

O manifesto de módulo de exemplo a seguir mostra as chaves e valores padrão em um manifesto de módulo. Este exemplo foi criado usando o `New-ModuleManifest` cmdlet no Windows PowerShell 3.0. Durante a criação de vários módulos, você pode usar este cmdlet para criar um modelo de manifesto que, em seguida, pode ser modificado para diferentes módulos.

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 1/24/2012
#

@{

# Script module or binary module file associated with this manifest
#RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = 'd0a9150d-b6a4-4b17-a325-e3a24fed0aa9'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2012 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of the .NET Framework required by this module
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module
FunctionsToExport = '*'

# Cmdlets to export from this module
CmdletsToExport = '*'

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module
AliasesToExport = '*'

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess
# PrivateData = ''

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>Consulte Também

[Escrevendo um módulo do Windows PowerShell](./writing-a-windows-powershell-module.md)
