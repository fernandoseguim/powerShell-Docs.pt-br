---
manager: carmonm
ms.topic: article
author: rpsqrd
ms.author: ryanpu
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2017-03-07
title: "Considerações sobre segurança de JEA"
ms.technology: powershell
ms.openlocfilehash: 02384465e3c1b6d9633cc346ba88a2566fea1af1
ms.sourcegitcommit: 910f090edd401870fe137553c3db00d562024a4c
translationtype: HT
---
# <a name="jea-security-considerations"></a>Considerações sobre segurança de JEA

> Aplica-se a: Windows PowerShell 5.0

O JEA ajuda a melhorar a sua situação de segurança, reduzindo o número de administradores permanentes em seus computadores.
Ele faz isso criando um novo ponto de entrada para os usuários para gerenciar o sistema (uma configuração de sessão do PowerShell) que é rigidamente bloqueada por padrão para evitar o uso indevido.
Usuários que precisam de algum acesso ao computador, mas não um acesso ilimitado, para realizar tarefas administrativas, podem ter acesso concedido ao ponto de extremidade JEA.
Como o JEA permite a execução de comandos de administrador sem ter diretamente o acesso de administrador, você então pode remover esses usuários de grupos de segurança altamente privilegiados (torná-los usuários padrão).

Este tópico descreve o modelo de segurança JEA e as práticas recomendadas mais detalhadamente.

## <a name="run-as-account"></a>Conta Executar como

Cada ponto de extremidade JEA tem uma conta "Run As" designada, que é a conta na qual são executadas as ações do usuário que está se conectando.
Essa conta é configurável no [arquivo de configuração de sessão](session-configurations.md) e a conta que você escolher tem uma influência significativa sobre a segurança de seu ponto de extremidade.

As **contas virtuais** são a maneira recomendada de se configurar a conta Run As.
As contas virtuais são avulsas, temporárias e locais que são criadas para o usuário que está se conectando para ser usada durante a duração de sua sessão JEA.
Assim que a sessão é encerrada, a conta virtual será destruída e não poderá mais ser usada.
O usuário que está se conectando não conhece as credenciais da conta virtual e não pode usar a conta virtual para acessar o sistema por outros meios, como Área de Trabalho Remota ou um ponto de extremidade irrestrito do PowerShell.

Por padrão, as contas virtuais pertencem ao grupo local de administradores no computador.
Isso dá a eles direitos totais para gerenciar qualquer coisa no sistema, mas não dá direito para gerenciar recursos na rede.
Durante a autenticação em outros computadores, o contexto do usuário será aquele da conta de computador local e não da conta virtual.

Os controladores de domínio são um caso especial, uma vez que não há um conceito de grupo de administradores locais.
Em vez disso, as contas virtuais pertencem a Administradores de Domínio e podem gerenciar os serviços de diretório no controlador de domínio.
A identidade do domínio ainda é restrita para uso no controlador de domínio onde a sessão da JEA foi instanciada e qualquer acesso à rede parecerá vir do objeto do computador controlador do domínio.

Em ambos os casos, você pode definir explicitamente a quais grupos de segurança a conta virtual deve pertencer.
Essa é uma boa prática quando você executa uma tarefa que pode ser feita sem privilégios de administrador local ou de domínio.
Se você já tiver um grupo de segurança definido para seus administradores, você poderá simplesmente conceder a associação de conta virtual a esse grupo para dar a ele as permissões necessárias.
A associação de grupo de conta virtual é limitada a grupos de segurança local na estação de trabalho e servidores membro, mas em um controlador de domínio, eles só podem ser membros de grupos de segurança de domínio.
Depois de especificar um ou mais grupos de segurança para a conta virtual pertencer, ela não pertencerá mais aos grupos padrão (administrador local ou administrador de domínio).

A tabela a seguir resume as opções de configuração possíveis e as permissões resultantes para as contas virtuais

Tipo de Computador                | Configuração do grupo de conta virtual | Contexto de usuário local                                      | Contexto de usuário de rede
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
Controlador de domínio            | Padrão                             | Usuário do domínio, membro de '*DOMÍNIO*\Administradores de Domínio'         | Conta de Computador
Controlador de domínio            | Grupos de domínio A e B               | Usuário do domínio, membro de '*DOMÍNIO*\A', '*DOMÍNIO*\B'       | Conta de Computador
Estação de trabalho ou servidor membro | Padrão                             | Usuário local, membro de '*BUILTIN*\Administradores'        | Conta de Computador
Estação de trabalho ou servidor membro | Grupos locais C e D                | Usuário local, membro de '*COMPUTADOR*\C' e '*COMPUTADOR*\D' | Conta de Computador

