---
title: Glossário do Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b0f88cbe-cb83-4912-a301-184534cb35c7
---
# Glossário do Windows PowerShell


|Termo|Definição|
|--------|--------------|
|módulo binário|Um módulo do Windows PowerShell cuja raiz é um arquivo de módulo binário (.dll). Um módulo binário pode ou não incluir um manifesto de módulo.|
|parâmetro comum|Um parâmetro que é adicionado a todos os cmdlets e funções avançadas pelo mecanismo do Windows PowerShell.|
|dot source|No Windows PowerShell, iniciar um comando digitando um ponto e um espaço antes do comando. Comandos que são dot sourced são executados no escopo atual em vez de em um novo escopo. Quaisquer variáveis, aliases, funções ou unidades que o comando criar serão criadas no escopo atual e estarão disponíveis para os usuários quando o comando for concluído.|
|módulo dinâmico|Um módulo que existe apenas na memória. O cmdlet de Import-PSSession cria módulos dinâmicos.|
|parâmetro dinâmico|Um parâmetro que é adicionado a um cmdlet, função ou script do Windows PowerShell sob determinadas condições. Cmdlets, funções, provedores e scripts podem adicionar parâmetros dinâmicos.|
|arquivo de formatação|Um arquivo XML do Windows PowerShell que tem a extensão .format.ps1xml e que define como o Windows PowerShell exibe um objeto com base em seu tipo de .NET Framework.|
|estado de sessão global|O estado de sessão que contém os dados que são acessíveis para o usuário de uma sessão do Windows PowerShell.|
|host|A interface que o mecanismo do Windows PowerShell usa para se comunicar com o usuário. Por exemplo, o host especifica como os avisos são tratados entre o usuário e o Windows PowerShell.|
|aplicativo host|Um programa que carrega o mecanismo do Windows PowerShell em seu processo e o utiliza para executar operações.|
|método de processamento de entrada|Um método que um cmdlet pode usar para processar os registros que ele recebe como entrada. Os métodos de processamento de entrada incluem o método BeginProcessing, o método ProcessRecord, o método EndProcessing e o método StopProcessing.|
|módulo de manifesto|Um módulo do Windows PowerShell que tem um manifesto e cuja chave ModulesToProcess está vazia.|
|manifesto de módulo|Um arquivo de dados do Windows PowerShell (.psd1) que descreve o conteúdo de um módulo e que controla como um módulo é processado.|
|estado de sessão do módulo|O estado de sessão que contém os dados públicos e privados de um módulo do Windows PowerShell. Os dados privados nesse estado de sessão não estão disponíveis para o usuário de uma sessão do Windows PowerShell.|
|erro não fatal|Um erro não impede que o Windows PowerShell continue a processar o comando.|
|noun|A palavra que segue o hífen em um nome de cmdlet do Windows PowerShell. O substantivo descreve os recursos sobre os quais o cmdlet atua.|
|conjunto de parâmetros|Um grupo de parâmetros que podem ser usados no mesmo comando para executar uma ação específica.|
|pipe|No Windows PowerShell, enviar os resultados do comando anterior como entrada para o próximo comando no pipeline.|
|pipeline|Uma série de comandos conectados por operadores de pipeline (&#124;) (ASCII 124). Cada operador de pipeline envia os resultados do comando anterior como entrada para o próximo comando.|
|PSSession|Um tipo de sessão do Windows PowerShell que é criada, gerenciada e fechada pelo usuário.|
|módulo raiz|O módulo especificado na chave ModuleToProcess em um manifesto de módulo.|
|runspace|No Windows PowerShell, o ambiente operacional em que cada comando em um pipeline é executado.|
|bloco de script|Na linguagem de programação do Windows PowerShell, um conjunto de instruções ou expressões que podem ser usadas como uma única unidade. Um bloco de script pode aceitar argumentos e valores de retorno.|
|módulo de script|Um módulo do Windows PowerShell cuja raiz é um arquivo de módulo de script (.psm1). Um módulo de script pode ou não incluir um manifesto de módulo.|
|arquivo de módulo de script|Um arquivo que contém um script do Windows PowerShell. O script define os membros que exporta o módulo de script. Arquivos de módulo de script tem a extensão de nome de arquivo .psm1.|
|shell|O interpretador de comando que é usado para passar comandos para o sistema operacional.|
|parâmetro de opção|Um parâmetro que não têm um argumento.|
|erro fatal|Um erro que interrompe o processamento do comando do Windows PowerShell.|
|transação|Uma unidade atômica de trabalho. O trabalho em uma transação deve ser concluído como um todo; se qualquer parte da transação falhar, a transação inteira falhará.|
|arquivo de tipos|Um arquivo XML do Windows PowerShell que tem a extensão. ps1xml e que estende as propriedades de tipos do Microsoft .NET Framework para o Windows PowerShell.|
|verbo|A palavra que precede o hífen em um nome de cmdlet do Windows PowerShell. O verbo descreve a ação que o cmdlet executa.|
|Usando o Windows PowerShell|Um shell de linha de comando e uma tecnologia de script baseada em tarefa que fornece aos administradores de TI controle e automação abrangentes das tarefas de administração do sistema.|
|comando do Windows PowerShell|Os elementos em um pipeline que fazem uma ação ser realizada. Comandos do Windows PowerShell são digitados no teclado ou invocados programaticamente.|
|Arquivo de dados do Windows PowerShell|Um arquivo de texto que tem a extensão de nome de arquivo .psd1. O Windows PowerShell usa os arquivos de dados para várias finalidades como armazenar dados de manifesto de módulo e cadeias de caracteres traduzidas para a internacionalização de script.|
|Unidade do Windows PowerShell|Uma unidade virtual que fornece acesso direto a um armazenamento de dados. Ele pode ser definido por um provedor do Windows PowerShell ou criado na linha de comando. Unidades criadas na linha de comando são unidades de sessão específica e serão perdidas quando a sessão for fechada.|
|Ambiente de script integrado do Windows PowerShell (ISE)|Um aplicativo host do Windows PowerShell que permite executar comandos e gravar, testar e depurar scripts em um ambiente amigável, com sintaxe colorida e compatível com Unicode.|
|Módulo do Windows PowerShell|Uma unidade reutilizável autocontida que permite a partição, organizar e abstrair o código do Windows PowerShell. Um módulo pode conter cmdlets, provedores, funções, variáveis e outros tipos de recursos que podem ser importados como uma única unidade.|
|Provedor do Windows PowerShell|Um programa baseado no Microsoft .NET Framework que disponibiliza dados em um armazenamento de dados especializado no Windows PowerShell para que você possa vê-los e gerenciá-los facilmente.|
|Script do Windows PowerShell|Um script que está escrito na linguagem do Windows PowerShell.|
|Arquivo de script do Windows PowerShell|Um arquivo que tem a extensão .ps1 e que contém um script que está escrito na linguagem do Windows PowerShell.|
|snap-in do Windows PowerShell|Um recurso que define um conjunto de cmdlets, provedores e tipos de Microsoft .NET Framework que podem ser adicionados ao ambiente do Windows PowerShell.|
|Fluxo de trabalho do Windows PowerShell|Um fluxo de trabalho é uma sequência de etapas programadas e conectadas que executam tarefas de execução longa ou exigem a coordenação de várias etapas em vários dispositivos ou nós gerenciados. O fluxo de trabalho do Windows PowerShell permite que os desenvolvedores e profissionais de TI criem sequências de atividades de gerenciamento de vários dispositivos ou tarefas únicas dentro de um fluxo de trabalho, como fluxos de trabalho. O fluxo de trabalho do Windows PowerShell permite adaptar e executar ambos os scripts e arquivos XAML do Windows PowerShell como fluxos de trabalho.|



<!--HONumber=May16_HO2-->


