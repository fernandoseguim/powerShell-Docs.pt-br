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
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 46f4e5b231d09952f11387cec7c80fbfce9f9d4b

---

# Introdução

##  **Motivação**  
Quando você concede acesso privilegiado aos sistemas a alguém, está oferecendo seu limite de confiança para essa pessoa.
Esse é um risco, pois os administradores são uma superfície de ataque.
Ataques internos e roubo de credenciais são reais e comuns.

##  **Não é um novo problema**  
Você provavelmente conhece muito bem o princípio de privilégios mínimos e pode usar alguma forma de RBAC (Controle de Acesso Baseado em Função) com aplicativos que o fornecem.
No entanto, a eficiência e a gerenciabilidade dessas soluções geralmente são limitadas por seu escopo amplo e imprecisão.
Além disso, existem lacunas na cobertura do RBAC.
Por exemplo, no Windows, o acesso privilegiado é basicamente um comutador binário, o que força você a conceder permissões desnecessárias ao adicionar usuários ao grupo Administradores.

##  **JEA (Administração Just Enough)** 
Fornece uma plataforma de RBAC (controle de acesso baseado em função) por meio da Comunicação Remota do PowerShell.
*Ele permite que usuários específicos executem tarefas administrativas específicas nos servidores sem conceder direitos de administrador.*
Isso permite que você preencha as lacunas entre suas soluções existentes de RBAC e simplifica o gerenciamento dessas configurações.




<!--HONumber=Jun16_HO4-->


