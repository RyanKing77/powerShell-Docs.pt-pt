---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Executar Tarefas de Rede
ms.assetid: a43cc55f-70c1-45c8-9467-eaad0d57e3b5
ms.openlocfilehash: 64c57c95a70bc4cad4b695a59d96673ed18afdf4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954131"
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="59e7b-103">Executar Tarefas de Rede</span><span class="sxs-lookup"><span data-stu-id="59e7b-103">Performing Networking Tasks</span></span>

<span data-ttu-id="59e7b-104">Porque o TCP/IP é o protocolo de rede mais frequentemente utilizadas, a maioria das tarefas de administração de protocolo de rede de baixo nível envolvem TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="59e7b-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="59e7b-105">Nesta secção, utilizamos do Windows PowerShell e o WMI para efetuar estas tarefas.</span><span class="sxs-lookup"><span data-stu-id="59e7b-105">In this section, we use Windows PowerShell and WMI to do these tasks.</span></span>

### <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="59e7b-106">Lista de endereços IP para um computador</span><span class="sxs-lookup"><span data-stu-id="59e7b-106">Listing IP Addresses for a Computer</span></span>

<span data-ttu-id="59e7b-107">Para obter todos os endereços IP em utilização no computador local, utilize o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="59e7b-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

<span data-ttu-id="59e7b-108">O resultado deste comando difere de acordo com a maioria das listas de propriedades, porque os valores são colocados entre chavetas:</span><span class="sxs-lookup"><span data-stu-id="59e7b-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

<span data-ttu-id="59e7b-109">Para compreender por que razão são apresentadas as chavetas, utilize o cmdlet Get-membro para examinar o **IPAddress** propriedade:</span><span class="sxs-lookup"><span data-stu-id="59e7b-109">To understand why the braces appear, use the Get-Member cmdlet to examine the **IPAddress** property:</span></span>

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

<span data-ttu-id="59e7b-110">A propriedade IPAddress para cada adaptador de rede é, na verdade, uma matriz.</span><span class="sxs-lookup"><span data-stu-id="59e7b-110">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="59e7b-111">As chavetas na definição do indicam que **IPAddress** não é um **String** valor, mas uma matriz de **String** valores.</span><span class="sxs-lookup"><span data-stu-id="59e7b-111">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

### <a name="listing-ip-configuration-data"></a><span data-ttu-id="59e7b-112">Listar os dados de configuração de IP</span><span class="sxs-lookup"><span data-stu-id="59e7b-112">Listing IP Configuration Data</span></span>

<span data-ttu-id="59e7b-113">Para apresentar dados de configuração de IP detalhados para cada adaptador de rede, utilize o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="59e7b-113">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

<span data-ttu-id="59e7b-114">A apresentação predefinida para o objeto de configuração do adaptador de rede é um conjunto muito reduzido das informações disponíveis.</span><span class="sxs-lookup"><span data-stu-id="59e7b-114">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="59e7b-115">Para inspeção aprofundada e resolução de problemas, utilize Select-Object ou um cmdlet de formatação, tais como formato-lista, para especificar as propriedades a apresentar.</span><span class="sxs-lookup"><span data-stu-id="59e7b-115">For in-depth inspection and troubleshooting, use Select-Object or a formatting cmdlet, such as Format-List, to specify the properties to be displayed.</span></span>

<span data-ttu-id="59e7b-116">Se não estiver interessado em propriedades IPX ou WINS — provavelmente as maiúsculas e minúsculas numa rede de TCP/IP moderna — pode utilizar o parâmetro ExcludeProperty Select-Object para ocultar propriedades com nomes que começam por "WINS" ou "IPX:"</span><span class="sxs-lookup"><span data-stu-id="59e7b-116">If you are not interested in IPX or WINS properties—probably the case in a modern TCP/IP network—you can use the ExcludeProperty parameter of Select-Object to hide properties with names that begin with "WINS" or "IPX:"</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="59e7b-117">Este comando devolve informações detalhadas sobre o DHCP, DNS, encaminhamento e outras propriedades de configuração de IP secundárias.</span><span class="sxs-lookup"><span data-stu-id="59e7b-117">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

