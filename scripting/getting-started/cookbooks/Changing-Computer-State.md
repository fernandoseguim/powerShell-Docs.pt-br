---
title: Alterando o estado do computador
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 13b1fd65b9dddf2570e7ab9c5420c0a6d18ce35e

---

# Alterando o estado do computador
Para redefinir um computador no Windows PowerShell, use uma ferramenta de linha de comando padrão ou uma classe WMI. Embora você esteja usando o Windows PowerShell somente para executar a ferramenta, aprender como alterar o estado de energia do computador no Windows PowerShell ilustra alguns dos detalhes importantes sobre como trabalhar com ferramentas externas no Windows PowerShell.

### Bloquear um computador
A única maneira de bloquear um computador diretamente com as ferramentas padrão disponíveis é chamar a função **LockWorkstation ()** em **user32.dll**:

```
rundll32.exe user32.dll,LockWorkStation
```

Esse comando bloqueia imediatamente a estação de trabalho. Ele usa o *rundll32.exe*, que executa DLLs Windows (e salva suas bibliotecas para uso repetido) para executar o user32.dll, uma biblioteca de funções de gerenciamento do Windows.

Quando você bloqueia uma estação de trabalho enquanto a Troca Rápida de Usuário estiver habilitada, como no Windows XP, o computador exibe a tela de logon do usuário em vez de iniciar a proteção de tela do usuário atual.

Para encerrar uma sessão específica em um Servidor de Terminal, use a ferramenta de linha de comando **tsshutdn.exe**.

### Sair da sessão atual
Você pode usar várias técnicas diferentes para sair de uma sessão no sistema local. A maneira mais simples é usar a ferramenta de linha de comando Área de Trabalho Remota/Serviços de Terminal, **logoff.exe** (para obter mais detalhes, no prompt do Windows PowerShell, digite **logoff \/?**). Para fazer logoff da sessão ativa atual, digite **logoff** sem argumentos.

Você também pode usar a ferramenta **shutdown.exe** com a opção de fazer logoff:

```
shutdown.exe -l
```

Uma terceira opção é usar o WMI. A classe Win32\_OperatingSystem tem um método Win32Shutdown. Chamar o método com o sinalizador 0 inicia o logoff:

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Para obter mais informações e para encontrar outros recursos do método Win32Shutdown, veja “Win32Shutdown method of the Win32\_OperatingSystem” (Método Win32Shutdown da Classe Win32_OperatingSystem) no MSDN.

### Desligar ou reiniciar um computador
Desligar e reiniciar computadores geralmente são os mesmos tipos de tarefa. Ferramentas que desligam um computador geralmente também o reiniciam e vice-versa. Há duas opções simples para reiniciar um computador do Windows PowerShell. Use Tsshutdn.exe ou Shutdown.exe com os argumentos apropriados. Obtenha informações de uso detalhadas em **tsshutdn.exe \/?** ou **shutdown.exe \/?**.

Você também pode executar as operações de desligamento e reinicialização usando **Win32\_OperatingSystem** diretamente no Windows PowerShell.

Para desligar o computador, use o método Win32Shutdown com o sinalizador **1**.

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(1)
```

Para reiniciar sistema operacional, use o método Win32Shutdown com o sinalizador **2**.

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(2)
```




<!--HONumber=Jun16_HO4-->