Quando você examinar os eventos de auditoria de segurança e logs de eventos do aplicativo, verá que cada sessão de usuário JEA tem uma conta virtual exclusiva.
Isso ajuda você a rastrear ações de usuário em um ponto de extremidade JEA até o usuário original que executou o comando.
Os nomes de conta virtual seguem o formato "WinRM Virtual Users\\WinRM\_VA\_*ACCOUNTNUMBER*\_*DOMAIN*\_*sAMAccountName*", por exemplo, se o usuário "Alice" no domínio "Contoso" reinicia um serviço em um ponto de extremidade JEA, o nome de usuário associado a qualquer evento do Gerenciador de Controle de Serviço seria "WinRM Virtual Users\\WinRM\_VA\_1\_contoso\_alice".


**As gMSAs (contas de serviço gerenciado de grupo)** são úteis quando um servidor membro necessita ter acesso aos recursos de rede na sessão JEA.
Um exemplo de uso é um ponto de extremidade JEA que é usado para controlar o acesso a uma API REST hospedada em um computador diferente.
É fácil escrever funções para fazer as invocações desejadas na API REST, mas para autenticar na API, é necessário uma identidade de rede.
A utilização de uma conta de serviço gerenciado de grupo possibilita o "segundo salto", sem perder o controle sobre quais computadores podem usar a conta.
As permissões efetivas da gMSA são definidas pelos grupos de segurança (local ou de domínio) ao qual a conta gMSA pertence.

Quando um ponto de extremidade JEA é configurado para usar uma conta gMSA, as ações de todos os usuários JEA parecerão vir da mesma conta de serviço gerenciado de grupo.
A única maneira de rastrear ações até um usuário específico é identificar o conjunto de comandos executados em uma transcrição de sessão do PowerShell.

