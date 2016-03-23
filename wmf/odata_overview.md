# Gerar cmdlets do PowerShell com base em um ponto de extremidade OData
Gerar cmdlets do Windows PowerShell com base em um ponto de extremidade OData
--------------------------------------------------------------

**Export-ODataEndpointProxy** é um cmdlet que gera um conjunto de cmdlets do Windows PowerShell com base na funcionalidade exposta por determinado ponto de extremidade OData.

O seguinte exemplo mostra como usar este novo cmdlet:

\# Caso de uso básico de Export-ODataEndpointProxy

```powershell
Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -OutputModule C:\Users\user\Generated.psd1

ipmo 'C:\Users\user\Generated.psd1'
# Cmdlets are created based on the following heuristics
# New-<EntityType> -<Key> [-<Other Attributes>]
#
# Get-<EntityType> [-<Key> -Top –Skip –Filter -OrderBy]
# # If there is a complex key, the keys will actually be -<Key1> -<Key2>…
# # Note this rule applies to any other instances of the key
#
# Set-<EntityType> -<Key> [-<Other Attributes>]
#
# Remove-<EntityType> -<Key>
#
# Invoke-<EntityType><Action> [-<Key> -<Other Parameters>]
#
#
# Cmdlets from associations (Note: Get and Remove get additional parameter sets)
# Get-<EntityType> -<AssociatedEntity>
# New-<EntityType> -<AssociatedEntity> -<Key>
# Remove-<EntityType> -<AssociatedEntity> -<Key>
#
#
# Note: Every cmdlet has the –ConnectionURI parameter for explicitly setting the URI of the endpoint. This normally uses the same address that you gave the Export-ODataEndpointProxy cmdlet, but can be overridden in this fashion for the sake of similar endpoints.
#
```

Ainda há partes de casos de uso básico em desenvolvimento para essa funcionalidade, incluindo, entre outros:
-   Associações
-   Fluxos para passar argumentos

Gerar cmdlets do Windows PowerShell com base em um ponto de extremidade OData com ODataUtils
------------------------------------------------------------------------------
O módulo ODataUtils permite a geração de cmdlets do Windows PowerShell de pontos de extremidade REST que dão suporte a OData. As seguintes melhorias incrementais estão no módulo Microsoft.PowerShell.ODataUtils do Windows PowerShell.
-   Informações adicionais do canal do ponto de extremidade do lado do servidor para o do lado do cliente.
-   Suporte à paginação do lado do cliente
-   Filtragem do lado do servidor usando o parâmetro -Select
-   Suporte para cabeçalhos de solicitação da Web

Os cmdlets do proxy gerados pelo cmdlet Export-ODataEndPointProxy fornecem informações adicionais (não mencionadas no $metadata usado durante a geração de proxy do lado do cliente) do ponto de extremidade OData do lado do servidor no Fluxo de informações (um novo recurso do Windows PowerShell 5.0). Aqui está um exemplo de como obter essas informações.
```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
Import-Module $generatedProxyModuleDir -Force

# In the below command, we are retrieving top 1 product.
# By specifying -IncludeTotalResponseCount parameter,
# we are getting the total count of all the Product records
# available on the server side. This information
# is surfaced on the client side through the Information stream.
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
# The Information stream contains the additional
# information sent from the server side.
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
# 'Odata.Count' indicates the total product records
# available on the server side Odata endpoint.
$additionalInfo['odata.count']
```

É possível obter os registros do lado do servidor em lotes usando o suporte à paginação do lado do cliente. Isso é útil quando é necessário obter uma grande quantidade de dados do servidor pela rede.
```powershell
$skipCount = 0
$batchSize = 3
# Client-Side Paging Support: The records from the server side
# are retrieved in batches of $batchSize
while($skipCount -le $additionalInfo['odata.count'])
{
Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
$skipCount += $batchSize
}
```

Os cmdlets do proxy gerados dão suporte ao parâmetro –Select, que pode ser usado como um filtro para receber apenas as propriedades de registro de que o cliente precisa. Isso reduz a quantidade de dados que são transferidos pela rede, pois a filtragem ocorre no lado do servidor.
```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

O cmdlet Export-ODataEndpointProxy, bem como os cmdlets do proxy gerados por ele, agora dão suporte ao parâmetro Headers (fornecem valores como uma tabela de hash), que pode ser usado para transmitir qualquer informação adicional esperada pelo ponto de extremidade OData do lado do servidor. No exemplo a seguir, é possível transmitir uma chave de Assinatura por meio de Cabeçalhos para serviços que esperam uma chave de Assinatura para autenticação.
```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
<!--HONumber=Mar16_HO2-->
