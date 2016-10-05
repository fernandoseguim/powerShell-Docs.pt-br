# Cache de análise do módulo #

Da versão 5.1 em diante, o PowerShell oferece o seguinte controle sobre o arquivo usado para armazenar em cache dados sobre um módulo como os comandos que ele exporta.

Por padrão, esse cache é armazenado no arquivo `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
O cache normalmente é lido na inicialização ao procurar um comando e é gravado em um thread em segundo plano em algum momento após a importação de um módulo.

Para alterar o local padrão do cache, defina a variável de ambiente PSModuleAnalysisCachePath antes de iniciar o PowerShell. As alterações a esta variável de ambiente afetarão apenas processos filhos.
O valor deve nomear um caminho completo (incluindo nome do arquivo) em que o PowerShell tenha permissão para criar e gravar arquivos.
Para desabilitar o cache de arquivo, esse valor pode ser definido para um local inválido, por exemplo

```PowerShell
$env:PSModuleAnalysisCachePath = 'nul'
```

Isso define o caminho para um dispositivo inválido. Nenhum erro se o PowerShell não conseguir gravar no caminho, embora você possa ver um relatório de erro por meio do rastreador:

```PowerShell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Ao gravar o cache, o PowerShell verificará se há módulos que não existem mais para evitar um cache desnecessariamente grande.
Às vezes, essas verificações não são desejáveis, caso em que você pode desativá-las configurando

```PowerShell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Definir essa variável de ambiente entrará em vigor imediatamente no processo atual.

<!--HONumber=Aug16_HO3-->


