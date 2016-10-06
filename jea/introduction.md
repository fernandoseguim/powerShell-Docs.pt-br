---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "introdução"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6b5107b7222708dcceff14bc26f0e12ef98d728
ms.openlocfilehash: 00d568234b1453b9161b60d20117374ee4111ab3

---

# Introdução

##  **Motivação**  
Quando você concede acesso privilegiado aos sistemas a alguém, está oferecendo seu limite de confiança para essa pessoa.
Esse é um risco, pois os administradores são uma superfície de ataque.
Ataques internos e roubo de credenciais são reais e comuns.

##  **Não é um novo problema**  
Você provavelmente conhece muito bem o princípio de privilégio mínimo e pode usar alguma forma de RBAC (controle de acesso baseado em função) com aplicativos que o fornecem.
No entanto, a eficiência e a gerenciabilidade dessas soluções geralmente são limitadas por seu escopo amplo e imprecisão.
Além disso, existem lacunas na cobertura do RBAC.
Por exemplo, no Windows, o acesso privilegiado é basicamente um comutador binário, o que força você a conceder permissões desnecessárias ao adicionar usuários ao grupo Administradores.

##  **JEA (Administração Just Enough)** 
Fornece uma plataforma de RBAC (controle de acesso baseado em função) por meio da Comunicação Remota do PowerShell.
*Ele permite que usuários específicos executem tarefas administrativas específicas nos servidores sem conceder direitos de administrador.*
Isso permite que você preencha as lacunas entre suas soluções existentes de RBAC e simplifica o gerenciamento dessas configurações.




<!--HONumber=Aug16_HO3-->


