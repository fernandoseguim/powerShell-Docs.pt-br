---
title: Compreendendo o Pipeline do Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
---
# Compreendendo o Pipeline do Windows PowerShell
O redirecionamento funciona praticamente em qualquer lugar no Windows PowerShell. Embora você veja o texto na tela, o Windows PowerShell não redireciona o texto entre comandos. Em vez disso, ele redireciona os objetos.

A notação usada para as pipelines é semelhante àquela usada em outros shells, então à primeira vista, pode não ser aparente que o Windows PowerShell apresenta algo novo. Por exemplo, se você usar o cmdlet **Out-Host** para forçar uma exibição de página a página da saída de outro comando, a saída parecerá ser apenas o texto normal exibido na tela, dividida em páginas, como:

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

O comando Out-Host -Paging é um elemento de pipeline útil sempre que houver uma saída longa que você gostaria de exibir lentamente. Ele será especialmente útil se a operação for utilizar muito da CPU. Como o processamento é transferido para o cmdlet Out-Host, quando ele tem uma página completa pronta para ser exibida, os cmdlets que o precedem no pipeline interrompem a operação até que a próxima página de saída esteja disponível. Você poderá ver isso se usar o Gerenciador de Tarefas do Windows para monitorar o uso de CPU e memória do Windows PowerShell.

Execute o seguinte comando: **Get-ChildItem C:\Windows -Recurse**. Compare o uso de CPU e de memória ao deste comando: **Get-ChildItem C:\Windows -Recurse | Out-Host -Paging**. O que você vê na tela é texto, mas isso é porque é necessário representar objetos como texto em uma janela de console. Isso é apenas uma representação do que é realmente ocorre dentro do Windows PowerShell. Por exemplo, considere o cmdlet Get-Location. Se você digitar **Get-Location** enquanto seu local atual é a raiz da unidade C, você verá a seguinte saída:

```
PS> Get-Location

Path
----
C:\
```

Se o Windows PowerShell redirecionasse o texto, emitir um comando como **Get-Location | Out-Host** passaria de **Get-Location** para **Out-Host** um conjunto de caracteres na ordem em que eles são exibidos na tela. Em outras palavras, se você ignorar as informações de cabeçalho, **Out-Host** receberá primeiro o caractere “**C”**, em seguida, o caractere “**:”** e depois o caractere “**\”**. O cmdlet **Out-Host** não pôde determinar qual significado associar aos caracteres de saída do cmdlet **Get-Location**.

Em vez de usar o texto para permitir que os comandos em um pipeline se comuniquem, o Windows PowerShell usa objetos. Do ponto de vista de um usuário, os objetos empacotam informações relacionadas em um formulário que torna mais fácil manipular as informações como uma unidade e extrair itens específicos que você precisa.

O comando **Get-Location** não retornar o texto que contém o caminho atual. Ele retorna um pacote de informações chamado de um objeto **PathInfo** que contém o caminho atual juntamente com outras informações. O cmdlet **Out-Host** envia então esse objeto **PathInfo** para a tela e o Windows PowerShell decide quais informações exibir e como exibi-las com base em suas regras de formatação.

Na verdade, a saída das informações de cabeçalho do cmdlet **Get-Location** é adicionada somente no final do processo, como parte do processo de formatação de dados para exibição na tela. O que você vê na tela é um resumo das informações e não uma representação completa do objeto de saída.

Considerando que pode haver mais saída de informações de um comando do Windows PowerShell do que é exibido na janela do console, como podemos recuperar os elementos não visíveis? Como exibir os dados extras? E se você desejar exibir os dados em um formato diferente do que o Windows PowerShell normalmente usa?

O restante deste capítulo discute como é possível pode descobrir a estrutura de objetos específicos do Windows PowerShell selecionando itens específicos e formatando-os para exibição mais fácil, bem como enviar essas informações para locais de saída alternativos, como arquivos e impressoras.



<!--HONumber=Apr16_HO1-->


