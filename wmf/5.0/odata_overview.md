---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 1153738fdf6f926d5d819bbf91450408dcb17f71
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794502"
---
# <a name="generate-powershell-cmdlets-based-on-odata-endpoint"></a><span data-ttu-id="f4fa4-102">Gerar os Cmdlets do PowerShell com base no Ponto Final de OData</span><span class="sxs-lookup"><span data-stu-id="f4fa4-102">Generate PowerShell Cmdlets based on OData Endpoint</span></span>

## <a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint"></a><span data-ttu-id="f4fa4-103">Gerar os cmdlets do Windows PowerShell com base num ponto de final de OData</span><span class="sxs-lookup"><span data-stu-id="f4fa4-103">Generate Windows PowerShell cmdlets based on an OData endpoint</span></span>

<span data-ttu-id="f4fa4-104">**Exportação ODataEndpointProxy** é um cmdlet que gera um conjunto de cmdlets do Windows PowerShell com base na funcionalidade exposta por um determinado ponto de final de OData.</span><span class="sxs-lookup"><span data-stu-id="f4fa4-104">**Export-ODataEndpointProxy** is a cmdlet that generates a set of Windows PowerShell cmdlets based on the functionality exposed by a given OData endpoint.</span></span>

<span data-ttu-id="f4fa4-105">O exemplo seguinte mostra como utilizar o novo cmdlet:</span><span class="sxs-lookup"><span data-stu-id="f4fa4-105">The following example shows how to use this new cmdlet:</span></span>

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

<span data-ttu-id="f4fa4-106">Ainda há partes de casos de utilização de chaves no desenvolvimento para essa funcionalidade, incluindo, mas não limitado a:</span><span class="sxs-lookup"><span data-stu-id="f4fa4-106">There are still parts of key use cases in development for this functionality, including, but not limited to:</span></span>
-   <span data-ttu-id="f4fa4-107">Associações</span><span class="sxs-lookup"><span data-stu-id="f4fa4-107">Associations</span></span>
-   <span data-ttu-id="f4fa4-108">Fluxos de aprovação</span><span class="sxs-lookup"><span data-stu-id="f4fa4-108">Passing streams</span></span>

## <a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="f4fa4-109">Gerar os cmdlets do Windows PowerShell com base num ponto de final de OData com ODataUtils</span><span class="sxs-lookup"><span data-stu-id="f4fa4-109">Generate Windows PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>

<span data-ttu-id="f4fa4-110">O módulo de ODataUtils permite a geração de cmdlets do Windows PowerShell a partir de pontos de extremidade REST que dão suporte a OData.</span><span class="sxs-lookup"><span data-stu-id="f4fa4-110">The ODataUtils module allows generation of Windows PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="f4fa4-111">Os seguintes melhoramentos incrementais estão no módulo Microsoft.PowerShell.ODataUtils Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f4fa4-111">The following incremental enhancements are in the Microsoft.PowerShell.ODataUtils Windows PowerShell module.</span></span>
-   <span data-ttu-id="f4fa4-112">Canal de informações adicionais do ponto de extremidade do lado do servidor para o lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="f4fa4-112">Channel additional information from server-side endpoint to client side.</span></span>
-   <span data-ttu-id="f4fa4-113">Suporte de paginação do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="f4fa4-113">Client-side paging support</span></span>
-   <span data-ttu-id="f4fa4-114">Filtragem do lado do servidor utilizando o - parâmetro selecione</span><span class="sxs-lookup"><span data-stu-id="f4fa4-114">Server-side filtering by using the -Select parameter</span></span>
-   <span data-ttu-id="f4fa4-115">Suporte para cabeçalhos de solicitação da web</span><span class="sxs-lookup"><span data-stu-id="f4fa4-115">Support for web request headers</span></span>

<span data-ttu-id="f4fa4-116">Os cmdlets do proxy gerados pelo cmdlet Export-ODataEndPointProxy fornecem informações adicionais (não mencionadas no $metadata utilizado durante a geração de proxy do lado do cliente) do servidor de ponto final de OData do lado no fluxo de informações (um novo Windows Funcionalidade de PowerShell 5.0).</span><span class="sxs-lookup"><span data-stu-id="f4fa4-116">The proxy cmdlets generated by the Export-ODataEndPointProxy cmdlet provide additional information (not mentioned in the $metadata used during the client-side proxy generation) from the server side OData endpoint on the Information stream (a new Windows PowerShell 5.0 feature).</span></span> <span data-ttu-id="f4fa4-117">Eis um exemplo de como obter essas informações.</span><span class="sxs-lookup"><span data-stu-id="f4fa4-117">Here is an example of how to get that information.</span></span>

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

<span data-ttu-id="f4fa4-118">Pode obter os registos do lado do servidor em lotes com o suporte de paginação do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="f4fa4-118">You can get the records from the server side in batches by using client-side paging support.</span></span> <span data-ttu-id="f4fa4-119">Isto é útil quando tem de obter uma grande quantidade de dados do servidor através da rede.</span><span class="sxs-lookup"><span data-stu-id="f4fa4-119">This is useful when you must get a large amount of data from the server over the network.</span></span>

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

<span data-ttu-id="f4fa4-120">Os cmdlets do proxy gerado suportam o selecione parâmetro – que pode ser usado como um filtro para receber apenas as propriedades de registo que o cliente precisa.</span><span class="sxs-lookup"><span data-stu-id="f4fa4-120">The generated proxy cmdlets support the –Select parameter which you can use as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="f4fa4-121">Isso reduz a quantidade de dados que são transferidos através da rede, uma vez que a filtragem ocorre no lado do servidor.</span><span class="sxs-lookup"><span data-stu-id="f4fa4-121">This reduces the amount of data that is transferred over the network, because the filtering occurs on the server side.</span></span>

```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="f4fa4-122">O cmdlet Export-ODataEndpointProxy e os cmdlets do proxy gerados por ele, agora suporta o parâmetro de cabeçalhos (fonte de alimentação valores como uma tabela de hash), que pode utilizar para qualquer informação adicional que é esperada pelo ponto de final de OData do lado do servidor de canal.</span><span class="sxs-lookup"><span data-stu-id="f4fa4-122">The Export-ODataEndpointProxy cmdlet, and the proxy cmdlets generated by it, now support the Headers parameter (supply values as a hash table), which you can use to channel any additional information that is expected by the server-side OData endpoint.</span></span> <span data-ttu-id="f4fa4-123">No exemplo a seguir, pode canalizar uma chave de assinatura por meio de cabeçalhos para serviços que esperam uma chave de subscrição para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="f4fa4-123">In the following example, you can channel a Subscription key through Headers for services that are expecting a Subscription key for authentication.</span></span>

```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
