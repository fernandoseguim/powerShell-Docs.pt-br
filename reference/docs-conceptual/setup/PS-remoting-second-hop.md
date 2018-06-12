---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Dando o segundo salto na Comunicação Remota do PowerShell
ms.openlocfilehash: 1d24473178bc50321a81ebf1115a20f17078844f
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34483008"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>Dando o segundo salto na Comunicação Remota do PowerShell

O "problema do segundo salto" refere-se a uma situação semelhante ao seguinte:

1. Você está conectado no _ServerA_.
2. No _ServerA_, você inicia uma sessão remota do PowerShell para se conectar ao _ServerB_.
3. Um comando executado no _ServerB_ por meio de sua sessão de Conexão Remota do PowerShell tenta acessar um recurso no _ServerC_.
4. O acesso ao recurso no _ServerC_ é negado, pois as credenciais usadas para criar a sessão de Comunicação Remota do PowerShell não foram passadas do _ServerB_ para o _ServerC_.

Há várias maneiras de resolver esse problema. Neste tópico, vamos examinar várias soluções mais comuns para o problema do segundo salto.

## <a name="credssp"></a>CredSSP

Você pode usar o [CredSSP (Credential Security Support Provider)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) para autenticação. O CredSSP armazena em cache as credenciais no servidor remoto (_ServerB_), portanto, usá-lo abre para ataques de roubo de credenciais. Se o computador remoto estiver comprometido, o invasor terá acesso às credenciais do usuário. O CredSSP é desabilitado por padrão nos computadores cliente e servidor. Você só deve habilitar o CredSSP nos ambientes mais confiáveis. Por exemplo, um administrador de domínio que se conecta a um controlador de domínio porque o controlador de domínio é altamente confiável.

Para saber mais sobre questões de segurança ao usar o CredSSP para comunicação remota do PowerShell, consulte [Accidental Sabotage: Beware of CredSSP (Sabotagem acidental: cuidado com o CredSSP)](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).

