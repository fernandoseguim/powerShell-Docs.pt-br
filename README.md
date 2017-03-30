## <a name="microsoft-open-source-code-of-conduct"></a>Código de Conduta Aberto da Microsoft

Este projeto adotou o [Código de Conduta Aberto da Microsoft](https://opensource.microsoft.com/codeofconduct/).
Para saber mais, confira as [Perguntas Frequentes sobre o Código de Conduta](https://opensource.microsoft.com/codeofconduct/faq/) ou contate [opencode@microsoft.com](mailto:opencode@microsoft.com) com perguntas ou comentários adicionais.

[![Status do build](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)

# <a name="powershell-documentation"></a>Documentação do PowerShell

Bem-vindo ao repositório de documentos do PowerShell, que hospeda a documentação oficial do Windows PowerShell. 

## <a name="repository-structure"></a>Estrutura do Repositório
Cada pasta neste repositório publica no [MSDN](https://msdn.microsoft.com/en-us/powershell). As pastas correspondem aos seguintes ativos do PowerShell:
* [/dsc/](https://msdn.microsoft.com/en-us/powershell/dsc/) é para o recurso de Configuração do Estado Desejado
* [/gallery/](https://msdn.microsoft.com/powershell/gallery) é para a [Galeria do PowerShell](https://www.powershellgallery.com/)
* [/jea/](https://msdn.microsoft.com/powershell/jea/) é para o recurso Administração Just Enough
* [/reference/](https://msdn.microsoft.com/powershell/reference/) é para a referência de módulo do PowerShell nas versões 2.0, 3.0, 4.0, 5.0, 5.1 e 6.0
  * Este conteúdo será recuperado pelo cmdlet `Get-Help` no futuro
* [/scripting/](https://msdn.microsoft.com/en-us/powershell/scripting/) é o conteúdo geral de referência do PowerShell
* [/wmf](https://msdn.microsoft.com/en-us/powershell/wmf/readme) contém notas de versão do Windows Management Framework, o pacote usado para distribuir novas versões do PowerShell para versões anteriores do Windows. 



## <a name="contributing"></a>Contribuindo

Ativamente mesclamos contribuições neste repositório via [solicitação pull](https://help.github.com/articles/using-pull-requests/) para o branch de *preparo*. Observe que antes de enviar uma solicitação pull, você deve [assinar um Contrato de Licença de Contribuição](https://cla.microsoft.com/) para garantir que a comunidade está livre para usar seus envios.
Para obter mais informações sobre a contribuição, leia nosso [guia de contribuições](CONTRIBUTING.md).
Há um rascunho de [guia de estilo](./style.md) que deve ser analisado antes de fazer contribuições.
Use os modelos de Solicitação Pull e de Problemas para ajudar a manter a consistência da documentação em diferentes versões. 
