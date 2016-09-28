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
ms.sourcegitcommit: 3dde62efa7ba595ed5160cc81b4e2b17a54e52a2
ms.openlocfilehash: d4c9e88ddd6cfaec611527d19d00cbd4db9f5d1d

---

#Problemas conhecidos no WMF 5.1 (Preview) #

> Observação: essas informações são preliminares e estão sujeitas a alteração.

##Iniciando o atalho do PowerShell como administrador
Na instalação do Windows Media Format, se você tentar iniciar o PowerShell no atalho como administrador, poderá receber uma mensagem de "Erro não especificado".
Abra novamente o atalho como não administrador. Em seguida, ele funcionará também como administrador.

##Pester
Nesta versão, há dois problemas dos quais você deve estar ciente ao usar o Pester no Nano Server:

* A execução de testes em relação ao Pester em si pode resultar em algumas falhas devido às diferenças entre FULL CLR e CORE CLR. Particularmente, o método Validate não está disponível no tipo XmlDocument. Seis testes que tentam validar o esquema dos logs de saída do NUnit são conhecidos por falharem. 
* Um teste de cobertura de código falha atualmente porque o Recurso de DSC *WindowsFeature* não existe no Nano Server. No entanto, essas falhas geralmente são benignas e podem ser ignoradas com segurança.

##Validação da operação 

* Update-Help falhará no módulo Microsoft.PowerShell.Operation.Validation devido a um URI de ajuda que não funciona



<!--HONumber=Sep16_HO4-->


