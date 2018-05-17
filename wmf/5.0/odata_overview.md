---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 01d4989711c22db20431876c52740afb350caad0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="generate-powershell-cmdlets-based-on-odata-endpoint"></a>Gerar os Cmdlets do PowerShell com base no Ponto Final de OData
<a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint"></a>Gerar cmdlets do Windows PowerShell com base num ponto final de OData
--------------------------------------------------------------

**Exportação ODataEndpointProxy** é um cmdlet que gera um conjunto de cmdlets do Windows PowerShell com base na funcionalidade exposta por um determinado ponto final de OData.

O exemplo seguinte mostra como utilizar este cmdlet de novo:

\# Caso de utilização básica da exportação ODataEndpointProxy

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

Ainda existem partes de casos de utilização da chave de desenvolvimento para esta funcionalidade, incluindo, mas não se limitando a:
-   Associações
-   Fluxos de transmissão

<a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>Gerar cmdlets do Windows PowerShell com base num ponto final de OData com ODataUtils
------------------------------------------------------------------------------
O módulo de ODataUtils permite a geração de cmdlets do Windows PowerShell de pontos finais REST que suportam OData. Os seguintes melhoramentos incrementais são no módulo Microsoft.PowerShell.ODataUtils Windows PowerShell.
-   Canal informação adicional sobre o ponto final do lado do servidor para o lado do cliente.
-   Suporte de paginação do lado do cliente
-   Filtragem do lado do servidor utilizando o parâmetro-selecione
-   Suporte para os cabeçalhos de pedido web

Os cmdlets de proxy gerados pelo cmdlet Export-ODataEndPointProxy fornecem informações adicionais (não mencionadas no $metadata utilizado durante a geração de proxy do lado do cliente) do servidor de ponto final de OData lado no fluxo de informações (uma nova janela Funcionalidade de PowerShell 5.0). Eis um exemplo de como obter essa informação.
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

Pode obter os registos do lado do servidor em lotes utilizando o suporte de paginação do lado do cliente. Isto é útil quando tem de obter uma grande quantidade de dados do servidor através da rede.
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

Os cmdlets de proxy gerado suportam selecione parâmetro – que pode utilizar como um filtro para receber apenas as propriedades de registo que o cliente. Isto reduz a quantidade de dados que são transferidos através da rede, porque a filtragem ocorre no lado do servidor.
```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

O cmdlet Export-ODataEndpointProxy e os cmdlets de proxy gerados pelo, agora suporta o parâmetro de cabeçalhos (alimentação valores como uma tabela hash), que pode utilizar para o canal qualquer informação adicional que é esperada pelo ponto final de OData do lado do servidor. No exemplo seguinte, pode canal uma chave de subscrição através de cabeçalhos para serviços que está à espera de uma chave de subscrição para autenticação.
```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
