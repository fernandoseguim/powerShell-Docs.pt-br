---
title: Gerenciando unidades do Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
---
# Gerenciando unidades do Windows PowerShell
Uma *unidade do Windows PowerShell* é um local de armazenamento de dados que pode ser acessado como uma unidade de sistema de arquivos no Windows PowerShell. Provedores do Windows PowerShell criam algumas unidades, como unidades de sistema de arquivos (inclusive C: e D:), as unidades do registro (HKCU: e HKLM:) e a unidade de certificado (Cert:), e você também pode criar suas próprias unidades no Windows PowerShell. Essas unidades são muito úteis, mas estão disponíveis apenas no Windows PowerShell. Você não poderá acessá-las usando outras ferramentas do Windows, como o Explorador de Arquivos ou Cmd.exe.

O Windows PowerShell usa o substantivo **PSDrive** para comandos que funcionam com o Windows PowerShell. Para ver uma lista de unidades do Windows PowerShell presentes na sua sessão do Windows PowerShell, use o cmdlet **Get-PSDrive**.

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

Embora as unidades na exibição variem de acordo com as unidades no sistema, a listagem será semelhante à saída do comando **Get-PSDrive** mostrado acima.

Unidades do sistema de arquivos são um subconjunto das unidades do Windows PowerShell. Você pode identificar as unidades de sistema de arquivo pela entrada FileSystem na coluna de Provider. (As unidades do sistema de arquivo no Windows PowerShell têm suporte no provedor do sistema de arquivos do Windows PowerShell).

Para ver a sintaxe do cmdlet **Get-PSDrive**, digite um comando **Get-Command** com o parâmetro **Syntax**:

```
PS> Get-Command -Name Get-PSDrive -Syntax
Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

O parâmetro **PSProvider** permite exibir somente as unidades do Windows PowerShell com suporte em um provedor específico. Por exemplo, para exibir somente unidades do Windows PowerShell com suporte no provedor do Sistema de Arquivos do Windows PowerShell, digite um comando **Get-PSDrive** com o parâmetro **PSProvider** e valor **FileSystem**:

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

Para exibir as unidades do Windows PowerShell que representam os hives do Registro, use o parâmetro **PSProvider** para exibir somente as unidades do Windows PowerShell que têm suporte no provedor de Registro do Windows PowerShell:

<pre>PS> Get-PSDrive -PSProvider Registry
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE</pre>

Você também pode usar o cmdlets Location padrão com as unidades do Windows PowerShell:

<pre>PS> Set-Location HKLM:SOFTWARE
PS> Push-Location .Microsoft
PS> Get-Location
Caminho
----
HKLM:\SOFTWARE\Microsoft</pre>

### Adicionando novas unidades do Windows PowerShell (New-PSDrive)
Você pode adicionar suas próprias unidades do Windows PowerShell usando o comando **New-PSDrive**. Para ver a sintaxe do comando **New-PSDrive**, digite o comando **Get-Command** com o parâmetro **Syntax**:

```
PS> Get-Command -Name New-PSDrive -Syntax
New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

Para criar uma nova unidade do Windows PowerShell, você deve fornecer três parâmetros:

-   Um nome para a unidade (você pode usar qualquer nome válido do Windows PowerShell)

-   O PSProvider (use "FileSystem" para locais de sistema de arquivos e "Registry" para locais de registro)

-   A raiz, ou seja, o caminho para a raiz da unidade nova

Por exemplo, você pode criar uma unidade chamada "Office" mapeada para a pasta que contém os aplicativos do Microsoft Office no seu computador, como **C:\Program Files\Microsoft Office\OFFICE11**. Para criar a unidade, digite o seguinte comando:

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> Em geral, os caminhos não diferenciam maiúsculas de minúsculas.

Referencie a nova unidade do Windows PowerShell como todas as demais unidades do Windows PowerShell: pelo nome seguido por dois pontos (**:**).

Uma unidade do Windows PowerShell pode tornar diversas tarefas muito mais simples. Por exemplo, algumas das chaves mais importantes no registro do Windows têm caminhos extremamente longos, tornando-os complicados de acessar e difíceis de serem lembradas. Informações críticas de configuração residem em **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion**. Para exibir e alterar itens na chave do registro CurrentVersion, você pode criar uma unidade do Windows PowerShell que está enraizada na chave digitando:

<pre>PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...</pre>

Você poderá então alterar o local para a unidade **cvkey:**, tal como faria com qualquer outra unidade:

`PS> cd cvkey:`

ou:

<pre>PS> Set-Location cvkey: -PassThru
Caminho
----
cvkey:</pre>

O cmdlet New-PsDrive adiciona a nova unidade apenas à sessão atual do Windows PowerShell. Se você fechar a janela do Windows PowerShell, a nova unidade será perdida. Para salvar uma unidade do Windows PowerShell, use o cmdlet Export-Console para exportar a sessão atual do Windows PowerShell e use o parâmetro **PSConsoleFile** do PowerShell.exe para importá-la. Ou então, adicione a nova unidade ao seu perfil do Windows PowerShell.

### Excluindo unidades do Windows PowerShell (Remove-PSDrive)
Você pode excluir unidades do Windows PowerShell usando o cmdlet **Remove-PSDrive**. O cmdlet **Remove-PSDrive** é fácil de usar. Para excluir uma unidade específica do Windows PowerShell, basta fornecer o nome da unidade.

Por exemplo, se você adicionou a unidade do Windows PowerShell **Office:**, como mostrado no tópico **New-PSDrive**, você poderá excluí-la digitando:

```
PS> Remove-PSDrive -Name Office
```

Para excluir a unidade **cvkey:** do Windows PowerShell, também mostrada no tópico **New-PSDrive** use o seguinte comando:

```
PS> Remove-PSDrive -Name cvkey
```

É muito fácil excluir uma unidade do Windows PowerShell, mas não é possível excluí-la enquanto você estiver na unidade. Por exemplo:

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

### Adicionando e removendo unidades externas ao Windows PowerShell
O Windows PowerShell detecta as unidades do sistema de arquivos que foram adicionados ou removidas no Windows, incluindo unidades de rede mapeadas, unidades USB conectadas e unidades excluídas usando o comando **net use** ou os métodos **WScript.NetworkMapNetworkDrive** e **RemoveNetworkDrive** de um script do Windows Script Host (WSH).



<!--HONumber=Apr16_HO1-->


