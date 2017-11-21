---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Criando um pipeline de integração contínua e implantação contínua com DSC"
ms.openlocfilehash: baa56088d83fba56d3a19cff7954d3081f341f9a
ms.sourcegitcommit: 60c6f9d8cf316e6d5b285854e6e5641ac7648f3f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a>Criando um pipeline de integração contínua e implantação contínua com DSC

Este exemplo demonstra como criar um pipeline de CI/CD (implantação contínua/integração contínua) usando o PowerShell, a DSC, o Pester e o Visual Studio Team Foundation Server (TFS).

Depois que o pipeline é criado e configurado, você pode usá-lo para implantar, configurar e testar completamente um servidor DNS e os registros de host associados. Esse processo simula a primeira parte de um pipeline que seria usado em um ambiente de desenvolvimento.

Um pipeline de CI/CD automatizado ajuda a atualizar softwares com mais rapidez e confiança, garantir que todo o código seja testado e que um build atual do código esteja sempre disponível.

## <a name="prerequisites"></a>Pré-requisitos

Para usar este exemplo, você deve estar familiarizado com o seguinte:

- Os conceitos de CI-CD. Uma boa referência pode ser encontrada em [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf) (O modelo de pipeline de versão).
- O controle do código-fonte [Git](https://git-scm.com/)
- A estrutura de testes [Pester](https://github.com/pester/Pester)
- O [Team Foundation Server](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a>O que será necessário

Para compilar e executar esse exemplo, você precisará de um ambiente com vários computadores e/ou máquinas virtuais.

### <a name="client"></a>Remota

Este é o computador no qual você fará todo o trabalho de configurar e executar o exemplo.

O computador cliente deve ser um computador Windows com o seguinte instalado:
- [Git](https://git-scm.com/)
- um repositório git local clonado de https://github.com/PowerShell/Demo_CI
- um editor de texto, como o [Visual Studio Code](https://code.visualstudio.com/)

### <a name="tfssrv1"></a>TFSSrv1

O computador que hospeda o servidor do TFS no qual você definirá o build e a versão.
Este computador deve ter o [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) instalado.

### <a name="buildagent"></a>BuildAgent

O computador que executa o agente de build do Windows que compila o projeto.
Este computador deve ter um agente de build do Windows instalado e em execução.
Consulte [Deploy an agent on Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) (Implantar um agente no Windows ) para obter instruções de como instalar e executar um agente de build do Windows.

Você também precisa instalar os módulos de DSC `xDnsServer` e `xNetworking` nesse computador.

### <a name="testagent1"></a>TestAgent1

Este é o computador que está configurado como um servidor DNS pela configuração DSC neste exemplo.
O computador deve estar executando o [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

### <a name="testagent2"></a>TestAgent2

Este é o computador que hospeda o site, que este exemplo configura.
O computador deve estar executando o [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016). 

## <a name="add-the-code-to-tfs"></a>Adicione o código no TFS

Vamos começar criando um repositório Git no TFS e importando o código de seu repositório local no computador cliente.
Se você ainda não clonou o repositório Demo_CI no computador cliente, faça isso agora, executando o seguinte comando git:

`git clone https://github.com/PowerShell/Demo_CI`

1. No computador cliente, navegue até o servidor do TFS em um navegador da Web.
1. No TFS, [Crie um novo projeto de equipe](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) chamado Demo_CI.

    Verifique se o **Controle de versão** é definido como **Git**.
1. No computador cliente, adicione um remoto no repositório que você acabou de criar no TFS com o seguinte comando:

    `git remote add tfs <YourTFSRepoURL>`

    Em que `<YourTFSRepoURL>` é a URL clone para o repositório do TFS que você criou na etapa anterior.

    Se você não souber onde encontrar essa URL, consulte [Clone an existing Git repo](https://www.visualstudio.com/en-us/docs/git/tutorial/clone) (Clonar um repositório Git existente).
1. Envie o código por push de seu repositório local para o repositório do TFS com o seguinte comando:

    `git push tfs --all`
1. O repositório do TFS será preenchido com o código Demo_CI.

>**Observação:** este exemplo usa o código na ramificação `ci-cd-example` do repositório Git.
>Assegure-se de especificar essa ramificação como a ramificação padrão em seu projeto do TFS e para os gatilhos de CI/CD que você criar.

## <a name="understanding-the-code"></a>Noções básicas sobre o código

Antes de criar os pipelines de build e implantação, vamos analisar parte do código para entender o que está acontecendo.
No computador cliente, abra o editor de texto favorito e navegue até a raiz do repositório Git Demo_CI.

### <a name="the-dsc-configuration"></a>A configuração DSC

Abra o arquivo `DNSServer.ps1` (da raiz do repositório local Demo_CI, `./InfraDNS/Configs/DNSServer.ps1`).

Este arquivo contém a configuração DSC que configura o servidor DNS. Aqui está ele por inteiro:

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

Observe a instrução `Node`:

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

Isso localiza todos os nós que foram definidos como tendo uma função de `DNSServer` nos [dados de configuração](configData.md), que são criados pelo script `DevEnv.ps1`.

Usar dados de configuração para definir nós é importante ao fazer CI porque as informações do nó provavelmente serão alteradas entre os ambientes e usar dados de configuração permite fazer alterações facilmente nas informações do nó sem alterar o código de configuração.

No primeiro bloco de recurso, a configuração chama o [WindowsFeature](windowsFeatureResource.md) para garantir que o recurso DNS esteja habilitado. Os blocos de recurso que seguem chamam recursos do módulo [xDnsServer](https://github.com/PowerShell/xDnsServer) para configurar os registros DNS e a zona primária.

Observe que os dois blocos `xDnsRecord` são encapsulados em loops `foreach` que iteram em matrizes nos dados de configuração.
Novamente, os dados de configuração são criados pelo script `DevEnv.ps1`, o que veremos a seguir.

### <a name="configuration-data"></a>Dados de configuração

O arquivo `DevEnv.ps1` (da raiz do repositório local Demo_CI, `./InfraDNS/DevEnv.ps1`) especifica os dados de configuração específicos ao ambiente em uma tabela de hash e, em seguida, passa essa tabela de hash para uma chamada da função `New-DscConfigurationDataDocument`, que é definida em `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).

O arquivo `DevEnv.ps1`:

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

A função `New-DscConfigurationDataDocument` (definida em `\Assets\DscPipelineTools\DscPipelineTools.psm1`) cria programaticamente um documento de dados de configuração da tabela de hash (dados do nó) e da matriz (dados que não são do nó) que são passados como parâmetros `RawEnvData` e `OtherEnvData`.

Em nosso caso, somente o parâmetro `RawEnvData` é usado.

### <a name="the-psake-build-script"></a>O script de build psake

O script de build [psake](https://github.com/psake/psake) definido em `Build.ps1` (da raiz do repositório Demo_CI, `./InfraDNS/Build.ps1`) define as tarefas que fazem parte do build.
Ele também define de quais outras tarefas cada tarefa depende. Quando chamado, o script psake garante que a tarefa especificada (ou a tarefa chamada `Default` se não houver nenhuma especificada) seja executada e que todas as dependências também sejam executadas (isso é recursivo, para que as dependências das dependências sejam executadas e assim por diante).

Neste exemplo, a tarefa `Default` é definida como:

```powershell
Task Default -depends UnitTests
```

A tarefa `Default` não tem nenhuma implementação em si, mas tem uma dependência da tarefa `CompileConfigs`.
A cadeia de dependências de tarefa resultante garante que todas as tarefas no script de build sejam executadas.

Neste exemplo, o script psake é invocado por uma chamada para `Invoke-PSake` no arquivo `Initiate.ps1` (localizado na raiz do repositório Demo_CI):

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

Quando criarmos a definição de build para o nosso exemplo no TFS, forneceremos o arquivo de script psake como o parâmetro `fileName` para esse script.

O script de build define as seguintes tarefas:

#### <a name="generateenvironmentfiles"></a>GenerateEnvironmentFiles

Executa `DevEnv.ps1`, que gera o arquivo de dados de configuração.

#### <a name="installmodules"></a>InstallModules

Instala os módulos necessários para a configuração `DNSServer.ps1`.

#### <a name="scriptanalysis"></a>ScriptAnalysis

Chama o [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).

#### <a name="unittests"></a>UnitTests

Executa os testes de unidade do [Pester](https://github.com/pester/Pester/wiki).

#### <a name="compileconfigs"></a>CompileConfigs

Compila a configuração (`DNSServer.ps1`) em um arquivo MOF, usando os dados de configuração gerados pela tarefa `GenerateEnvironmentFiles`.

#### <a name="clean"></a>Clean

Cria as pastas usadas para o exemplo e remove todos os resultados do teste, os arquivos de dados de configuração e os módulos das execuções anteriores.

### <a name="the-psake-deploy-script"></a>O script de implantação psake

O script de implantação [psake](https://github.com/psake/psake) definido em `Deploy.ps1` (da raiz do repositório Demo_CI, `./InfraDNS/Deploy.ps1`) define as tarefas que implantam e executam a configuração.

`Deploy.ps1` define as seguintes tarefas:

#### <a name="deploymodules"></a>DeployModules

Inicia uma sessão do PowerShell no `TestAgent1` e instala os módulos que contêm os recursos de DSC necessários para a configuração.

#### <a name="deployconfigs"></a>DeployConfigs

Chama o cmdlet [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) para executar a configuração em `TestAgent1`.

#### <a name="integrationtests"></a>IntegrationTests

Executa os testes de integração do [Pester](https://github.com/pester/Pester/wiki).

#### <a name="acceptancetests"></a>AcceptanceTests

Executa os testes de aceitação do [Pester](https://github.com/pester/Pester/wiki).

#### <a name="clean"></a>Clean

Remove todos os módulos instalados nas execuções anteriores e verifica se a pasta de resultados do teste exista.

### <a name="test-scripts"></a>Scripts de teste

Os testes de unidade, integração e aceitação são definidos em scripts na pasta `Tests` (da raiz do repositório Demo_CI, `./InfraDNS/Tests`), cada um em arquivos denominados `DNSServer.tests.ps1` em suas respectivas pastas.

O teste de scripts usam as sintaxes [Pester](https://github.com/pester/Pester/wiki) e [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).

#### <a name="unit-tests"></a>Testes de unidade

Os testes de unidade testam as próprias configurações DSC para garantir que elas farão o que é esperado ao serem executadas.
O script de teste de unidade usa o [Pester](https://github.com/pester/Pester/wiki).

#### <a name="integration-tests"></a>Testes de integração

Os testes de integração testam a configuração do sistema para garantir que quando for integrado com outros componentes, o sistema esteja configurado como esperado. Esses testes são executados no nó de destino depois que ele foi configurado com DSC.
O script de teste de integração usa uma combinação da sintaxe [Pester](https://github.com/pester/Pester/wiki) e [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).

#### <a name="acceptance-tests"></a>Testes de aceitação

Os testes de aceitação testam o sistema para garantir que ele se comporte como esperado.
Por exemplo, ele testa para garantir que uma página da Web retorne as informações corretas quando consultada.
Esses testes são executados remotamente do nó de destino para testar os cenários reais.
O script de teste de integração usa uma combinação da sintaxe [Pester](https://github.com/pester/Pester/wiki) e [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).

## <a name="define-the-build"></a>Definir o build

Agora que já carregado o código para o TFS e examinamos o que ele faz, vamos definir o build.

Aqui, vamos abordar apenas as etapas de build que você adicionará ao build. Para obter instruções de como criar uma definição de build no TFS, consulte [Create and queue a build definition](https://www.visualstudio.com/en-us/docs/build/define/create) (Criar e enfileirar uma fila uma definição de build).

Crie uma nova definição de build (selecione o modelo **Vazio**) denominado "InfraDNS".
Adicione as seguintes etapas em sua definição de build:

- Script do PowerShell
- Publicar resultados de teste
- Copiar arquivos
- Publicar artefato

Depois de adicionar essas etapas de build, edite as propriedades de cada etapa da seguinte maneira:

### <a name="powershell-script"></a>Script do PowerShell

1. Defina a propriedade **Tipo** como `File Path`.
1. Defina a propriedade **Caminho de script** como `initiate.ps1`.
1. Adicione `-fileName build` na propriedade **Argumentos**.

Essa etapa de build executa o arquivo `initiate.ps1`, que chama o script de build psake.

### <a name="publish-test-results"></a>Publicar resultados de teste

1. Defina o **Formato de resultado do teste** para `NUnit`
1. Defina os **Arquivos de resultados de teste** para `InfraDNS/Tests/Results/*.xml`
1. Defina o **Título da execução de teste** para `Unit`.
1. Verifique se as **Opções de controle** **Habilitado** e **Sempre executar** estão selecionadas.

Essa etapa de build executa os testes de unidade no script Pester que vimos anteriormente e armazena os resultados na pasta `InfraDNS/Tests/Results/*.xml`.

### <a name="copy-files"></a>Copiar arquivos

1. Adicione cada uma das linhas a seguir em **Conteúdo**:

    ```
    initiate.ps1
    **\deploy.ps1
    **\Acceptance\**
    **\Integration\**
    ```

1. Defina **TargetFolder** para `$(Build.ArtifactStagingDirectory)\`

Esta etapa copia os scripts de build e de teste no diretório de preparo para que eles possam ser publicados como artefatos de build na próxima etapa.

### <a name="publish-artifact"></a>Publicar artefato

1. Defina o **Caminho para publicar** para `$(Build.ArtifactStagingDirectory)\`
1. Defina o **Nome do artefato** para `Deploy`
1. Defina o **Tipo de artefato** para `Server`
1. Selecione `Enabled` em **Opções de controle**

## <a name="enable-continuous-integration"></a>Habilitar integração contínua

Agora vamos definir um gatilho que faz com que o projeto seja compilado sempre que uma alteração for verificada na ramificação `ci-cd-example` do repositório git.

1. No TFS, clique na guia **Build e versão**
1. Selecione a definição de build `DNS Infra` e, em seguida, clique em **Editar**
1. Clique na guia **Gatilhos**
1. Selecione **CI (integração contínua)** e selecione `refs/heads/ci-cd-example` na lista suspensa da ramificação
1. Clique em **Salvar** e em **OK**

Agora qualquer alteração no repositório git do TFS vai disparar um build automatizado.

## <a name="create-the-release-definition"></a>Criar a definição de versão

Vamos criar uma definição de versão para que o projeto seja implantado no ambiente de desenvolvimento com cada verificação de código.

Para fazer isso, adicione uma nova definição de versão associada à definição de build `InfraDNS` que você criou anteriormente.
Assegure-se de selecionar **Implantação contínua** para que uma nova versão seja disparada sempre que um novo build for concluído.
[[How to: Work with release definitions](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions) (Instruções: trabalhar com definições de versão)] e configure da seguinte maneira:

Adicione as seguintes etapas na definição de versão:

- Script do PowerShell
- Publicar resultados de teste
- Publicar resultados de teste

Edite as etapas da seguinte maneira:

### <a name="powershell-script"></a>Script do PowerShell

1. Defina o campo **Caminho de script** para `$(Build.DefinitionName)\Deploy\initiate.ps1"`
1. Defina o campo **Argumentos** para `-fileName Deploy`

### <a name="first-publish-test-results"></a>Primeiro publicar resultados de teste

1. Selecione `NUnit` para o campo **Formato de resultado do teste**
1. Defina o campo **Arquivos de resultados do teste** para `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`
1. Defina o **Título da execução de teste** para `Integration`
1. Em **Opções de controle**, marque **Sempre executar**

### <a name="second-publish-test-results"></a>Segundo publicar resultados de teste

1. Selecione `NUnit` para o campo **Formato de resultado do teste**
1. Defina o campo **Arquivos de resultados do teste** para `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`
1. Defina o **Título da execução de teste** para `Acceptance`
1. Em **Opções de controle**, marque **Sempre executar**

## <a name="verify-your-results"></a>Verifique os resultados

Agora, sempre que você enviar alterações por push na ramificação `ci-cd-example` para o TFS, será iniciado um novo build.
Se o build for concluído com êxito, uma nova implantação será disparada.

Você pode verificar o resultado da implantação, abrindo um navegador no computador cliente e navegando para `www.contoso.com`.

## <a name="next-steps"></a>Próximas etapas

Este exemplo configura o servidor DNS `TestAgent1` para que a URL `www.contoso.com` seja resolvida para `TestAgent2`, mas na verdade isso não implanta um site.
O esqueleto para fazer isso é fornecido no repositório na pasta `WebApp`.
Você pode usar os stubs fornecidos para criar scripts psake, testes do Pester e configurações DSC para implantar seu próprio site.







