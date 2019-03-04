---
title: Criação de espaços de execução | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857902"
---
# <a name="creating-runspaces"></a>Criar runspaces

Um espaço de execução é o ambiente operacional para os comandos que são invocados por um aplicativo host. Esse ambiente inclui os comandos e os dados que estão atualmente presentes e quaisquer restrições de linguagem que atualmente se aplica.

 Aplicativos de host podem usar o runspace padrão que é fornecido pelo Windows PowerShell, que inclui todos os comandos de núcleo disponível, ou criar um espaço de execução personalizado que inclui apenas um subconjunto de comandos disponíveis. Para criar um espaço de execução personalizado, você cria um [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object e atribuí-lo ao seu espaço de execução.

## <a name="runspace-tasks"></a>Tarefas do espaço de execução

1. [Criando um InitialSessionState](./creating-an-initialsessionstate.md)

2. [Criando um runspace com restrição](./creating-a-constrained-runspace.md)

3. [Criar vários espaços de execução](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Consulte Também
