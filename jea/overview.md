---
description: 
manager: dongill
ms.topic: article
author: rpsqrd
ms.author: ryanpu
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-12-05
title: ARQUIVO LEIAME
ms.technology: powershell
ms.openlocfilehash: f9609f6eb7547c627bc23687c7eb242dd2f5f457
ms.sourcegitcommit: f75fc25411ce6a768596d3438e385c43c4f0bf71
translationtype: HT
---
# <a name="just-enough-administration"></a>Just Enough Administration

JEA (Just Enough Administration) é uma tecnologia de segurança que habilita o uso de administração delegada para qualquer coisa que pode ser gerenciada com o PowerShell.
Com o JEA, você pode:

- **Reduzir o número de administradores em seus computadores** aproveitando contas virtuais que executam ações privilegiadas em nome dos usuários regulares.
- **Limitar o que os usuários podem fazer** especificando quais cmdlets, funções e comandos externos eles podem executar.
- **Entender melhor o que seus usuários estão fazendo** com transcrições e logs que mostram exatamente quais comandos um usuário executou durante uma sessão.

**Por que isso é importante?**

Contas altamente privilegiadas, usadas para administrar os servidores, representam um sério risco de segurança.
Caso um invasor comprometa uma dessas contas, poderia iniciar [ataques laterais](http://aka.ms/pth) por toda a sua organização.
Cada conta que eles comprometessem poderia dar acesso a mais contas e recursos, colocando-os a um passo de roubar segredos da empresa, iniciar um ataque de negação de serviço e muito mais.

No entanto, nem sempre é fácil remover privilégios administrativos.
Considere um cenário comum no qual a função DNS é instalada no mesmo computador que seu Controlador de Domínio do Active Directory.
Os administradores de DNS necessitam de privilégios de administrador local para corrigir problemas com o servidor DNS, porém, para isso você precisa torná-los membros do grupo de segurança altamente privilegiado "Administradores do Domínio".
Essa abordagem concede de forma efetiva aos Administradores de DNS o controle todo o domínio e o acesso a todos os recursos nesse computador.

O JEA auxilia na resolução desse problema, ajudando a adotar o princípio de *Privilégio Mínimo*.
Com o JEA, você pode configurar um ponto de extremidade de gerenciamento para administradores de DNS que concede acesso a todos os comandos do PowerShell que eles precisam para trabalhar e nada mais.
Isso significa que você pode fornecer o acesso apropriado para reparar um cache DNS inviabilizado ou reiniciar o servidor DNS, sem acidentalmente conceder a eles direitos ao Active Directory, para navegar no sistema de arquivos ou para executar scripts potencialmente perigosos.
Melhor ainda, quando a sessão JEA está configurada para usar contas virtuais privilegiadas temporárias, seus administradores de DNS podem se conectar ao servidor usando credenciais *não administrativas* e ainda poderão executar comandos que, geralmente, necessitam de privilégios de administrador.
Essa capacidade permite que você remova usuários das funções de administrador local ou de domínio com privilégios amplos e, em vez disso, controle cuidadosamente o que eles podem fazer em cada computador.

## <a name="get-started-with-jea"></a>Introdução ao JEA

Você pode começar a usar o JEA hoje em qualquer computador executando o Windows Server 2016 ou Windows 10.
Também é possível executar o JEA em sistemas operacionais mais antigos com uma atualização do Windows Management Framework.
Para saber mais sobre os requisitos para usar o JEA e aprender a criar, usar e auditar um ponto de extremidade JEA, consulte os tópicos a seguir:

- [Pré-requisitos](prerequisites.md) – explica como configurar seu ambiente para usar o JEA.
- [Recursos de Função](role-capabilities.md) – explica como criar funções que determinam o que um usuário pode fazer em uma sessão do JEA.
- [Configurações de Sessão](session-configurations.md) – explica como configurar pontos de extremidade JEA que mapeiam usuários às funções e como definir a identidade JEA
- [Registrando JEA](register-jea.md) – criar um ponto de extremidade JEA e torná-lo disponível para os usuários se conectarem.
- [Usando JEA](using-jea.md) – conheça as várias maneiras de usar o JEA.
- [Considerações de Segurança](security-considerations.md) – examine as práticas recomendadas de segurança e as implicações das opções de configuração de JEA.
- [Auditoria e relatórios no JEA](audit-and-report.md) – aprenda a fazer auditoria e relatórios em pontos de extremidade JEA.