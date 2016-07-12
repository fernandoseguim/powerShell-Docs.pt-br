---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: conceitos fundamentais usados neste guia
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 178fea44987b0c457b8e5d23fbe851ee12f03b31

---

# Conceitos fundamentais usados em todo este guia
**O que exatamente é o JEA?**

O JEA é uma extensão de [pontos de extremidade restritos](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx) do PowerShell que adiciona definições de função, contas virtuais e vários outros aprimoramentos para facilitar ainda mais o bloqueio dos seus pontos de extremidade de gerenciamento.
Um ponto de extremidade de JEA consiste em um arquivo de Configuração de Sessão do PowerShell e um ou mais arquivos de Capacidade de Função.

**Oque são arquivos de Configuração de Sessão e Capacidade de Função?**

Arquivos de Configuração de Sessão do PowerShell (.pssc) definem *quem* pode se conectar a um ponto de extremidade do PowerShell e *como* ele é configurado.
É aqui que os usuários e grupos de segurança são mapeados para funções específicas de gerenciamento e defina as configurações globais como contas virtuais e políticas de transcrição.
Arquivos de configuração de sessão são específicos para cada computador, permitindo que você controle o acesso por computador, se desejado.

Arquivos de Capacidade de Função do PowerShell (.psrc) definem o *que* os usuários que pertencem a uma função são capazes de fazer no sistema.
Aqui você pode restringir quais cmdlets, funções, provedores e programas externos um usuário pode usar em sua sessão JEA.
Arquivos de Capacidade de Função geralmente são genéricos para a função atendida (administrador DNS, suporte técnico de nível 1, auditoria de inventário de somente leitura, etc.) e pertencem a módulos do PowerShell, facilitando compartilhá-los em seu ambiente e com outras pessoas.

**Como o JEA aproveita as contas virtuais?**

No arquivo de Configuração de Sessão do PowerShell, você pode configurar sessões JEA para usar contas virtuais "Executar como".
As contas virtuais são contas privilegiadas avulsas geradas para o usuário específico da conexão nessa sessão específica na qual o contexto dos comandos do usuário são executados.
Contas virtuais pertencem ao grupo de segurança "Administradores" por padrão, mas podem ser opcionalmente configuradas para pertencer somente aos grupos de segurança que você especificar.

**Comunicação Remota do PowerShell**: a comunicação remota do PowerShell permite que você execute comandos do PowerShell em computadores remotas.
Você pode operar em um ou vários computadores e usar conexões temporárias ou persistentes.
Nesta demonstração, você acessará remotamente seu computador local com uma sessão interativa.
O JEA restringe a funcionalidade disponível por meio de comunicação remota do PowerShell.
Para obter mais informações sobre a conexão remota do PowerShell, execute `Get-Help about_Remote`.

**Usuário "RunAs"**: ao usar JEA, um não administrador "é executado como" uma conta com privilégios de "Conta Virtual".
A Conta Virtual dura apenas pela duração da sessão remota.
Isso significa que ela é criada quando um usuário se conecta ao ponto de extremidade e é destruída quando o usuário encerra a sessão.
Por padrão, a Conta Virtual é um membro do grupo Administradores local.
Em um controlador de domínio, ele é um membro do grupo Administradores de Domínio.
Contas Virtuais são locais no computador no qual são criadas e não têm permissões fora desse computador.
Isso significa que eles não são registrados no Active Directory (nenhum RID atribuído).
Além disso, se um comando/script permitido tentar acessar recursos fora do computador local, ele acessará esses recursos com a identidade do computador, não da Conta Virtual.

**Usuário "Conectado"**: o usuário não administrador que se conecta ao ponto de extremidade JEA e ao qual são atribuídas as funções.
Quaisquer comandos executado por esse usuário são executados sob o contexto do usuário RunAs ou conta virtual.




<!--HONumber=Jul16_HO1-->


