---
title: Criando um fluxo de trabalho com atividades do Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055420"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>Criar um fluxo de trabalho com atividades do Windows PowerShell

Você pode criar um fluxo de trabalho do Windows PowerShell selecionando as atividades de ferramentas do Visual Studio e arrastando-os para a janela do Designer de fluxo de trabalho. Para obter informações sobre como adicionar atividades do Windows PowerShell para ferramentas do Visual Studio, consulte [adicionando atividades do Windows PowerShell para ferramentas do Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).

Os procedimentos a seguir descrevem como criar um fluxo de trabalho que verifica o status de domínio de um grupo de computadores especificados pelo usuário, une-as em um domínio, se eles não estão associados e, em seguida, verifica o status novamente.

### <a name="setting-up-the-project"></a>Configuração do projeto

1. Siga o procedimento [adicionando atividades do Windows PowerShell para o Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) para criar um projeto de fluxo de trabalho e adicionar as atividades da [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) e [ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies à caixa de ferramentas.

2. Adicione Automation, Microsoft.PowerShell.Activities, System. Management, Microsoft.PowerShell.Management.Activities e Microsoft.PowerShell.Commands.Management como para o projeto como assemblies de referência.

### <a name="adding-activities-to-the-workflow"></a>Adicionando atividades ao fluxo de trabalho

1. Adicionar um **sequência** atividade ao fluxo de trabalho.

2. Crie um argumento nomeado `ComputerName` com um tipo de argumento `String[]`. Esse argumento representa os nomes dos computadores para verificar e Junte-se.

3. Crie um argumento nomeado `DomainCred` do tipo [pscredential](/dotnet/api/System.Management.Automation.PSCredential). Esse argumento representa as credenciais de domínio de uma conta de domínio que está autorizado para ingressar um computador ao domínio.

4. Crie um argumento nomeado `MachineCred` do tipo [pscredential](/dotnet/api/System.Management.Automation.PSCredential). Esse argumento representa as credenciais de administrador nos computadores para verificar e Junte-se.

5. Adicionar um **ParallelForEach** atividade dentro de **sequência** atividade. Insira `comp` e `ComputerName` nas caixas de texto para que o loop itera através dos elementos da `ComputerName` matriz.

6. Adicionar um **sequência** atividade ao corpo do **ParallelForEach** atividade. Defina as **DisplayName** propriedade da sequência a `JoinDomain`.

7. Adicionar um **GetWmiObject** atividade para o **JoinDomain** sequência.

8. Editar as propriedades do **GetWmiObject** atividade da seguinte maneira.

   |Propriedade|Valor|
   |--------------|-----------|
   |**Classe**|"Win32_ComputerSystem"|
   |**PSComputerName**|{comp}|
   |**PSCredential**|MachineCred|

9. Adicionar um **AddComputer** atividade para o **JoinDomain** sequência após a **GetWmiObject** atividade.

10. Editar as propriedades do **AddComputer** atividade da seguinte maneira.

    |Propriedade|Valor|
    |--------------|-----------|
    |**ComputerName**|{comp}|
    |**DomainCredential**|DomainCred|

11. Adicionar um **RestartComputer** atividade para o **JoinDomain** sequência após a **AddComputer** atividade.

12. Editar as propriedades do **RestartComputer** atividade da seguinte maneira.

    |Propriedade|Valor|
    |--------------|-----------|
    |**ComputerName**|{comp}|
    |**Credential**|MachineCred|
    |**para**|Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell|
    |**Force**|verdadeiro|
    |Wait|verdadeiro|
    |PSComputerName|{""}|

13. Adicionar um **GetWmiObject** atividade para o **JoinDomain** sequência após a **RestartComputer** atividade. Editar suas propriedades para ser o mesmo que o anterior **GetWmiObject** atividade.

    Quando você terminar de procedimentos, a janela de design de fluxo de trabalho deve ter esta aparência.

    ![XAML JoinDomain no designer de fluxo de trabalho](../media/joindomainworkflow.png)
    ![JoinDomain XAML no designer de fluxo de trabalho](../media/joindomainworkflow.png "JoinDomainWorkflow")