Para obter mais informações sobre ataques de roubo de credenciais, consulte [Mitigando ataques PtH (Pass-the-Hash) e outro roubo de credenciais](https://www.microsoft.com/en-us/download/details.aspx?id=36036).

Para obter um exemplo de como habilitar e usar o CredSSP para a Comunicação Remota do PowerShell, consulte [Usando o CredSSP para resolver o problema do segundo salto](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).

### <a name="pros"></a>Vantagens

- Ele funciona para todos os servidores com o Windows Server 2008 ou posterior.

### <a name="cons"></a>Desvantagens

- Tem vulnerabilidades de segurança.
- Requer a configuração de funções de cliente e servidor.

## <a name="kerberos-delegation-unconstrained"></a>Delegação Kerberos (irrestrita)

Você pode também pode usar a delegação Kerberos irrestrita para realizar o segundo salto. No entanto, esse método não fornece controle de onde as credenciais delegadas são usadas.

>**Observação:** As contas do Active Directory que têm a propriedade **Conta sensível à segurança não pode ser delegada** definida, não podem ser delegadas. Para obter mais informações, consulte [Foco de Segurança: analisando 'Conta sensível à segurança não pode ser delegada' para Contas Privilegiadas](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) e [Configurações e Ferramentas da Autenticação Kerberos](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Vantagens

- Não exige nenhuma codificação especial.

### <a name="cons"></a>Desvantagens

- Não oferece suporte ao segundo salto para o WinRM.
- Não fornece controle sobre onde as credenciais são usadas, criando uma vulnerabilidade de segurança.

## <a name="kerberos-constrained-delegation"></a>Delegação restrita de Kerberos

Você pode usar a delegação restrita herdada (não baseada em recursos) para realizar o segundo salto.

>**Observação:** As contas do Active Directory que têm a propriedade **Conta sensível à segurança não pode ser delegada** definida, não podem ser delegadas. Para obter mais informações, consulte [Foco de Segurança: analisando 'Conta sensível à segurança não pode ser delegada' para Contas Privilegiadas](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) e [Configurações e Ferramentas da Autenticação Kerberos](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Vantagens

- Não exige nenhuma codificação especial

### <a name="cons"></a>Desvantagens

- Não oferece suporte ao segundo salto para o WinRM.
- Deve ser configurada no objeto do Active Directory do servidor remoto (_ServerB_).
- Limitado a um domínio. Não pode cruzar domínios ou florestas.
- Requer direitos para atualizar objetos e SPNs (Nomes de Entidade de Serviço).

## <a name="resource-based-kerberos-constrained-delegation"></a>Delegação restrita de Kerberos com base em recursos

A utilização da delegação restrita de Kerberos baseada em recursos (introduzida no Windows Server 2012) permite que seja configurada a delegação de credencial no objeto do servidor no qual os recursos residem.
No cenário de segundo salto descrito acima, você configura o _ServerC_ para especificar de onde ele aceitará as credenciais delegadas.

>**Observação:** As contas do Active Directory que têm a propriedade **Conta sensível à segurança não pode ser delegada** definida, não podem ser delegadas. Para obter mais informações, consulte [Foco de Segurança: analisando 'Conta sensível à segurança não pode ser delegada' para Contas Privilegiadas](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) e [Configurações e Ferramentas da Autenticação Kerberos](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Vantagens

- As credenciais não são armazenadas.
- É relativamente fácil de configurar usando cmdlets do PowerShell – não é necessária nenhuma codificação especial.
- Não é necessário acesso de domínio especial.
- Funciona entre domínios e florestas.
- Código do PowerShell.

### <a name="cons"></a>Desvantagens

- Requer o Windows Server 2012 ou posterior.
- Não oferece suporte ao segundo salto para o WinRM.
- Requer direitos para atualizar objetos e SPNs (Nomes de Entidade de Serviço).

### <a name="example"></a>Exemplo

Vejamos um exemplo do PowerShell que configura a delegação restrita baseada em recursos no _ServerC_ para permitir credenciais delegadas de um _ServerB_.
Este exemplo pressupõe que todos os servidores estão executando o Windows Server 2012 ou posterior, e que há pelo menos um controlador de domínio do Windows Server 2012 em cada domínio aos quais os servidores pertencem.

Antes de configurar a delegação restrita, você deve adicionar o recurso `RSAT-AD-PowerShell` para instalar o módulo Active Directory PowerShell e, em seguida, importar esse módulo na sua sessão:

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
Vários cmdlets disponíveis agora têm um parâmetro **PrincipalsAllowedToDelegateToAccount**:

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

O parâmetro **PrincipalsAllowedToDelegateToAccount** define o atributo de objeto do Active Directory **msDS-AllowedToActOnBehalfOfOtherIdentity**, que contém uma lista de controle de acesso (ACL) que especifica as contas que têm permissão para delegar credenciais para a conta associada (no nosso exemplo, será a conta do computador para _Servidor_).

Agora vamos configurar as variáveis que usaremos para representar os servidores:

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

O WinRM (e, portanto, comunicação remota do PowerShell) é executado como a conta de computador por padrão. Você pode ver isso examinando a propriedade **StartName** do serviço `winrm`:

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

Para que o _ServerC_ permita a delegação de uma sessão de comunicação remota do PowerShell no _ServerB_, vamos conceder acesso ao definir o parâmetro **PrincipalsAllowedToDelegateToAccount** no _ServerC_ para o objeto de computador do _ServerB_:

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

O Kerberos [KDC (Centro de distribuição de chaves)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) armazena em cache as tentativas de acesso negado (cache negativo) por 15 minutos. Se _ServerB_ tentou acessar anteriormente o _ServerC_, será necessário limpar o cache no _ServerB_ invocando o seguinte comando:

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

Você também pode reiniciar o computador ou aguardar pelo menos 15 minutos para limpar o cache.

Depois de limpar o cache, é possível executar com êxito o código do _ServerA_ por meio do _ServerB_ no _ServerC_:

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

Neste exemplo, a variável `$using` é usada para tornar a variável `$ServerC` visível ao _ServerB_. Para obter mais informações sobre a variável `$using`, consulte [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).

Para permitir que vários servidores deleguem credenciais ao _ServerC_, defina o valor do parâmetro **PrincipalsAllowedToDelegateToAccount** no _ServerC_ em uma matriz:

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

Se você quiser realizar o segundo salto entre domínios, adicione o FQDN (nome de domínio totalmente qualificado) do controlador de domínio do domínio ao qual o _ServerB_ pertence:

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

Para remover a capacidade de delegar credenciais para o ServerC, defina o valor do parâmetro **PrincipalsAllowedToDelegateToAccount** no _ServerC_ como `$null`:

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>Informações sobre delegação restrita de Kerberos baseada em recursos

- [Novidades na Autenticação Kerberos](https://technet.microsoft.com/library/hh831747.aspx)
- [Como o Windows Server 2012 Ameniza a Dificuldade da Delegação Restrita de Kerberos, Parte 1](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [Como o Windows Server 2012 Ameniza a Dificuldade da Delegação Restrita de Kerberos, Parte 2](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [Noções básicas sobre a Delegação Restrita de Kerberos para Implantações de Proxy de Aplicativo do Azure Active Directory com a Autenticação Integrada do Windows](http://aka.ms/kcdpaper)
- [[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)
- [[MS-SFU]: Extensões do protocolo Kerberos: serviço para usuário e Protocolo de Delegação Restrita 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)
- [Delegação Restrita de Kerberos Baseada em Recursos](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [Administração remota sem a delegação restrita usando PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a>PSSessionConfiguration usando RunAs

Você pode criar uma configuração de sessão no _ServerB_ e definir o parâmetro **RunAsCredential**.

Para obter informações sobre como usar PSSessionConfiguration e RunAs para resolver o problema do segundo salto, consulte [Outra solução para a comunicação remota de saltos múltiplos do PowerShell](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).

### <a name="pros"></a>Vantagens

- Funciona com qualquer servidor com o WMF 3.0 ou posterior.

### <a name="cons"></a>Desvantagens

- Requer a configuração de **PSSessionConfiguration** e de **RunAs** em cada servidor intermediário (_ServerB_).
- Requer manutenção de senha ao usar uma conta **RunAs** de domínio

## <a name="just-enough-administration-jea"></a>JEA (Administração Just Enough)

O JEA permite restringir os comandos que um administrador pode executar durante uma sessão do PowerShell. Pode ser usado para resolver o problema do segundo salto.

Para obter informações sobre o JEA, consulte [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).

### <a name="pros"></a>Vantagens

- Não necessita manutenção de senha ao usar uma conta virtual.

### <a name="cons"></a>Desvantagens

- Requer o WMF 5.0 ou posterior.
- Requer a configuração em cada servidor intermediário (_ServerB_).

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>Passar credenciais dentro de um bloco de script Invoke-Command

É possível passar credenciais dentro do parâmetro **ScriptBlock** de uma chamada do cmdlet [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command).

### <a name="pros"></a>Vantagens

- Não requer configuração especial do servidor.
- Funciona em qualquer servidor que executa o WMF 2.0 ou posterior.

### <a name="cons"></a>Desvantagens

- Requer uma técnica de código complicada.
- Se estiver executando o WMF 2.0, necessita de uma sintaxe diferente para passar argumentos para uma sessão remota.

### <a name="example"></a>Exemplo

O exemplo a seguir mostra como passar credenciais em um bloco de script **Invoke-Command**:

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a>Consulte também

[Considerações de segurança de comunicação remota do PowerShell](WinRMSecurity.md)