# Área de transferência de Cmdlets
**Get-Clipboard** e **Set-Clipboard** facilitam a transferência do conteúdo de e para uma sessão do Windows PowerShell. O seguinte exemplo usa o Explorador de Arquivos para copiar três arquivos:

Agora, é possível acessar facilmente o conteúdo da área de transferência como uma lista de arquivos:

PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt

Os cmdlets Clipboard dão suporte a imagens, arquivos de áudio, listas de arquivo e texto.
<!--HONumber=Mar16_HO2-->
