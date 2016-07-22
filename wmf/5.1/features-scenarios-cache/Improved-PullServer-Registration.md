---
title: Registros do Servidor de Pull Aprimorados
author: jaimeo
contributor: Indhu Sivaramakrishnan
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: d9f7dea63e6541b673ac6be5ccad59368b301440

---

## Registro do Servidor de Pull Aprimorado ##

Nas versões anteriores do WMF, as solicitações de registros/relatórios simultâneas em um Servidor de Pull da DSC durante o uso do banco de dados ESENT provocariam uma falha de LCM para registrar e/ou reportar, conforme o caso. Nesses casos, os logs de eventos no Servidor de Pull terão o erro "O nome da instância já está em uso."
Isso ocorria porque um padrão incorreto era usado para acessar o banco de dados ESENT em um cenário Multi-Threaded. No WMF 5.1, esse problema foi corrigido. Os registros ou relatórios simultâneos (que envolvem o banco de dados ESENT) funcionarão bem no WMF 5.1. Esse problema é aplicável somente ao banco de dados ESENT e não se aplica ao banco de dados OLEDB. 



<!--HONumber=Jul16_HO3-->