### <a name="pinging-computers"></a><span data-ttu-id="59e7b-118">Computadores de envio de ping</span><span class="sxs-lookup"><span data-stu-id="59e7b-118">Pinging Computers</span></span>

<span data-ttu-id="59e7b-119">Pode efetuar um simple ping contra um computador a utilizar pelo **Win32_PingStatus**.</span><span class="sxs-lookup"><span data-stu-id="59e7b-119">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="59e7b-120">O seguinte comando efetua o ping, mas devolve o resultado demorado:</span><span class="sxs-lookup"><span data-stu-id="59e7b-120">The following command performs the ping, but returns lengthy output:</span></span>

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

<span data-ttu-id="59e7b-121">Mais útil formulário para informações de resumo de uma visualização das propriedades do endereço, ResponseTime e StatusCode, à medida que gerados pelo seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="59e7b-121">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="59e7b-122">O parâmetro Autosize Format-Table redimensiona colunas da tabela para que possam aparecer corretamente no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="59e7b-122">The Autosize parameter of Format-Table resizes the table columns so that they display properly in Windows PowerShell.</span></span>

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

<span data-ttu-id="59e7b-123">Um StatusCode do 0 indica um ping enviado com êxito.</span><span class="sxs-lookup"><span data-stu-id="59e7b-123">A StatusCode of 0 indicates a successful ping.</span></span>

<span data-ttu-id="59e7b-124">Pode utilizar uma matriz ping a vários computadores com um único comando.</span><span class="sxs-lookup"><span data-stu-id="59e7b-124">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="59e7b-125">Porque não há mais de um endereço, utilize o **ForEach-Object** em separado um ping a cada endereço:</span><span class="sxs-lookup"><span data-stu-id="59e7b-125">Because there is more than one address, use the **ForEach-Object** to ping each address separately:</span></span>

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="59e7b-126">Pode utilizar o mesmo formato de comando ping a todos os computadores numa sub-rede, como uma rede privada que utiliza o número de rede 192.168.1.0 e uma máscara de sub-rede de classe C (255.255.255.0) padrão., apenas os endereços no intervalo de 192.168.1.1 através de 192.168.1.254 são legítimos endereços locais (0 é sempre reservado para o número de rede e 255 é um endereço de difusão de sub-rede).</span><span class="sxs-lookup"><span data-stu-id="59e7b-126">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="59e7b-127">Para representar uma matriz dos números entre 1 e 254 no Windows PowerShell, utilize a instrução **1..254.**</span><span class="sxs-lookup"><span data-stu-id="59e7b-127">To represent an array of the numbers from 1 through 254 in Windows PowerShell, use the statement **1..254.**</span></span> <span data-ttu-id="59e7b-128">Pode ser executado um ping de sub-rede concluída gerar a matriz e, em seguida, adicionando os valores para um endereço parcial na instrução ping:</span><span class="sxs-lookup"><span data-stu-id="59e7b-128">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="59e7b-129">Tenha em atenção que esta técnica para a geração de um intervalo de endereços pode ser utilizada noutro local, bem como.</span><span class="sxs-lookup"><span data-stu-id="59e7b-129">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="59e7b-130">Pode gerar um conjunto completo de endereços desta forma:</span><span class="sxs-lookup"><span data-stu-id="59e7b-130">You can generate a complete set of addresses in this way:</span></span>

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

### <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="59e7b-131">Obter as propriedades do adaptador de rede</span><span class="sxs-lookup"><span data-stu-id="59e7b-131">Retrieving Network Adapter Properties</span></span>

<span data-ttu-id="59e7b-132">Anteriormente, no Guia do utilizador, iremos mencionado que foi possível obter propriedades de configuração geral utilizando **Win32_NetworkAdapterConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="59e7b-132">Earlier in this user's guide, we mentioned that you could retrieve general configuration properties by using **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="59e7b-133">Embora não seja estritamente informações de TCP/IP, endereços de informações de adaptador de rede, tais como MAC e os tipos de placa podem ser útil para compreender o que se passa com um computador.</span><span class="sxs-lookup"><span data-stu-id="59e7b-133">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="59e7b-134">Para obter um resumo destas informações, utilize o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="59e7b-134">To get a summary of this information, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

