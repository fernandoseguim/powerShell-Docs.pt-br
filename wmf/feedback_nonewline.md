# Parâmetro NoNewLine
**Out-File**, **Add-Content** e **Set-Content** agora têm uma nova opção **–NoNewline**, que simplesmente omite uma nova linha após a saída.
```PowerShell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
Sem **–NoNewline** especificado, cada fragmento ficaria em uma linha separada:
```PowerShell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```
<!--HONumber=Mar16_HO2-->
