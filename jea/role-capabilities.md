---
manager: carmonm
ms.topic: article
author: rpsqrd
ms.author: ryanpu
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-12-05
title: "Recursos de Função JEA"
ms.technology: powershell
ms.openlocfilehash: e67b38344e2d1d0d347c7850f2097e31c0945e15
ms.sourcegitcommit: b88151841dd44c8ee9296d0855d8b322cbf16076
translationtype: HT
---
# <a name="jea-role-capabilities"></a>Recursos de Função JEA

> Aplica-se a: Windows PowerShell 5.0

Ao criar um ponto de extremidade JEA, é necessário definir um ou mais "recursos de função" que descrevem *o que* alguém pode fazer em uma sessão JEA.
Uma capacidade de função é um arquivo de dados do PowerShell com a extensão .psrc que lista todos os cmdlets, as funções, os provedores e os programas externos que devem ser disponibilizados para usuários que estão se conectando.

Este tópico descreve como criar um arquivo da capacidade de função do PowerShell para seus usuários JEA.

## <a name="determine-which-commands-to-allow"></a>Determinar quais comandos permitir

A primeira etapa ao criar um arquivo de capacidade de função é considerar o que os usuários que recebem a função precisarão acessar.
Esse processo de coleta de requisitos pode levar algum tempo, mas é um processo muito importante.
Conceder aos usuários acesso a poucos cmdlets e funções pode impedi-los de cumprir suas tarefas.
Permitir o acesso a muitos cmdlets e funções pode resultar em usuários fazendo mais do que você pretendia com os privilégios implícitos de administrador, enfraquecendo a sua postura de segurança.

A maneira como você avança nesse processo dependerá da sua organização e dos objetivos, no entanto, as dicas a seguir podem ajudar a garantir que você esteja no caminho certo.

1. **Identificar** os comandos que os usuários estão usando para executar seus trabalhos. Isso pode envolver pesquisar a equipe de TI, verificar scripts de automação ou analisar transcrições ou logs de sessão do PowerShell.
2. **Atualizar** o uso de ferramentas de linha de comando para equivalentes do PowerShell, sempre que possível, para uma melhor experiência de auditoria e de personalização de JEA. Os programas externos não podem ser restritos de forma tão granular como os cmdlets e funções nativas do PowerShell no JEA.
3. **Restringir** o escopo dos cmdlets se necessário, para permitir apenas parâmetros ou valores de parâmetro específicos. Isso é particularmente importante se os usuários devem ser capazes de gerenciar apenas uma parte de um sistema.
4. **Criar** funções personalizadas para substituir comandos complexos ou comandos que são difíceis de restringir no JEA. Uma função simples que encapsula um comando complexo ou que aplica lógica de validação adicional pode oferecer controle adicional para administradores e simplicidade para usuários finais.
5. **Testar** a lista de escopo de comandos permitidos com seus usuários e/ou serviços de automação e ajustar conforme necessário.

É importante lembrar que os comandos em uma sessão JEA são geralmente executados com privilégios de administrador (ou elevados de outra maneira).
A seleção cuidadosa de comandos disponíveis é importante para garantir que o ponto de extremidade JEA não permita que o usuário que está se conectando eleve suas permissões.
Abaixo estão alguns exemplos de comandos que podem ser usados maliciosamente se forem permitidos em um estado sem restrições.
Observe que essa não é uma lista completa e só deve ser usada como um ponto de partida preventivo.

### <a name="examples-of-potentially-dangerous-commands"></a>Exemplos de comandos potencialmente perigosos

Risco | Exemplo | Comandos relacionados
-----|---------|-----------------
Concedendo privilégios de administrador ao usuário que está se conectando, para ignorar o JEA | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`
Execução de código arbitrário, como malware, explorações ou scripts personalizados para ignorar proteções | `Start-Process -FilePath '\\san\share\malware.exe'` | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`

## <a name="create-a-role-capability-file"></a>Criar um arquivo de capacidade de função

Você pode criar um novo arquivo de capacidade de função do PowerShell com o cmdlet [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile).

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

O arquivo de capacidade de função resultante pode ser aberto em um editor de texto e modificado para permitir os comandos desejados para a função.
A documentação de ajuda do PowerShell contém vários exemplos de como você pode configurar o arquivo.

### <a name="allowing-powershell-cmdlets-and-functions"></a>Permitir cmdlets e funções do PowerShell