### <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="59e7b-135">Atribuir o domínio DNS para um adaptador de rede</span><span class="sxs-lookup"><span data-stu-id="59e7b-135">Assigning the DNS Domain for a Network Adapter</span></span>

<span data-ttu-id="59e7b-136">Para atribuir o domínio DNS para resolução automática de nomes, utilize o **Win32_NetworkAdapterConfiguration SetDNSDomain** método.</span><span class="sxs-lookup"><span data-stu-id="59e7b-136">To assign the DNS domain for automatic name resolution, use the **Win32_NetworkAdapterConfiguration SetDNSDomain** method.</span></span> <span data-ttu-id="59e7b-137">Como atribuir o domínio DNS para cada configuração da placa de rede de forma independente, tem de utilizar um **ForEach-Object** instrução para atribuir o domínio a cada placa:</span><span class="sxs-lookup"><span data-stu-id="59e7b-137">Because you assign the DNS domain for each network adapter configuration independently, you need to use a **ForEach-Object** statement to assign the domain to each adapter:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

<span data-ttu-id="59e7b-138">A declaração de filtragem "IPEnabled = $true" é necessário, porque, mesmo numa rede que utiliza apenas TCP/IP, várias das configurações de adaptadores de rede num computador não são adaptadores de TCP/IP true; Estes são os elementos de software geral RAS, PPTP, QoS e outros serviços para todas as placas de suporte e, por conseguinte, não dispõe de um endereço os seus próprios.</span><span class="sxs-lookup"><span data-stu-id="59e7b-138">The filtering statement "IPEnabled=$true" is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="59e7b-139">Pode filtrar o comando utilizando a **Where-Object** cmdlet, em vez de utilizar o **Get-WmiObject** filtro.</span><span class="sxs-lookup"><span data-stu-id="59e7b-139">You can filter the command by using the **Where-Object** cmdlet, instead of using the **Get-WmiObject** filter.</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

### <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="59e7b-140">Executar tarefas de configuração de DHCP</span><span class="sxs-lookup"><span data-stu-id="59e7b-140">Performing DHCP Configuration Tasks</span></span>

<span data-ttu-id="59e7b-141">Modificar os detalhes DHCP envolve a trabalhar com um conjunto de adaptadores de rede, tal como sucede da configuração de DNS.</span><span class="sxs-lookup"><span data-stu-id="59e7b-141">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="59e7b-142">Existem várias ações distintas, que pode realizar através da utilização de WMI e iremos irá seguir algumas das comuns dos.</span><span class="sxs-lookup"><span data-stu-id="59e7b-142">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

#### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="59e7b-143">Determinar adaptadores preparados para DHCP</span><span class="sxs-lookup"><span data-stu-id="59e7b-143">Determining DHCP-Enabled Adapters</span></span>

<span data-ttu-id="59e7b-144">Para localizar os adaptadores de DHCP ativado num computador, utilize o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="59e7b-144">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

<span data-ttu-id="59e7b-145">Para excluir adaptadores com problemas de configuração de IP, pode obter apenas os adaptadores IP ativados:</span><span class="sxs-lookup"><span data-stu-id="59e7b-145">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

#### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="59e7b-146">Obter as propriedades DHCP</span><span class="sxs-lookup"><span data-stu-id="59e7b-146">Retrieving DHCP Properties</span></span>

<span data-ttu-id="59e7b-147">Porque as propriedades relacionadas com o DHCP para um adaptador geralmente começam com "DHCP", pode utilizar o parâmetro de propriedade de formato de tabela para apresentar apenas essas propriedades:</span><span class="sxs-lookup"><span data-stu-id="59e7b-147">Because DHCP-related properties for an adapter generally begin with "DHCP," you can use the Property parameter of Format-Table to display only those properties:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

#### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="59e7b-148">Ativar o DHCP em cada adaptador</span><span class="sxs-lookup"><span data-stu-id="59e7b-148">Enabling DHCP on Each Adapter</span></span>

<span data-ttu-id="59e7b-149">Para ativar o DHCP em todos os adaptadores, utilize o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="59e7b-149">To enable DHCP on all adapters, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="59e7b-150">Pode utilizar o **filtro** instrução "IPEnabled = $true e DHCPEnabled = $false" para evitar a ativar o DHCP em que já se encontra ativada, mas omitindo este passo não irá causar erros.</span><span class="sxs-lookup"><span data-stu-id="59e7b-150">You can use the **Filter** statement "IPEnabled=$true and DHCPEnabled=$false" to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

#### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="59e7b-151">Libertar e renovar concessões DHCP nos adaptadores específicos</span><span class="sxs-lookup"><span data-stu-id="59e7b-151">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>

<span data-ttu-id="59e7b-152">O **Win32_NetworkAdapterConfiguration** classe tem **ReleaseDHCPLease** e **RenewDHCPLease** métodos.</span><span class="sxs-lookup"><span data-stu-id="59e7b-152">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="59e7b-153">Ambos são utilizadas da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="59e7b-153">Both are used in the same way.</span></span> <span data-ttu-id="59e7b-154">Em geral, deve Utilize estes métodos se só precisa de libertação ou renovar endereços para um adaptador na sub-rede específica.</span><span class="sxs-lookup"><span data-stu-id="59e7b-154">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="59e7b-155">A forma mais fácil para os adaptadores de filtro numa sub-rede é escolher apenas as configurações de adaptadores que utilizam o gateway para dessa sub-rede.</span><span class="sxs-lookup"><span data-stu-id="59e7b-155">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="59e7b-156">Por exemplo, o seguinte comando versões todas as concessões DHCP nos adaptadores no computador local que estão a obter concessões de DHCP de 192.168.1.254:</span><span class="sxs-lookup"><span data-stu-id="59e7b-156">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="59e7b-157">A única alteração para renovar uma concessão DHCP está a utilizar o **RenewDHCPLease** método em vez do **ReleaseDHCPLease** método:</span><span class="sxs-lookup"><span data-stu-id="59e7b-157">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="59e7b-158">Ao utilizar estes métodos num computador remoto, lembre-se de que pode perder o acesso ao sistema remoto se estiverem ligados ao mesmo através do adaptador com o período de concessão lançado ou renovado.</span><span class="sxs-lookup"><span data-stu-id="59e7b-158">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

#### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="59e7b-159">Libertar e renovar concessões DHCP em todos os adaptadores</span><span class="sxs-lookup"><span data-stu-id="59e7b-159">Releasing and Renewing DHCP Leases on All Adapters</span></span>

<span data-ttu-id="59e7b-160">Pode executar global versões de endereço DHCP ou renovações em todos os adaptadores utilizando o **Win32_NetworkAdapterConfiguration** métodos, **ReleaseDHCPLeaseAll** e **RenewDHCPLeaseAll** .</span><span class="sxs-lookup"><span data-stu-id="59e7b-160">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span> <span data-ttu-id="59e7b-161">No entanto, o comando tem de aplicar a classe WMI, em vez de uma determinada placa, porque libertar e renovar concessões global é efetuada na classe, não num adaptador específico.</span><span class="sxs-lookup"><span data-stu-id="59e7b-161">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="59e7b-162">Pode obter uma referência a uma classe WMI, em vez de instâncias de classe, ao listar todas as classes WMI e, em seguida, selecionar apenas a classe pretendida por nome.</span><span class="sxs-lookup"><span data-stu-id="59e7b-162">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="59e7b-163">Por exemplo, o comando seguinte devolve a classe Win32_NetworkAdapterConfiguration:</span><span class="sxs-lookup"><span data-stu-id="59e7b-163">For example, the following command returns the Win32_NetworkAdapterConfiguration class:</span></span>

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

