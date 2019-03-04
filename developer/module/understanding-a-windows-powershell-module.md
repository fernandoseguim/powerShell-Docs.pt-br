---
title: Noções básicas sobre um módulo do Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: 77d328bc1cb8cb42d5a10f107a149c05ab270ce3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862732"
---
# <a name="understanding-a-windows-powershell-module"></a>Noções básicas sobre um módulo do Windows PowerShell

Um *módulo* é um conjunto de funcionalidades relacionadas do Windows PowerShell, agrupados juntos como uma unidade conveniente (normalmente, salva em um único diretório). Definindo um conjunto de arquivos de script relacionadas, assemblies e recursos relacionados como um módulo, você pode fazer referência, carregar, persistir e compartilhar seu código mais fácil do que você precisaria de outra forma.

O objetivo principal de um módulo é permitir que a modularização (ou seja, reutilização e abstração) de código do Windows PowerShell. Por exemplo, a maneira mais básica de criação de um módulo é simplesmente salvar um script do Windows PowerShell como um arquivo. psm1. Fazer então permite que você controle (ou seja, tornar público ou privado) as funções e variáveis contidas no script. Salvando o script como um arquivo. psm1 também permite que você controle o escopo de certas variáveis. Por fim, você também pode usar cmdlets como [Install-Module](/powershell/module/PowershellGet/Install-Module) para organizar, instalar e usar o script como blocos de construção para soluções maiores.

## <a name="module-components-and-types"></a>Tipos e os componentes de módulo

Um módulo é composto por quatro componentes básicos:

1. Algum tipo de arquivo de código, normalmente, um script do PowerShell ou um assembly de cmdlet gerenciadas.

2. Qualquer outra coisa que o arquivo de código acima pode precisa, como assemblies adicionais, ajudar a arquivos ou scripts.

3. Um arquivo de manifesto que descreve os arquivos acima, bem como armazena metadados, como informações de autor e controle de versão...

4. Um diretório que contém todo o conteúdo acima e está localizado onde PowerShell razoavelmente pode encontrá-lo.

   Observe que nenhum desses componentes, por si só, é realmente necessário. Por exemplo, um módulo pode tecnicamente ser somente um script armazenado em um arquivo. psm1. Você também pode ter um módulo que é nada além de um arquivo de manifesto, que é usado principalmente para fins de organização. Você também pode escrever um script que cria dinamicamente um módulo e, assim, não precisa realmente um diretório para armazenar qualquer coisa no. As seções a seguir descrevem os tipos de módulos, que você pode obter ao misturar e combinar as diferentes partes possíveis de um módulo juntos.

### <a name="script-modules"></a>Módulos de script

Como o nome implica, uma *módulo de script* é um arquivo (. psm1) que contém qualquer código válido do Windows PowerShell. Os administradores e desenvolvedores de script podem usar esse tipo de módulo para criar módulos cujos membros incluem funções, variáveis e muito mais. Em essência, um módulo de script é simplesmente um script do Windows PowerShell com uma extensão diferente, que permite aos administradores usar funções de gerenciamento, exportação e importação nele.

Além disso, você pode usar um arquivo de manifesto para incluir outros recursos em seu módulo, como arquivos de dados, outros módulos dependentes ou scripts de tempo de execução. Arquivos de manifesto também são úteis para metadados, como informações de criação e controle de versão de controle.

Por fim, um módulo de script, como qualquer outro módulo que não será criado dinamicamente, precisa ser salvo em uma pasta que o PowerShell razoavelmente pode descobrir. Geralmente, isso é no caminho do módulo do PowerShell; mas, se necessário você pode descrever explicitamente onde o módulo está instalado. Para obter mais informações, consulte [como escrever um módulo de Script do PowerShell](./how-to-write-a-powershell-script-module.md).

### <a name="binary-modules"></a>Módulos binários

