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
# <a name="performing-networking-tasks"></a>Executar Tarefas de Rede

Porque o TCP/IP é o protocolo de rede mais frequentemente utilizadas, a maioria das tarefas de administração de protocolo de rede de baixo nível envolvem TCP/IP. Nesta secção, utilizamos do Windows PowerShell e o WMI para efetuar estas tarefas.

### <a name="listing-ip-addresses-for-a-computer"></a>Lista de endereços IP para um computador

Para obter todos os endereços IP em utilização no computador local, utilize o seguinte comando:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

O resultado deste comando difere de acordo com a maioria das listas de propriedades, porque os valores são colocados entre chavetas:

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

Para compreender por que razão são apresentadas as chavetas, utilize o cmdlet Get-membro para examinar o **IPAddress** propriedade:

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

A propriedade IPAddress para cada adaptador de rede é, na verdade, uma matriz. As chavetas na definição do indicam que **IPAddress** não é um **String** valor, mas uma matriz de **String** valores.

### <a name="listing-ip-configuration-data"></a>Listar os dados de configuração de IP

Para apresentar dados de configuração de IP detalhados para cada adaptador de rede, utilize o seguinte comando:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

A apresentação predefinida para o objeto de configuração do adaptador de rede é um conjunto muito reduzido das informações disponíveis. Para inspeção aprofundada e resolução de problemas, utilize Select-Object ou um cmdlet de formatação, tais como formato-lista, para especificar as propriedades a apresentar.

Se não estiver interessado em propriedades IPX ou WINS — provavelmente as maiúsculas e minúsculas numa rede de TCP/IP moderna — pode utilizar o parâmetro ExcludeProperty Select-Object para ocultar propriedades com nomes que começam por "WINS" ou "IPX:"

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

Este comando devolve informações detalhadas sobre o DHCP, DNS, encaminhamento e outras propriedades de configuração de IP secundárias.

### <a name="pinging-computers"></a>Computadores de envio de ping

Pode efetuar um simple ping contra um computador a utilizar pelo **Win32_PingStatus**. O seguinte comando efetua o ping, mas devolve o resultado demorado:

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

Mais útil formulário para informações de resumo de uma visualização das propriedades do endereço, ResponseTime e StatusCode, à medida que gerados pelo seguinte comando. O parâmetro Autosize Format-Table redimensiona colunas da tabela para que possam aparecer corretamente no Windows PowerShell.

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

Um StatusCode do 0 indica um ping enviado com êxito.

Pode utilizar uma matriz ping a vários computadores com um único comando. Porque não há mais de um endereço, utilize o **ForEach-Object** em separado um ping a cada endereço:

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Pode utilizar o mesmo formato de comando ping a todos os computadores numa sub-rede, como uma rede privada que utiliza o número de rede 192.168.1.0 e uma máscara de sub-rede de classe C (255.255.255.0) padrão., apenas os endereços no intervalo de 192.168.1.1 através de 192.168.1.254 são legítimos endereços locais (0 é sempre reservado para o número de rede e 255 é um endereço de difusão de sub-rede).

Para representar uma matriz dos números entre 1 e 254 no Windows PowerShell, utilize a instrução **1..254.** Pode ser executado um ping de sub-rede concluída gerar a matriz e, em seguida, adicionando os valores para um endereço parcial na instrução ping:

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Tenha em atenção que esta técnica para a geração de um intervalo de endereços pode ser utilizada noutro local, bem como. Pode gerar um conjunto completo de endereços desta forma:

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

### <a name="retrieving-network-adapter-properties"></a>Obter as propriedades do adaptador de rede

Anteriormente, no Guia do utilizador, iremos mencionado que foi possível obter propriedades de configuração geral utilizando **Win32_NetworkAdapterConfiguration**. Embora não seja estritamente informações de TCP/IP, endereços de informações de adaptador de rede, tais como MAC e os tipos de placa podem ser útil para compreender o que se passa com um computador. Para obter um resumo destas informações, utilize o seguinte comando:

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

### <a name="assigning-the-dns-domain-for-a-network-adapter"></a>Atribuir o domínio DNS para um adaptador de rede

Para atribuir o domínio DNS para resolução automática de nomes, utilize o **Win32_NetworkAdapterConfiguration SetDNSDomain** método. Como atribuir o domínio DNS para cada configuração da placa de rede de forma independente, tem de utilizar um **ForEach-Object** instrução para atribuir o domínio a cada placa:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

A declaração de filtragem "IPEnabled = $true" é necessário, porque, mesmo numa rede que utiliza apenas TCP/IP, várias das configurações de adaptadores de rede num computador não são adaptadores de TCP/IP true; Estes são os elementos de software geral RAS, PPTP, QoS e outros serviços para todas as placas de suporte e, por conseguinte, não dispõe de um endereço os seus próprios.

Pode filtrar o comando utilizando a **Where-Object** cmdlet, em vez de utilizar o **Get-WmiObject** filtro.

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

