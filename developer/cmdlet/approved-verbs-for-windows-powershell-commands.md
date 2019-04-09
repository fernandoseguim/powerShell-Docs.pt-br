---
title: Os verbos aprovados para comandos do PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- action names [PowerShell SDK]
- verb names [PowerShell SDK]
- cmdlets [PowerShell SDK], verb names
ms.assetid: 2d4e58a9-05bc-437c-86b9-d8d55cba7d48
caps.latest.revision: 36
ms.openlocfilehash: 4475b3f5e15826efbe8bab867011985cd7e2e1ae
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293343"
---
# <a name="approved-verbs-for-powershell-commands"></a>Verbos aprovados para comandos do PowerShell

PowerShell usa um par verbo-substantivo para nomes de cmdlets e suas classes derivadas de Microsoft .NET Framework.
Por exemplo, o `Get-Command` cmdlet fornecido pelo PowerShell é usado para recuperar todos os comandos que estão registrados no PowerShell.
A parte de verbo do nome identifica a ação que executa o cmdlet.
A parte do substantivo do nome identifica a entidade na qual a ação é executada.

> [!NOTE]
> O PowerShell usa o termo *verbo* para descrever uma palavra que implica uma ação, mesmo se essa palavra não é um verbo padrão no idioma inglês.
> Por exemplo, o termo *New* é um nome válido de verbo do PowerShell, porque ele implica uma ação, mesmo que não seja um verbo no idioma inglês.

## <a name="verb-naming-rules"></a>Regras de nomenclatura de verbo

A lista a seguir fornece diretrizes a serem consideradas quando você escolhe o verbo para um nome de cmdlet:

* Quando você especifica o verbo, é recomendável que você use um dos verbos predefinidos para nomes fornecidos pelo PowerShell (aliases para esses verbos predefinidos estão incluídos nas tabelas a seguir).
  Quando você usa um verbo predefinido, você garante a consistência entre os cmdlets que você cria, os cmdlets que são fornecidos pelo PowerShell e os cmdlets que são criados por outras pessoas.

* Usar os verbos predefinidos para descrever o escopo geral da ação e usar os parâmetros para refinar ainda mais a ação do cmdlet.

* Para impor a consistência entre os cmdlets, não use um sinônimo de um verbo aprovado.

* Use apenas o formulário de cada verbo listado neste tópico.
  Por exemplo, use "Get", mas não use "Introdução" ou "Obtém".

* Use o casing Pascal casing para verbos.
  Em Pascal casing a letra inicial de cada palavra está em maiusculas, como "ForEach".

* Não use os seguintes verbos reservados ou alias.
  Esses verbos são usados pela linguagem PowerShell, ou pelos cmdlets de casos especiais fornecidos pelo PowerShell.
  - ForEach (foreach)
  - Formato (f)
  - Grupo (gp)
  - Classificação (sr)
  - TEE (te)
  - Onde (o que é)

## <a name="similar-verbs-for-different-actions"></a>Verbos semelhantes para diferentes ações

Os seguintes verbos semelhantes representam ações diferentes.

### <a name="new-vs-set"></a>Nova vs. Set
O `New` verbo é usado para criar um novo recurso.
O `Set` verbo é usado para modificar um recurso existente, opcionalmente criando o recurso se ele não existir, tal como o `Set-Variable` cmdlet.

### <a name="find-vs-search"></a>Encontre vs. Pesquisar
O `Find` verbo é usado para procurar por um objeto.
O `Search` verbo é usado para criar uma referência a um recurso em um contêiner.

### <a name="get-vs-read"></a>Obtenha vs. Leitura
O `Get` verbo é usado para recuperar um recurso, como um arquivo.
O `Read` verbo é usado para obter informações de uma fonte, como um arquivo.

### <a name="invoke-vs-start"></a>Invocar vs. Inicie o
O `Invoke` verbo é usado para executar uma operação que geralmente é uma operação síncrona, como a execução de um comando.
O `Start` verbo é usado para iniciar uma operação que geralmente é uma operação assíncrona, por exemplo, iniciar um processo.

### <a name="ping-vs-test"></a>Ping vs. Teste
Use o `Test` verbo.

## <a name="common-verbs"></a>Common Verbs

O PowerShell usa o [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) classe de enumeração para definir ações genéricas que podem ser aplicadas a praticamente qualquer cmdlet.
A tabela a seguir lista a maioria dos verbos definidos.

