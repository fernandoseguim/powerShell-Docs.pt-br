---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Usando o Windows PowerShell para Administração
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
ms.openlocfilehash: 69790ddd6bae26dd18e30af860bad4c749cd86a5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="using-windows-powershell-for-administration"></a>Usando o Windows PowerShell para Administração
O objetivo fundamental do Windows PowerShell é fornecendo um controle administrativo melhor e mais fácil sobre os sistemas, seja interativamente ou de script. Este capítulo apresenta soluções para muitos problemas específicos na administração de sistemas do Windows com o Windows PowerShell. Embora ainda não tenhamos abordado scripts ou funções no Guia do Usuário do Windows PowerShell, as soluções podem ser usadas de scripts ou como funções posteriormente. Mostraremos exemplos que incluem funções como parte da solução para resolver problemas.

Durante toda as descrições da solução, você verá uma mistura de soluções que usam cmdlets específicos, o cmdlet geral Get-WmiObject e até mesmo ferramentas externas que fazem parte das infraestruturas do Windows e .NET Framework. O uso de ferramentas externas faz parte da intenção de design de longo prazo do Windows PowerShell. Mesmo que o sistema aumente, os usuários continuamente encontrarão situações em que os conjuntos de ferramentas disponíveis não fazem tudo de que eles precisam. Em vez de promover a dependência apenas em implementações de cmdlet, o Windows PowerShell tenta dar suporte a soluções de integração de todos os possíveis cenários alternativos.