---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: ARQUIVO LEIAME
ms.technology: powershell
ms.sourcegitcommit: 47593773fb0f34e0b52d35617522d7b1db7f48e6
ms.openlocfilehash: 1cecf1b6bf5a55ed785c8ff43bdd4a0a41e96cd0

---

# Just Enough Administration
JEA (Just Enough Administration) é uma tecnologia de segurança que habilita o uso de administração delegada para qualquer coisa que pode ser gerenciada com o PowerShell.
Com o JEA, você pode:
- **Reduzir o número de administradores em seus computadores** aproveitando contas virtuais que executam ações privilegiadas em nome dos usuários regulares.
- **Limitar o que os usuários podem fazer** especificando quais cmdlets, funções e comandos externos eles podem executar.
- **Entender melhor o que seus usuários estão fazendo** com transcrições "Over The Shoulder” que mostram exatamente quais comandos um usuário executou durante uma sessão.

**Por que isso é importante?**  
Considere o cenário comum em que os servidores DNS estão colocalizados com seus Controladores de Domínio do Active Directory.
Os administradores DNS precisam ter privilégios de administrador local para corrigir problemas com o servidor DNS, porém para isso você precisa torná-los membros do grupo de segurança altamente privilegiado "Administradores do Domínio".
Essa abordagem concede de forma efetiva aos Administradores de DNS o controle todo o domínio e o acesso a todos os recursos nesse computador.

Com o JEA em vigor, você pode configurar uma função para seus administradores de DNS que concede acesso a todos os comandos que eles precisam para trabalhar, e nada mais.
Isso significa que você pode fornecer o acesso apropriado para reparar um cache DNS inviabilizado sem acidentalmente conceder a eles direitos ao Active Directory, para navegar no sistema de arquivos ou para executar scripts potencialmente perigosos.
Melhor ainda, quando a sessão JEA está configurada para usar contas virtuais privilegiadas avulsas, seus administradores de DNS podem se conectar ao servidor usando credenciais *sem privilégios* e ainda poderão executar comandos privilegiados.

## Disponibilidade
O JEA está sendo desenvolvido paralelamente ao Windows Server 2016 e está disponível em versões anteriores mais antigas do Windows por meio de atualizações do Windows Management Framework.
A versão atual do JEA está disponível nas seguintes plataformas:

**Windows Server**
- Windows Server 2016 Technical Preview 4 e superior
- Windows Server 2012 R2, 2012 e 2008 R2\* com [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) instalado

**Windows Client**
- Windows 10 com a Atualização de Novembro (1511) instalada
- Windows 8.1, 8 e 7\* com [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) instalado

\* Suporte para contas virtuais em sessões JEA atualmente não está disponível no Windows Server 2008 R2 ou Windows 7.


## Explorar o guia de experiência
Pronto para aprender a criar, implantar e usar seu próprio ponto de extremidade JEA?

Este guia o familiariza rapidamente com um ponto de extremidade de JEA pré-criado para dar uma ideia de como é a experiência do usuário final, além de explicar a recriação de um ponto de extremidade do zero para ajudar a demonstrar conceitos como configurações de sessão e Recursos de Função.

1.  [Introdução](introduction.md)   
Examina rapidamente por que o JEA é importante

2.  [Pré-requisitos](prerequisites.md)  
Explica como configurar seu ambiente

3.  [Usando JEA](using-jea.md)  
Ajuda a entender a experiência do operador com o JEA

4.  [Recrie a demonstração](remake-the-demo-endpoint.md)  
Criar uma configuração de sessão JEA do zero

5.  [Capacidades de Função](role-capabilities.md)  
Saiba mais sobre como personalizar funcionalidades JEA com Arquivos de Funcionalidade de Função

6.  [Ponta a Ponta - Active Directory](end-to-end---active-directory.md)  
Criar um novo ponto de extremidade para gerenciar o Active Directory

7.  [Manutenção e implantação de vários computador](multi-machine-deployment-and-maintenance.md)  
Descobrir como a implantação e criação mudam com a escala

8.  [Relatando no JEA](reporting-on-jea.md)  
Descobrir como auditar e relatar todas as ações e a infraestrutura do JEA

9.  Apêndices
  - [Conceitos fundamentais usados em todo este guia](key-concepts-used-throughout-this-guide.md)  
  -  [Criar um Controlador de Domínio](creating-a-domain-controller.md)  
  -  [Sobre lista negra](on-blacklisting.md)  
  -  [Considerações sobre a limitação de comandos](considerations-when-limiting-commands.md)  
  -  [Armadilhas comuns de Capacidade de Função](common-role-capability-pitfalls.md)

## Começar a criar seus próprios pontos de extremidade de JEA
É fácil criar um ponto de extremidade de JEA, tudo o que você precisa é um sistema habilitado para JEA e um editor de texto (como o ISE do PowerShell).
Uma dica útil para começar é criar arquivos esqueleto usando `New-PSRoleCapabilityFile -Path <path>` e `New-PSSessionCapabilityFile -Path <Path>` sem outros argumentos.
Esses arquivos de esqueleto contêm todos os campos de configuração aplicáveis juntamente com comentários úteis para explicar a finalidade de cada campo.

Para tornar a criação dos pontos de extremidade de JEA ainda mais fácil, confira o [Auxiliar do Kit de Ferramentas JEA](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx) que fornece uma interface gráfica com a qual você pode criar arquivos de Configuração de Sessão e de Capacidade de Função.
Ela ainda dão suporte à geração de Capacidades de Função com base nos logs do PowerShell para dar os primeiros passos nos comandos que os usuários executam regularmente para trabalhar.




<!--HONumber=Jun16_HO4-->


