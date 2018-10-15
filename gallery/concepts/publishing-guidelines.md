---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
description: Diretrizes para publicadores
title: Diretrizes e práticas recomendadas da Galeria do PowerShell
ms.openlocfilehash: 2ddeae9fdb33a58f97bfeb66079541bb7c5791b1
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851162"
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>Diretrizes e práticas recomendadas da Galeria do PowerShell

Este tópico descreve as etapas recomendadas usadas pelas equipes da Microsoft para garantir que os itens publicados na Galeria do PowerShell sejam amplamente adotados e forneçam um valor alto para os usuários, com base em como a Galeria do PowerShell lida com os dados de manifesto e nos comentários de um grande número de usuários da Galeria do PowerShell.
Os itens que forem publicados seguindo essas diretrizes terão maior probabilidade de ser instalados, de ganhar confiança e de atrair mais usuários.

Abaixo estão as diretrizes para que um item da Galeria do PowerShell seja o ideal, quais configurações opcionais de manifesto são mais importantes, melhorias do código com comentários de revisores inicias e do [Powershell Script Analyzer](https://aka.ms/psscriptanalyzer), controle de versão de seu módulo, documentação, testes e exemplos de como usar o que você compartilhou.
Grande parte desta documentação segue as diretrizes para publicar [High Quality DSC Resource Modules](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md) (Módulos de recurso de DSC de alta qualidade).

Para obter o mecanismo de publicação de um item na Galeria do PowerShell, consulte [Criar e publicar um item](https://msdn.microsoft.com/powershell/gallery/psgallery/creating-and-publishing-an-item).

Comentários sobre essas diretrizes são boas-vindos. Se você tiver comentários, abra problemas no nosso [Repositório de documentação do Github](https://github.com/powershell/powershell-docs/).

## <a name="best-practices-for-publishing-items"></a>Práticas recomendadas para a publicação de itens

As seguintes práticas recomendadas são o que os usuários de itens da Galeria do PowerShell dizem que é importante e são elas listadas em ordem de prioridade nominal.
Os itens que seguem estas diretrizes têm uma probabilidade muito maior de ser baixados e adotados por outras pessoas.

- Usar PSScriptAnalyzer
- Incluir a documentação e exemplos
- Seja receptivo aos comentários
- Fornecer módulos em vez de scripts
- Fornecer links para um site do projeto
- Incluir testes com os módulos
- Incluir e/ou vincular aos termos de licença
- Assinar o código
- Seguir as diretrizes [SemVer](http://semver.org/) para controle de versão
- Use marcas comuns, conforme documentado em Marcas comuns da Galeria do PowerShell
- Publicação de teste usando um repositório local
- Usar o PowerShellGet para publicar

Cada uma delas é abordada brevemente nas seções a seguir.

## <a name="use-psscriptanalyzer"></a>Usar PSScriptAnalyzer

O [PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) é uma ferramenta de análise de código estático gratuita que funciona em códigos do PowerShell.
O PSScriptAnalyzer identificará os problemas mais comuns vistos no código do PowerShell e, geralmente, uma recomendação para corrigir o problema.
A ferramenta é fácil de usar e categoriza os problemas como Erros (graves, devem ser abordados), Avisos (precisam ser examinados e devem ser resolvidos) e Informações (vale a pena verificar visando as práticas recomendadas).
Todos os itens de itens publicados na Galeria do PowerShell serão examinados usando o PSScriptAnalyzer e todos os erros serão ser relatados para o proprietário e deverão ser abordados.

A prática recomendada é executar `Invoke-ScriptAnalyzer` com Aviso `-Recurse` e `-Severity`.

Examine os resultados e verifique se:

- Todos os erros foram corrigidos ou abordados na documentação
- Todos os avisos foram examinados e resolvidos quando aplicável

Os usuários que adquirem itens da Galeria do PowerShell são altamente incentivados a executar PSScriptAnalyzer e s avaliar todos os Erros e Avisos.
Os usuários têm maior probabilidade de entrar em contato com os proprietários do item quando percebem que um erro foi relatado pelo PSScriptAnalyzer.
Se houver um motivo convincente para o item manter o código sinalizado como um erro, adicione essas informações à documentação para evitar precisar responder à mesma pergunta muitas vezes.

## <a name="include-documentation-and-examples"></a>Incluir a documentação e exemplos

Documentação e exemplos são a melhor maneira de garantir que os usuários possam aproveitar qualquer código compartilhado.

A documentação é a coisa mais útil a ser incluída nos itens publicados na Galeria do PowerShell.
Os usuários geralmente ignoram itens sem a documentação, pois a alternativa é ler o código para entender o que é o item e como usá-lo.
Há vários artigos disponíveis no MSDN sobre como fornecer documentação com itens do PowerShell, incluindo:

- As diretrizes para fornecer ajuda estão em [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) (Como escrever a ajuda do cmdlet)
- Criar a ajuda do cmdlet, que é a melhor abordagem para qualquer script, função ou cmdlet do PowerShell.
  Para obter informações de como criar a Ajuda do cmdlet, comece com [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) (Como escrever a Ajuda do cmdlet) na biblioteca MSDN.
  Para adicionar a ajuda dentro de um script, consulte [About Comment Based Help](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_comment_based_help) (Sobre a ajuda baseada em comentários).
- Muitos módulos também incluem documentação no formato de texto, como arquivos de MarkDown.
  Isso pode ser particularmente útil quando há um site do projeto no Github, no qual o Markdown é um formato muito usado.
  A prática recomendada é usar [Markdown para Github](https://help.github.com/categories/writing-on-github/)

Exemplos mostram aos usuários como o item deve ser usado.
Muitos desenvolvedores dirão que eles consultam os exemplos antes da documentação para entender como usar algo.
O melhor tipo de exemplo mostra o uso básico, além de um caso de uso realista simulado e o código é bem comentado.
Os exemplos de módulos publicados na Galeria do PowerShell devem estar em uma pasta Exemplos na raiz do módulo.

Um bom padrão de exemplos pode ser encontrado no [Módulo PSDscResource](https://www.powershellgallery.com/packages/PSDscResources) na pasta Examples\RegistryResource.
Há quatro exemplos de casos de uso com uma breve descrição na parte superior de cada arquivo que documenta o que está sendo demonstrado.

## <a name="respond-to-feedback"></a>Responder aos comentários

Os proprietários de item que respondem corretamente aos comentários são altamente valorizados pela comunidade.
É importante responder aos usuários que fornecem comentários construtivos, pois eles estão interessados no item o bastante para tentar ajudar a melhorá-lo.

Há dois métodos de comentários disponíveis na Galeria do PowerShell:

- Contatar proprietário: permite que um usuário envie um email para o proprietário do item. Como proprietário de um item, é importante monitorar o endereço de email usado com os itens da Galeria do PowerShell e responder aos problemas que surgirem. Uma desvantagem desse método é que apenas o usuário e o proprietário verão a comunicação, portanto, o proprietário poderá precisar responder à mesma pergunta várias vezes.
- Comentários: Na parte inferior da página do item há um campo Comentário.
  A vantagem desse sistema é que outros usuários podem ver os comentários e as respostas, o que reduz o número de vezes que uma mesma pergunta deve ser respondida.
  Como proprietário de um item, é altamente recomendável que você Siga os comentários de cada item.
Consulte [Fornecendo comentários por meio de mídia social ou do recurso Comentários](../how-to/working-with-items/social-media-feedback.md) para obter detalhes de como fazer isso.

Os proprietários que respondem aos comentários de forma construtiva são apreciados pela comunidade.
Use a oportunidade no relatório para solicitar mais informações, se necessário, fornecer uma solução alternativa ou identificar se uma atualização corrige um problema.

Se houver comportamento inadequado observado em algum desse canais de comunicação, use o recurso Relatar abuso da Galeria do PowerShell para contatar os administradores da galeria.

## <a name="modules-versus-scripts"></a>Módulos versus scripts

Compartilhar um script com outros usuários é ótimo e fornece aos outros alguns exemplos de como resolver os problemas que eles possam ter.
O problema é que os scripts na Galeria do PowerShell são arquivos únicos sem documentação, testes e exemplos separados.

Os módulos do PowerShell têm uma estrutura de pasta que permite que várias pastas e arquivos sejam incluídos no pacote.
A estrutura do módulo permite incluir os outros itens listados como práticas recomendadas: ajuda do cmdlet, documentação, exemplos e testes.
A maior desvantagem é que um script dentro de um módulo deve ser exposto e usado como uma função.
Para obter informações de como criar um módulo, consulte [Writing a Windows PowerShell Module](http://go.microsoft.com/fwlink/?LinkId=144916) (Escrevendo um módulo do Windows PowerShell).

Há situações em que um script fornece uma experiência melhor para o usuário, principalmente com configurações DSC.
A prática recomendada para configurações DSC é publicar a configuração como um script com um módulo de acompanhamento que contenha documentos, exemplos e testes.
O script lista o módulo de acompanhamento usando RequiredModules = @(Nome do módulo).
Essa abordagem pode ser usada com qualquer script.

Os scripts autônomos que seguem as práticas recomendadas fornecem um grande valor aos outros usuários.
Fornecer a documentação baseada em comentários e um link para um site do projeto são práticas altamente recomendadas ao publicar um script na Galeria do PowerShell.

## <a name="provide-a-link-to-a-project-site"></a>Fornecer um link para um site do projeto

Um Site do projeto é onde um publicador pode interagir diretamente com os usuários de seus itens da Galeria do PowerShell.
Os usuários preferem itens que fornecem um site, porque assim eles podem obter informações sobre o item com mais facilidade.
Muitos itens na Galeria do PowerShell são desenvolvidos no GitHub, outros são oferecidos por organizações com uma presença na Web dedicada.
Cada um deles pode ser considerado um site do projeto.

A adição de um link é feita incluindo ProjectURI na seção PSData do manifesto da seguinte maneira:

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

Quando um ProjectURI for fornecido, a Galeria do PowerShell incluirá um link para o site do projeto no lado esquerdo da página do item.

## <a name="include-tests"></a>Incluir testes

Incluir testes com código de software livre é importante para os usuários, porque isso oferece uma garantia sobre o que você valida e fornece informações sobre o funcionamento do código. Isso também permite que os usuários não prejudiquem a funcionalidade original caso modifiquem o seu código para ajustá-lo ao ambiente deles.

É altamente recomendável que os testes sejam escritos para aproveitar a estrutura de testes do Pester, que foi projetada especificamente para o PowerShell.
O Pester está disponível no [GitHub](https://github.com/Pester/Pester), na [Galeria do PowerShell](https://www.powershellgallery.com/packages/Pester/) e é fornecido no Windows 10, no Windows Server 2016, no WMF 5.0 e no WMF 5.1.

O [Site do projeto Pester no GitHub](https://github.com/Pester/Pester) inclui uma boa documentação de como escrever testes Pester, desde a introdução até as práticas recomendadas.

As metas de cobertura do teste são destacadas na [Documentação do módulo do recurso de alta qualidade](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md), com 70% de cobertura de código de teste de unidade recomendada.

## <a name="include-andor-link-to-license-terms"></a>Incluir e/ou vincular aos termos de licença

Todos os itens publicados na Galeria do PowerShell devem especificar os termos de licença ou estarem associados à licença incluída nos [Termos de uso](https://www.powershellgallery.com/policies/Terms) na "Exibição A".
A melhor abordagem para especificar uma licença diferente é fornecer um link para a licença usando o LicenseURI em PSData.
Você pode encontrar um exemplo no tópico Campos de manifesto recomendados.

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>Assinar o código

A assinatura de código fornece aos usuários o nível mais alto de segurança sobre quem publicou o item e de garantia de que a cópia do código adquirido é exatamente o que o publicador lançou.
Para saber mais sobre assinatura de código em geral, consulte [Introduction to Code Signing](http://go.microsoft.com/fwlink/?LinkId=106296) (Introdução à assinatura de código).
O PowerShell dá suporte à validação de assinatura de código por meio de duas abordagens principais:

- Assinando arquivos de script
- Assinado um módulo por catálogo

A assinatura de arquivos do PowerShell é uma abordagem bem estabelecida para garantir que o código que está sendo executado foi produzido por uma fonte confiável e não foi modificado.
Os detalhes de como assinar arquivos de script do PowerShell são abordados no tópico [Sobre assinatura](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_signing).
Em geral, uma assinatura pode ser adicionada a qualquer arquivo .PS1 que o PowerShell validar quando o script for carregado.
O PowerShell pode ser restrito usando os cmdlets [Política de execução](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_execution_policies) para garantir o uso de scripts.

A assinatura de catálogo de módulo é um recurso que foi adicionado no PowerShell na versão 5.1.
Como assinar um módulo é abordado no tópico [Cmdlets de catálogo](https://msdn.microsoft.com/powershell/wmf/5.1/catalog-cmdlets).
Em geral, a assinatura do catálogo é feita criando um arquivo de catálogo que contenha um valor de hash para cada arquivo no módulo e, em seguida, assinando esse arquivo.
Os cmdlets publish-module, install-module, save-module e update-module do PowerShellGet verificarão a assinatura para garantir que ela seja válida e confirmarão se o valor de hash de cada item corresponde ao que está no catálogo.
Se uma versão anterior do módulo estiver instalada no sistema, install-module confirmará se autoridade de assinatura da nova versão coincide com a que já estava instalada.
A assinatura de catálogo funciona com os arquivos de script de assinatura, mas não os substitui. O PowerShell não valida as assinaturas de catálogo no tempo de carregamento do módulo.

## <a name="follow-semver-guidelines-for-versioning"></a>Siga as diretrizes de SemVer para controle de versão

[SemVer](http://semver.org/) é uma convenção pública que descreve como estruturar e alterar uma versão para permitir uma interpretação fácil das alterações.
A versão do item deve ser incluída nos dados de manifesto.

- A versão deve ser estruturada como 3 blocos numéricos separados por pontos, como em 0.1.1 ou 4.11.192
- Versões que começam com "0" indicam que o item ainda não está preparado para produção e o primeiro número somente deverá começar com "0" se esse for o único número usado
- As alterações no primeiro número (1.9.9999 para 2.0.0) indicam alterações impactantes e recentes entre as versões
- As alterações no segundo número (1.01 para 1.02) indicam alterações em nível de recurso, como a adição de novos cmdlets em um módulo
- As alterações no terceiro número indicam alterações não impactantes, como novos parâmetros, exemplos atualizados ou novos testes
- Ao listar versões, o PowerShell as classificará como cadeias de caracteres de modo que 1.01.0 seja tratado como maior que 1.001.0

O PowerShell foi criado antes da publicação do SemVer, portanto ele dá suporte para muitos elementos do SemVer, mas não para todos, especificamente:

- Ele não dá suporte para cadeias de caracteres de pré-versão em números de versão. Isso é útil quando um publicador deseja fornecer uma versão prévia de uma nova versão principal depois de fornecer uma versão 1.0.0. Isso terá suporte em uma versão futura da Galeria do PowerShell e dos cmdlets PowerShellGet.
- O PowerShell e a Galeria do PowerShell permitem cadeias de caracteres de versão com 1, 2 e 4 segmentos. Muitos módulos anteriores não seguiram as diretrizes e as versões de produto da Microsoft incluem as informações de build como um 4º bloco de números (por exemplo, 5.1.14393.1066). Do ponto de vista do controle de versão, essas diferenças são ignoradas.

## <a name="test-using-a-local-repository"></a>Teste usando um repositório local

A Galeria do PowerShell não foi projetada para ser um destino para testar o processo de publicação.
A melhor maneira de testar o processo de ponta a ponta de publicação na Galeria do PowerShell é configurar e usar seu próprio repositório local.
Isso pode ser feito de várias maneiras, incluindo:

- Configurar uma instância local da Galeria do PowerShell, usando o [projeto Galeria Privada do PS](https://github.com/PowerShell/PSPrivateGallery) no Github. Este projeto de visualização o ajudará a configurar uma instância da Galeria do PowerShell que você pode controlar e usar para seus testes.
- Configurar um [repositório interno do NuGet](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/). Essa opção dará mais trabalho para configurar, mas terá a vantagem de validar mais alguns dos requisitos, como, validar o uso de uma chave de API e se há ou não há dependências presentes no destino ao publicar.
- Configurar um compartilhamento de arquivos como o "repositório" do teste. Essa opção é fácil de configurar, mas como se trata de um compartilhamento de arquivos, as validações indicadas acima não ocorrerão. A vantagem dessa opção é que o compartilhamento de arquivos não verifica a chave de API (obrigatória), então você pode usar a mesma chave que usaria para publicar na Galeria do PowerShell.

Com qualquer uma dessas soluções, use Register-PSRepository para definir um novo "repositório", a ser usado na propriedade Repositório do Publish-Module.

Um ponto adicional sobre teste de publicação: os itens que você publicar na Galeria do PowerShell não poderão ser excluídos sem a ajuda da equipe de operações, que confirmará se não há nada dependente do item que você deseja publicar.
Por esse motivo, não damos suporte à Galeria do PowerShell como um destino de teste e contataremos qualquer publicador que fizer isso.

## <a name="use-powershellget-to-publish"></a>Usar o PowerShellGet para publicar

É altamente recomendável que os editores usem os cmdlets Publish-Module e Publish-Script ao trabalhar com a Galeria do PowerShell. O PowerShellGet foi criado para ajudar você a evitar lembrar-se de todos os detalhes importantes sobre como instalar de uma publicação na Galeria do PowerShell. Às vezes, os editores optaram por ignorar o PowerShellGet e usar o cliente do NuGet ou os cmdlets PackageManagement, em vez do Publish-Module. Há inúmeros detalhes que são facilmente perdidos, o que resulta em uma variedade de solicitações de suporte.

Se houver um motivo pelo qual você não possa usar Publish-Module ou Publish-Script, informe-nos. Registre um problema no repositório GitHub do PowerShellGet e forneça os detalhes que fazem você optar pelo NuGet ou PackageManagement. 

## <a name="recommended-workflow"></a>Fluxo de trabalho recomendado

A abordagem mais bem-sucedida que encontramos para itens publicados na Galeria do PowerShell é a seguinte:

- Faça o desenvolvimento inicial em um site de projeto de software livre. A equipe do PowerShell usa o Github.
- Use comentários de revisores e do [Powershell Script Analyzer](https://aka.ms/psscriptanalyzer) para levar o código ao estado estável
- Inclua a documentação, para que outras pessoas saibam como usar o seu trabalho
- Teste a ação de publicação usando um repositório local.
- Publique uma versão estável ou Alfa na Galeria do PowerShell, lembrando-se de incluir a documentação e o link para o site do projeto
- Colete comentários, itere o código no site do projeto e, em seguida, publique atualizações estáveis na Galeria do PowerShell
- Adicione exemplos e testes do Pester no projeto e no módulo
- Decida se deseja assinar o código do seu item
- Quando você achar que o projeto está pronto para ser usado em um ambiente de produção, publique uma versão 1.0.0 na Galeria do PowerShell
- Continue a coletar comentários e itere em seu código com base nas informações fornecidas pelos usuários

