---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Obter objetos WMI obtém WmiObject
ms.openlocfilehash: 93276ce12135342af2d6f238976e65e5d8bdde7a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030211"
---
# <a name="getting-wmi-objects-get-wmiobject"></a>Obter objetos WMI (Get-WmiObject)

## <a name="getting-wmi-objects-get-wmiobject"></a>Obter objetos WMI (Get-WmiObject)

Windows Management Instrumentation (WMI) é uma tecnologia de núcleos para a administração de sistema do Windows porque ela expõe uma vasta gama de informações de forma uniforme. Devido a quanto o WMI torna possível, o cmdlet do Windows PowerShell para o acesso a objetos WMI **Get-WmiObject**, é um dos mais úteis para fazer o trabalho real. Vamos discutir como usar o Get-WmiObject para acessar objetos do WMI e, em seguida, como utilizar objetos WMI para fazer coisas específicas.

### <a name="listing-wmi-classes"></a>Listagem Classes WMI

O primeiro problema que encontrar a maioria dos usuários WMI está tentando descobrir o que pode ser feito com o WMI. WMI classes descrevem os recursos que podem ser geridos. Há centenas de classes WMI, alguns dos quais contêm dezenas de propriedades.

**Get-WmiObject** resolve este problema, tornando o WMI Detetáveis. Pode obter uma lista das classes WMI disponíveis no computador local digitando:

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

Pode recuperar as mesmas informações de um computador remoto utilizando o parâmetro ComputerName, especificando um nome de computador ou endereço IP:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

A listagem de classe devolvida por computadores remotos pode variar por sistema operativo específico, que o computador está em execução e as extensões WMI particulares adicionadas por aplicativos instalados.

> [!NOTE]
> Ao utilizar Get-WmiObject para ligar a um computador remoto, o computador remoto deve estar em execução WMI e, sob a configuração predefinida, a conta que está a utilizar tem de estar no grupo de administradores locais no computador remoto. O sistema remoto não é necessário ter o PowerShell de Windows instalado. Isso permite que a administração de sistemas operativos que não estejam a executar o Windows PowerShell, mas têm WMI disponível.

Pode incluir ComputerName ao ligar ao sistema local. Pode utilizar o nome do computador local, o endereço IP (ou o endereço de loopback 127.0.0.1), ou o estilo de WMI "." como o nome do computador. Se estiver a executar o Windows PowerShell num computador denominado Admin01 com o endereço IP 192.168.1.90, os seguintes comandos todos retornará a classe WMI de listagem para esse computador:

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

Get-WmiObject utiliza o espaço de nomes de raiz/cimv2, por predefinição. Se pretender especificar outro espaço de nomes WMI, utilize o **espaço de nomes** parâmetro e especificar o caminho de espaço de nomes correspondente:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a>Exibição de detalhes da classe de WMI

Se já sabe o nome de uma classe WMI, pode usar para obter informações de imediato. Por exemplo, uma das classes WMI comumente usadas para recuperar informações sobre um computador é **Win32_OperatingSystem**.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

Embora estamos mostrando todos os parâmetros, o comando pode ser expresso de forma mais sucinta. O **ComputerName** parâmetro não é necessário quando se liga ao sistema local. Vamos mostrá-lo para demonstrar o caso mais comum e lembrá-lo sobre o parâmetro. O **espaço de nomes** utiliza por predefinição a raiz/cimv2 e pode ser omitida também. Por fim, a maioria dos cmdlets permitem-lhe omitir o nome dos parâmetros comuns. Com o Get-WmiObject, não se for especificado nenhum nome para o primeiro parâmetro, Windows PowerShell trata-a como o **classe** parâmetro. Isso significa que foram emitido o último comando, digitando:

```powershell
Get-WmiObject Win32_OperatingSystem
```

O **Win32_OperatingSystem** classe tem muitas propriedades adicionais que são apresentados aqui. Pode usar o Get-Member para ver todas as propriedades. As propriedades de uma classe WMI estão automaticamente disponíveis, como de outras propriedades de objeto:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Get-Member -MemberType Property

   TypeName: System.Management.ManagementObject#root\cimv2\Win32_OperatingSyste
m

Name                                      MemberType Definition
----                                      ---------- ----------
__CLASS                                   Property   System.String __CLASS {...
...
BootDevice                                Property   System.String BootDevic...
BuildNumber                               Property   System.String BuildNumb...
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Visualizar propriedades de não-padrão com Cmdlets de formato

Se pretender que as informações contidas no **Win32_OperatingSystem** isto é a classe não é apresentado por predefinição, pode apresentá-lo utilizando o **formato** cmdlets. Por exemplo, se desejar exibir dados de memória disponível, escreva:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> Carateres universais funcionam com nomes de propriedade no **Format-Table**, por isso, o elemento de final pipeline pode ser reduzido a `Format-Table -Property Total,Free`

Os dados de memória podem ser mais legíveis, se formatar como uma lista ao escrever:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
