---
ms.date: 05/17/2018
keywords: powershell,core
title: Problemas conhecidos do PowerShell 6.0
ms.openlocfilehash: 6ad1bcaf1de06f204b57eb8ce23b3053ba4a5b38
ms.sourcegitcommit: 2d9cf1ccb9a653db7726a408ebcb65530dcb1522
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2018
ms.locfileid: "34309597"
---
# <a name="known-issues-for-powershell-60"></a>Problemas conhecidos do PowerShell 6.0

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a>Problemas conhecidos do PowerShell em plataformas diferentes do Windows

As versões alfa do PowerShell no Linux e no macOS são em grande parte funcionais, mas têm limitações consideráveis e problemas de uso. As versões beta do PowerShell no Linux e no macOS são mais funcionais e estáveis do que as versões alfa, mas ainda carecem de alguns recursos e podem conter bugs. Em alguns casos, esses problemas são simplesmente bugs ainda não corrigidos. Em outros casos (como acontece com os aliases padrão para ls, cp etc)., queremos comentários da comunidade sobre as escolhas que fazemos.

Observação: devido a semelhanças dos vários subsistemas subjacentes, o PowerShell no Linux e no macOS tendem a compartilhar o mesmo nível de maturidade com relação a recursos e bugs. Com exceção do que será indicado abaixo, os problemas nesta seção se aplicam aos dois sistemas operacionais.

### <a name="case-sensitivity-in-powershell"></a>Diferenciação de maiúsculas e minúsculas no PowerShell

Historicamente, o PowerShell nunca diferenciou maiúsculas de minúsculas, com algumas exceções. Em sistemas operacionais do tipo UNIX, o sistema de arquivos é predominantemente indiferente a maiúsculas e minúsculas, e o PowerShell segue o padrão do sistema de arquivos. Isso é exposto de várias maneiras, óbvias e não óbvias.

#### <a name="directly"></a>Diretamente

- Ao especificar um arquivo no PowerShell, a capitalização correta deve ser usada.

#### <a name="indirectly"></a>Indiretamente

- Se um script tentar carregar um módulo, e o nome do módulo não estiver com as maiúsculas e minúsculas corretas, o carregamento do módulo falhará. Isso pode causar um problema com os scripts existentes, se o nome pelo qual o módulo é chamado não corresponder ao nome real do arquivo.
- O preenchimento com Tab não ocorrerá automaticamente se a capitalização do nome do arquivo estiver incorreta. O fragmento para preenchimento deve ter a capitalização correta. O preenchimento não diferencia maiúsculas de minúsculas para o nome do tipo e conclusões de membro do tipo.

### <a name="ps1-file-extensions"></a>Extensões de arquivo .PS1

Os scripts do PowerShell devem terminar em `.ps1` para o interpretador entender como carregar e executá-los no processo atual. A execução de scripts no processo atual é o comportamento normal esperado para o PowerShell. O número mágico `#!` pode ser adicionado a um script que não tem uma extensão `.ps1`, mas isso fará com que o script seja executado em uma nova instância do PowerShell, impedindo que o script funcione corretamente ao trocar objetos. Observação: esse pode ser o comportamento desejável ao executar um script do PowerShell do `bash` ou outro shell.

### <a name="missing-command-aliases"></a>Aliases de comando ausentes

No Linux/macOS, os "aliases de conveniência" para os comandos básicos `ls`, `cp`, `mv`, `rm`, `cat`, `man`, `mount`, `ps` foram removidos. No Windows, o PowerShell fornece um conjunto de aliases mapeados para nomes de comando do Linux para conveniência do usuário. Esses aliases foram removidos do PowerShell padrão em distribuições Linux/macOS, permitindo a execução do executável nativo sem especificar um caminho.

Há vantagens e desvantagens nisso. A remoção dos aliases expõe a experiência do comando nativo ao usuário do PowerShell, mas reduz a funcionalidade no shell, pois os comandos nativos retornam cadeias de caracteres em vez de objetos.

