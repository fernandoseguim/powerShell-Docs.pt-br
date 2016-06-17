# Just Enough Administration
JEA (Just Enough Administration) é uma tecnologia de segurança que habilita o uso de administração delegada para qualquer coisa que pode ser gerenciada com o PowerShell.
Com o JEA, você pode:
- **Reduzir o número de administradores em seus computadores** aproveitando contas virtuais que executam ações privilegiadas em nome dos usuários regulares.
- **Limitar o que os usuários podem fazer** especificando quais cmdlets, funções e comandos externos eles podem executar.
- **Entender melhor o que seus usuários estão fazendo** com transcrições "Over The Shoulder” que mostram exatamente quais comandos um usuário executou durante uma sessão.

Por que isso é importante?
Considere o cenário comuns em que os servidores DNS estão colocalizados com seus Controladores de Domínio do Active Directory.
Os administradores DNS precisam ter privilégios de administrador local para corrigir problemas com o servidor DNS, porém para isso você precisa torná-los membros do grupo de segurança altamente privilegiado "Administradores do Domínio".
Isso efetivamente concede controle sobre todo o domínio e acesso a todos os recursos nesse computador.

Com o JEA em vigor, você pode configurar uma função para seus administradores DNS que concede acesso a todos os comandos que eles precisam para trabalhar e nada mais.
Isso significa que eles podem reparar com facilidade um cache DNS inviabilizado sem ter direitos ao Active Directory, navegar pelo sistema de arquivos ou executar scripts potencialmente perigosos.
Melhor ainda, quando a sessão JEA está configurada para usar contas virtuais privilegiadas avulsas, seus administradores DNS podem se conectar ao servidor usando credenciais *sem privilégios* e ainda poderão executar comandos privilegiados.

## Introdução

### Instalação
O JEA está sendo desenvolvido junto com a versão do Windows Server 2016 e está disponível em versões anteriores do Windows por meio de atualizações do Windows Management Framework.
A versão atual do JEA está disponível nas seguintes plataformas:

**Windows Server**
- Windows Server 2016 Technical Preview 4 e superior
- Windows Server 2012 R2, 2012 e 2008 R2\* com [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) instalado

**Windows Client**
- Windows 10 com a Atualização de Novembro (1511) instalada
- Windows 8.1, 8 e 7\* com [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) instalado

\* Suporte para contas virtuais em sessões JEA atualmente não está disponível no Windows Server 2008 R2 ou Windows 7.


### Conceitos fundamentais
**O que exatamente é o JEA?**

O JEA é uma extensão de [pontos de extremidade restritos](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx) do PowerShell que adiciona definições de função, contas virtuais e vários outros aprimoramentos para facilitar ainda mais o bloqueio dos seus pontos de extremidade de gerenciamento.
Um ponto de extremidade de JEA consiste em um arquivo de Configuração de Sessão do PowerShell e um ou mais arquivos de Capacidade de Função.

**Oque são arquivos de Configuração de Sessão e Capacidade de Função?**

Arquivos de Configuração de Sessão do PowerShell (.pssc) definem *quem* pode se conectar a um ponto de extremidade do PowerShell e *como* ele é configurado.
É aqui que os usuários e grupos de segurança são mapeados para funções específicas de gerenciamento e defina as configurações globais como contas virtuais e políticas de transcrição.
Arquivos de configuração de sessão são específicos para cada computador, permitindo que você controle o acesso por computador, se desejado.

Arquivos de Capacidade de Função do PowerShell (.psrc) definem o *que* os usuários que pertencem a uma função são capazes de fazer no sistema.
Aqui você pode restringir quais cmdlets, funções, provedores e programas externos um usuário pode usar em sua sessão JEA.
Arquivos de Capacidade de Função geralmente são genéricos para a função atendida (administrador DNS, suporte técnico de nível 1, auditoria de inventário de somente leitura, etc.) e pertencem a módulos do PowerShell, facilitando compartilhá-los em seu ambiente e com outras pessoas.

**Como o JEA aproveita as contas virtuais?**

No arquivo de Configuração de Sessão do PowerShell, você pode configurar sessões JEA para usar contas virtuais "Executar como".
As contas virtuais são contas privilegiadas avulsas geradas para o usuário específico da conexão nessa sessão específica na qual o contexto dos comandos do usuário são executados.
Contas virtuais pertencem ao grupo de segurança "Administradores" por padrão, mas podem ser opcionalmente configuradas para pertencer somente aos grupos de segurança que você especificar.

### Explorar o guia de experiência
Pronto para criar seu primeiro ponto de extremidade de JEA?
Confira o [JEA Experience Guide](jea-uide.md) (Guia de Experiência de JEA) para aprender a criar, implantar e usar seu próprio ponto de extremidade de JEA.
O guia introduz rapidamente com um ponto de extremidade de JEA pré-criado para dar uma ideia de como é a experiência do usuário final, percorrendo então pela recriação do ponto de extremidade do zero para ajudar a explicar as configurações de sessão e Capacidades de Função.

### Começar a criar seus próprios pontos de extremidade de JEA
É fácil criar um ponto de extremidade de JEA, tudo o que você precisa é um sistema habilitado para JEA e um editor de texto (como o ISE do PowerShell).
Uma dica útil para começar é criar arquivos esqueleto usando `New-PSRoleCapabilityFile -Path <path>` e `New-PSSessionCapabilityFile -Path <Path>` sem outros argumentos.
Esses arquivos de esqueleto contêm todos os campos de configuração aplicáveis juntamente com comentários úteis para explicar a finalidade de cada campo.

Para tornar a criação dos pontos de extremidade de JEA ainda mais fácil, confira o [Auxiliar do Kit de Ferramentas JEA](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx) que fornece uma interface gráfica com a qual você pode criar arquivos de Configuração de Sessão e de Capacidade de Função.
Ela ainda dão suporte à geração de Capacidades de Função com base nos logs do PowerShell para dar os primeiros passos nos comandos que os usuários executam regularmente para trabalhar.


<!--HONumber=Jun16_HO1-->


