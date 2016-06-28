---
title: WinRMSecurityRedirect
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
redirect_url: https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity
translationtype: Human Translation
ms.sourcegitcommit: afa259b8611f995bbf5b824179a12e3d8f15df86
ms.openlocfilehash: 207792452c563ec6cca5c17fbcd122372442d8ac

---

# Considerações de segurança de comunicação remota do PowerShell

Comunicação remota do PowerShell é a maneira recomendada de gerenciar sistemas Windows. A comunicação remota do PowerShell é habilitada por padrão no Windows Server 2012 R2. Este documento aborda questões, recomendações e práticas recomendadas de segurança ao usar a comunicação remota do PowerShell.

## O que é a comunicação remota do PowerShell?

A comunicação remota do PowerShell usa o [WinRM (Gerenciamento Remoto do Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426.aspx), que é a implementação do protocolo [WS-Managment (Serviços Web para Gerenciamento)](http://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) da Microsoft, para permitir que os usuários executem comandos do PowerShell em computadores remotos. Você pode encontrar mais informações sobre como usar a comunicação remota do PowerShell em [Executando comandos remotos](https://technet.microsoft.com/en-us/library/dd819505.aspx).

A comunicação remota do PowerShell não é igual ao parâmetro **ComputerName** de um cmdlet para executá-lo em um computador remoto, que usa RPC (Chamada de Procedimento Remoto) como seu protocolo subjacente.

##  Configurações padrão de comunicação remota do PowerShell

A comunicação remota do PowerShell (e WinRM) escutam nas seguintes portas:

- HTTP: 5985
- HTTPS: 5986

Por padrão, a comunicação remota do PowerShell só permite conexões de membros do grupo de Administradores. As sessões são iniciadas no contexto do usuário, de modo que todos os controles de acesso do sistema operacional aplicados a usuários individuais e grupos continuam a serem aplicados enquanto conectados via comunicação remota do PowerShell.

Em redes privadas, a regra de Firewall do Windows padrão para comunicação remota do PowerShell aceita todas as conexões. Em redes públicas, a regra padrão do Firewall do Windows permite as conexões da comunicação remota do PowerShell somente dentro da mesma sub-rede. Você precisa alterar explicitamente a regra para abrir a comunicação remota do PowerShell para todas as conexões em uma rede pública.

>**Aviso:** a regra de firewall para redes públicas destina-se a proteger o computador contra tentativas de conexão externa potencialmente mal-intencionada. Tenha cuidado ao remover essa regra.

## Isolamento do processo

A comunicação remota do PowerShell usa o [WinRM (Gerenciamento Remoto do Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426) para comunicação entre computadores. O WinRM é executado como um serviço na conta de serviço de rede e gera processos isolados executados como contas de usuário para hospedar instâncias do PowerShell. Uma instância do PowerShell em execução como um usuário não tem acesso a um processo que executa uma instância do PowerShell como outro usuário.

## Logs de eventos gerados pela comunicação remota do PowerShell

O FireEye forneceu um bom resumo dos logs de eventos e outras evidências de segurança gerados pelo sessões de comunicação remota do PowerShell, disponíveis em  
[Investigando ataques ao PowerShell](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf).

## Protocolos de transporte e criptografia

Vale a pena considerar a segurança de uma conexão de comunicação remota do PowerShell de duas perspectivas: autenticação inicial e comunicação em andamento. 

Independentemente do protocolo de transporte usado (HTTP ou HTTPS), a comunicação remota do PowerShell sempre criptografa todas as comunicações após a autenticação inicial com uma chave simétrica de AES-256 por sessão.
    
### Autenticação inicial

A autenticação confirma a identidade do cliente para o servidor - e idealmente - do servidor para o cliente.
    
Quando um cliente se conecta a um servidor de domínio usando seu nome do computador (por exemplo: servidor01 ou servidor01.contoso.com), o protocolo de autenticação padrão é [Kerberos](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378747.aspx).
Kerberos garante a identidade do usuário e a identidade do servidor sem enviar qualquer tipo de credencial reutilizável.

Quando um cliente se conecta a um servidor de domínio usando seu endereço IP, ou se conecta a um servidor de grupo de trabalho, a autenticação Kerberos não é possível. Nesse caso, a comunicação remoto do PowerShell depende do [protocolo de autenticação NTLM](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378749.aspx). O protocolo de autenticação NTLM garante a identidade do usuário sem enviar qualquer tipo de credencial delegável. Para provar a identidade do usuário, o protocolo NTLM exige que o cliente e o servidor computem uma chave de sessão da senha do usuário sem nunca trocar a senha. O servidor normalmente não sabe a senha do usuário, de modo que ele se comunica com o controlador de domínio, que sabe a senha do usuário e calcula a chave de sessão para o servidor. 
      
No entanto, o protocolo NTLM não assegura a identidade do servidor. Como ocorre com todos os protocolos que usam NTLM para autenticação, um invasor com acesso a uma conta do computador ingressado do domínio pode invocar o controlador de domínio para computar uma chave de sessão NTLM e, assim, representar o servidor.

A autenticação NTLM é desabilitada por padrão, mas pode ser permitida ao configurar SSL no servidor de destino, ou ao definir a configuração de WinRM TrustedHosts.
    
#### Usando certificados SSL para validar a identidade do servidor durante conexões baseadas em NTLM

Como o protocolo de autenticação NTLM não pode garantir a identidade do servidor de destino (somente que ele já sabe sua senha), você pode configurar servidores de destino para usar SSL na comunicação remota do PowerShell. Atribuir um certificado SSL ao servidor de destino (se emitido por uma autoridade de certificação em que o cliente também confia) permite a autenticação baseada em NTLM, que garante a identidade do usuário e do servidor.
    
#### Ignorando erros de identidade de servidor baseada em NTLM
      
Se for inviável implantar um certificado SSL em um servidor para conexões de NTLM, você poderá suprimir os erros de identidade resultantes adicionando o servidor à lista **TrustedHosts** do WinRM. Observe que adicionar um nome de servidor à lista TrustedHosts não deve ser considerada como uma forma de declaração de confiabilidade dos hosts em si, uma vez que o protocolo de autenticação NTLM não pode garantir que você esteja de fato se conectando ao host ao qual está pretendendo se conectar.
Em vez disso, você deve considerar a configuração TrustedHosts como a lista de hosts para a qual você deseja suprimir o erro gerado por não ter sido capaz de verificar a identidade do servidor.
    
    
### Comunicação em andamento

Quando a autenticação inicial é concluída, o [Protocolo de Comunicação Remota do PowerShell](https://msdn.microsoft.com/en-us/library/dd357801.aspx) criptografa toda a comunicação em andamento com um chave simétrica AES-256 por sessão.  


## Dando o segundo salto

Por padrão, a comunicação remota do PowerShell usa o Kerberos (se disponível) ou o NTLM para autenticação. Ambos os protocolos autenticam o computador remoto sem enviar as credenciais para ele.
Essa é a maneira mais segura de autenticar, mas como o computador remoto não tem as credenciais do usuário, não é possível acessar outros computadores e serviços em nome do usuário. Isso é conhecido como o problema de "Salto duplo".

Há várias maneiras de evitar esse problema:

### Delegação restrita de Kerberos

Para servidores altamente confiáveis, você pode habilitar a [Delegação restrita de Kerberos](https://technet.microsoft.com/en-us/library/cc995228.aspx). Isso permite ao servidor remoto representar o usuário autenticado para uma lista especificada de computadores e serviços.

### Relação de confiança entre computadores remotos

Se você confiar usuários conectados remotamente ao *Server1* aos recursos do *Server2*, poderá conceder explicitamente acesso do *Server1* a esses recursos.

### Usar credenciais explícitas ao acessar recursos remotos

Você pode passar explicitamente suas credenciais para um recurso remoto usando o parâmetro **Credential** de um cmdlet. Por exemplo:

```powershell
$myCredential = Get-Credential
New-PSDrive -Name Tools \\Server2\Shared\Tools -Credential $myCredential 
```

### CredSSP

Você pode usar o [CredSSP (Credential Security Support Provider)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb931352.aspx) para autenticação (especificando "CredSSP" como o valor do parâmetro `Authentication` de uma chamada ao cmdlet [New-PSSession](https://technet.microsoft.com/en-us/library/hh849717.aspx). O CredSSP passa credenciais em texto sem formatação para o servidor, de modo que usá-lo deixa você vulnerável a ataques de roubo de credenciais. Se o computador remoto estiver comprometido, o invasor terá acesso às credenciais do usuário. O CredSSP é desabilitado por padrão nos computadores cliente e servidor. Você só deve habilitar o CredSSP nos ambientes mais confiáveis. Por exemplo, um administrador de domínio que se conecta a um controlador de domínio porque o controlador de domínio é altamente confiável.

Para saber mais sobre questões de segurança ao usar o CredSSP para comunicação remota do PowerShell, consulte [Accidental Sabotage: Beware of CredSSP (Sabotagem acidental: cuidado com o CredSSP)](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).

Para obter mais informações sobre ataques de roubo de credenciais, consulte [Mitigando ataques PtH (Pass-the-Hash) e outro roubo de credenciais](https://www.microsoft.com/en-us/download/details.aspx?id=36036).











<!--HONumber=Jun16_HO4-->


