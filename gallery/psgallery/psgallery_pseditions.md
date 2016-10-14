# Itens com edições compatíveis do PowerShell
Da versão 5.1 em diante, o PowerShell está disponível nas edições diferentes que denotam diferentes conjuntos de recursos e compatibilidade de plataforma.

- **Desktop Edition:** criada no .NET Framework e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell em execução em edições de superfície completa do Windows, como Server Core e Área de Trabalho do Windows.
- **Core Edition:** criada no .NET Core e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell executando em edições de superfície reduzida do Windows, como o Nano Server e Windows IoT.

## A Galeria do PowerShell extrai metadados de PSEditions com suporte e permite filtrar itens compatíveis para edições específicas do PowerShell

Se um item tiver PSEditions compatíveis especificadas, elas serão listadas como parte das "Edições do PowerShell" na página de exibição de item e nos resultados de itens.
![Página de exibição do item com PSEditions](Images/ItemDisplayPageWithPSEditions.PNG)

## Pesquise por itens na interface do usuário da Galeria que funcionem no PowerShellCore
Use as marcas: "PSEdition_Desktop" e "PSEdition_Core" para filtrar os itens na Galeria do PowerShell.

### Use as marcas: "PSEdition_Core" para pesquisar itens compatíveis com o PowerShell Core Edition.
![Resultados da pesquisa para itens compatíveis com o Core PSEdition](Images/SearchResultsWithPSEditions.PNG)

### Use as marcas: "PSEdition_Desktop" para pesquisar itens compatíveis com o PowerShell Desktop Edition.
![Resultados da pesquisa para itens compatíveis com o Desktop PSEdition](Images/SearchResultsWithPSEdition_Desktop.PNG)

## Mais detalhes sobre como criar e localizar os itens com as edições compatíveis do PowerShell
### [Módulos com PSEditions](../psget/module/modulewithpseditionsupport.md)
### [Scripts com PSEditions](../psget/script/scriptwithpseditionsupport.md)

<!--HONumber=Aug16_HO3-->


