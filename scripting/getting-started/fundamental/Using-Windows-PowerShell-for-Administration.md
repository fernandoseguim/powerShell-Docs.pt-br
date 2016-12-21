---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet
ms.date: 2016-12-12
title: "Usando o Windows PowerShell para Administração"
ms.technology: powershell
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
ms.openlocfilehash: c0a15bc813e6fdb850fe2d957711f1ad005d853d
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="using-windows-powershell-for-administration"></a>Usando o Windows PowerShell para Administração
O objetivo fundamental do Windows PowerShell é fornecendo um controle administrativo melhor e mais fácil sobre os sistemas, seja interativamente ou de script. Este capítulo apresenta soluções para muitos problemas específicos na administração de sistemas do Windows com o Windows PowerShell. Embora ainda não tenhamos abordado scripts ou funções no Guia do Usuário do Windows PowerShell, as soluções podem ser usadas de scripts ou como funções posteriormente. Mostraremos exemplos que incluem funções como parte da solução para resolver problemas.

Durante toda as descrições da solução, você verá uma mistura de soluções que usam cmdlets específicos, o cmdlet geral Get-WmiObject e até mesmo ferramentas externas que fazem parte das infraestruturas do Windows e .NET Framework. O uso de ferramentas externas faz parte da intenção de design de longo prazo do Windows PowerShell. Mesmo que o sistema aumente, os usuários continuamente encontrarão situações em que os conjuntos de ferramentas disponíveis não fazem tudo de que eles precisam. Em vez de promover a dependência apenas em implementações de cmdlet, o Windows PowerShell tenta dar suporte a soluções de integração de todos os possíveis cenários alternativos.

