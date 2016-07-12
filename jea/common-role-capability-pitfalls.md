---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "armadilhas comuns da capacidade de função"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 0e221c840f083ce0b8ecbcbb34c184bcdbc0c73e

---

### Armadilhas comuns de Capacidade de Função
Você pode se deparar com comum algumas armadilhas até passar por este processo por conta própria.
Veja este guia rápido que explica como identificar e corrigir esses problemas ao modificar ou criar um novo ponto de extremidade:

#### Funções vs. Cmdlets
Comandos do PowerShell gravados no PowerShell são funções dele.
Comandos do PowerShell gravados como classes especializadas de .NET são Cmdlets do PowerShell.
Você pode verificar o tipo de comando executando `Get-Command`.

#### VisibleProviders
Você precisará expor quaisquer provedores que precisam de seus comandos.
O mais comum é o provedor do Sistema de Arquivos, mas você também pode precisar expor outros, como o provedor do Registro.
Para obter uma introdução aos provedores, verifique o [post do blog Hey, Scripting Guy](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).
Tenha cuidado ao expor provedores, visto que, geralmente, é melhor definir sua própria função que funciona com os provedores subjacentes do que expor diretamente o provedor em uma sessão JEA.
Dessa forma, você ainda pode permitir aos usuários trabalhar com arquivos, chaves do Registro, etc., mas mantém o controle sobre com **quais** arquivos e chaves do Registro eles podem trabalhar usando uma lógica de validação personalizada.




<!--HONumber=Jul16_HO1-->


