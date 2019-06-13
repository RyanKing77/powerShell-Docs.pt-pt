---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Executar Tarefas de Rede
ms.openlocfilehash: e581296b4b7609b374f206c447c4f797e3e2c400
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030867"
---
# <a name="performing-networking-tasks"></a>Executar Tarefas de Rede

Como o TCP/IP é o protocolo de rede mais comumente usada, a maioria das tarefas de administração de protocolo de rede de baixo nível envolvem TCP/IP. Nesta secção, vamos utilizar Windows PowerShell e o WMI para realizar estas tarefas.

## <a name="listing-ip-addresses-for-a-computer"></a>A listagem de endereços IP para um computador

Para obter todos os endereços IP em utilização no computador local, utilize o seguinte comando:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

O resultado deste comando é diferente da maioria das listas de propriedades, porque os valores são colocados entre chavetas:

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

Para compreender por que motivo são apresentadas as chavetas, utilize o cmdlet Get-Member para examinar os **IPAddress** propriedade:

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

A propriedade IPAddress para cada adaptador de rede é, na verdade, uma matriz. As chavetas na definição de indicam que **IPAddress** não é um **System. String** valor, mas uma matriz de **System. String** valores.

## <a name="listing-ip-configuration-data"></a>Dados de configuração de IP de listagem

Para apresentar dados de configuração de IP detalhados para cada adaptador de rede, utilize o seguinte comando:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

A apresentação predefinida para o objeto de configuração do adaptador de rede é um conjunto muito reduzido as informações disponíveis. Para inspeção aprofundada e resolução de problemas, utilize o Select-Object ou um cmdlet de formatação como, por exemplo, Format-List, para especificar as propriedades a serem exibidos.

Se não estiver interessado nas propriedades IPX ou o WINS, provavelmente o caso numa rede TCP/IP moderna — pode utilizar o parâmetro ExcludeProperty de Select-Object para ocultar propriedades com nomes que começam por "WINS" ou "IPX:"

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

Este comando devolve informações detalhadas sobre o encaminhamento DHCP, DNS e outras propriedades de configuração de IP secundárias.

## <a name="pinging-computers"></a>Computadores de ping

Pode executar ping simple num computador a utilizar pelo **Win32_PingStatus**. O seguinte comando efetua o ping, mas retorna longa saída:

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

Um mais útil formulário para informações de resumo de uma exibição das propriedades do endereço, o tempo de resposta e o StatusCode, à medida que gerados pelo seguinte comando. O parâmetro de dimensionamento automático do Format-Table redimensiona as colunas da tabela para que exibam corretamente no Windows PowerShell.

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

Um StatusCode de 0 indica um ping enviado com êxito.

Pode usar uma matriz para enviar um ping de vários computadores com um único comando. Como há mais de um endereço, utilize o **ForEach-Object** fazer ping a cada endereço separadamente:

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Pode utilizar o mesmo formato de comando para enviar um ping de todos os computadores numa sub-rede, como uma rede privada que utiliza o número de rede 192.168.1.0 e uma máscara de sub-rede classe C (255.255.255.0) padrão., são apenas de endereços no intervalo de 192.168.1.1 por meio de 192.168.1.254 legítimos endereços locais (0 é sempre reservado para o número de rede e 255 é um endereço de difusão de sub-rede).

Para representar uma matriz de números entre 1 e 254 no Windows PowerShell, utilize a instrução **1..254.** Pode ser executado um ping de sub-rede completa, gerando a matriz e, em seguida, adicionar os valores para um endereço parcial na declaração de ping:

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Tenha em atenção que esta técnica para gerar um intervalo de endereços pode ser utilizada noutro. Pode gerar um conjunto completo de endereços desta forma:

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a>Ao obter propriedades da placa de rede

Anteriormente no guia deste utilizador, mencionamos que foi possível obter as propriedades de configuração geral usando **Win32_NetworkAdapterConfiguration**. Embora não seja estritamente informações de TCP/IP, endereços de informações de adaptador de rede, tais como o MAC e os tipos de adaptador podem ser útil para entender o que está acontecendo com um computador. Para obter um resumo dessas informações, utilize o seguinte comando:

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a>Atribuir o domínio DNS para um adaptador de rede

Para atribuir o domínio DNS para resolução de nomes automática, utilize o **Win32_NetworkAdapterConfiguration SetDNSDomain** método. Como atribuir o domínio DNS para cada configuração de placa de rede de forma independente, precisa usar um **ForEach-Object** instrução para atribuir o domínio para cada adaptador:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

A instrução de filtragem "IPEnabled = $true" é necessário, porque, mesmo numa rede que utiliza apenas TCP/IP, várias das configurações de adaptador de rede num computador não são placas de TCP/IP verdadeiras; eles são os elementos de software geral de suporte RAS, PPTP, QoS e outros serviços de todos os adaptadores e, portanto, é necessário um endereço de seus próprios.

