---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Remover pacotes da lista
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003644"
---
# <a name="unlisting-packages"></a>Remover pacotes da lista

**Por que a remoção de um pacote da Galeria do PowerShell não é exposta como uma opção?**

A Galeria do PowerShell não dá suporte à exclusão permanente dos pacotes pelos usuários.
Isso permite que outros usuários possam usar as dependências de seus pacotes sem se preocupar com possíveis interrupções no futuro.
Por exemplo, se o módulo do Pester depender do módulo do Azure e o módulo do Azure for removido da galeria, o usuário não poderá mais usar o módulo do Pester.

No entanto, em vez de remover um pacote, você poderá removê-lo da lista.

**Qual o resultado da remoção de um pacote da lista na Galeria do PowerShell?**

A remoção de um pacote da lista como um módulo ou script na Galeria do PowerShell o removerá da guia Pacotes. Além disso, os pacotes removidos da lista não serão detectáveis usando a barra de pesquisa.
A única maneira de baixar um pacote removido da lista é especificar o nome exato e a versão do pacote.
Por isso, a remoção de um pacote não interromperá outros módulos ou scripts que dependem dele.

Para remover o pacote da lista, visite a página de detalhes do pacote e selecione "Excluir Pacote". Desmarque a caixa de seleção “Listado” e clique em Salvar.

**Como faço para remover um pacote?**

Se você tiver um cenário em que a exclusão do pacote é necessária, entre em contato com os Administradores da Galeria do PowerShell.
Os cenários de exclusão válidos são:
- Problemas de violação de direitos autorais.
- O pacote possui conteúdo potencialmente perigoso.
- O pacote contém dados confidenciais.

Para enviar uma Solicitação de Exclusão de Pacote aos Administradores da Galeria do PowerShell, visite a página de detalhes do pacote e selecione Entrar em Contato com o Suporte.
