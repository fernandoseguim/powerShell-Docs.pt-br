---
title: Melhorias de Recursos de Classe da DSC
author: jaimeo
contributor: amitsara
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: b24e70c1e1aaf71487b00fbccaf6edb0f375b888

---

## Melhorias de Recursos de Classe da DSC

Nesta versão, corrigimos os seguintes problemas conhecidos do WMF 5.0:
* O Get-DscConfiguration poderá retornar valores vazios (nulos) ou erros se um tipo complexo/de tabela de hash for retornado pela função Get() de um recurso da DSC baseado em classe.
* O Get-DscConfiguration retornará um erro se a credencial RunAs for usada na Configuração da DSC.
* Os recursos baseados em classe não podem ser usados em uma Configuração de Composição.
* O Start-DscConfiguration será suspenso se o recurso baseado em Classe tiver uma propriedade de seu próprio tipo.
* O recurso baseado em classe não pode ser usado como um recurso exclusivo.



<!--HONumber=Jul16_HO3-->


