# Removendo itens da lista

**Por que a remoção de um item da Galeria do PowerShell não é exposta como uma opção?**

A Galeria do PowerShell não dá suporte à exclusão permanente dos itens pelos usuários. Isso permite que outros usuários possam usar as dependências de seus itens sem se preocupar sobre possíveis interrupções no futuro. Por exemplo, se o módulo do Pester depender do módulo do Azure e o módulo do Azure for removido da galeria, o usuário não poderá mais usar o módulo do Pester.

No entanto, em vez de remover um item, você poderá removê-lo da lista.

**Qual o resultado da remoção de um item da lista na Galeria do PowerShell?**

A remoção de um item da lista como um módulo ou script na Galeria do PowerShell o removerá da guia Itens.
Além disso, os itens removidos da lista não serão detectáveis usando a barra de pesquisa.
A única maneira de baixar um item removido da lista é especificar o nome exato e a versão do item.
Por isso, a remoção de um item não interromperá outros módulos ou scripts que dependem dele.

Para remover o item da lista, visite a página de detalhes do item e selecione “Excluir Item”. Desmarque a caixa de seleção “Listado” e clique em Salvar.

**Como faço para remover um item?**

Se você tiver um cenário em que a exclusão do item é necessária, entre em contato com os Administradores da Galeria do PowerShell.
Os cenários de exclusão válidos são:
- Problemas de violação de direitos autorais.
- O item contém conteúdo potencialmente perigoso.
- O item contém dados confidenciais.

Para enviar uma Solicitação de Exclusão de Item aos Administradores da Galeria do PowerShell, visite a página de detalhes do item e selecione Entrar em Contato com o Suporte.  




<!--HONumber=Aug16_HO3-->