Para autorizar usuários a executar funções ou cmdlets do PowerShell, adicione o nome do cmdlet ou da função nos campos VisbibleCmdlets ou VisibleFunctions.
Se você não tiver certeza se um comando é um cmdlet ou uma função, você poderá executar `Get-Command <name>` e verificar a propriedade "CommandType" na saída.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Às vezes, o escopo de um cmdlet ou de uma função específica é muito amplo para as necessidades dos usuários.
Um administrador de DNS, por exemplo, provavelmente só precisa de acesso para reiniciar o serviço DNS.
Em um ambiente de multilocatário em que os locatários recebem acesso a ferramentas de gerenciamento de autoatendimento, os locatários devem ser limitados ao gerenciamento com seus próprios recursos.
Nesses casos, você pode restringir quais parâmetros são expostos do cmdlet ou da função.

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

Em cenários mais avançados, também pode ser necessário restringir os valores que alguém pode fornecer a esses parâmetros.
Os recursos de função permitem que seja definido um conjunto de valores permitidos ou um padrão de expressão regular que é avaliado para determinar se uma determinada entrada é permitida.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> Os [parâmetros comuns do PowerShell](https://technet.microsoft.com/en-us/library/hh847884.aspx) são sempre permitidos, mesmo que você restrinja os parâmetros disponíveis.
> Você não deve listá-los explicitamente no campo Parâmetros.

A tabela a seguir descreve as várias maneiras que podem ser usadas para personalizar um cmdlet ou função visível.
Você pode misturar e combinar qualquer item abaixo no campo VisibleCmdlets.

Exemplo                                                                                      | Caso de uso
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
`'My-Func'` ou `@{ Name = 'My-Func' }`                                                       | Permite que o usuário execute `My-Func` sem quaisquer restrições nos parâmetros.
`'MyModule\My-Func'`                                                                         | Permite que o usuário execute `My-Func` do módulo `MyModule` sem quaisquer restrições nos parâmetros.
`'My-*'`                                                                                     | Permite que o usuário execute qualquer cmdlet ou função com o verbo `My`.
`'*-Func'`                                                                                   | Permite que o usuário execute qualquer cmdlet ou função com o substantivo `Func`.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | Permite que o usuário execute `My-Func` com os parâmetros `Param1` e/ou `Param2`. Qualquer valor pode ser fornecido para os parâmetros.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | Permite que o usuário execute `My-Func` com o parâmetro `Param1`. Somente "Value1" e "Value2" podem ser fornecidos ao parâmetro.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | Permite que o usuário execute `My-Func` com o parâmetro `Param1`. Qualquer valor começando com "contoso" pode ser fornecido ao parâmetro.


> [!WARNING]
> Como práticas recomendadas de segurança, não é recomendável usar curingas ao definir cmdlets ou funções visíveis.
> Em vez disso, você deve listar explicitamente cada comando confiável para garantir que outros comandos que compartilham o mesmo esquema de nomenclatura não sejam acidentalmente autorizados.

Você não pode aplicar um ValidatePattern e ValidateSet no mesmo cmdlet ou função.

Se isso acontecer, o ValidatePattern substituirá o ValidateSet.

Para obter mais informações sobre ValidatePattern, dê uma olhada [nessa postagem *Hey, Scripting Guy!*](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) e no conteúdo de referência [Expressões regulares do PowerShell](https://technet.microsoft.com/en-us/library/hh847880.aspx).

### <a name="allowing-external-commands-and-powershell-scripts"></a>Permitindo comandos externos e scripts do PowerShell

Para permitir que os usuários executem scripts do PowerShell (.ps1) e arquivos executáveis em uma sessão JEA, é necessário adicionar o caminho completo para cada programa no campo VisibleExternalCommands.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

É recomendável, sempre que possível, usar cmdlets ou funções do PowerShell equivalentes às dos arquivos externos executáveis que você autorizar, pois você tem controle sobre quais parâmetros são permitidos com cmdlets ou funções do PowerShell.

Muitos executáveis permitem que você leia o estado atual e, em seguida, altere-o simplesmente fornecendo parâmetros diferentes.

Por exemplo, considere a função de um administrador de servidor de arquivo que deseja verificar quais compartilhamentos de rede são hospedados pelo computador local.
Uma maneira de verificar é usar `net share`.
No entanto, permitir o net.exe é muito perigoso, pois o administrador poderia facilmente usar o comando para obter privilégios de administrador com `net group Administrators unprivilegedjeauser /add`.
Uma abordagem melhor é permitir o [Get-SmbShare](https://technet.microsoft.com/en-us/library/jj635704.aspx) que alcança o mesmo resultado, mas tem um escopo muito mais limitado.

Ao disponibilizar comandos externos aos usuários em uma sessão JEA, sempre especifique o caminho completo para o executável para garantir que um programa nomeado da mesma forma (e potencialmente mal-intencionado) colocado em outro lugar no sistema não seja executado em vez disso.

### <a name="allowing-access-to-powershell-providers"></a>Permitindo acesso aos provedores do PowerShell

Por padrão, nenhum provedor de PowerShell está disponível em sessões JEA.

Isso é, principalmente, para reduzir o risco da revelação de informações confidenciais e definições de configuração ao usuário que está se conectando.

Quando necessário, você pode permitir acesso aos provedores do PowerShell usando o comando `VisibleProviders`.
Para obter uma lista completa dos provedores, execute o `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

Para tarefas simples que exigem acesso ao sistema de arquivos, Registro, repositório de certificados ou outros provedores confidenciais, você também pode considerar escrever uma função personalizada que funcione com o provedor em nome do usuário.
Funções, cmdlets e programas externos que estão disponíveis em uma sessão JEA não estão sujeitos às mesmas restrições que o JEA. Eles podem acessar qualquer provedor por padrão.
Considere também usar a [unidade de usuário](session-configurations.md#user-drive) quando for necessário copiar arquivos para/de um ponto de extremidade JEA.

### <a name="creating-custom-functions"></a>Criando funções personalizadas

Você pode criar funções personalizadas em um arquivo de capacidade de função para simplificar tarefas complexas para os seus usuários finais.
As funções personalizadas também são úteis quando você precisar de lógica de validação avançada para valores de parâmetro de cmdlet.
É possível escrever funções simples no campo **FunctionDefinitions**:

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> Não se esqueça de adicionar o nome de suas funções personalizadas no campo **VisibleFunctions** para que elas possam ser executadas pelos usuários JEA.


O corpo (bloco de script) de funções personalizadas é executado no modo de idioma padrão do sistema e não está sujeito a restrições de linguagem do JEA.
Isso significa que as funções podem acessar o sistema de arquivos e o Registro e executar comandos que não foram tornados visíveis no arquivo de capacidade de função.
Tome cuidado para evitar a permissão de execução de códigos arbitrários ao usar parâmetros e evitar redirecionar a entrada do usuário diretamente em cmdlets como o `Invoke-Expression`.

No exemplo acima, você observará que o FQMN (nome do módulo totalmente qualificado) `Microsoft.PowerShell.Utility\Select-Object` foi usado em vez da abreviação `Select-Object`.
As funções definidas em arquivos de capacidade de função ainda estão sujeitas ao escopo das sessões JEA, que inclui as funções de proxy que o JEA cria para restringir os comandos existentes.

O Select-Object é um cmdlet padrão, restrito em todas as sessões JEA que não permite que você selecione propriedades arbitrárias em objetos.
Para usar o Select-Object irrestrito nas funções, você deve solicitar explicitamente a implementação completa, especificando o FQMN.
Qualquer cmdlet restrito em uma sessão JEA exibirá o mesmo comportamento ao ser invocado de uma função, em acordo com a [precedência de comando](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence) do PowerShell.

Se você estiver escrevendo muitas funções personalizadas, poderá ser mais fácil colocá-las em um [Módulo de Script do PowerShell](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).
Em seguida, você pode tornar essas funções visíveis na sessão JEA, usando o campo VisibleFunctions, assim como faria com módulos internos e de terceiros.

## <a name="place-role-capabilities-in-a-module"></a>Colocar recursos de função em um módulo

Para que o PowerShell localize um arquivo de capacidade de função, ele deve ser armazenado em uma pasta "RoleCapabilities" em um módulo do PowerShell.
O módulo pode ser armazenado em qualquer pasta incluída na variável de ambiente `$env:PSModulePath`, porém você não deve colocá-lo na System32 (reservada para módulos internos) ou uma pasta em que os usuários não confiáveis que estejam se conectando poderiam modificar os arquivos.
Abaixo está um exemplo de criação de um módulo de script do PowerShell básico chamado *ContosoJEA* no caminho "Arquivos de Programas".

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

Consulte [Noções básicas sobre um Módulo do PowerShell](https://msdn.microsoft.com/en-us/library/dd878324.aspx) para obter mais informações sobre módulos do PowerShell, manifestos de módulo e sobre a variável de ambiente PSModulePath.

## <a name="updating-role-capabilities"></a>Atualizando recursos de função


Você pode atualizar um arquivo de capacidade de função a qualquer momento, bastando salvar as alterações no arquivo de capacidade de função.
Qualquer nova sessão JEA iniciada depois que a capacidade de função foi atualizado refletirá os recursos revisados.

É por isso que é tão importante controlar o acesso à pasta de recursos de função.
Apenas administradores altamente confiáveis devem ser capazes de alterar os arquivos de capacidade de função.
Se um usuário não confiável puder alterar os arquivos de capacidade de função, poderá facilmente conceder a si próprio o acesso aos cmdlets que permitem que ele eleve seus privilégios.


Para os administradores que desejam bloquear o acesso às capacidades de função, verifique se a Sistema Local tem acesso de leitura aos arquivos de capacidade de função e aos módulos nesses arquivos.

## <a name="how-role-capabilities-are-merged"></a>Como os recursos de função são mesclados

Os usuários podem ter acesso a vários recursos de função quando ingressam em uma sessão JEA, dependendo dos mapeamentos de função no [arquivo de configuração de sessão](session-configurations.md).
Quando isso acontece, o JEA tenta conceder ao usuário o conjunto *mais permissivo* de comandos, permitido por qualquer uma das funções.

**VisibleCmdlets e VisibleFunctions**

A lógica mais complexa de mesclagem afeta cmdlets e funções, que podem ter seus parâmetros e valores de parâmetro limitados no JEA.

As regras são as seguintes:


1. Se um cmdlet só for visível em uma função, será visível para o usuário com qualquer restrição de parâmetro aplicável.
2. Se um cmdlet se torna visível em mais de uma função e cada função tem as mesmas restrições sobre o cmdlet, o cmdlet será visível para o usuário com essas restrições.
3. Se um cmdlet se torna visível em mais de uma função e cada função permite um conjunto diferente de parâmetros, o cmdlet e todos os parâmetros definidos em cada função serão visíveis ao usuário. Se uma função não tem restrições nos parâmetros, todos os parâmetros serão permitidos.
4. Se uma função define um conjunto de validação ou padrão de validação para um parâmetro de cmdlet e a outra função permite o parâmetro, mas não restringe os valores do parâmetro, o conjunto ou padrão de validação serão ignorados.
5. Se um conjunto de validação for definido para o mesmo parâmetro de cmdlet em mais de uma função, todos os valores de todos os conjuntos de validação serão permitidos.
6. Se um padrão de validação for definido para o mesmo parâmetro de cmdlet em mais de uma função, qualquer valor que corresponde a qualquer dos padrões será permitido.
7. Se um conjunto de validação for definido em uma ou mais funções e um padrão de validação for definido em outra função para o mesmo parâmetro de cmdlet, o conjunto de validação será ignorado e a regra (6) se aplica aos padrões de validação restantes.

A tabela a seguir mostra alguns exemplos dessa lógica na prática, usando duas funções A e B, que são atribuídas a um usuário em uma sessão JEA.

Regra | VisibleCmdlets da função A                                                                          | VisibleCmdlets da função B                                                                             | Permissões efetivas de usuário
-----|------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|----------------------------
1    | `Get-Service`                                                                                  | N/D                                                                                               | `Get-Service`
1    | N/D                                                                                            | `Get-Service`                                                                                     | `Get-Service`
2    | `Get-Service`                                                                                  | `Get-Service`                                                                                     | `Get-Service`
3    | `@{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName' }}`                             | `Get-Service`                                                                                     | `Get-Service`
3    | `@{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName' }}`                             | `@{ Name = 'Get-Service'; Parameters = @{ Name = 'Name' }}`                                       | `@{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName' }, @{ Name = 'Name' }}`
4    | `@{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' }}` | `@{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName' }}`                                | `@{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName' }}`
5    | `@{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' }}` | `@{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DHCP Client' }}`   | `@{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DHCP Client' }}`
6    | `@{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' }}`  | `@{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'contoso.*' }}` | `@{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = '(DNS.*)\|(contoso.*)' }}`
7    | `@{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' }}` | `@{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'contoso.*' }}` | `@{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = '(DNS.*)\|(contoso.*)' }}`



**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**

Todos os outros campos no arquivo de capacidade de função são simplesmente adicionados a um conjunto cumulativo de comandos externos permitidos, aliases, provedores e scripts de inicialização.
Qualquer comando, alias, provedor ou script disponível em um capacidade de função estará disponível para o usuário JEA.

Verifique com cuidado se o conjunto combinado de provedores de um capacidade de função e funções/cmdlets/comandos de outro recurso de função não permitem aos usuários que estão se conectando o acesso involuntário aos recursos do sistema.
Por exemplo, se uma função permite o cmdlet `Remove-Item` e outra função permite o provedor `FileSystem`, haverá um risco de um usuário JEA excluir arquivos arbitrários no seu computador.
Informações adicionais sobre como identificar as permissões efetivas dos usuários podem ser encontradas no [tópico auditoria do JEA](audit-and-report.md).

## <a name="next-steps"></a>Próximas etapas

- [Criar um arquivo de configuração de sessão](session-configurations.md)