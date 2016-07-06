---
title: "Usando o Windows PowerShell para Administração"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: f6d5477c32f8f254ab7280945847509588002e83

---

# Usando o Windows PowerShell para Administração
O objetivo fundamental do Windows PowerShell é fornecendo um controle administrativo melhor e mais fácil sobre os sistemas, seja interativamente ou de script. Este capítulo apresenta soluções para muitos problemas específicos na administração de sistemas do Windows com o Windows PowerShell. Embora ainda não tenhamos abordado scripts ou funções no Guia do Usuário do Windows PowerShell, as soluções podem ser usadas de scripts ou como funções posteriormente. Mostraremos exemplos que incluem funções como parte da solução para resolver problemas.

Ao longo das descrições da solução, você verá uma combinação de soluções que usam cmdlets específicos, o cmdlet geral Get\-WmiObject e até mesmo ferramentas externas que fazem parte das infraestruturas do Windows e do .NET Framework. O uso de ferramentas externas faz parte da tentativa de design a longo prazo do Windows PowerShell. Mesmo que o sistema aumente, os usuários continuamente encontrarão situações em que os conjuntos de ferramentas disponíveis não fazem tudo de que eles precisam. Em vez de promover a dependência apenas em implementações de cmdlet, o Windows PowerShell tenta dar suporte a soluções de integração de todos os possíveis cenários alternativos.




<!--HONumber=Jun16_HO4-->


