# <a name="microsoft-open-source-code-of-conduct"></a>Código de Conduta Aberto da Microsoft

Este projeto adotou o [Código de Conduta Aberto da Microsoft](https://opensource.microsoft.com/codeofconduct/).
Para saber mais, confira as [Perguntas Frequentes sobre o Código de Conduta](https://opensource.microsoft.com/codeofconduct/faq/) ou contate [opencode@microsoft.com](mailto:opencode@microsoft.com) com perguntas ou comentários adicionais.

[![Status do build](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)

## <a name="powershell-documentation"></a>Documentação do PowerShell

Bem-vindo ao repositório de documentos do PowerShell, que abriga a documentação oficial do PowerShell.

## <a name="repository-structure"></a>Estrutura do Repositório

Cada uma das seguintes pastas de nível superior neste repositório contém um DocSet publicado no [Microsoft Docs](https://docs.microsoft.com/powershell).

- [/developer/](https://docs.microsoft.com/powershell/developer/) é o futuro lar da documentação do SDK do PowerShell
  - Estamos em processo de migração deste conteúdo do MSDN
- [/dsc/](https://docs.microsoft.com/powershell/dsc/) é para o recurso de Configuração do Estado Desejado
- [/gallery/](https://docs.microsoft.com/powershell/gallery) é para a [Galeria do PowerShell](https://www.powershellgallery.com/)
- [/jea/](https://docs.microsoft.com/powershell/jea/) é para o recurso Administração Just Enough
- [/reference/](https://docs.microsoft.com/powershell/scripting/) é para os tópicos conceituais do PowerShell e a referência de módulo entre as versões 3.0, 4.0, 5.0, 5.1 e 6.0
  - Este conteúdo também é a origem do conteúdo da Ajuda recuperado pelo cmdlet `Get-Help`
- [/wmf](https://docs.microsoft.com/powershell/wmf/readme) contém notas de versão do Windows Management Framework, o pacote usado para distribuir novas versões do PowerShell para versões anteriores do Windows.

## <a name="contributing"></a>Contribuindo

Ativamente mesclamos contribuições neste repositório via [solicitação pull](https://help.github.com/articles/using-pull-requests/) para o branch de *preparo*.
Observe que antes de enviar uma solicitação pull, você deve [assinar um Contrato de Licença de Contribuição](https://cla.microsoft.com/) para garantir que a comunidade está livre para usar seus envios.

Saiba mais sobre como contribuir no [guia do colaborador](CONTRIBUTING.md).
Ele traz informações detalhadas sobre como contribuir com a documentação, ferramentas sugeridas e requisitos de formatação e estilo.
Use os modelos de Solicitação Pull e de Problemas para ajudar a manter a consistência da documentação em diferentes versões.

## <a name="licenses"></a>Licenças

Há dois arquivos de licença para este projeto.
A licença do MIT aplica-se ao código contido neste repositório.
A licença Creative Commons aplica-se à documentação.