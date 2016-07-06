---
title: "Apêndice 2   Criar um atalho do PowerShell personalizado"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 5d4fd421-5d43-4ec7-86fd-acfe887b066e
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 24e9b67cf51b99156db3f0bdfb446996b9d3df76

---

# Apêndice 2: Criar um atalho do PowerShell personalizado
O procedimento a seguir descreve como criar um atalho para o Windows PowerShell que tem várias opções convenientes personalizadas.

1.  Crie um atalho que aponta para Powershell.exe.

2.  Clique com o botão direito do mouse no atalho e clique em **Propriedades**.

3.  Clique na guia **Opções**.

4.  Na seção **Editar Opções**, selecione a caixa de seleção **Edição Rápida**.

    Essa configuração permite selecionar o texto na janela do console do Windows PowerShell arrastando o botão esquerdo do mouse e permite copiar o texto para a área de transferência pressionando ENTER ou clicando com o botão direito do mouse.

5.  Na seção **Editar Opções**, selecione a caixa de seleção **Modo Inserir**. Essa configuração permite clicar com o botão direito do mouse na janela do console para colar o texto da área de transferência automaticamente.

6.  Na seção **Histórico de Comandos**, digite ou selecione um número entre 1 e 999 na caixa **Tamanho do Buffer**. Isso define o número de comandos digitados que serão mantidas no buffer do console.

7.  Na seção **Histórico de Comandos**, marque a caixa de seleção **Descartar Duplicatas Antigas** para eliminar comandos repetidos do console do buffer.

8.  Clique na guia **Layout**.

9. Na seção **Buffer da Tela**, digite um número entre 1 e 9999 na caixa **Altura**. A altura representa o número de linhas de saída que são armazenados no buffer. Este é o número máximo de linhas mantido para exibição ao rolar a janela do console. Se este número for menor do que a altura mostrada na seção **Tamanho da Janela**, a altura do tamanho da janela será automaticamente reduzida com o mesmo valor.

10. Na seção **Tamanho da Janela**, digite um número entre 1 e 9999 para a largura. Isso representa o número de caracteres que são exibidas na janela do console. A largura padrão é 80 e a formatação de saída do Windows PowerShell foi projetada para essa largura.

11. Se você quiser colocar o console em um ponto específico na área de trabalho quando ele for aberto, desmarque a caixa de seleção **Permitir que o sistema posicione a janela** na seção **Posição da janela** e altere os valores nas caixas **Esquerda** e **Superior** na seção **Posição da janela**.

12. Clique em **OK**.




<!--HONumber=Jun16_HO4-->