Um *módulo binário* é um assembly do .NET Framework (. dll) que contém o código compilado, como C#. Os desenvolvedores de cmdlet podem usar esse tipo de módulo para compartilhar cmdlets, provedores e muito mais. (Os snap-ins existentes também pode ser usados como módulos binários.) Em comparação com um módulo de script, um módulo binário permite que você crie cmdlets que são mais rápidos ou usar os recursos (como multithreading) que não são tão fácil de codificar em scripts do Windows PowerShell.

Como com módulos de script, você pode incluir um arquivo de manifesto para descrever os recursos adicionais que usa seu módulo e para controlar metadados sobre seu módulo. Da mesma forma, você provavelmente deve instalar o módulo binário em uma pasta em algum lugar no caminho do módulo do PowerShell. Para obter mais informações, consulte como [como escrever um módulo binário do PowerShell](./how-to-write-a-powershell-binary-module.md).

### <a name="manifest-modules"></a>Módulos de manifesto

Um *módulo de manifesto* é um módulo que usa um arquivo de manifesto para descrever todos os seus componentes, mas não tem qualquer tipo de assembly principal ou script. (Formalmente, o módulo de manifesto deixa o `ModuleToProcess` ou `RootModule` elemento do manifesto vazio.) No entanto, você ainda pode usar outros recursos de um módulo, como a capacidade de carregar assemblies de dependente ou executar certos scripts de pré-processando automaticamente. Você também pode usar um módulo de manifesto como uma maneira conveniente de empacotar os recursos que outros módulos serão usadas, como módulos aninhados, assemblies, tipos ou formatos. Para obter mais informações, consulte [como escrever um manifesto de módulo do PowerShell](./how-to-write-a-powershell-module-manifest.md).

### <a name="dynamic-modules"></a>Módulos dinâmicos

