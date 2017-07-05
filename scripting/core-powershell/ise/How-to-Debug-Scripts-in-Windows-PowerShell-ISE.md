---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: Como depurar scripts no ISE do Windows PowerShell
ms.assetid: 6dc6d8f9-8978-46e9-a92f-169af37e2817
ms.openlocfilehash: db8847e2cc9abeec729ed8d939fc170529a93846
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a>Como depurar scripts no ISE do Windows PowerShell
Este tópico descreve como depurar scripts em um computador local usando os recursos de depuração visual do ISE (Ambiente de Script Integrado) do Windows PowerShell®.

[Como gerenciar pontos de interrupção](#bkmk_1)
[Como gerenciar uma sessão de depuração](#bkmk_2)
[Como contornar, intervir e sair durante a depuração](#bkmk_3)
[Como exibir os valores de variáveis durante a depuração](#bkmk_4)

## <a name="bkmk_1"></a>Como gerenciar pontos de interrupção
Um ponto de interrupção é um ponto designado em um script em que você deseja pausar a operação para poder examinar o estado atual das variáveis e o ambiente no qual o script está sendo executado. Depois de o script ser pausado por um ponto de interrupção, você pode executar comandos no Painel de Console para examinar o estado do script.  Você pode gerar variáveis ou executar outros comandos. Você ainda pode modificar o valor de todas as variáveis que estão visíveis para o contexto do script em execução no momento. Após examinar o que deseja ver, você pode retomar a operação do script.

É possível definir três tipos de pontos de interrupção no ambiente de depuração do Windows PowerShell:

1.  **Ponto de interrupção de linha**. O script faz uma pausa quando a linha designada é atingida durante a operação do script

2.  **Ponto de interrupção de variável.** O script faz uma pausa sempre que o valor da variável designada é alterado.

3.  **Ponto de interrupção de comando.** O script faz uma pausa sempre que o comando designado está prestes a ser executado durante a operação do script. Ele pode incluir parâmetros para filtrar ainda mais o ponto de interrupção para somente a operação desejada. O comando também pode ser uma função que você criou.

Desses, no ambiente de depuração do ISE do Windows PowerShell, somente os pontos de interrupção de linha podem ser definidos usando o menu ou os atalhos de teclado. Os outros dois tipos de pontos de interrupção podem ser definidos, mas são definidos no Painel de Console usando o cmdlet [Set-PSBreakpoint](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8). Esta seção descreve como executar tarefas de depuração no ISE do Windows PowerShell usando os menus quando disponíveis e como executar uma variedade maior de comandos no Painel de Console usando scripts.

### <a name="to-set-a-breakpoint"></a>Para definir um ponto de interrupção
Um ponto de interrupção pode ser definido em um script somente depois de ele ser salvo. Clique com o botão direito do mouse na linha em que você quer definir um ponto de interrupção e clique em **Alternar Ponto de Interrupção**. Ou então clique com o botão direito do mouse na linha na qual você deseja definir um ponto de interrupção e pressione **F9** ou, no menu **Depurar**, clique em **Alternar Ponto de Interrupção**.

O script a seguir é um exemplo de como é possível definir um ponto de interrupção de variável no Painel de Console usando o cmdlet [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420).

``` PowerShell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a>Listar todos os pontos de interrupção
Exibe todos os pontos de interrupção na sessão atual do Windows PowerShell®.

No menu **Depurar**, clique em **Listar Pontos de Interrupção**. O script a seguir é um exemplo de como é possível listar todos os pontos de interrupção no Painel de Console usando o cmdlet [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6).

``` PowerShell
# This command lists all breakpoints in the current session. 
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a>Remover um ponto de interrupção
Remover um ponto de interrupção o excluirá.  Se você achar que talvez possa querer usá-lo novamente mais tarde, considere [desabilitá-lo](#bkmk_disable) em vez disso.  Clique com o botão direito do mouse na linha de onde você quer remover um ponto de interrupção e clique em **Alternar Ponto de Interrupção**. Ou então, clique na linha na qual você deseja remover um ponto de interrupção e, no menu **Depurar**, clique em **Alternar Ponto de Interrupção**. O script a seguir é um exemplo de como remover um ponto de interrupção com uma ID especificada do Painel de Console usando o cmdlet [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6).

``` PowerShell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a>Remover Todos os Pontos de Interrupção
Para remover todos os pontos de interrupção definidos na sessão atual, no menu **Depurar**, clique em **Remover Todos os Pontos de Interrupção**.

O script a seguir é um exemplo de como remover todos os pontos de interrupção no Painel de Console usando o cmdlet [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6).

``` PowerShell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="bkmk_disable"></a>Desabilitar um ponto de interrupção
Desabilitar um ponto de interrupção não o remove; ele é desativado até ele ser habilitado.  Para desabilitar um ponto de interrupção de linha específico, clique com o botão direito do mouse na linha na qual você quer desabilitar um ponto de interrupção e clique em **Desabilitar Ponto de Interrupção**. Ou então, clique na linha na qual você deseja desabilitar um ponto de interrupção e pressione **F9** ou, no menu **Depurar**, clique em **Desabilitar Ponto de Interrupção**. O script a seguir é um exemplo de como é possível remover um ponto de interrupção com uma ID especificada do Painel de Console usando o cmdlet [Disable-PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8).

``` PowerShell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a>Desabilitar Todos os Pontos de Interrupção
Desabilitar um ponto de interrupção não o remove; ele é desativado até ele ser habilitado.  Para desabilitar todos os pontos de interrupção na sessão atual, no menu **Depurar**, clique em **Desabilitar Todos os Pontos de Interrupção**. O script a seguir é um exemplo de como é possível desabilitar todos os pontos de interrupção no Painel de Console usando o cmdlet [Disable-PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8).

``` PowerShell
# This command disables all breakpoints in the current session. 
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a>Habilitar um ponto de interrupção
Para habilitar um ponto de interrupção específico, clique com o botão direito do mouse na linha na qual você quer habilitar um ponto de interrupção e clique em **Habilitar Ponto de Interrupção**. Ou então, clique na linha na qual você deseja habilitar um ponto de interrupção e pressione **F9** ou, no menu **Depurar**, clique em **Habilitar Ponto de Interrupção**. O script a seguir é um exemplo de como é possível habilitar pontos de interrupção específicos no Painel de Console usando o cmdlet [Enable-PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0).

``` PowerShell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a>Habilitar Todos os Pontos de Interrupção
Para habilitar todos os pontos de interrupção definidos na sessão atual, no menu **Depurar**, clique em **Habilitar Todos os Pontos de Interrupção**. O script a seguir é um exemplo de como é possível habilitar todos os pontos de interrupção no Painel de Console usando o cmdlet [Enable-PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0).

``` PowerShell
# This command enables all breakpoints in the current session. 
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="bkmk_2"></a>Como gerenciar uma sessão de depuração
Antes de iniciar a depuração, você deve definir um ou mais pontos de interrupção. Não é possível definir um ponto de interrupção, a menos que o script que você deseja depurar esteja salvo. Para obter instruções sobre como definir um ponto de interrupção, consulte [Como gerenciar pontos de interrupção](#bkmk_1) ou [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420). Depois de iniciar a depuração, não é possível editar um script até interromper a depuração. Um script que tem um ou mais pontos de interrupção definido é salvo automaticamente antes de ser executado.

### <a name="to-start-debugging"></a>Para iniciar a depuração
Pressione **F5** ou, na barra de ferramentas, clique no ícone **Executar Script** ou, no menu **Depurar**, clique em **Executar/Continuar**. O script é executado até encontrar o primeiro ponto de interrupção. Ele pausa a operação neste ponto e realça a linha na qual ele pausa.

### <a name="to-continue-debugging"></a>Para continuar a depuração
Pressione **F5** ou, na barra de ferramentas, clique no ícone **Executar Script** ou, no menu **Depurar**, clique em **Executar/Continuar** ou então, no Painel Console, digite **C** e pressione **Enter**. Isso fará com que o script continue em execução até o próximo ponto de interrupção ou até o fim do script se outros pontos de interrupção não forem encontrados.

### <a name="to-view-the-call-stack"></a>Para exibir a pilha de chamadas
A pilha de chamadas exibe a execução local no script atual. Se o script for executado em uma função que foi chamada por uma função diferente, isso será representado na exibição por linhas adicionais na saída. A linha inferior exibe o script original e a linha em que uma função foi chamada. A próxima linha mostra essa função e a linha em que outra função pode ter sido chamada.  A linha superior mostra o contexto atual da linha atual em que o ponto de interrupção foi definido.

Enquanto está em pausa, para ver a pilha de chamadas atual, pressione **Ctrl+Shift+D** ou, no menu **Depurar**, clique em **Exibir a Pilha de Chamadas** ou, no Painel Console, digite **K** e pressione **Enter**.

### <a name="to-stop-debugging"></a>Para interromper a depuração
Pressione **Shift+F5** ou, no menu **Depurar**, clique em **Parar Depurador** ou então, no Painel Console, digite **Q** e pressione **Enter**.

## <a name="bkmk_3"></a>Como contornar, intervir e sair durante a depuração
Passo a passo é o processo de executar uma instrução de cada vez. Você pode parar em uma linha de código e examinar os valores de variáveis e o estado do sistema. A tabela a seguir descreve as tarefas comuns de depuração como contornar, intervir e sair.

| Tarefa de Depuração | Descrição | Como fazer isso no ISE do PowerShell |
| --- | --- | --- |
| **Intervir** | Executa a instrução atual e para na próxima instrução. Se a instrução atual for uma função ou uma chamada de script, o depurador intervirá nessa função ou script, caso contrário, ele parará na próxima instrução. | Pressione **F11** ou, no menu **Depurar**, clique em **Intervir** ou então, no Painel de Console, digite **S** e pressione **Enter**. |
| **Contornar** | Executa a instrução atual e para na próxima instrução. Se a instrução atual for uma função ou uma chamada de script, o depurador executará a função ou script completos e parará na próxima instrução após a chamada de função. | Pressione **F10** ou, no menu **Depurar**, clique em **Contornar** ou então, no Painel de Console, digite **V** e pressione **Enter**. |
| **Sair** | Sairá da função atual e subirá um nível se a função for aninhada. Se estiver no corpo principal, o script será executado ao final ou no próximo ponto de interrupção. As instruções ignoradas são executadas, mas não percorridas. | Pressione **Shift+F11** ou, no menu **Depurar**, clique em **Sair** ou então, no Painel Console, digite **O** e pressione **Enter**. |
| **Continuar** | Continua a execução até o final ou até o próximo ponto de interrupção. As funções e invocações ignoradas são executadas, mas não são percorridas. | Pressione **F5** ou, no menu **Depurar**, clique em **Executar/Continuar** ou então, no Painel Console, digite **C** e pressione **Enter**. |

## <a name="bkmk_4"></a>Como exibir os valores de variáveis durante a depuração
Você pode exibir os valores atuais das variáveis no script ao percorrer o código.

### <a name="to-display-the-values-of-standard-variables"></a>Para exibir os valores das variáveis padrão
Use um dos seguintes métodos:

-   No Painel de Script, passe o mouse sobre a variável para exibir seu valor como uma dica de ferramenta.

-   No Painel de Console, digite o nome da variável e pressione **Enter**.

Todos os painéis no ISE estão sempre no mesmo escopo. Portanto, enquanto você estiver depurando um script, os comandos que você digitar no Painel de Console são executados no escopo do script. Isso permite usar o Painel de Console para encontrar os valores das variáveis e chamar funções definidas apenas no script.

### <a name="to-display-the-values-of-automatic-variables"></a>Para exibir os valores de variáveis automáticas
Você pode usar o método anterior para exibir o valor de quase todas as variáveis enquanto está depurando um script. No entanto, esses métodos não funcionam para as seguintes variáveis automáticas.

-   $_

-   $Input

-   $MyInvocation

-   $PSBoundParameters

-   $Args

Se você tentar exibir o valor de qualquer uma dessas variáveis, obterá o valor dessa variável para em um pipeline interno usado pelo depurador, não o valor da variável no script. É possível contornar isso para algumas variáveis ($_, $Input, $MyInvocation, $PSBoundParameters e $Args) usando o seguinte método:

1.  No script, atribua o valor da variável automática a uma nova variável.

2.  Exiba o valor da nova variável passando o mouse sobre a nova variável no Painel de Script ou digitando a nova variável no Painel de Console.

Por exemplo, para exibir o valor da variável $MyInvocation, no script, atribua o valor a uma nova variável, como $scriptname, e passe o mouse sobre ou digite a variável $scriptname para exibir seu valor.

``` PowerShell
#In MyScript.ps1
$scriptname = $MyInvocation.MyCommand.Path

#In the Console Pane:
C:\ps-test> $scriptname
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a>Consulte Também
- [Usando o ISE do Windows PowerShell](Using-the-Windows-PowerShell-ISE.md)

