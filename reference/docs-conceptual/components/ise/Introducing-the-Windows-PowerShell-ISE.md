---
ms.date: 08/14/2018
keywords: powershell, cmdlet
title: Apresentando o Windows PowerShell ISE
ms.openlocfilehash: 09a28b295855fd2a3c62bba8a681399dae3454f8
ms.sourcegitcommit: 3402a478cf118c11a5642038eb117bc76553e3ab
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53411575"
---
# <a name="the-windows-powershell-ise"></a>O Windows PowerShell ISE

O ISE (Ambiente de Script Integrado) do Windows PowerShell é um aplicativo host do Windows PowerShell. No ISE, você pode executar comandos e escrever, testar e depurar scripts em uma interface gráfica de usuário único com base em Windows. O ISE fornece edição em várias linhas, preenchimento com tab, coloração de sintaxe, execução seletiva, ajuda contextual e suporte para idiomas da direita para esquerda. Itens de menu e atalhos de teclado são mapeados para executar muitas das mesmas tarefas que você executaria no console do Windows PowerShell. Por exemplo, quando você depurar um script no ISE, pode clicar duas vezes em uma linha de código no painel de edição para definir um ponto de interrupção.

## <a name="support"></a>Suporte

O ISE foi introduzido pela primeira vez com o Windows PowerShell V2 e foi projetado novamente com o PowerShell V3. Há suporte para o ISE em todas as versões com suporte do Windows PowerShell até e incluindo versão do Windows PowerShell v 5.1. No entanto, é o ISE no modo de manutenção e nenhum recurso novo têm probabilidade de ser adicionado.
Além disso, não há nenhum suporte para o ISE com o PowerShell v6 e muito mais. Os usuários que desejam uma ferramenta gráfica para gerenciar scrips do PowerShell, etc., devem considerar [Visual Studio Code](https://code.visualstudio.com/).

## <a name="key-features"></a>Recursos Principais

Os principais recursos no ISE do Windows PowerShell incluem:

- Edição em várias linhas: Para inserir uma linha em branco abaixo da linha atual no painel de comando, pressione SHIFT + ENTER.
- Execução seletiva: Para executar parte de um script, selecione o texto que você deseja executar e clique no botão **Executar Script**. Ou pressione F5.
- Ajuda contextual: Digite **Invoke-Item** e pressione F1. O arquivo de Ajuda é aberto no artigo para o cmdlet **Invoke-Item**.

O ISE do Windows PowerShell permite personalizar alguns aspectos de sua aparência. Ele também tem seu próprio script de perfil do Windows PowerShell.

## <a name="to-start-the-windows-powershell-ise"></a>Para iniciar o Windows PowerShell ISE

Clique em **Iniciar**, selecione **Windows PowerShell** e clique em **ISE do Windows PowerShell**.
Como alternativa, você pode digitar `powershell_ise.exe` em qualquer shell de comando ou na caixa Executar.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>Para obter ajuda no Windows PowerShell ISE

No menu **Ajuda**, clique em **Ajuda do Windows PowerShell**. Ou pressione F1. O arquivo aberto descreve o Windows PowerShell ISE e Windows PowerShell, incluindo toda a ajuda disponível para no cmdlet Get-Help.
