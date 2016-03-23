# Atualizações ao objeto FileInfo
Informações de versão do arquivo podem ser confusas, especialmente nos casos em que foi aplicado patch ao arquivo. Esta versão da Preview de Produção do WMF adiciona novas propriedades de script **FileVersionRaw** e **ProductVersionRaw** a objetos FileInfo. Aqui estão as propriedades, conforme exibidas para powershell.exe:

PS C:\\&gt; Get-Process -Id $pid -FileVersionInfo | fl \*version\* -Force

FileVersionRaw : 10.0.10055.0

ProductVersionRaw : 10.0.10055.0

FileVersion : 10.0.10055.0 (fbl\_srv2.150402-1826)

ProductVersion : 10.0.10055.0
<!--HONumber=Mar16_HO2-->
