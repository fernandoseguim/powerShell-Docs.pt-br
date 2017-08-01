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
ms.translationtype: HT
ms.contentlocale: pt-BR
---
### <a name="common-role-capability-pitfalls"></a><span data-ttu-id="5494a-103">Armadilhas comuns de Capacidade de Função</span><span class="sxs-lookup"><span data-stu-id="5494a-103">Common Role Capability Pitfalls</span></span>
<span data-ttu-id="5494a-104">Você poderá se deparar com algumas armadilhas comuns se passar por este processo por conta própria.</span><span class="sxs-lookup"><span data-stu-id="5494a-104">You may run into a few common pitfalls if you go through this process yourself.</span></span>
<span data-ttu-id="5494a-105">Veja este guia rápido que explica como identificar e corrigir esses problemas ao modificar ou criar um novo ponto de extremidade:</span><span class="sxs-lookup"><span data-stu-id="5494a-105">Here is a quick guide explaining how to identify and remediate these issues when modifying or creating a new endpoint:</span></span>

#### <a name="functions-vs-cmdlets"></a><span data-ttu-id="5494a-106">Funções vs. Cmdlets</span><span class="sxs-lookup"><span data-stu-id="5494a-106">Functions vs. Cmdlets</span></span>
<span data-ttu-id="5494a-107">Comandos do PowerShell gravados no PowerShell são funções dele.</span><span class="sxs-lookup"><span data-stu-id="5494a-107">PowerShell commands written in PowerShell are PowerShell functions.</span></span>
<span data-ttu-id="5494a-108">Comandos do PowerShell gravados como classes especializadas de .NET são cmdlets do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5494a-108">PowerShell commands written as specialized .NET classes are PowerShell cmdlets.</span></span>
<span data-ttu-id="5494a-109">Você pode verificar o tipo de comando executando `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="5494a-109">You can check the command type by running `Get-Command`.</span></span>

#### <a name="visibleproviders"></a><span data-ttu-id="5494a-110">VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="5494a-110">VisibleProviders</span></span>
<span data-ttu-id="5494a-111">Você precisará expor quaisquer provedores que precisam de seus comandos.</span><span class="sxs-lookup"><span data-stu-id="5494a-111">You will need to expose any providers your commands need.</span></span>
<span data-ttu-id="5494a-112">O mais comum é o provedor do Sistema de Arquivos, mas você também pode precisar expor outros, como o provedor do Registro.</span><span class="sxs-lookup"><span data-stu-id="5494a-112">The most common is the FileSystem provider, but you may also need to expose others, like the Registry provider.</span></span>
<span data-ttu-id="5494a-113">Para obter uma introdução aos provedores, verifique o [post do blog Hey, Scripting Guy](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).</span><span class="sxs-lookup"><span data-stu-id="5494a-113">For an introduction to providers, check out this [Hey, Scripting Guy blog post](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).</span></span>
<span data-ttu-id="5494a-114">Tenha cuidado ao expor provedores, visto que, geralmente, é melhor definir sua própria função que funciona com os provedores subjacentes do que expor diretamente o provedor em uma sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="5494a-114">Be careful when exposing providers -- often, it is better to define your own function that works with the underlying providers than to directly expose the provider in a JEA session.</span></span>
<span data-ttu-id="5494a-115">Dessa forma, você ainda pode permitir aos usuários trabalhar com arquivos, chaves do Registro, etc., mas mantém o controle sobre com **quais** arquivos e chaves do Registro eles podem trabalhar usando uma lógica de validação personalizada.</span><span class="sxs-lookup"><span data-stu-id="5494a-115">This way, you can still allow users to work with files, registry keys, etc. but retain control over **which** files and registry keys they can work with using custom validation logic.</span></span>

