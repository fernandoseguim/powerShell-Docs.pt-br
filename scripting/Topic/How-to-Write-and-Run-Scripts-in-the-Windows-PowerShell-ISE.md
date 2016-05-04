---
title: Como gravar e executar scripts no ISE do Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
---
# Como gravar e executar scripts no ISE do Windows PowerShell
Este tópico descreve como criar, editar, executar e salvar scripts no Painel de Script.

-   [Como criar e executar scripts](#bkmk_1)

-   [Como gravar e editar texto no Painel de Script](#bkmk_2)

-   [Como salvar um script](#bkmk_3)

## <a name="bkmk_1"></a>Como criar e executar scripts
Você pode abrir e editar arquivos [!INCLUDE[wps_1](../Token/wps_1_md.md)] no Painel de Script. Tipos de arquivos específicos de interesse no [!INCLUDE[wps_1](../Token/wps_1_md.md)] são arquivos de script (.ps1), arquivos de dados de script (.psd1) e arquivos de módulo de script (.psm1). Esses tipos de arquivo são coloridos por sintaxe no editor do Painel de Script. Outros tipos de arquivo comuns que você pode abrir no Painel de Script são arquivos de configuração (.ps1xml), arquivos XML e arquivos de texto.

> [!NOTE]
> A política de execução do [!INCLUDE[wps_2](../Token/wps_2_md.md)] determina se você pode executar scripts e carregar arquivos de configuração e de perfis do Windows PowerShell. A política de execução padrão, Restricted, impede a execução de todos os scripts e impede o carregamento dos perfis. Para alterar a política de execução para permitir que os perfis sejam carregados usados, consulte [Set-ExecutionPolicy [PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) e [about_Signing [v4]](https://technet.microsoft.com/en-us/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).

### Para criar um novo arquivo de script
Na barra de ferramentas, clique em **Novo** ou, no menu **Arquivo**, clique em **Novo**. O arquivo criado aparece em uma nova guia do arquivo sob a guia atual do PowerShell. Lembre-se de que as guias do PowerShell são visíveis apenas quando há mais de uma. Por padrão, um arquivo de script de tipo (.ps1) é criado, mas pode ser salvo com um novo nome e uma extensão. Vários arquivos de script podem ser criados na mesma guia do PowerShell.

### Para abrir um script existente
Na barra de ferramentas, clique em **Abrir...** ou, no menu **Arquivo**, clique em **Abrir**. Na caixa de diálogo **Abrir**, selecione o arquivo que você deseja abrir. O arquivo aberto aparece em uma nova guia.

### Para fechar uma guia de script
Clique na guia script do script que deseja fechar e siga um destes procedimentos:

1.  Clique no ícone **Fechar** (X) na guia do script.

2.  No menu **Arquivo**, clique em **Abrir**.

Se o arquivo tiver sido alterado desde que foi salvo pela última vez, você precisará salvá-lo ou descartá-lo.

### Para exibir o caminho do arquivo
Na guia arquivo, aponte para o nome do arquivo. O caminho totalmente qualificado para o arquivo de script é exibido em uma dica de ferramenta.

### Para executar um script
Na barra de ferramentas, clique em **Executar Script** ou, no menu **Arquivo**, clique em **Executar**.

### Para executar uma parte de um script

1.  No Painel de Script, selecione uma parte de um script.

2.  No menu **Arquivo**, clique em **Executar Seleção** ou, na barra de ferramentas, clique em **Executar Seleção**.

### Para interromper um script em execução
Na barra de ferramentas, clique em **Parar Operação**, pressione CTRL+BREAK ou, no menu **Arquivo**, clique em **Parar Operação**. Pressionar **CTRL+C** também funciona, a menos que algum texto esteja selecionado no momento, quando então **CTRL+C** é mapeado para a função de cópia do texto selecionado.

## <a name="bkmk_2"></a>Como gravar e editar texto no Painel de Script
Use as etapas a seguir para editar texto no Painel de Script. Você pode copiar, recortar, colar, localizar e substituir texto. Você também pode desfazer e refazer a última ação que você acabou de executar. Os atalhos de teclado para executar essas ações são os mesmos usados para todos os aplicativos do Windows.

### Para inserir texto no Painel de Script

1.  Mova o cursor para o Painel de Script clicando em qualquer lugar no Painel de Script ou clicando em **Ir para o Painel de Script** no menu **Exibição**.

2.  Crie um script. As cores de sintaxe e o preenchimento com Tab fazem desta uma experiência mais avançada no [!INCLUDE[ise_2](../Token/ise_2_md.md)].

3.  Consulte [Como usar o preenchimento com Tab no Painel de Script e no Painel de Console](../Topic/How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) para obter detalhes sobre como usar o recurso de preenchimento com Tab para ajudar na digitação.

### Para localizar texto no Painel de Script

1.  Para localizar texto em qualquer lugar, pressione **CTRL+F** ou, no menu **Editar**, clique em **Localizar no Script**.

2.  Para localizar texto após o cursor, pressione **F3** ou, no menu **Editar**, clique em **Localizar Próximo no Script**.

3.  Para localizar texto antes do cursor, pressione **SHIFT+F3** ou, no menu **Editar**, clique em **Localizar Anterior no Script**.

### Para localizar e substituir texto no Painel de Script
Pressione **CRTL+H** ou, no menu **Editar**, clique em **Substituir no Script**. Insira o texto que você deseja localizar e o texto com o qual você deseja substituí-lo, e então pressione **ENTER**.

### Para ir para uma determinada linha de texto no Painel de Script

1.  No Painel de Script, pressione **CTRL+G** ou no menu **Editar**, clique em **Ir para a Linha**.

2.  Insira um número de linha.

### Para copiar o texto no Painel de Script

1.  No Painel de Script, selecione o texto que você deseja copiar.

2.  Pressione **CTRL+C** ou, na barra de ferramentas, clique no ícone **Copiar** ou, no menu **Editar**, clique em **Copiar**.

### Para recortar texto no Painel de Script

1.  No Painel de Script, selecione o texto que você deseja recortar.

2.  Pressione **CTRL+X** ou, na barra de ferramentas, clique no ícone **Recortar** ou então, no menu **Editar**, clique em **Recortar**.

### Para colar o texto no Painel de Script
Pressione **CTRL+V** ou, na barra de ferramentas, clique no ícone **Colar** ou então, no menu **Editar**, clique em **Colar**.

### Para desfazer uma ação no Painel de Script
Pressione **CTRL+Z** ou, na barra de ferramentas, clique no ícone **Desfazer** ou então, no menu **Editar**, clique em **Desfazer**.

### Para refazer uma ação no Painel de Script
Pressione **CTRL+Y** ou, na barra de ferramentas, clique no ícone **Refazer** ou então, no menu **Editar**, clique em **Refazer**.

## <a name="bkmk_3"></a>Como salvar um script
Use as etapas a seguir para salvar e nomear um script. Um asterisco é exibido ao lado do nome do script para marcar um arquivo que não foi salvo desde que ele foi alterado. O asterisco desaparece quando o arquivo é salvo.

### Para salvar um script
Pressione **CTRL+S** ou, na barra de ferramentas, clique no ícone **Salvar** ou então, no menu **Arquivo**, clique em **Salvar**.

### Para salvar e nomear um script

1.  No menu **Arquivo**, clique em **Salvar Como**. A caixa de diálogo **Salvar Como** é exibida.

2.  Na caixa **Nome do arquivo**, insira um nome para o arquivo.

3.  Na caixa **Salvar como tipo**, selecione um tipo de arquivo. Por exemplo, na caixa **Salvar como tipo**, selecione "Scripts do PowerShell (\* .ps1)".

4.  Clique em **Salvar**.

### Para salvar um script em codificação ASCII
Por padrão, o [!INCLUDE[ise_2](../Token/ise_2_md.md)] salva os novos arquivos de script (.ps1), arquivos de dados de script (.psd1) e arquivos de módulo de script (.psm1) como Unicode (BigEndianUnicode) por padrão. Para salvar um script em outra codificação, como ASCII (ANSI), use os métodos **Save** ou **SaveAs** do objeto [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile).

O comando a seguir salva um novo script como MyScript.ps1 com codificação ASCII.

```
$psise.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

O comando a seguir substitui o arquivo de script atual por um arquivo com o mesmo nome, mas com codificação ASCII.

```
$psise.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

O comando a seguir obtém a codificação do arquivo atual.

```
$psise.CurrentFile.encoding
```

O [!INCLUDE[ise_2](../Token/ise_2_md.md)] dá suporte às seguintes opções de codificação: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 e Padrão. O valor da opção Padrão varia de acordo com o sistema.

O [!INCLUDE[ise_2](../Token/ise_2_md.md)] não altera a codificação de scripts criados por outros editores, mesmo quando você usa os comandos Salvar ou Salvar Como em [!INCLUDE[ise_2](../Token/ise_2_md.md)].

## Consulte Também
[Usando o ISE do Windows PowerShell](../Topic/Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=Apr16_HO2-->


