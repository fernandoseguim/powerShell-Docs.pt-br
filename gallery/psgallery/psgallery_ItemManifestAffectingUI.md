# <a name="item-manifest-values-that-impact-the-powershell-gallery-ui"></a>Valores de manifesto de itens que afetam a interface do usuário da Galeria do PowerShell

Este tópico fornece um resumo informativo aos editores sobre como modificar o manifesto das publicações na Galeria do PowerShell a fim de alterar os recursos de cmdlets PowerShellGet e da interface do usuário da Galeria do PowerShell.
Este conteúdo está organizado de acordo com o local onde as alterações serão exibidas, começando pela seção central até a área de navegação à esquerda. Há uma seção Detalhes que aborda as marcas, identifica as marcas importantes, bem como algumas das marcas usadas com mais frequência.
Há dois tópicos que fornecem exemplos de manifesto:

* No caso dos módulos, confira o artigo [Atualizar o manifesto de módulo](https://docs.microsoft.com/powershell/gallery/psget/module/psget_update-modulemanifest)
* No caso dos scripts, confira o artigo [Cria um arquivo de script com metadados](https://docs.microsoft.com/powershell/gallery/psget/script/psget_new-scriptfileinfo)

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>Elementos de recurso da Galeria do PowerShell controlados pelo manifesto

A tabela a seguir mostra os elementos da interface do usuário da página do item da Galeria do PowerShell, que são controlados pelo editor.
Cada item indica se pode ser controlado pelo manifesto de módulo ou de script.

| Elemento da interface do usuário | Descrição | Módulo | script |
| --- | --- | --- | --- |
| **Título** | Este é o nome do item publicado na Galeria  | Não | Não |
| **Versão** | A versão exibida representa a cadeia de caracteres da versão nos metadados e um pré-lançamento, se for especificado. A parte principal da versão em um manifesto de módulo é a ModuleVersion. No caso de um script, ela é identificada como .VERSION. Se a cadeia de caracteres da versão de um pré-lançamento for especificada, ela será adicionada à ModuleVersion nos módulos ou especificada como parte da .VERSION nos scripts. Veja a documentação sobre como especificar cadeias de caracteres de pré-lançamento em [módulos](https://docs.microsoft.com/en-us/powershell/gallery/psget/module/prereleasemodule) e [scripts](https://docs.microsoft.com/en-us/powershell/gallery/psget/script/prereleasescript) | Sim | Sim |
| **Descrição** | Esta é a descrição do manifesto de módulo. No manifesto do arquivo de script será .DESCRIPTION | Sim | Sim |
| **Exigir a aceitação da licença** | Um módulo pode exigir que o usuário aceite uma licença, modificando o respectivo manifesto com RequireLicenseAcceptance = $true, fornecendo um LicenseURI e um arquivo license.txt na raiz da pasta do módulo. Saiba mais no tópico [Exigir a aceitação da licença](https://docs.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_requires_license_acceptance). | Sim | Não |
| **Notas de versão** | No caso dos módulos, esta informação é extraída da seção ReleaseNotes, em PSData\PrivateData. Nos manifestos de script, representa o elemento .RELEASENOTES. | Sim | Sim |
| **Proprietários** | Os proprietários representam a lista de usuários que podem atualizar itens na Galeria do PowerShell. A lista de proprietários não está incluída no manifesto do item. A documentação adicional descreve como [gerenciar proprietários do item](https://docs.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners). | Não | Não |
| **Autor** | Está incluído no manifesto de módulo como Autor e em um manifesto de script como .AUTHOR. O campo Autor é usado geralmente para especificar uma empresa ou organização associada a um item. | Sim | Sim |
| **Direitos autorais** | Este é o campo Direitos autorais no manifesto de módulo e .COPYRIGHT em um manifesto de script. | Sim | Sim |
| **FileList** | A lista de arquivos é extraída do pacote quando ele é publicado na Galeria do PowerShell. Ela não é controlada pelas informações do manifesto. Observação: há um arquivo .nuspec adicional relacionado a cada item na Galeria do PowerShell, que fica ausente após a instalação do item no sistema. Este é o manifesto do Pacote Nuget do item e pode ser ignorado. | Não | Não |
| **Marcas** | Nos módulos, as Marcas estão incluídas em PSData\PrivateData. Nos scripts, a seção é rotulada como .TAGS. Observe que as marcas não podem conter espaços, mesmo quando estão entre aspas. Elas têm significados e requisitos adicionais que são descritos mais adiante neste artigo, na seção Detalhes da marca. | Sim | Sim |
| **Cmdlets** | São fornecidos no manifesto de módulo com CmdletsToExport. Observe que a prática recomendada consiste em relacionar explicitamente os itens, em vez de usar o curinga "*", a fim de melhorar o desempenho do módulo de carga para os usuários. | Sim | Não |
| **Funções** | São fornecidas no manifesto de módulo com FunctionsToExport. Observe que a prática recomendada consiste em relacionar explicitamente os itens, em vez de usar o curinga "*", a fim de melhorar o desempenho do módulo de carga para os usuários. | Sim | Não |
| **Recursos de DSC** | No caso dos módulos que serão usados no PowerShell 5.0 ou superior, são fornecidos no manifesto com DscResourcesToExport. Se o módulo for usado no PowerShell 4, DSCResourcesToExport não deverá ser usada, por não se tratar de uma Chave de Manifesto compatível. (A DSC não era disponibilizada antes do PowerShell 4.) | Sim | Não |
| **Fluxos de trabalho** | Os fluxos de trabalho são publicados na Galeria do PowerShell como scripts e identificados como fluxos de trabalho (confira [Connect-AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1) para obter um exemplo) no código. Eles não são controlados pelo manifesto. | Não | Não |
| **Recursos de função** | São relacionados quando o módulo publicado na Galeria do PowerShell contém um ou mais arquivos de recurso de função (.psrc), que são usados pelo JEA. Confira a documentação do JEA para saber mais sobre [recursos de função](https://docs.microsoft.com/en-us/powershell/jea/role-capabilities). | Sim | Não |
| **Edições do PowerShell** | São especificadas no manifesto de módulo ou de script. No caso dos módulos projetados para uso com o PowerShell 5.0 ou posterior, elas são controladas com marcas. Para o Desktop, use a marca PSEdition_Desktop. No caso do núcleo, use a marca PSEdition_Core. Para os módulos que serão usados apenas no PowerShell 5.1 ou superior, há uma chave CompatiblePSEditions no manifesto principal. Para obter mais detalhes, veja o recurso PS Edition na [documentação do PowerShell Get](https://docs.microsoft.com/en-us/powershell/gallery/psget/module/modulewithpseditionsupport). | Sim | Sim |
| **Dependências** | As dependências representam os módulos na Galeria do PowerShell. Elas são declaradas no módulo como RequiredModules ou no manifesto de script como #Requires –Module (nome). | Sim | Sim |
| **Versão mínima do Powershell** | Pode ser especificada em um manifesto de módulo como PowerShellVersion | Sim | Não |
| **Histórico de versão** | O histórico de versão representa as atualizações feitas em um módulo na Galeria do PowerShell. Quando a versão de um item é ocultada com o recurso Excluir, ela não é exibida no histórico de versão, exceto para os proprietários do item. | Não | Não |
| **Site do Projeto** | O site do projeto é fornecido para os módulos na seção Privatedata\PSData do manifesto de módulo, especificando um ProjectURI. No manifesto de script, ele é controlado pela especificação .PROJECTURI. | Sim | Sim |
| **Licença** | O link da licença é fornecido para os módulos na seção Privatedata\PSData do manifesto de módulo, especificando uma propriedade LicenseURI. No manifesto de script, ele é controlado pela especificação .LICENSEURI. É importante observar que, quando uma licença não é fornecida por meio de uma propriedade LicenseURI ou dentro de um módulo, os termos de uso da Galeria do PowerShell especificam os termos de uso do item. Confira os termos de uso para saber mais. | Sim | Sim |

## <a name="editing-item-details"></a>Edição de detalhes do item

A página Editar item, na Galeria do PowerShell, permite aos editores alterar vários campos exibidos de um item, especificamente:

* Título
* Descrição
* Resumo
* URL do ícone
* URL da página inicial do projeto
* Autores
* Direitos autorais
* Marcas
* Notas de versão
* Exigir licença

Geralmente, esta abordagem não é recomendável, exceto quando é necessário corrigir o conteúdo exibido na versão anterior de um módulo.
Os usuários que adquirem o módulo podem observar que os metadados não correspondem ao conteúdo exibido na Galeria do PowerShell, causando preocupações em relação ao item.
Isso gera consultas frequentes aos proprietários do item a fim de confirmar as alterações.
É altamente recomendável publicar uma nova versão do item com as mesmas alterações, sempre que usar esta abordagem.

## <a name="tag-details"></a>Detalhes das marcas

As marcas são cadeias de caracteres simples que os consumidores usam para localizar itens.
Elas são mais eficientes quando usadas regularmente em vários itens relacionados ao mesmo tópico. O uso de variações de um mesmo termo (por exemplo banco de dados e bancos de dados ou teste e testes) normalmente traz poucos benefícios.
As marcas são cadeias de caracteres de palavras únicas que não diferenciam maiúsculas e minúsculas e não podem incluir espaços. Se você acredita que os usuários vão pesquisar uma determinada frase, adicione-a à descrição do item para que ela seja encontrada nos resultados da pesquisa. Use o padrão Pascal Case, hífen, sublinhado ou ponto, se quiser melhorar a legibilidade. Cuidado quando criar marcas diferentes, longas e complexas, pois às vezes você poderá escrevê-las de forma incorreta.

É importante observar certas marcas, pois a Galeria do PowerShell e os cmdlets PowerShellGet tratam elas de forma exclusiva. PSEdition_Desktop e PSEdition_Core são exemplos específicos descritos anteriormente.

Conforme observado acima, as marcas são mais eficientes quando são específicas e usadas regularmente em vários itens.
Quando o editor tenta localizar as marcas ideais que pretende usar, a abordagem mais fácil consiste em pesquisá-las na Galeria do PowerShell.
O ideal é que vários itens sejam retornados e que a descrição do item corresponda ao uso da palavra-chave.

Como referência, aqui estão algumas das marcas mais usadas até 14/12/2017.
Em alguns casos, há opções parecidas, mas talvez menos ideais ao lado da marca.
É prática recomendada usar as marcas preferenciais, já que elas resultam em menos correspondências difusas e geram melhores resultados de pesquisa para os usuários.


| **Marca preferencial** | **Alternativas e observações** |
| --- | --- |
| **Azure** |  |
| **DSC** | DesiredStateConfiguration é menos recomendado, pois é muito longo |
| **ResourceManager** | "ARM" é usado para descrever um grupo de processadores e não deve ser usado para o Azure Resource Manager | **DSCResourceKit** |  |
| **SQL** |  |
| **AWS** |  |
| **DSCResource** |  |
| **Automation** |  |
| **REST** |  |
| **ActiveDirectory** | "AD" por si só não está em uso no momento  |
| **SQLServer** |  |
| **DBA** |  |
| **Segurança** | "Defense" é menos preciso |
| **Database** | "Databases" (plural) é menos recomendado |
| **DevOps** |  |
| **Windows** |  |
| **Build** |  |
| **Deployment** | "Deploy" é usado com menos frequência |
| **Cloud** |  |
| **GIT** |  |
| **Test** | "Testing" é menos recomendado |
| **VersionControl** | "Version" é menos preciso, embora seja usado com mais frequência  |
| **Logging** | Recomendamos usar "Logging" como uma ação |
| **Log** | Recomendamos usar "Log" como um objeto |
| **Backup** |  |
| **IaaS** |  |
| **Linux** |  |
| **IIS** |  |
| **AzureAutomation** |  |
| **Storage** |  |
| **GitHub** |  |
| **Json** |  |
| **Exchange** |  |
| **Network** | "Networking" é semelhante, porém usado com menos frequência |
| **SharePoint** |  |
| **Reporting** | "Reporting" é uma ação e "Report" é um objeto |
| **Report** | "Report" é um objeto |
| **WinRM** |  |
| **Monitoring** |  |
| **VSTS** |  |
| **Excel** |  |
| **Google** |  |
| **Color** |  |
| **DNS** |  |
| **Office365** | Recomendamos usar "Office" sem abreviação. Embora seja mais curto, "O365" é usado com menos frequência | **Gitlab** |  |
| **Pester** |  |
| **AzureAD** |  |
| **HTML** |  |
| **Hyper-V** | "HyperV" é menos comum como marca |
| **Configuration** |  |
| **ChatOps** |  |
| **PackageManagement** |  |
| **WMI** |  |
| **Firewall** |  |
| **Docker** |  |
| **Appveyor** |  |
| **AzureRm** | Usado principalmente nos módulos do AzureRM |
| **Zip** |  |
| **MSI** |  |
| **Mac** |  |
| **PoshBot** |  |