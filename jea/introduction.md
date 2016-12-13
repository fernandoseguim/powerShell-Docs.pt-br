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
ms.openlocfilehash: 71264d1001228249d9f2bb0f72473e9761170bf0
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="introduction"></a>Introdução

##  <a name="motivation"></a>**Motivação**  
Quando você concede acesso privilegiado aos sistemas a alguém, está oferecendo seu limite de confiança para essa pessoa.
Esse é um risco, pois os administradores são uma superfície de ataque.
Ataques internos e roubo de credenciais são reais e comuns.

##  <a name="not-a-new-problem"></a>**Não é um novo problema**  
Você provavelmente conhece muito bem o princípio de privilégio mínimo e pode usar alguma forma de RBAC (controle de acesso baseado em função) com aplicativos que o fornecem.
No entanto, a eficiência e a gerenciabilidade dessas soluções geralmente são limitadas por seu escopo amplo e imprecisão.
Além disso, existem lacunas na cobertura do RBAC.
Por exemplo, no Windows, o acesso privilegiado é basicamente um comutador binário, o que força você a conceder permissões desnecessárias ao adicionar usuários ao grupo Administradores.

##  <a name="just-enough-administration-jea"></a>**JEA (Administração Suficiente)** 
Fornece uma plataforma de RBAC (controle de acesso baseado em função) por meio da Comunicação Remota do PowerShell.
*Ele permite que usuários específicos executem tarefas administrativas específicas nos servidores sem conceder direitos de administrador.*
Isso permite que você preencha as lacunas entre suas soluções existentes de RBAC e simplifica o gerenciamento dessas configurações.

