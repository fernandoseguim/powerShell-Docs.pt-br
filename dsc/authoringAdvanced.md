# <a name="advanced-dsc-authoring-for-composition-and-collaboration"></a>DSC avançada de criação para composição e colaboração

Este artigo descreve os tipos de abordagens disponíveis para combinar configurações e recursos.
A meta para cada cenário é a mesma, para reduzir a complexidade quando várias configurações são preferíveis para acessar o estado final de implantação de um servidor.
Um exemplo disso seria várias equipes que contribuem para o resultado de uma implantação de servidor, como um proprietário de aplicativo que mantém o estado do aplicativo e uma equipe central liberar alterações em linhas de base de segurança.
As nuances de cada abordagem, incluindo benefícios e riscos, são descritas aqui.

![Pipeline](images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a>Tipos de técnicas de criação colaborativa

Há duas soluções internas no Configuration Manager Local para habilitar esse conceito:

| Conceito | Informações detalhadas
|-|-
| Configurações Parciais | [Documentação](partialconfigs.md)
| Recursos de composição | [Documentação](authoringresourcecomposite.md)

## <a name="understanding-the-impact-of-each-approach"></a>Noções básicas sobre o impacto de cada abordagem

Qualquer uma dessas soluções pode ser usada para gerenciar o resultado de uma implantação de servidor.
No entanto, há uma diferença significativa no impacto do uso de cada abordagem.

## <a name="partial-configurations"></a>Configurações Parciais

Ao usar Configurações Parciais, o Configuration Manager Local é configurado para gerenciar várias configurações de forma independente.
As configurações são compiladas de forma independente e, em seguida, são atribuídas ao nó.
Isso exige que o LCM seja configurado com antecedência com o nome de cada configuração.

![PartialConfiguration](images/PartialConfiguration.jpg)

As Configurações Parciais oferecem controle completo sobre a configuração de um servidor a duas ou mais equipes, geralmente sem o benefício da comunicação ou da colaboração.

Segundo os clientes, isso pode levar a conflitos de recursos, substituições não intencionais e, por fim, perda de controle da configuração do ativo.

Além disso, comentaram que ao usar esse modelo, é improvável que as alterações em cada configuração feita pelas equipes de controle sejam completamente testadas em um pipeline de lançamento, o que gera resultados inesperados na produção.

**É essencial que um único pipeline seja usado para avaliar o lançamento de todas as alterações nos servidores.**

Na ilustração abaixo, a Equipe B libera a configuração parcial para a Equipe A. Em seguida, a Equipe A executa seus testes em um servidor com ambas as configurações aplicadas.
Nesse modelo, somente uma autoridade tem permissão para fazer alterações na produção.

![PartialSinglePipeline](images/PartialSinglePipeline.jpg)

Quando a Equipe B requisitar alterações, ela deverá enviar uma solicitação de pull para o ambiente de controle do código-fonte da Equipe A.
Depois, a Equipe A examinará as alterações usando a automação de teste e liberará para a produção quando estiver certa de que as alterações não gerarão erros nos aplicativos ou serviços hospedados pelo servidor.

## <a name="composite-resources"></a>Recursos de composição

Um recurso de composição é simplesmente uma configuração de DSC empacotada como um recurso.
Não há nenhum requisito especial para configurar o LCM para aceitar os recursos de composição.
Os recursos são usados dentro de uma nova configuração e uma única compilação resulta em um arquivo MOF.

![CompositeResource](images/CompositeResource.jpg)

Há dois cenários comuns para recursos de composição.
O primeiro é reduzir a complexidade e os conceitos abstratos únicos.
O segundo é permitir que as linhas de base sejam empacotadas para uma equipe do aplicativo implantar com segurança por meio do pipeline de lançamento para produção após todos os testes serem aprovados.

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

Os recursos de composição promovem a composição e a colaboração usando um pipeline durante a criação de maturidade operacional

Você já pode estar usando recursos de composição sem perceber.
Um exemplo é **ServiceSet**.
Esse recurso gerencia o estado dos vários serviços do Windows sem listá-los individualmente.
A propriedade Name aceita uma matriz de cadeias de caracteres para fornecer o nome de cada serviço.
Quando a configuração for compilada, o MOF conterá uma seção de Serviço exclusiva para cada um dos nomes passados para ServiceSet.

As organizações podem ter "agentes" ou "middleware" que devem ser instalados em todos os servidores.
Um recurso de composição é a melhor resposta para gerenciar as dependências, a instalação e a configuração de tais ferramentas e utilitários.

A pessoa ou a equipe responsável por soluções que abrangem vários servidores cria uma configuração que contém seus requisitos.
Em seguida, a configuração seria empacotada como um recurso de composição usando as instruções fornecidas na documentação do recurso de composição.
Por fim, o novo recurso de composição deve ser publicado em um local como um compartilhamento de arquivos ou feed do NuGet em que as equipes de aplicativo possam consumi-lo em suas configurações.

Toda vez que a equipe libera uma nova versão, o número de versão é aumentado no manifesto do módulo do recurso de composição.
As equipes de aplicativo incluem o recurso de composição na configuração que criam para gerenciar as dependências de aplicativo.
Quando as equipes de Operações/Segurança liberam uma nova versão do recurso, elas notificam as equipes de aplicativo sobre a nova alteração.

As equipes de aplicativo podem disparar uma versão para produção em que a única alteração é nas linhas de base.
No entanto, isso cria uma oportunidade de avaliar o impacto nos aplicativos antes do risco de uma interrupção de serviço.

Observação: nos comentários sobre o uso de recursos de composição, houve críticas sobre a necessidade de compilar e liberar um novo MOF ao fazer alterações.
Isso ocorre por design.
Cada nova versão de configuração deve incluir uma referência estática a uma versão específica de cada recurso e ser validada por testes antes de chegar aos nós de servidor de produção.
O processo de teste e liberação de alterações do controle do código-fonte cria um ambiente seguro para liberar alterações em lotes pequenos, mas frequentes.

Para saber mais sobre como usar pipelines de lançamento para gerenciar a infraestrutura de núcleo, confira o white paper: [O modelo de pipeline de lançamento](http://aka.ms/thereleasepipelinemodel).
