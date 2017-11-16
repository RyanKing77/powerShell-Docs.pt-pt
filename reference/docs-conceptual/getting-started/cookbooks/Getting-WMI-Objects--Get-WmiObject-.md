---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Objetos WMI ao obter obter WmiObject
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
ms.openlocfilehash: fbaac2797dd62eb03a2be581b3b5f8be6dafc0ad
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="getting-wmi-objects-get-wmiobject"></a>Obter os objetos WMI (Get-WmiObject)

## <a name="getting-wmi-objects-get-wmiobject"></a>Obter os objetos WMI (Get-WmiObject)
Windows Management Instrumentation (WMI) é uma tecnologia de núcleos para a administração de sistema do Windows porque expõe uma vasta gama de informações de forma uniforme. Devido à quantidade WMI torna possível, o cmdlet do Windows PowerShell para aceder a objetos WMI, **Get-WmiObject**, é uma das mais úteis para fazer o trabalho real. Vamos discutir como utilizar o Get-WmiObject para aceder a objetos WMI e, em seguida, como utilizar objetos WMI para efetuar ações específicas.

### <a name="listing-wmi-classes"></a>Listar as WMI Classes
O primeiro problema que ocorrer a maior parte dos utilizadores WMI está a tentar descobrir o que pode ser feito com WMI. WMI classes descrevem os recursos que podem ser geridos. Existem centenas de classes WMI, algumas das quais contém dezenas de propriedades.

**Get-WmiObject** resolve este problema ao efetuar WMI Detetáveis. Pode obter uma lista das classes WMI disponíveis no computador local, escrevendo:

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

Pode obter as mesmas informações de um computador remoto utilizando o parâmetro ComputerName, especificando um nome de computador ou endereço IP:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

A listagem de classe devolvida por computadores remotos pode variar devido ao sistema operativo específico, que o computador está em execução e as extensões WMI específicas adicionadas por aplicações instaladas.

> [!NOTE]
> Quando utiliza o Get-WmiObject para ligar a um computador remoto, o computador remoto tem de executar WMI e, em configuração predefinida, a conta que está a utilizar tem de estar no grupo de administradores locais no computador remoto. O sistema remoto não precisa de ter o Windows PowerShell instalada. Isto permite-lhe administrar os sistemas operativos que não estejam a executar o Windows PowerShell, mas ter WMI disponível.

Pode incluir ComputerName, mesmo quando estabelecer ligação com o sistema local. Pode utilizar o nome do computador local, o endereço IP (ou o endereço de loopback 127.0.0.1), ou o estilo de WMI '.' como o nome do computador. Se estiver a executar o Windows PowerShell num computador denominado Admin01 com o endereço IP 192.168.1.90, os seguintes comandos todas devolverá a classe WMI listagem desse computador:

```
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

Get-WmiObject utiliza o espaço de nomes de raiz/cimv2 por predefinição. Se pretender especificar outro espaço de nomes WMI, utilize o **espaço de nomes** parâmetro e especifique o caminho de espaço de nomes correspondente:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a>Apresentar detalhes da classe WMI
Se já conhece o nome de uma classe WMI, pode utilizá-lo para obter informações imediatamente. Por exemplo, uma das classes WMI normalmente utilizadas para obter informações sobre um computador é **Win32_OperatingSystem**.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

Embora iremos são Mostrar todos os parâmetros, os comandos podem ser expressas de forma mais sucinta. O **ComputerName** parâmetro não é necessário quando estabelecer ligação com o sistema local. Vamos mostrá-lo para demonstrar o cenário mais comum e relembrá-o sobre o parâmetro. O **espaço de nomes** será assumida a raiz/cimv2 e pode ser omitido bem. Por fim, a maioria dos cmdlets permitem-lhe omitir o nome dos parâmetros comuns. Com o Get-WmiObject, não se for especificado nenhum nome para o primeiro parâmetro, do Windows PowerShell trata-lo como o **classe** parâmetro. Isto significa que foram emitido o último comando, escrevendo:

```
Get-WmiObject Win32_OperatingSystem
```

O **Win32_OperatingSystem** classe tem muitas mais propriedades que são apresentados aqui. Pode utilizar o Get-membro para ver todas as propriedades. As propriedades de uma classe WMI estão automaticamente disponíveis como outras propriedades do objeto:

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Visualizar propriedades não predefinido com Cmdlets de formato
Se pretender que as informações contidas na **Win32_OperatingSystem** classe que não é apresentado por predefinição, pode apresentá-lo utilizando o **formato** cmdlets. Por exemplo, se pretender apresentar dados de memória disponível, escreva:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> Carateres universais trabalham com os nomes de propriedade no **Format-Table**, por isso, o elemento de final pipeline pode ser reduzido aos  **Format-Table-Total de propriedade*, livre*

Os dados de memória podem ser mais legíveis se formatar como uma lista escrevendo:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```

