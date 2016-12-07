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
ms.openlocfilehash: 8e928ec07ef98b2ec8186a27d3aefa1450a3a424
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
### <a name="common-role-capability-pitfalls"></a>Armadilhas comuns de Capacidade de Função
Você poderá se deparar com algumas armadilhas comuns se passar por este processo por conta própria.
Veja este guia rápido que explica como identificar e corrigir esses problemas ao modificar ou criar um novo ponto de extremidade:

#### <a name="functions-vs-cmdlets"></a>Funções vs. Cmdlets
Comandos do PowerShell gravados no PowerShell são funções dele.
Comandos do PowerShell gravados como classes especializadas de .NET são cmdlets do PowerShell.
Você pode verificar o tipo de comando executando `Get-Command`.

#### <a name="visibleproviders"></a>VisibleProviders
Você precisará expor quaisquer provedores que precisam de seus comandos.
O mais comum é o provedor do Sistema de Arquivos, mas você também pode precisar expor outros, como o provedor do Registro.
Para obter uma introdução aos provedores, verifique o [post do blog Hey, Scripting Guy](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).
Tenha cuidado ao expor provedores, visto que, geralmente, é melhor definir sua própria função que funciona com os provedores subjacentes do que expor diretamente o provedor em uma sessão JEA.
Dessa forma, você ainda pode permitir aos usuários trabalhar com arquivos, chaves do Registro, etc., mas mantém o controle sobre com **quais** arquivos e chaves do Registro eles podem trabalhar usando uma lógica de validação personalizada.