As **credenciais pass-thru** são usadas quando você não especifica uma conta Run As e deseja que o PowerShell use a credencial dos usuários que estão se conectando para executar comandos no servidor remoto.
Essa configuração *não* é recomendada para o JEA, pois exigiria conceder ao usuário que está se conectando o acesso direto aos grupos de gerenciamento privilegiado.
Se o usuário que estiver se conectando já tiver privilégios de administrador, poderá evitar totalmente o JEA e gerenciar o sistema por outros meios irrestritos.
Consulte a seção abaixo sobre como [o JEA não protege contra administradores](#jea-does-not-protect-against-admins) para obter mais informações.

**As contas Run As padrão** permitem especificar qualquer conta de usuário que executará toda a sessão do PowerShell.
Essa é uma distinção importante, porque uma configuração de sessão definida para usar uma conta Run As fixa (com o parâmetro `-RunAsCredential`) não reconhece o JEA.
Isso significa que as definições de função deixarão de funcionar conforme o esperado e todos os usuários autorizados a acessar o ponto de extremidade terão a mesma função atribuída.

Você não deve usar um RunAsCredential em um ponto de extremidade JEA devido a dificuldade no rastreamento de ações até usuários específicos e devido à falta de suporte para mapeamento de usuários às funções.

## <a name="winrm-endpoint-acl"></a>ACL do Ponto de Extremidade do WinRM

Assim como acontece com pontos de extremidade regulares de comunicação remota do PowerShell, cada ponto de extremidade JEA tem uma ACL (lista de controle de acesso) separada definida na configuração do WinRM que controla quem pode autenticar no ponto de extremidade JEA.
Se for configurada incorretamente, usuários confiáveis poderão não acessar o ponto de extremidade JEA e/ou usuários não confiáveis poderão acessar.
No entanto, a ACL do WinRM não afeta o mapeamento de usuários às funções JEA.
Este é controlado pelo campo *RoleDefinitions* no arquivo de configuração de sessão que foi registrado no sistema.

Por padrão, quando você registra um ponto de extremidade JEA usando um arquivo de configuração de sessão e um ou mais recursos de função, a ACL do WinRM será configurada para permitir que todos os usuários com mapeamento para uma ou mais funções acessem o ponto de extremidade.
Por exemplo, uma sessão JEA configurada com o uso dos comandos a seguir, concede acesso total a *CONTOSO\JEA\_Lev1* e *CONTOSO\JEA\_Lev2*.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

Você pode auditar as permissões de usuário com o cmdlet [Get-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration).

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Para alterar quais usuários têm acesso, execute `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` para um prompt interativo ou `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` para atualizar as permissões.
Os usuários precisam, pelo menos, de direitos de *Invocar* para acessar o ponto de extremidade JEA.

Se usuários adicionais tiverem permissão para acessar o ponto de extremidade JEA, mas não se encaixarem em nenhuma das funções definidas no arquivo de configuração de sessão, eles poderão iniciar uma sessão JEA, mas terão acesso somente aos cmdlets padrão.
Você pode auditar as permissões de usuário em um ponto de extremidade JEA executando o `Get-PSSessionCapability`.
Confira o artigo [Auditoria e relatórios no JEA](audit-and-report.md) para obter mais informações sobre a auditoria de quais comandos um usuário tem acesso em um ponto de extremidade JEA.

## <a name="least-privilege-roles"></a>Funções de privilégio mínimo

Durante a criação de funções JEA, é importante lembrar que a conta virtual ou a conta de serviço gerenciado de grupo em execução em segundo plano geralmente tem acesso irrestrito para gerenciar o computador local.
Os recursos de função do JEA ajudam a restringir o uso que pode ser feito por essa conta, limitando os comandos e os aplicativos que podem ser executados usando o contexto privilegiado.
Funções desenvolvidas de modo inadequado podem permitir a execução de comandos perigosos que podem permitir que um usuário ultrapasse os limites do JEA ou obtenha acesso a informações confidenciais.

Por exemplo, considere a seguinte entrada de capacidade de função:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Essa capacidade de função permite que os usuários executem qualquer cmdlet do PowerShell com o substantivo "Processo" do módulo Microsoft.PowerShell.Management.
Os usuários podem precisar acessar cmdlets como o `Get-Process` para entender quais aplicativos estão sendo executados no sistema e o `Stop-Process` para eliminar qualquer aplicativo pendente.
No entanto, essa entrada também permite o `Start-Process`, que pode ser usado para iniciar um programa arbitrário com permissões de administrador completas.
O programa não precisa ser instalado localmente no sistema, portanto um adversário pode simplesmente iniciar um programa em um compartilhamento de arquivo que concede privilégios de administrador local ao usuário que está se conectando, pode executar um malware e muito mais.'

Uma versão muito mais segura desse mesma capacidade de função seria:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Evite usar curingas em recursos de função e não se esqueça de [auditar as permissões efetivas de usuário](audit-and-report.md#check-effective-rights-for-a-specific-user) regularmente para entender a quais comandos um usuário tem acesso.

## <a name="jea-does-not-protect-against-admins"></a>O JEA não protege contra administradores

Um aos princípios básicos do JEA é que ele permite que não administradores executem *algumas* tarefas de administração.
O JEA não protege contra aqueles que já têm privilégios de administrador.
Os usuários que pertencem a "administradores do domínio", "administradores local" ou outros grupos altamente privilegiados no seu ambiente ainda poderão contornar as proteções do JEA, conectando-se ao computador por outras formas.
Eles poderiam, por exemplo, entrar com o RDP, usar os consoles remotos do MMC ou conectar-se aos pontos de extremidade irrestritos do PowerShell.
Os administradores locais no sistema também podem modificar as configurações de JEA para permitir que usuários adicionais gerenciem o sistema ou alterem uma capacidade de função para estender o escopo do que um usuário pode fazer em sua sessão JEA.
Portanto, é importante avaliar as permissões estendidas dos usuários de JEA para ver se existem outras maneiras pelas quais eles poderiam obter acesso privilegiado ao sistema.

Uma prática comum é usar o JEA para a manutenção de rotina e usar uma solução de gerenciamento de acesso privilegiado "just in time" que permita que os usuários sejam temporariamente administradores locais em situações de emergência.
Isso ajuda a garantir que os usuários não sejam administradores permanentes no sistema, mas possam obter esses direitos se e somente quando concluírem um fluxo de trabalho que documente o uso dessas permissões.