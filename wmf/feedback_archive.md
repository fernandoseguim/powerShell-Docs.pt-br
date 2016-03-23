# Cmdlets Archive

Dois novos cmdlets, **Compress-Archive** e **Expand-Archive**, permitem compactar e expandir arquivos ZIP.

## Compress-Archive
O cmdlet **Compress-Archive** cria um novo arquivo morto dos arquivos especificados. Um arquivo morto permite que vários arquivos sejam empacotados e, opcionalmente, compactados em um único arquivo para facilitar o tratamento e armazenamento. Um arquivo morto pode ser compactado usando um algoritmo de compactação especificado no parâmetro **-CompressionLevel**.
```PowerShell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>] 
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## Expand-Archive
O cmdlet **Expand-Archive** extrai os arquivos de um arquivo morto especificado. Um arquivo morto permite que vários arquivos sejam empacotados e, opcionalmente, compactados em um único arquivo para facilitar o tratamento e armazenamento.
```PowerShell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
<!--HONumber=Mar16_HO2-->