Um *módulo dinâmico* é um módulo não foi carregado ou salvo em um arquivo. Em vez disso, eles são criados dinamicamente por um script, usando o [New-Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet. Esse tipo de módulo permite que um script criar um módulo sob demanda que não precisam ser carregados ou salvos no armazenamento persistente. Por sua natureza, um módulo dinâmico se destina a ser de curta duração e, portanto, não pode ser acessado pelo `Get-Module` cmdlet. Da mesma forma, eles geralmente não precisam de manifestos de módulo, nem fazem que provavelmente precisarão permanentes pastas para armazenar seus assemblies relacionados.

## <a name="module-manifests"></a>Manifestos de módulo

Um *manifesto de módulo* é um arquivo. psd1 que contém uma tabela de hash. As chaves e valores na tabela de hash fazem o seguinte:

- Descreva o conteúdo e os atributos do módulo.

- Defina os pré-requisitos.

- Determine como os componentes são processados.

  Manifestos não são necessários para um módulo. Módulos podem fazer referência a arquivos de script (. ps1), arquivos de módulo (. psm1), arquivos de manifesto (. psd1), formatação de script e digite arquivos (. ps1xml), conjuntos de módulos de cmdlet e o provedor (. dll), arquivos de recurso, arquivos de Ajuda, arquivos de localização ou qualquer outro tipo de arquivo ou recurso que é fornecido como parte do módulo. Para obter um script internacionalizado, a pasta de módulo também contém um conjunto de arquivos de catálogo de mensagens. Se você adicionar um arquivo de manifesto para a pasta de módulo, você pode fazer referência os vários arquivos como uma única unidade referenciando o manifesto.

  O manifesto do próprio descreve categorias de informações a seguir:

- Metadados sobre o módulo, como o número de versão do módulo, o autor e a descrição.

- Pré-requisitos necessários para importar o módulo, como a versão do Windows PowerShell, a versão do common language runtime (CLR) e os módulos necessários.

- Diretivas de processamento, como os scripts, formatos e tipos para processar.

- Restrições sobre os membros do módulo para exportar, como os aliases, funções, variáveis e cmdlets para exportar.

  Para obter mais informações, consulte [como escrever um manifesto de módulo do PowerShell](./how-to-write-a-powershell-module-manifest.md).

## <a name="storing-and-installing-a-module"></a>Armazenando e instalando um módulo

Depois de criar um script, o módulo binário ou manifesto, você pode salvar seu trabalho em um local que outras pessoas possam acessá-lo. Por exemplo, o módulo pode ser armazenado na pasta do sistema onde o Windows PowerShell está instalado, ou ele pode ser armazenado em uma pasta de usuário.

Em termos gerais, você pode determinar onde você deve instalar o módulo usando um dos caminhos armazenados no `$ENV:PSModulePath` variável. Usar um desses caminhos significa PowerShell pode localizar e carregar o módulo quando um usuário faz uma chamada a ele em seu código automaticamente. Se você armazenar seu módulo em outro lugar, você pode explicitamente informar PowerShell passando o local do seu módulo como um parâmetro ao chamar `Install-Module`.

Independentemente disso, o caminho da pasta é conhecido como o *base* do módulo (ModuleBase) e o nome do script, o arquivo de módulo binário ou de manifesto deve ser o mesmo que o nome da pasta de módulo, com as seguintes exceções:

- Módulos dinâmicos que são criados pela `New-Module` cmdlet pode ser nomeado usando o `Name` parâmetro do cmdlet.

- Módulos importados de objetos de assembly, o  **`Import-Module` -Assembly** comando são nomeados de acordo com a seguinte sintaxe: `"dynamic_code_module_" + assembly.GetName()`.

  Para obter mais informações, consulte [instalando um módulo do PowerShell](./installing-a-powershell-module.md) e [modificando o caminho de instalação do PSModulePath](./modifying-the-psmodulepath-installation-path.md).

## <a name="module-cmdlets-and-variables"></a>Variáveis e os Cmdlets do módulo

As variáveis e os cmdlets a seguir são fornecidas pelo Windows PowerShell para a criação e gerenciamento de módulos.

[Novo módulo](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet esse cmdlet cria um novo módulo dinâmico que existe apenas na memória. O módulo é criado a partir de um bloco de script e seus membros exportados, como suas funções e variáveis, ficam imediatamente disponíveis na sessão e permanecem disponíveis até que a sessão é fechada.

[New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet esse cmdlet cria um novo arquivo de manifesto (. psd1) do módulo, preenche os valores e salva o arquivo de manifesto no caminho especificado. Esse cmdlet também pode ser usado para criar um modelo de manifesto de módulo que pode ser preenchido manualmente.

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet esse cmdlet adiciona um ou mais módulos à sessão atual.

[Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet este cmdlet recupera informações sobre os módulos que foram ou que podem ser importados para a sessão atual.

[Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) cmdlet esse cmdlet especifica os membros do módulo (como cmdlets, funções, variáveis e aliases) que são exportados a partir de um arquivo de módulo (. psm1) de script ou um módulo dinâmico criado usando o `New-Module` cmdlet.

[Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) cmdlet esse cmdlet remove módulos da sessão atual.

[Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) cmdlet esse cmdlet verifica se um manifesto de módulo descreve com precisão os componentes de um módulo, verificando se os arquivos que estão listados no arquivo de manifesto de módulo (. psd1) realmente existem nos caminhos especificados.

$PSScriptRoot essa variável contém o diretório do qual o módulo de script está sendo executado. Ele permite que os scripts usar o caminho do módulo para acessar outros recursos.

$env: PSModulePath essa variável de ambiente contém uma lista dos diretórios nos quais Windows PowerShell módulos são armazenados. Windows PowerShell usa o valor dessa variável ao importar módulos automaticamente e atualizando os tópicos de ajuda para módulos.

## <a name="see-also"></a>Consulte Também

[Escrevendo um módulo do Windows PowerShell](./writing-a-windows-powershell-module.md)
