---
title: "Usando a expansão com Tab"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 644dbbb51e98efda9735f0ff23489e936f6b28a2

---

# Usando a expansão com Tab
Em geral, os shells de linha de comando fornecem uma maneira de preencher nomes longos de arquivos ou de comandos automaticamente, acelerando a entrada de comandos e fornecendo dicas. O Windows PowerShell permite preencher os nomes de arquivo e nomes de cmdlet pressionando a tecla **Tab**.

> [!NOTE]
> A expansão com Tab é controlada pela função TabExpansion interna. Como essa função pode ser modificada ou substituída, essa discussão é um guia para o comportamento da configuração padrão do Windows PowerShell.

Para preencher automaticamente um nome de arquivo ou um caminho com as opções disponíveis automaticamente, digite parte do nome e pressione a tecla **Tab**. O Windows PowerShell expandirá automaticamente o nome da primeira correspondência que encontrar. Pressionar a tecla **Tab** repetidamente percorrerá todas as opções disponíveis.

A expansão com Tab de nomes de cmdlet é ligeiramente diferente. Para usar a expansão com Tab em um nome de cmdlet, digite a primeira parte inteira do nome (o verbo) e o hífen que o segue. Você pode preencher mais do mesmo nome de uma correspondência parcial. Por exemplo, se você digitar **get\-co** e pressionar a tecla **Tab**, o Windows PowerShell expandirá isso automaticamente para o cmdlet **Get\-Command** (observe que ele também altera as letras maiúsculas e minúsculas para sua forma padrão). Se você pressionar a tecla **Tab** novamente, o Windows PowerShell substituirá isso pelo outro único nome de cmdlet correspondente, **Get\-Content**.

Você pode usar a expansão com Tab várias vezes na mesma linha. Por exemplo, você pode usar a expansão de guias no nome do cmdlet **Get\-Content** digitando:

```
PS> Get-Con<Tab>
```

Quando você pressiona a tecla **Tab**, o comando se expande para:

```
PS> Get-Content
```

Você pode especificar parcialmente o caminho para o arquivo de log Active Setup e usar a expansão com Tab novamente:

```
PS> Get-Content c:\windows\acts<Tab>
```

Quando você pressiona a tecla **Tab**, o comando se expande para:

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> Uma limitação do processo de expansão de guia é que as guias são sempre interpretadas como tentativas de preencher uma palavra. Se você copiar e colar os exemplos de comando em um console do Windows PowerShell, verifique se o exemplo não contém guias; se isso acontecer, os resultados serão imprevisíveis e certamente não serão o que você pretendia.




<!--HONumber=Jun16_HO4-->


