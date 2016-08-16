---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: sobre a lista de bloqueios
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 8892e5e08a763fbc66d782bbc9252d1f3a7dcfcf

---

### Sobre lista de bloqueios
Depois de explorar o JEA, você pode estar se perguntando se é possível colocar comandos na lista de bloqueios.
Essa é uma solicitação compreensível, mas ela não está planejada para JEA pelos seguintes motivos:

1.  Criamos o JEA para limitar os operadores somente às ações que eles precisam realizar.
Uma lista de bloqueios é o oposto.

2.  Os autores de comando do PowerShell não projetaram comandos dele tendo o JEA em mente.
Em uma instalação nova do Windows Server 2016, há cerca de 1520 comandos disponíveis imediatamente.
Os modelos de ameaças para esses comandos não incluem a possibilidade de que um usuário poderia executar comandos como uma conta com mais privilégios.
Por exemplo, determinados comandos permitem realizar injeção de código por design (por exemplo, Add-Type e Invoke-Command no módulo do núcleo do PowerShell).
O JEA pode avisá-lo quando você expõe os comandos específicos que conhecemos, mas não reavaliamos todos os outros comandos no Windows com base no novo modelo de ameaça.
Você deve compreender as capacidades dos comandos que são expostos por meio do JEA.  

3.  Além disso, mesmo que o JEA bloqueie todos os comandos com vulnerabilidades de injeção de código, não há nenhuma garantia de que um usuário mal-intencionado não poderá executar uma ação na lista de bloqueios com outro comando relacionado.
A menos que você compreenda todos os comandos que estiver expondo, é impossível assegurar que uma determinada ação não será possível.
Cabe a você entender os comandos que você está expondo, seja usando uma lista de permissões ou uma lista de bloqueios.
O número de comandos que uma lista de bloqueios poderia expor é impossível de gerenciar, portanto o JEA é implementado usando listas de permissões.




<!--HONumber=Jul16_HO1-->


