---
title: Trabalhando com arquivos e pastas
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: c9bc3460e25063347de3c594ef5ce437b0f8961d

---

# Trabalhando com arquivos e pastas
Navegar pelas unidades do Windows PowerShell e manipular os itens nelas é semelhante a manipular arquivos e pastas em unidades de disco físico do Windows. Abordaremos como lidar com tarefas específicas de manipulação de arquivo e pasta nesta seção.

### Listar todos os arquivos e pastas dentro de uma pasta
Você pode obter todos os itens diretamente em uma pasta usando **Get\-ChildItem**. Adicione o parâmetro opcional **Force** para exibir itens ocultos ou do sistema. Por exemplo, este comando exibe o conteúdo direto da unidade do Windows PowerShell C (que é a mesma que a unidade física C do Windows):

```
Get-ChildItem -Force C:\
```

O comando lista apenas os itens contidos diretamente, similar ao uso do comando **DIR** do Cmd.exe ou do **ls** em um shell do UNIX. Para mostrar os itens contidos, também é necessário especificar o parâmetro **\-Recurse**. (Isso pode levar muitíssimo tempo para ser concluído.) Para listar todos os itens na unidade C:

```
Get-ChildItem -Force C:\ -Recurse
```

**Get\-ChildItem** pode filtrar itens com seus parâmetros **Path**, **Filter**, **Include** e **Exclude**, mas eles normalmente se baseiam apenas no nome. Você pode executar a filtragem complexa com base em outras propriedades de itens usando **Where\-Object**.

O comando a seguir localiza todos os executáveis na pasta Arquivos de Programa que foi modificado após 1º de outubro de 2005 e que não são menores que 1 megabyte nem maiores que 10 megabytes:

```
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt "2005-10-01") -and ($_.Length -ge 1m) -and ($_.Length -le 10m)}
```

### Copiar arquivos e pastas
A cópia é feita com **Copy\-Item**. O comando a seguir faz backup de C:\\boot.ini em C:\\boot.bak:

```
Copy-Item -Path c:\boot.ini -Destination c:\boot.bak
```

Se o arquivo de destino já existir, a tentativa de cópia falhará. Para substituir um destino pré-\-existente, use o parâmetro Force:

```
Copy-Item -Path c:\boot.ini -Destination c:\boot.bak -Force
```

Esse comando funciona mesmo quando o destino é somente leitura.

Copiar a pasta funciona da mesma maneira. Este comando copia a pasta C:\\temp\\test1 na nova pasta c:\\temp\\DeleteMe recursivamente:

```
Copy-Item C:\temp\test1 -Recurse c:\temp\DeleteMe
```

Você também pode copiar uma seleção de itens. O comando a seguir copia todos os arquivos .txt contidos em qualquer lugar em c:\\data em c:\\temp\\text:

```
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination c:\temp\text
```

Você ainda pode usar outras ferramentas para realizar cópias do sistema de arquivos. XCOPY, ROBOCOPY e objetos COM, como o **Scripting.FileSystemObject,** todos eles funcionam no Windows PowerShell. Por exemplo, você pode usar a classe **Scripting.FileSystem COM** do Windows Script Host para fazer backup de C:\\boot.ini em C:\\boot.bak:

```
(New-Object -ComObject Scripting.FileSystemObject).CopyFile("c:\boot.ini", "c:\boot.bak")
```

### Criar arquivos e pastas
Criar novos itens funciona da mesma forma em todos os provedores do Windows PowerShell. Se um provedor do Windows PowerShell tiver mais de um tipo de item, por exemplo, se o provedor do Sistema de Arquivos do Windows PowerShell fizer distinção entre arquivos e diretórios, você precisará especificar o tipo de item.

Este comando cria uma nova pasta C:\\temp\\Nova Pasta:

```
New-Item -Path 'C:\temp\New Folder' -ItemType "directory"
```

Este comando cria um novo arquivo vazio C:\\temp\\New Folder\\file.txt

```
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType "file"
```

### Remover todos os arquivos e pastas dentro de uma pasta
É possível remover os itens contidos usando **Remove\-Item**, mas será solicitado que você confirme a remoção se o item contiver alguma outra coisa. Por exemplo, se você tentar excluir a pasta C:\\temp\\DeleteMe que contém outros itens, o Windows PowerShell solicitará sua confirmação antes de excluí-la:

```
Remove-Item C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Se você não quiser ser solicitado para cada item contido, especifique o parâmetro **Recurse**:

```
Remove-Item C:\temp\DeleteMe -Recurse
```

### Mapear uma pasta local como uma Unidade Acessível do Windows
Você também pode mapear uma pasta local usando o comando **subst**. O comando a seguir cria uma unidade local P: com raiz no diretório de Arquivos de Programa local:

```
subst p: $env:programfiles
```

Assim como ocorre com unidades de rede, unidades mapeadas no Windows PowerShell usando **subst** ficam imediatamente visíveis para o shell do Windows PowerShell.

### Ler um arquivo de texto em uma matriz
Um dos formatos mais comuns de armazenamento para dados de texto é em um arquivo com linhas separadas, tratadas como elementos de dados distintos. O cmdlet **Get\-Content** pode ser usado para ler um arquivo inteiro em uma única etapa, como mostrado aqui:

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional 
with Data Execution Prevention" /noexecute=optin /fastdetect
```

**Get\-Content** já trata os dados lidos do arquivo como uma matriz, com um elemento por linha do conteúdo do arquivo. Você pode confirmar isso verificando o **Length** do conteúdo retornado:

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

Esse comando é mais útil para obter listas de informações no Windows PowerShell diretamente. Por exemplo, você pode armazenar uma lista de nomes de computador ou de endereços IP em um arquivo C:\\temp\\domainMembers.txt, com um nome em cada linha do arquivo. Você pode usar **Get\-Content** para recuperar o conteúdo do arquivo e colocá-lo na variável **$Computers**:

```
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

**$Computers** agora é uma matriz que contém um nome do computador em cada elemento.




<!--HONumber=Jun16_HO4-->