Pode filtrar o comando utilizando o **Where-Object** cmdlet, em vez de usar o **Get-WmiObject** filtro.

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a>Executar tarefas de configuração de DHCP

Modificar os detalhes DHCP envolve a trabalhar com um conjunto de adaptadores de rede, tal como faz a configuração de DNS. Existem várias ações distintas, que pode efetuar ao utilizar a WMI, e vamos conhecer alguns dos mais comuns.

### <a name="determining-dhcp-enabled-adapters"></a>Determinar os adaptadores de DHCP ativado

Para localizar os adaptadores de DHCP ativado num computador, utilize o seguinte comando:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

Para excluir adaptadores com problemas de configuração de IP, pode recuperar apenas os adaptadores habilitados no IP:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

### <a name="retrieving-dhcp-properties"></a>A obter propriedades DHCP

Uma vez que as propriedades relacionadas a DHCP para um adaptador em geral começam com "DHCP", pode utilizar o parâmetro de propriedade do Format-Table para exibir somente as propriedades:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a>Ativação do DHCP em cada adaptador

Para ativar o DHCP nos adaptadores de todos os, utilize o seguinte comando:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

Pode utilizar o **filtro** instrução "IPEnabled = $true e DHCPEnabled = $false" para evitar a ativação do DHCP em que já está a ser ativada, mas omitir este passo não causará erros.

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a>Lançar e renovações de concessões DHCP nos adaptadores específicos

O **Win32_NetworkAdapterConfiguration** classe tem **ReleaseDHCPLease** e **RenewDHCPLease** métodos. Ambos são usados da mesma forma. Em geral, use esses métodos se precisar apenas de versão ou renovar endereços de um adaptador numa sub-rede específica. A maneira mais fácil para os adaptadores de filtro numa sub-rede é escolher apenas as configurações de adaptador que utilizam o gateway para essa sub-rede. Por exemplo, o seguinte comando libera todas as concessões DHCP nos adaptadores no computador local que estão a obter concessões DHCP de 192.168.1.254:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

A única alteração por renovar uma concessão DHCP está a utilizar o **RenewDHCPLease** método em vez do **ReleaseDHCPLease** método:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> Ao usar esses métodos num computador remoto, lembre-se de que pode perder o acesso ao sistema remoto se estiver ligado à mesma através do adaptador com a concessão de lançamento ou renovado.

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a>Lançar e renovações de concessões DHCP em todos os adaptadores

Pode efetuar global versões de endereço DHCP ou renovações em todos os adaptadores ao utilizar o **Win32_NetworkAdapterConfiguration** métodos, **ReleaseDHCPLeaseAll** e **RenewDHCPLeaseAll** . No entanto, o comando tem de aplicar a classe WMI, em vez de uma determinada placa, porque a lançar e renovação de concessões globalmente é efetuada na classe, não num adaptador específico.

Pode obter uma referência a uma classe WMI, em vez de instâncias de classe, listando todas as classes WMI e, em seguida, selecionar apenas a classe pretendida por nome. Por exemplo, o comando seguinte devolve a classe Win32_NetworkAdapterConfiguration:

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

Pode tratar o comando inteiro como a classe e, em seguida, chamar o **ReleaseDHCPAdapterLease** método nele. No comando seguinte, os parênteses em torno da **Get-WmiObject** e **Where-Object** elementos de pipeline direcionar o Windows PowerShell para avaliá-los primeiro:

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

Pode utilizar o mesmo formato de comando para invocar a **RenewDHCPLeaseAll** método:

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a>Criar uma partilha de rede

Para criar uma partilha de rede, utilize o **Win32_Share criar** método:

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

Também pode criar a partilha usando **partilha de rede** no Windows PowerShell:

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a>Remover uma partilha de rede

Pode remover uma partilha de rede com **Win32_Share**, mas o processo é ligeiramente diferente da criação de uma partilha, uma vez que precisar de obter a partilha específica a ser removida, em vez de **Win32_Share** classe. A seguinte instrução elimina a partilha "TempShare":

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

**Partilha de rede** funciona bem:

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a>Ligar uma unidade de rede acessível do Windows

O **New-PSDrive** cmdlets cria uma unidade do Windows PowerShell, mas criadas dessa forma as unidades estão disponíveis apenas para o Windows PowerShell. Para criar uma nova unidade de rede, pode utilizar o **WScript** objeto COM. O comando seguinte mapeia a partilha \\ \\FPS01\\utilizadores para a unidade local b:

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

O **net use** comando também funciona:

```powershell
net use B: \\FPS01\users
```

Unidades mapeadas com ambos **WScript** ou net use imediatamente disponibilizadas para o Windows PowerShell.