### <a name="performing-dhcp-configuration-tasks"></a>Executar tarefas de configuração de DHCP

Modificar os detalhes DHCP envolve a trabalhar com um conjunto de adaptadores de rede, tal como sucede da configuração de DNS. Existem várias ações distintas, que pode realizar através da utilização de WMI e iremos irá seguir algumas das comuns dos.

#### <a name="determining-dhcp-enabled-adapters"></a>Determinar adaptadores preparados para DHCP

Para localizar os adaptadores de DHCP ativado num computador, utilize o seguinte comando:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

Para excluir adaptadores com problemas de configuração de IP, pode obter apenas os adaptadores IP ativados:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

#### <a name="retrieving-dhcp-properties"></a>Obter as propriedades DHCP

Porque as propriedades relacionadas com o DHCP para um adaptador geralmente começam com "DHCP", pode utilizar o parâmetro de propriedade de formato de tabela para apresentar apenas essas propriedades:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

#### <a name="enabling-dhcp-on-each-adapter"></a>Ativar o DHCP em cada adaptador

Para ativar o DHCP em todos os adaptadores, utilize o seguinte comando:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

Pode utilizar o **filtro** instrução "IPEnabled = $true e DHCPEnabled = $false" para evitar a ativar o DHCP em que já se encontra ativada, mas omitindo este passo não irá causar erros.

#### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a>Libertar e renovar concessões DHCP nos adaptadores específicos

O **Win32_NetworkAdapterConfiguration** classe tem **ReleaseDHCPLease** e **RenewDHCPLease** métodos. Ambos são utilizadas da mesma forma. Em geral, deve Utilize estes métodos se só precisa de libertação ou renovar endereços para um adaptador na sub-rede específica. A forma mais fácil para os adaptadores de filtro numa sub-rede é escolher apenas as configurações de adaptadores que utilizam o gateway para dessa sub-rede. Por exemplo, o seguinte comando versões todas as concessões DHCP nos adaptadores no computador local que estão a obter concessões de DHCP de 192.168.1.254:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

A única alteração para renovar uma concessão DHCP está a utilizar o **RenewDHCPLease** método em vez do **ReleaseDHCPLease** método:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> Ao utilizar estes métodos num computador remoto, lembre-se de que pode perder o acesso ao sistema remoto se estiverem ligados ao mesmo através do adaptador com o período de concessão lançado ou renovado.

#### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a>Libertar e renovar concessões DHCP em todos os adaptadores

Pode executar global versões de endereço DHCP ou renovações em todos os adaptadores utilizando o **Win32_NetworkAdapterConfiguration** métodos, **ReleaseDHCPLeaseAll** e **RenewDHCPLeaseAll** . No entanto, o comando tem de aplicar a classe WMI, em vez de uma determinada placa, porque libertar e renovar concessões global é efetuada na classe, não num adaptador específico.

Pode obter uma referência a uma classe WMI, em vez de instâncias de classe, ao listar todas as classes WMI e, em seguida, selecionar apenas a classe pretendida por nome. Por exemplo, o comando seguinte devolve a classe Win32_NetworkAdapterConfiguration:

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

Pode processar o comando completo como a classe e, em seguida, invoque o **ReleaseDHCPAdapterLease** método. O comando seguinte, parênteses envolvente o **Get-WmiObject** e **Where-Object** direcionam os elementos de pipeline do Windows PowerShell para avaliá-las primeiro:

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

Pode utilizar o mesmo formato de comando para invocar a **RenewDHCPLeaseAll** método:

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

### <a name="creating-a-network-share"></a>Criar uma partilha de rede

Para criar uma partilha de rede, utilize o **Win32_Share criar** método:

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

Também pode criar a partilha utilizando **partilha net** no Windows PowerShell:

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

### <a name="removing-a-network-share"></a>Remover uma partilha de rede

Pode remover uma partilha de rede com **Win32_Share**, mas o processo é ligeiramente diferente de criar uma partilha, porque terá de obter a partilha específica a serem removidos, em vez do **Win32_Share** classe. A seguinte instrução elimina a partilha "TempShare":

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

**Partilha de rede** funciona bem:

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

### <a name="connecting-a-windows-accessible-network-drive"></a>Ligar uma unidade de rede acessível do Windows

O **New-PSDrive** cmdlets cria uma unidade do Windows PowerShell, mas as unidades criadas desta forma estão disponíveis apenas para o Windows PowerShell. Para criar uma nova unidade de rede, pode utilizar o **WScript.Network** objecto COM. O seguinte comando mapeia a partilha \\ \\FPS01\\utilizadores para a unidade local b:

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

O **net utilize** comando funciona bem:

```powershell
net use B: \\FPS01\users
```

As unidades mapeadas com uma **WScript.Network** ou utilize net estão imediatamente disponíveis para o Windows PowerShell.