# Cmdlets da CMS (Sintaxe de Mensagem Criptografada)

Os cmdlets da Sintaxe de Mensagem Criptografada dão suporte à criptografia e descriptografia de conteúdo usando o formato padrão da IETF para proteger as mensagens criptograficamente, conforme documentado pelo [RFC5652](http://tools.ietf.org/html/rfc5652).

```powershell
Get-CmsMessage [-Content] <string>
Get-CmsMessage [-Path] <string>
Get-CmsMessage [-LiteralPath] <string>
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <string> [[-OutFile] <string>]
Unprotect-CmsMessage [-EventLogRecord] <EventLogRecord> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Content] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Path] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-LiteralPath] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
```

O padrão de criptografia CMS implementa a criptografia por chave pública, em que as chaves usadas para criptografar o conteúdo (a *chave pública*) e as chaves usadas para descriptografá-lo (a *chave privada*) são separadas.

Sua chave pública pode ser compartilhada amplamente e não contém dados confidenciais. Se algum conteúdo for criptografado com essa chave pública, somente sua chave privada poderá descriptografá-lo. Para obter mais informações sobre Criptografia por Chave Pública, veja: <http://en.wikipedia.org/wiki/Public-key_cryptography>.

Para ser reconhecidos no PowerShell, os certificados de criptografia exigem um EKU (identificador exclusivo de uso de chave) para identificá-los como certificados de criptografia de dados (como os identificadores para “Assinatura de Código”, “Mensagens Criptografadas”).

Aqui está um exemplo de como criar um certificado que seja válido para a Criptografia de Documento:

```powershell
(Change the text in **Subject** to your name, email, or other identifier), and put in a file (i.e.: DocumentEncryption.inf):
[Version]
Signature = "$Windows NT$"
[Strings]
szOID\_ENHANCED\_KEY\_USAGE = "2.5.29.37"
szOID\_DOCUMENT\_ENCRYPTION = "1.3.6.1.4.1.311.80.1"
[NewRequest]
Subject = "<cn=me@somewhere.com>"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT\_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT\_KEY\_ENCIPHERMENT\_KEY\_USAGE | CERT\_DATA\_ENCIPHERMENT\_KEY\_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"
[Extensions]
%szOID\_ENHANCED\_KEY\_USAGE% = "{text}%szOID\_DOCUMENT\_ENCRYPTION%"
```

Em seguida, execute:
```powershell
certreq -new DocumentEncryption.inf DocumentEncryption.cer
```

E agora você pode criptografar e descriptografar o conteúdo:

```powershell
$protected = "Hello World" | Protect-CmsMessage -To "\*me@somewhere.com\*[](mailto:*leeholm@microsoft.com*)"
$protected
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMMFWxlZWhv
bG1AbWljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYU5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNVmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPAwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84OHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1ZtDj7nSJc=
-----END CMS-----

$protected | Unprotect-CmsMessage
Hello World
```

Qualquer parâmetro do tipo **CMSMessageRecipient** dá suporte a identificadores nos seguintes formatos:
- Um certificado real (como aqueles recuperados pelo provedor de certificados)
- Caminho de um arquivo que contém o certificado
- Caminho de um diretório que contém o certificado
- Impressão digital do certificado (usada para pesquisar no repositório de certificados)
- Nome da entidade do certificado (usado para pesquisar no repositório de certificados)

Para exibir certificados de criptografia de documento no provedor de certificados, é possível usar o parâmetro dinâmico **-DocumentEncryptionCert**:

```powershell
dir -DocumentEncryptionCert
```

<!--HONumber=Jun16_HO4-->