> [!NOTE]
> Essa é uma área sobre a qual a equipe do PowerShell está procurando comentários.
> Qual é a solução preferida? Devemos deixar como está ou adicionar novamente os aliases de conveniência? Consulte a [Edição #929](https://github.com/PowerShell/PowerShell/issues/929).

### <a name="missing-wildcard-globbing-support"></a>Falta o suporte ao recurso de curinga

No momento, o PowerShell só faz expansão de curinga (recurso de curinga) para cmdlets internos do Windows, e para comandos externos ou binários, bem como os cmdlets no Linux. Isso significa que um comando como `ls
*.txt` falhará devido à falta de expansão do asterisco para corresponder aos nomes de arquivo. Você pode contornar esse problema fazendo `ls (gci *.txt | % name)` ou, simplificando, `gci *.txt` usando o equivalente interno do PowerShell para `ls`.

Confira [#954](https://github.com/PowerShell/PowerShell/issues/954) para fazer comentários sobre como melhorar a experiência de recurso de curinga no Linux/macOS.

### <a name="net-framework-vs-net-core-framework"></a>.NET Framework versus .NET Core Framework

O PowerShell no Linux/macOS usa .NET Core, que é um subconjunto do .NET Framework completo no Microsoft Windows. Isso é significativo, pois o PowerShell fornece acesso direto aos tipos de estrutura subjacentes, métodos etc. Como resultado, scripts executados no Windows não podem ser executados em outras plataformas devido às diferenças nas estruturas. Para saber mais sobre o .NET Core Framework, confira <https://dotnetfoundation.org/net-core>

Com o surgimento do [.NET Standard 2.0](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/), o .NET Core 2.0 trará de volta muitos tipos e métodos tradicionais presentes no .NET Framework completo. Isso significa que o PowerShell Core poderá carregar vários módulos tradicionais do Windows PowerShell sem modificação. Siga o nosso trabalho relacionado ao .NET Standard 2.0 [aqui](https://github.com/PowerShell/PowerShell/projects/4).

### <a name="redirection-issues"></a>Redirecionamento de problemas

Não há suporte para o redirecionamento de entrada no PowerShell em qualquer plataforma.
[Edição #1629](https://github.com/PowerShell/PowerShell/issues/1629)

Use `Get-Content` para gravar o conteúdo de um arquivo no pipeline.

A saída redirecionada conterá a BOM (marca de ordem de byte) Unicode quando a codificação UTF-8 padrão for usada. A BOM causará problemas ao trabalhar com utilitários que não a esperam, ou ao ser anexada a um arquivo. Use `-Encoding Ascii` para escrever texto ASCII (o qual, não sendo Unicode, não terá uma BOM). Observação: confira [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71) para nos enviar comentários sobre como melhorar a experiência de codificação no PowerShell Core em todas as plataformas. Estamos trabalhando para dar suporte a UTF-8 sem uma BOM e possivelmente alterando os padrões de codificação para diversos cmdlets entre plataformas.

### <a name="job-control"></a>Controle de trabalho

Não há nenhum suporte de controle de trabalho do PowerShell no Linux/macOS.
Os comandos `fg` e `bg` não estão disponíveis.

Por enquanto, você pode usar os [Trabalhos do PowerShell](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_jobs) que funcionam em todas as plataformas.

### <a name="remoting-support"></a>Suporte à comunicação remota

Atualmente, o PowerShell Core dá suporte à Comunicação Remota do PowerShell (PSRP) em WSMan com a Autenticação básica no macOS e Linux e com a autenticação baseada em NTLM no Linux. Não há suporte para a autenticação baseada em Kerberos.

O trabalho para comunicação remota baseada em WSMan está sendo feito no repositório [psl-omi-provider](https://github.com/PowerShell/psl-omi-provider).

O PowerShell Core também oferece suporte à Comunicação Remota do PowerShell (PSRP) sobre SSH em todas as plataformas (Windows, macOS e Linux). Embora isso não tenha suporte atualmente em produção, você pode aprender mais sobre como configurar isso [aqui](../core-powershell/ssh-remoting-in-powershell-core.md).

### <a name="just-enough-administration-jea-support"></a>Suporte a JEA (Administração Just Enough)

A capacidade de criar pontos de extremidade de comunicação remota de administração restrita (JEA) não está disponível no PowerShell no Linux/macOS. No momento, esse recurso não está no escopo para 6.0 e é algo que consideraremos após o 6.0, pois requer um trabalho considerável de design.

### <a name="sudo-exec-and-powershell"></a>`sudo`, `exec` e PowerShell

Como o PowerShell executa a maioria dos comandos na memória (como Python ou Ruby), não é possível usar o sudo diretamente com integrações do PowerShell. Você pode, obviamente, executar `powershell` com o sudo. Se for necessário executar um cmdlet do PowerShell de dentro do PowerShell com sudo, por exemplo, `sudo Set-Date 8/18/2016`, você faria `sudo powershell Set-Date 8/18/2016`. Da mesma forma, não é possível executar uma integração do PowerShell diretamente. Em vez disso, será necessário fazer `exec powershell item_to_exec`.

Esse problema está sendo acompanhado como parte da #3232.

### <a name="missing-cmdlets"></a>Cmdlets ausentes

Muitos comandos (cmdlets) normalmente disponíveis no PowerShell não está disponíveis no Linux/macOS. Em muitos casos, esses comandos não fazem nenhum sentido nessas plataformas (por exemplo, recursos específicos do Windows como o Registro). Outros comandos, como os comandos de controle de serviço (Get/Start/Stop-Service) estão presentes, mas não são funcionais. As versões futuras corrigirão esses problemas, arrumando os cmdlets quebrados e adicionando novos valores ao longo do tempo.

### <a name="command-availability"></a>Disponibilidade do comando

A tabela a seguir lista os comandos que não funcionam no PowerShell no Linux/macOS.

<table>
<th>Comandos</th><th>Estado Operacional</th><th>Observações</th>
<tr>
<td>Get-Service, New-Service, Restart-Service, Resume-Service, Set-Service, Start-Service, Stop-Service, Suspend-Service
<td>Não disponível.
<td>Esses comandos não serão reconhecidos. Isso deve ser corrigido em uma versão futura.
</tr>
<tr>
<td>Get-Acl, Set-Acl
<td>Não disponível.
<td>Esses comandos não serão reconhecidos. Isso deve ser corrigido em uma versão futura.
</tr>
<tr>
<td>Get-AuthenticodeSignature, Set-AuthenticodeSignature
<td>Não disponível.
<td>Esses comandos não serão reconhecidos. Isso deve ser corrigido em uma versão futura.
</tr>
<tr>
<td>Wait-Process
<td>Disponível, não funciona corretamente. <td>Por exemplo, `Start-Process gvim -PassThru | Wait-Process` não funciona; ele falha ao aguardar o processo.
</tr>
<tr>
<td>Register-PSSessionConfiguration, Unregister-PSSessionConfiguration, Get-PSSessionConfiguration
<td>Disponível, mas não funciona.
<td>Grava uma mensagem de erro indicando que os comandos não estão funcionando. Devem ser corrigidos em uma versão futura.
</tr>
<tr>
<td>Get-Event, New-Event, Register-EngineEvent, Register-WmiEvent, Remove-Event, Unregister-Event
<td>Disponível, mas não há fontes de evento disponíveis.
<td>Os comandos de evento do PowerShell estão presentes, mas a maioria das fontes de evento usadas com os comandos (como System.Timers.Timer) não está disponível no Linux, tornando os comandos inúteis na versão alfa.
</tr>
<tr>
<td>Set-ExecutionPolicy
<td>Disponível, mas não funciona.
<td>Retorna uma mensagem informando que não há suporte nessa plataforma. A política de execução é um "dispositivo de segurança" voltado ao usuário que o ajuda a não cometer erros caros. Não é um limite de segurança.
</tr>
<tr>
<td>New-PSSessionOption, New-PSTransportOption
<td>Disponível, mas New-PSSession não funciona.
<td>Não há confirmação de que New-PSSessionOption e New-PSTransportOption funcionem, agora que New-PSSession funciona.
</tr>
</table>