<span data-ttu-id="59e7b-164">Pode processar o comando completo como a classe e, em seguida, invoque o **ReleaseDHCPAdapterLease** método.</span><span class="sxs-lookup"><span data-stu-id="59e7b-164">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="59e7b-165">O comando seguinte, parênteses envolvente o **Get-WmiObject** e **Where-Object** direcionam os elementos de pipeline do Windows PowerShell para avaliá-las primeiro:</span><span class="sxs-lookup"><span data-stu-id="59e7b-165">In the following command, the parentheses surrounding the **Get-WmiObject** and **Where-Object** pipeline elements direct Windows PowerShell to evaluate them first:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="59e7b-166">Pode utilizar o mesmo formato de comando para invocar a **RenewDHCPLeaseAll** método:</span><span class="sxs-lookup"><span data-stu-id="59e7b-166">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

### <a name="creating-a-network-share"></a><span data-ttu-id="59e7b-167">Criar uma partilha de rede</span><span class="sxs-lookup"><span data-stu-id="59e7b-167">Creating a Network Share</span></span>

<span data-ttu-id="59e7b-168">Para criar uma partilha de rede, utilize o **Win32_Share criar** método:</span><span class="sxs-lookup"><span data-stu-id="59e7b-168">To create a network share, use the **Win32_Share Create** method:</span></span>

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

<span data-ttu-id="59e7b-169">Também pode criar a partilha utilizando **partilha net** no Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="59e7b-169">You can also create the share by using **net share** in Windows PowerShell:</span></span>

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

### <a name="removing-a-network-share"></a><span data-ttu-id="59e7b-170">Remover uma partilha de rede</span><span class="sxs-lookup"><span data-stu-id="59e7b-170">Removing a Network Share</span></span>

<span data-ttu-id="59e7b-171">Pode remover uma partilha de rede com **Win32_Share**, mas o processo é ligeiramente diferente de criar uma partilha, porque terá de obter a partilha específica a serem removidos, em vez do **Win32_Share** classe.</span><span class="sxs-lookup"><span data-stu-id="59e7b-171">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="59e7b-172">A seguinte instrução elimina a partilha "TempShare":</span><span class="sxs-lookup"><span data-stu-id="59e7b-172">The following statement deletes the share "TempShare":</span></span>

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="59e7b-173">**Partilha de rede** funciona bem:</span><span class="sxs-lookup"><span data-stu-id="59e7b-173">**Net share** works as well:</span></span>

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

### <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="59e7b-174">Ligar uma unidade de rede acessível do Windows</span><span class="sxs-lookup"><span data-stu-id="59e7b-174">Connecting a Windows Accessible Network Drive</span></span>

<span data-ttu-id="59e7b-175">O **New-PSDrive** cmdlets cria uma unidade do Windows PowerShell, mas as unidades criadas desta forma estão disponíveis apenas para o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="59e7b-175">The **New-PSDrive** cmdlets creates a Windows PowerShell drive, but drives created this way are available only to Windows PowerShell.</span></span> <span data-ttu-id="59e7b-176">Para criar uma nova unidade de rede, pode utilizar o **WScript.Network** objecto COM.</span><span class="sxs-lookup"><span data-stu-id="59e7b-176">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="59e7b-177">O seguinte comando mapeia a partilha \\ \\FPS01\\utilizadores para a unidade local b:</span><span class="sxs-lookup"><span data-stu-id="59e7b-177">The following command maps the share \\\\FPS01\\users to local drive B:</span></span>

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

<span data-ttu-id="59e7b-178">O **net utilize** comando funciona bem:</span><span class="sxs-lookup"><span data-stu-id="59e7b-178">The **net use** command works as well:</span></span>

```powershell
net use B: \\FPS01\users
```

<span data-ttu-id="59e7b-179">As unidades mapeadas com uma **WScript.Network** ou utilize net estão imediatamente disponíveis para o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="59e7b-179">Drives mapped with either **WScript.Network** or net use are immediately available to Windows PowerShell.</span></span>