# Suporte aos módulos para declaração dos intervalos de versão (1.*, etc.)
Combinado com **-MinimumVersion**, **-MaximumVersion** agora permite que o usuário obtenha/importe o módulo dentro de um intervalo específico. O parâmetro também dá suporte a **.***. O seguinte exemplo mostra como isso funciona:

```PowerShell
Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:

PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```
<!--HONumber=Mar16_HO2-->
