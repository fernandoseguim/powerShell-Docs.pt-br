---
title: Gerenciando o local atual
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
---
# Gerenciando o local atual
Ao navegar em sistemas de pasta no Explorador de Arquivos, normalmente há um local de trabalho específico, ou seja, a pasta aberta atual. Itens na pasta atual podem ser manipulados facilmente clicando neles. Para interfaces de linha de comando como Cmd.exe, quando você estiver na mesma pasta que um arquivo específico, poderá acessá-lo especificando um nome relativamente curto, em vez de precisar especificar todo o caminho para o arquivo. O diretório atual é chamado no diretório de trabalho.

O Windows PowerShell usa o substantivo **Location** para referir-se ao diretório de trabalho e implementa uma família de cmdlets para examinar e manipular seu local.

### Obtendo seu local atual (Get-Location)
Para determinar o caminho do seu local de diretório atual, digite o comando **Get-Location**:

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> O cmdlet Get-Location é semelhante do comando **pwd** no shell BASH. O cmdlet Set-Location é semelhante do comando **cd** do Cmd.exe.

### Configurando seu local atual (Set-Location)
O comando **Get-Location** é usado com o comando **Set-Location**. O comando **Set-Location** permite especificar seu local de diretório atual.

```
PS> Set-Location -Path C:\Windows
```

Depois de inserir o comando, você observará que não receberá nenhum feedback direto sobre o efeito do comando. A maioria dos comandos do Windows PowerShell que executam uma ação produzem pouca ou nenhuma saída porque a saída nem é sempre útil. Para confirmar que uma alteração de diretório foi executada com êxito ao digitar o comando **Set-Location**, inclua o parâmetro **-PassThru** ao digitar o comando **Set-Location**:

```
PS> Set-Location -Path C:\Windows -PassThru
Path
----
C:\WINDOWS
```

O parâmetro **-PassThru** pode ser usado com muitos comandos definidos no Windows PowerShell para retornar informações sobre o resultado em casos em que não há nenhuma saída padrão.

Você pode especificar caminhos em relação ao seu local atual da mesma forma que faria na maioria dos shells de comando UNIX e Windows. Na notação padrão para caminhos relativos, um ponto (**.**) representa a pasta atual e um ponto duplo (**..**) representa o diretório pai do seu local atual.

Por exemplo, se você está na pasta **C:\Windows**, um ponto (**.**) representa **C:\Windows** e um ponto duplo (**..**) representa **C:**. Você pode alterar do seu local atual para a raiz da unidade C: digitando:

<pre>PS> Set-Location -Path .. -PassThru
Caminho
----
C:\</pre>

A mesma técnica funciona em unidades do Windows PowerShell que não são unidades de sistema de arquivos, como **HKLM:**. Você pode definir seu local na chave HKLM\Software no Registro digitando:

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

Em seguida, você pode alterar o local do diretório para o diretório pai, que é a raiz da unidade HKLM: do Windows PowerShell, usando um caminho relativo:

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

Você pode digitar Set-Location ou usar qualquer um dos aliases internos do Windows PowerShell para Set-Location (cd, chdir, sl). Por exemplo:

```
cd -Path C:\Windows
```

`chdir -Path .. -PassThru`

```
sl -Path HKLM:\SOFTWARE -PassThru
```

### Salvar e recuperar locais recentes (Push-Location e Pop-Location)
Ao alterar locais, é muito útil controlar onde você esteve para poder retornar ao local anterior. O cmdlet do Windows PowerShell **Push-Location** cria um histórico ordenado (uma "pilha") de caminhos de diretório nos quais você esteve, para que você possa percorrer novamente o histórico de caminhos de diretório usando o cmdlet complementar **Pop-Location**.

Por exemplo, o Windows PowerShell inicia normalmente no diretório base do usuário.

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> A palavra *pilha* tem um significado especial em muitas configurações de programação, incluindo o .NET Framework. Como uma pilha física de itens, o último item que você coloca na pilha é o primeiro item que poderá obter dela. Adicionar um item a uma pilha é geralmente conhecido como "enviar" o item para a pilha. Extrair um item na pilha coloquialmente é conhecido como "retirar" o item da pilha.

Para enviar o local atual para a pilha e depois movê-lo para a pasta Configurações Locais, digite:

```
PS> Push-Location -Path "Local Settings"
```

Em seguida, você pode enviar o local de configurações para a pilha e movê-lo para a pasta Temp digitando:

```
PS> Push-Location -Path Temp
```

É possível confirmar a alteração dos diretórios digitando o comando **Get-Location**:

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

Você poderá então retornar para o último diretório visitado digitando o comando **Pop-Location** e verificar a mudança digitando o comando **Get-Location**:

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

Assim como no cmdlet **Set-Location**, você poderá incluir o parâmetro **-PassThru** ao inserir o cmdlet **Pop-Location** para exibir o diretório inserido:

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

Você também pode usar os cmdlets Location com caminhos de rede. Se você tiver um servidor denominado FS01 com um compartilhamento chamado Public, poderá alterar seu local digitando

```
Set-Location \\FS01\Public
```

ou

```
Push-Location \\FS01\Public
```

Você pode usar os comandos **Push-Location** e **Set-Location** para alterar o local de qualquer unidade disponível. Por exemplo, se você tiver uma unidade de CD-ROM local com a letra da unidade D contendo um CD de dados, poderá alterar o local na unidade de CD digitando o comando **Set-Location D:**.

Se a unidade estiver vazia, você receberá a seguinte mensagem de erro:

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

Ao usar uma interface de linha de comando, não é conveniente usar o Explorador de Arquivos para examinar os discos físicos disponíveis. Além disso, o Explorador de Arquivos não mostra todas as unidades do Windows PowerShell. O Windows PowerShell oferece um conjunto de comandos para manipular as unidades do Windows PowerShell, o qual abordaremos em seguida.



<!--HONumber=Apr16_HO1-->


