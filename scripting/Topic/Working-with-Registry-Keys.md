---
title: Trabalhando com chaves do Registro
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
---
# Trabalhando com chaves do Registro
Como as chaves do Registro são itens em unidades do Windows PowerShell, trabalhar com elas é muito semelhante a trabalhar com arquivos e pastas. Uma diferença fundamental é que cada item em uma unidade do Windows PowerShell com base no Registro é um contêiner, assim como uma pasta em uma unidade de sistema de arquivos. No entanto, as entradas do Registro e seus valores associados são propriedades de itens, não itens distintos.

### Listar todas as subchaves de uma chave do Registro
Você pode mostrar todos os itens dentro de uma chave do Registro usando **Get-ChildItem**. Adicione o parâmetro opcional **Force** para exibir itens ocultos ou do sistema. Por exemplo, este comando exibe os itens diretamente na unidade do Windows PowerShell HKCU:, que corresponde ao hive do Registro HKEY_CURRENT_USER:

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

Essas são as chaves de nível superior em HKEY_CURRENT_USER no Editor do Registro (Regedit.exe).

Você também pode especificar esse caminho de Registro definindo o nome do provedor de Registro, seguido por "**::**". O nome completo do provedor de Registro é **Microsoft.PowerShell.Core\Registry**, mas isso pode ser reduzido para apenas **Registry**. Qualquer um dos comandos a seguir lista o conteúdo diretamente sob o HKCU:

```
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

Esses comandos listam apenas os itens contidos diretamente, similar ao uso do comando **DIR** do Cmd.exe ou do **ls** em um shell do UNIX. Para mostrar os itens contidos, você precisa especificar o parâmetro **Recurse**. Para listar todas as chaves de Registro no HKCU, use o comando a seguir (esta operação pode demorar um muitíssimo tempo):

```
Get-ChildItem -Path hkcu:\ -Recurse
```

**Get-ChildItem** pode executar os recursos de filtragem complexos por meio de seus parâmetros **Path**, **Filter**, **Include** e **Exclude**, mas esses parâmetros normalmente são baseados apenas no nome. Você pode executar a filtragem complexa com base em outras propriedades de itens usando o cmdlet **Where-Object**. O comando a seguir localiza todas as chaves no HKCU:\Software que têm no máximo uma subchave e que também têm exatamente quatro valores:

```
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### Copiar chaves
A cópia é feita com **Copy-Item**. O comando a seguir copia HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion e todas as suas propriedades HKCU:\, criando uma nova chave chamada "CurrentVersion":

```
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

Se você examinar essa nova chave no editor do Registro ou usando **Get-ChildItem**, observará que não há cópias das subchaves contidas no novo local. Para copiar todo o conteúdo de um contêiner, você precisa especificar o parâmetro **Recurse**. Para tornar o comando de cópia anterior recursivo, você usaria este comando:

```
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

Você ainda pode usar outras ferramentas que já estão disponíveis para executar cópias do sistema de arquivos. Quaisquer ferramentas de edição de Registro, incluindo reg.exe, regini.exe e regedit.exe, e objetos COM que dão suporte à edição do Registro (como o WScript.Shell e a classe StdRegProv do WMI) podem ser usados de dentro do Windows PowerShell.

### Criar chaves
Criar novas chaves no Registro é mais simples do que criar um novo item em um sistema de arquivos. Como todas as chaves do Registro são contêineres, você não precisa especificar o tipo de item; basta fornecer um caminho explícito, como:

```
New-Item -Path hkcu:\software\_DeleteMe
```

Você também pode usar um caminho de provedor para especificar uma chave:

```
New-Item -Path Registry::HKCU\_DeleteMe
```

### Excluir chaves
Excluir itens é essencialmente o mesmo para todos os provedores. Os comandos a seguir removerão itens silenciosamente:

```
Remove-Item -Path hkcu:\Software\_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### Remover todas as chaves sob uma chave específica
Você pode remover os itens contidos usando **Remove-Item**, mas será solicitado confirmar a remoção se o item contiver qualquer outra coisa. Por exemplo, se tentarmos excluir a subchave HKCU:\\CurrentVersion que criamos, veremos isso:

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Para excluir os itens contidos sem nenhum prompt, especifique o parâmetro **-Recurse**:

```
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

Se desejar remover todos os itens dentro de HKCU:\\CurrentVersion, mas não o HKCU:\\CurrentVersion em si, você poderá usar:

```
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```



<!--HONumber=Apr16_HO1-->


