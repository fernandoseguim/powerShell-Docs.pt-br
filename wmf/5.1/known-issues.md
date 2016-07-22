---
title: Problemas conhecidos no WMF 5.1 (Preview)
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: krishna
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 387ebc0467b9f154444292f391af0f4b77123639

---

#Problemas conhecidos no WMF 5.1 (Preview) #

> Observação: essas informações são preliminares e estão sujeitas a alteração.

##Problemas do Pester
Nesta versão, há dois problemas dos quais você deve estar ciente ao usar o Pester no Nano Server:

* A execução de testes em relação ao Pester em si pode resultar em algumas falhas devido às diferenças entre FULL CLR e CORE CLR. Particularmente, o método Validate não está disponível no tipo XmlDocument. Seis testes que tentam validar o esquema dos logs de saída do NUnit são conhecidos por falharem. 
* Um teste de cobertura de código falha atualmente porque o Recurso de DSC *WindowsFeature* não existe no Nano Server. No entanto, essas falhas geralmente são benignas e podem ser ignoradas com segurança.


<!--HONumber=Jul16_HO3-->


