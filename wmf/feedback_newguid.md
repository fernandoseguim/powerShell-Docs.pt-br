# New-Guid
Geralmente, um script (ou talvez a escrita de um recurso DSC) exige um identificador exclusivo. GUIDs funcionam bem, e é fácil chamar a classe Guid do .NET Framework para gerar um; no entanto, ter um cmdlet faz com que isso seja mais detectável para os usuários finais que não ainda estão familiarizados com a classe do .NET Framework:

PS C:\\&gt; New-Guid

Guid

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
<!--HONumber=Mar16_HO2-->