|Verbo (alias)|Ação|Comentários|
|--------------------|------------|--------------|
|[Adicionar](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|Adiciona um recurso para um contêiner ou anexa um item para outro item. Por exemplo, o `Add-Content` cmdlet adiciona o conteúdo em um arquivo. Esse verbo é emparelhado com `Remove`.|Para esta ação, não use verbos como concatenar de acréscimo, anexar, ou inserir.|
|[Limpar](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (cl)|Remove todos os recursos de um contêiner, mas não exclui o contêiner. Por exemplo, o `Clear-Content` cmdlet Remove o conteúdo de um arquivo, mas não exclui o arquivo.|Para esta ação, não use verbos como Flush, apagar, versão, desmarcar, Unset ou Nullify.|
|[Fechar](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (cs)|Altera o estado de um recurso para torná-la inacessível, indisponível ou inutilizável. Esse verbo é emparelhado com `Open.`||
|[Cópia](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (cp)|Copia um recurso para outro nome ou em outro contêiner. Por exemplo, o `Copy-Item` cmdlet é usado para acessar dados armazenados copia um item de um local no armazenamento de dados para outro local.|Para esta ação, não use verbos como duplicata, Clone, replicação ou sincronização.|
|[Enter](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (et)|Especifica uma ação que permite ao usuário para serem movidas para um recurso. Por exemplo, o `Enter-PSSession` cmdlet coloca o usuário em uma sessão interativa. Esse verbo é emparelhado com `Exit`.|Para esta ação, não use verbos como o envio por Push ou no.|
|[Saída](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (ex)|Define o ambiente atual ou o contexto para o contexto usado mais recentemente. Por exemplo, o `Exit-PSSession` cmdlet coloca o usuário na sessão que foi usada para iniciar a sessão interativa. Esse verbo é emparelhado com `Enter`.|Para esta ação, não use verbos como Pop ou Check-Out.|
|[Localizar](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (fd)|Procura um objeto em um contêiner que é desconhecido, implícita, opcional ou especificado.||
|[Formato](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f)|Organiza objetos em um formulário especificado ou o layout.||
|[Obter](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|Especifica uma ação que recupera um recurso. Esse verbo é emparelhado com `Set`.|Para esta ação, não use verbos como leitura, abrir, Cat, tipo, Dir, obter, despejo de memória, aquisição, Examine, localizar ou pesquisa.|
|[Ocultar](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|Faz com que um recurso não puder ser detectada. Por exemplo, um cmdlet cujo nome inclui o verbo de ocultar pode ocultar um serviço de um usuário. Esse verbo é emparelhado com `Show`.|Para esta ação, não use um verbo, como o bloco.|
|[Junte-se](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|Combina os recursos em um recurso. Por exemplo, o `Join-Path` cmdlet combina um caminho com um dos seus caminhos de filho para criar um único caminho. Esse verbo é emparelhado com `Split`.|Para esta ação, não use verbos como combinar, Unite, conectar ou associar.|
|[Bloqueio](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (lk)|Protege um recurso. Esse verbo é emparelhado com `Unlock`.|Para esta ação, não use verbos como restringir ou seguro.|
|[Move](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|Move um recurso de um local para outro. Por exemplo, o `Move-Item` cmdlet Move um item de um local no armazenamento de dados para outro local.|Para esta ação, não use verbos como transferência, o nome ou as migrações.|
|[Novo](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|Cria um recurso. (O `Set` verbo também pode ser usado ao criar um recurso que inclui dados, como o `Set-Variable` cmdlet.)|Para esta ação, não use verbos como criar, gerar, compilação, verifique ou alocar.|
|[Abra](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (op)|Altera o estado de um recurso para torná-lo utilizável, disponível ou acessível. Esse verbo é emparelhado com `Close`.||
|[Otimizar](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (om)|Aumenta a eficácia de um recurso.||
|[Pop-up](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|Remove um item da parte superior de uma pilha. Por exemplo, o `Pop-Location` cmdlet altera o local atual para o local que foi mais recentemente inserido na pilha.||
|[Enviar por push](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (pu)|Adiciona um item na parte superior de uma pilha. Por exemplo, o `Push-Location` cmdlet envia o local atual para a pilha.||
|[Redo](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (re)|Redefine um recurso para o estado que foi desfeito.||
|[Remover](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|Exclui um recurso de um contêiner. Por exemplo, o `Remove-Variable` cmdlet exclui uma variável e seu valor. Esse verbo é emparelhado com `Add`.|Para esta ação, não use esses verbos tão clara, recortar, Dispose, descarte ou apagar.|
|[Renomear](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (rn)|Altera o nome de um recurso. Por exemplo, o `Rename-Item` cmdlet, que é usado para acessar dados armazenados, altera o nome de um item no armazenamento de dados.|Para esta ação, não use um verbo, como a alteração.|
|[Redefinir](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (rs)|Define um recurso de volta ao estado original.||
|[Pesquisa](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (sr)|Cria uma referência a um recurso em um contêiner.|Para esta ação, não use verbos como localizar ou localizar.|
|[Selecione](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (sc)|Localiza um recurso em um contêiner. Por exemplo, o `Select-String` cmdlet localiza texto em arquivos e cadeias de caracteres.|Para esta ação, não use verbos como localizar ou localizar.|
|[Definir](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|Substitui os dados em um recurso existente ou cria um recurso que contém alguns dados. Por exemplo, o `Set-Date` cmdlet altera a hora do sistema no computador local. (O `New` verbo também pode ser usado para criar um recurso.) Esse verbo é emparelhado com `Get`.|Para esta ação, não use verbos como gravação, a redefinição, atribuir ou configurar.|
|[Mostrar](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (sh)|Um recurso torna visíveis para o usuário. Esse verbo é emparelhado com `Hide`.|Para esta ação, não use verbos como exibição ou produzir.|
|[Ignorar](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (sk)|Ignora um ou mais recursos ou pontos em uma sequência.|Para esta ação, não use um verbo, como ignorar ou salto.|
|[Divisão](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (sl)|Separa as partes de um recurso. Por exemplo, o `Split-Path` cmdlet retorna diferentes partes de um caminho. Esse verbo é emparelhado com `Join`.|Para esta ação, não use um verbo tal separado.|
|[Etapa](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (st)|Move para o próximo ponto ou recurso em uma sequência.||
|[Comutador](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (sw)|Especifica uma ação que alterna entre dois recursos, como alterar entre dois locais, responsabilidades ou estados.||
|[Desfazer](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (DES)|Define um recurso ao seu estado anterior.||
|[Desbloquear](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (Reino Unido)|Libera um recurso que foi bloqueado. Esse verbo é emparelhado com `Lock`.|Para esta ação, não use verbos como versão, Unrestrict ou não seguro.|
|[Assista](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (wc)|Continuamente inspeciona ou monitora um recurso para que as alterações.||

## <a name="communications-verbs"></a>Verbos de comunicações

O PowerShell usa o [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) classe para definir ações que se aplicam a comunicações.
A tabela a seguir lista a maioria dos verbos definidos.

|Verbo (alias)|Ação|Comentários|
|--------------------|------------|--------------|
|[Conectar-se](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (cc)|Cria um link entre uma origem e um destino. Esse verbo é emparelhado com `Disconnect`.|Para esta ação, não use verbos como Join ou Telnet.|
|[Desconectar](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (dc)|Interrompe o link entre uma origem e um destino. Esse verbo é emparelhado com `Connect`.|Para esta ação, não use verbos como quebra ou Logoff.|
|[Leitura](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (rd)|Obtém informações de uma fonte. Esse verbo é emparelhado com `Write`.|Para esta ação, não use verbos como aquisição, solicitar ou obter.|
|[Receber](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (rc)|Aceita as informações enviadas de uma fonte. Esse verbo é emparelhado com `Send`.|Para esta ação, não use verbos como leitura, Accept, ou inspecionar.|
|[Enviar](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (sd)|Fornece informações para um destino. Esse verbo é emparelhado com `Receive`.|Para esta ação, não use verbos como Put, difusão, email ou Fax.|
|[Gravar](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (wr)|Adiciona informações para um destino. Esse verbo é emparelhado com `Read`.|Para esta ação, não use verbos como Put ou impressão.|

## <a name="data-verbs"></a>Verbos de dados

O PowerShell usa o [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData) classe para definir as ações que se aplicam a manipulação de dados.
A tabela a seguir lista a maioria dos verbos definidos.

|Nome do verbo (alias)|Ação|Comentários|
|-------------------------|------------|--------------|
|[Backup](/dotnet/api/System.Management.Automation.VerbsData.Backup) (ba)|Armazena dados por replicação.|Para esta ação, não use verbos como salvar Burn, replicação ou sincronização.|
|[Ponto de verificação](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (ch)|Cria um instantâneo do estado atual dos dados ou de sua configuração.|Para esta ação, não use um verbo, como comparação.|
|[Comparar](/dotnet/api/System.Management.Automation.VerbsData.Compare) (cr)|Avalia os dados de um recurso com os dados de outro recurso.|Para esta ação, não use um verbo, como comparação.|
|[Compactar](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|Compacta os dados de um recurso. Pares com `Expand`.|Para esta ação, não use um verbo, como CD.|
|[Converter](/dotnet/api/System.Management.Automation.VerbsData.Convert) (VC)|Altera os dados de uma representação para outra quando o cmdlet oferece suporte à conversão bidirecional ou quando o cmdlet oferece suporte à conversão entre vários tipos de dados.|Para esta ação, não use verbos como alteração, redimensionamento, ou criar nova amostra.|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (cf)|Converte um tipo de principal de entrada (o substantivo do cmdlet indica que a entrada) em um ou mais tipos de saída com suporte.|Para esta ação, não use verbos como Out, saída ou exportação.|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (ct)|Converte de um ou mais tipos de entrada para um tipo de saída primária (o substantivo do cmdlet indica o tipo de saída).|Para esta ação, não use verbos como importação, de entrada, ou no.|
|[Desmontar](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (dm)|Desconecta uma entidade nomeada de um local. Esse verbo é emparelhado com `Mount`.|Para esta ação, não use verbos como desmontar ou desvincular.|
|[Editar](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ed)|Modifica os dados existentes adicionando ou removendo o conteúdo.|Para esta ação, não use verbos como alteração, atualizar ou modificar.|
|[Expanda](/dotnet/api/System.Management.Automation.VerbsData.Expand) (em inglês)|Restaura os dados de um recurso que foram compactado para seu estado original. Esse verbo é emparelhado com `Compress`.|Para esta ação, não use verbos como detalhar ou descompactar.|
|[Exportar](/dotnet/api/System.Management.Automation.VerbsData.Export) (ep)|Encapsula a entrada principal em um repositório de dados persistentes, como um arquivo, ou em um formato de intercâmbio. Esse verbo é emparelhado com `Import`.|Para esta ação, não use verbos como Backup ou de extração.|
|[Grupo](/dotnet/api/System.Management.Automation.VerbsData.Group) (gp)|Organiza ou associa um ou mais recursos.|Para esta ação, não use verbos como agregação, organizar, associe ou correlacionar.|
|[Importação](/dotnet/api/System.Management.Automation.VerbsData.Import) (ip)|Cria um recurso de dados que são armazenados em um armazenamento de dados persistentes (como um arquivo) ou em um formato de intercâmbio. Por exemplo, o `Import-CSV` cmdlet importa dados de um arquivo de valores separados por vírgulas (CSV) para objetos que podem ser usados por outros cmdlets. Esse verbo é emparelhado com `Export`.|Para esta ação, não use verbos como carregamento em massa ou carga.|
|[Inicializar](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (in)|Prepara um recurso para uso e define-o para um estado padrão.|Para esta ação, não use verbos como apagamento, Init, Renew, recompilação, reinicializar ou instalação.|
|[Limite de](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|Aplica-se as restrições a um recurso.|Para esta ação, não use um verbo, como a cota.|
|[Mesclar](/dotnet/api/System.Management.Automation.VerbsData.Merge) (GM)|Cria um único recurso de vários recursos.|Para esta ação, não use verbos como combinar ou junção.|
|[Montar](/dotnet/api/System.Management.Automation.VerbsData.Mount) (mt)|Anexa uma entidade nomeada em um local. Esse verbo é emparelhado com `Dismount`.|Para esta ação, não use o verbo Connect.|
|[Out](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|Envia dados para fora do ambiente. Por exemplo, o `Out-Printer` cmdlet envia dados para uma impressora.||
|[Publicar](/dotnet/api/System.Management.Automation.VerbsData.Publish) (pb)|Disponibiliza um recurso para outras pessoas. Esse verbo é emparelhado com `Unpublish`.|Para esta ação, não use verbos como implantar, versão, ou instalar.|
|[Restaurar](/dotnet/api/System.Management.Automation.VerbsData.Restore) (rr)|Define um recurso para um estado predefinido, como um estado definido pela `Checkpoint`. Por exemplo, o `Restore-Computer` cmdlet inicia uma restauração do sistema no computador local.|Para esta ação, não use verbos como reparo, Return, desfazer ou correção.|
|[Salvar](/dotnet/api/System.Management.Automation.VerbsData.Save) (VA)|Preserva os dados para evitar a perda.||
|[Sincronização](/dotnet/api/System.Management.Automation.VerbsData.Sync) (sy)|Garante que duas ou mais recursos estão no mesmo estado.|Para esta ação, não use verbos como Replicate, retornos, ou corresponder.|
|[Cancelar a publicação](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) (ub)|Faz com que um recurso não está disponível para outras pessoas. Esse verbo é emparelhado com `Publish`.|Para esta ação, não use verbos como desinstalar, reverter, ou ocultar.|
|[Atualização](/dotnet/api/System.Management.Automation.VerbsData.Update) (ud)|Coloca um recurso atualizado para manter seu estado, exatidão, conformidade ou conformidade. Por exemplo, o `Update-FormatData` cmdlet atualiza e adiciona os arquivos de formatação para o console atual do PowerShell.|Para esta ação, não use verbos como atualização, Renew, recalcular ou reindexar.|

## <a name="diagnostic-verbs"></a>Verbos de diagnóstico

O PowerShell usa o [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) classe para definir ações que se aplicam ao diagnóstico.
A tabela a seguir lista a maioria dos verbos definidos.

|Verbo (alias)|Ação|Comentários|
|--------------------|------------|--------------|
|[Depurar](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (db)|Examina um recurso para diagnosticar problemas operacionais.|Para esta ação, não use um verbo como diagnosticar.|
|[Medida](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (ms)|Identifica os recursos que são consumidos por uma operação especificada ou recupera as estatísticas sobre um recurso.|Para esta ação, não use verbos como Calculate, Determine ou analisar.|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (pi)|Use o `Test` verbo.||
|[Repair](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (rp)|Restaura um recurso a uma condição utilizável|Para esta ação, não use verbos como correção ou restauração.|
|[Resolve](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (rv)|Mapeia uma representação de forma abreviada de um recurso para uma representação mais completa.|Para esta ação, não use verbos como expansão ou determinar.|
|[Teste](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|Verifica a consistência de um recurso ou operação.|Para esta ação, não use verbos como analisar, diagnosticar, recuperação ou verificar.|
|[Rastreamento](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (tr)|Rastreia as atividades de um recurso.|Para esta ação, não use verbos como faixa, seguem, inspecionar, ou se aprofundar.|

## <a name="lifecycle-verbs"></a>Verbos de ciclo de vida

O PowerShell usa o [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) classe para definir a ações que se aplicam ao ciclo de vida de um recurso.
A tabela a seguir lista a maioria dos verbos definidos.

|Verbo (alias)|Ação|Comentários|
|--------------------|------------|--------------|
|[Aprovar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (ap)|Confirma ou concorda com o status de um recurso ou processo.||
|[Assert](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (como)|Informa o estado de um recurso.|Para esta ação, não use um verbo, como o Certify.|
|[Compilar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (bd)|Cria um artefato (geralmente um binário ou documento) fora de um conjunto de arquivos de entrada (normalmente, o código-fonte ou documentos declarativos)|Esse verbo foi adicionado no PowerShell v6|
|[Completa](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (cp)|Conclui uma operação.||
|[Confirmar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (cn)|Reconhece, verifica ou valida o estado de um recurso ou processo.|Para esta ação, não use verbos como confirmação, concordo, Certify, validar ou verificar.|
|[Negar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (dn)|Se recusa, objetos, bloqueia ou se opõe o estado de um recurso ou processo.|Para esta ação, não use verbos como bloco, objeto, recusar ou rejeitar.|
|[Implantar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (dp)|Envia um aplicativo, um site ou uma solução para um destino remoto [s] de tal forma que um consumidor dessa solução pode acessá-lo após a conclusão da implantação|Esse verbo foi adicionado no PowerShell v6|
|[Desabilitar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|Configura um recurso para um estado inativo ou não está disponível. Por exemplo, o `Disable-PSBreakpoint` cmdlet faz um ponto de interrupção inativo. Esse verbo é emparelhado com `Enable`.|Para esta ação, não use verbos como interromper ou ocultar.|
|[Habilitar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|Configura um recurso para um estado disponível ou Active Directory. Por exemplo, o `Enable-PSBreakpoint` cmdlet ativa um ponto de interrupção. Esse verbo é emparelhado com `Disable`.|Para esta ação, não use verbos como iniciar ou Begin.|
|[Instalar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (é)|Coloca um recurso em um local e, opcionalmente, inicializa-lo. Esse verbo é emparelhado com `Uninstall`.|Para esta ação, fazer não um verbo de uso, como a instalação.|
|[Invoke](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|Executa uma ação, como a execução de um comando ou um método.|Para esta ação, não use verbos como execução ou iniciar.|
|[Registrar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (rg)|Cria uma entrada para um recurso em um repositório, como um banco de dados. Esse verbo é emparelhado com `Unregister`.||
|[Solicitar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (rq)|Solicita um recurso ou solicita permissões.||
|[Reiniciar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (rt)|Interrompe uma operação e, em seguida, inicia-lo novamente. Por exemplo, o `Restart-Service` cmdlet interrompe e inicia um serviço.|Para esta ação, não use um verbo, como reciclagem.|
|[Resume](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (ru)|Inicia uma operação que foi suspenso. Por exemplo, o `Resume-Service` cmdlet inicia um serviço que foi suspenso. Esse verbo é emparelhado com `Suspend`.||
|[Iniciar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (sa)|Inicia uma operação. Por exemplo, o `Start-Service` cmdlet inicia um serviço. Esse verbo é emparelhado com `Stop`.|Para esta ação, não use verbos como iniciar, iniciar ou inicialização.|
|[Parar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (sp)|Interrompe uma atividade. Esse verbo é emparelhado com `Start`.|Para esta ação, não use verbos como final, Kill, encerrar ou Cancelar.|
|[Enviar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (sb)|Apresenta um recurso para aprovação.|Para esta ação, não use um verbo como Post.|
|[Suspender](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (ss)|Pausa uma atividade. Por exemplo, o `Suspend-Service` cmdlet pausa um serviço. Esse verbo é emparelhado com `Resume`.|Para esta ação, não use um verbo como pausar.|
|[Desinstalar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (us)|Remove um recurso de um local indicado. Esse verbo é emparelhado com `Install`.||
|[Cancelar o registro](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (sua)|Remove a entrada para um recurso de um repositório. Esse verbo é emparelhado com `Register`.|Para esta ação, não use um verbo, como remover.|
|[Aguarde](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|Pausa uma operação até que ocorra um evento especificado. Por exemplo, o `Wait-Job` cmdlet pausa operações até que um ou mais dos trabalhos de plano de fundo forem concluídas.|Para esta ação, não use verbos como suspensão ou pausa.|

## <a name="security-verbs"></a>Verbos de segurança

O PowerShell usa o [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) classe para definir ações que se aplicam à segurança.
A tabela a seguir lista a maioria dos verbos definidos.

|Verbo (alias)|Ação|Comentários|
|--------------------|------------|--------------|
|[Bloco](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (bl)|Restringe o acesso a um recurso. Esse verbo é emparelhado com `Unblock`.|Para esta ação, não use verbos como impedir, limite ou negar.|
|[Grant](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (gr)|Permite o acesso a um recurso. Esse verbo é emparelhado com `Revoke`.|Para esta ação, não use verbos como permitir ou habilitar.|
|[Proteger](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (pt)|Protege um recurso de ataque ou perda. Esse verbo é emparelhado com `Unprotect`.|Para esta ação, não use verbos como criptografar, proteger ou lacre.|
|[Revoke](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (rk)|Especifica uma ação que não permite acesso a um recurso. Esse verbo é emparelhado com `Grant`.|Para esta ação, não use verbos como remover ou desabilitar.|
|[Desbloquear](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (ul)|Remove as restrições a um recurso. Esse verbo é emparelhado com `Block`.|Para esta ação, não use verbos como Clear ou permitir.|
|[Unprotect](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (up)|Remove as garantias de um recurso que foram adicionados para impedir a perda ou de ataque. Esse verbo é emparelhado com `Protect`.|Para esta ação, não use verbos como descriptografar ou Unseal.|

## <a name="other-verbs"></a>Outros verbos

O PowerShell usa o [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) classe para definir os nomes de verbos canônico que não cabem em uma categoria de nome do verbo específico como comum, comunicações, dados, do ciclo de vida, ou nomes de verbos de segurança verbos.

|Verbo (alias)|Ação|Comentários|
|--------------------|------------|--------------|
|[Use](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|Usa ou inclui um recurso para fazer algo.||

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

[System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

[System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

[System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

[System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

[Declaração de cmdlet](./cmdlet-class-declaration.md)

[Guia do programador do Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md)

[Shell do Windows PowerShell do SDK](../windows-powershell-reference.md)
