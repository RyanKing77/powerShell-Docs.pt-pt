---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Recolher Informações sobre os Computadores
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: ca92474eaf6fa546c3d6450f5a282e45157018a8
ms.sourcegitcommit: 4a841ebda3339ae2477e0f5f5be8c01740221232
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/07/2018
ms.locfileid: "33677319"
---
# <a name="collecting-information-about-computers"></a>Recolher Informações sobre os Computadores

Os cmdlets da **CimCmdlets** módulo são os cmdlets mais importantes para tarefas de gestão de sistema geral.
Todas as definições de subsistema críticas são expostas através do WMI.
Além disso, o WMI trata dados como objetos que estão em coleções de um ou mais itens.
Porque o Windows PowerShell também funciona com objetos e tem um pipeline que permite-lhe tratar único ou vários objetos da mesma forma, o acesso WMI genérico permite-lhe efetuar algumas tarefas avançadas com pouco trabalho.

Os exemplos seguintes demonstram como recolher informações específicas, utilizando `Get-CimInstance` contra um computador arbitrário.
Especificamos o **ComputerName** parâmetro com o valor de ponto (**.**), que representa o computador local.
Pode especificar um nome ou endereço IP associado a qualquer computador que pode aceder através do WMI.
Para obter informações sobre o computador local, pode omitir o **ComputerName** parâmetro.

### <a name="listing-desktop-settings"></a>Definições de ambiente de trabalho de listagem

Iremos irá começar com um comando que recolhe informações sobre os ambientes de trabalho no computador local.

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

Esta ação devolve informações para todos os ambientes de trabalho, quer sejam em utilização ou não.

> [!NOTE]
> As informações devolvidas pelo algumas classes WMI podem ser muito detalhada e, muitas vezes, incluir metadados sobre a classe WMI.
Porque a maioria destas propriedades de metadados tem nomes que começam por **Cim**, pode filtrar as propriedades utilizando `Select-Object`.
Especifique o **- ExcludeProperty** parâmetro com "Cim *" como valor.
Por exemplo:

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Para filtrar os metadados, utilize um operador de pipeline (|) para enviar os resultados do `Get-CimInstance` comando para `Select-Object -ExcludeProperty "CIM*"`.

### <a name="listing-bios-information"></a>Listar informações do BIOS

O WMI **Win32_BIOS** classe devolve informações bastante compact e completas sobre o BIOS do sistema no computador local:

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a>Listar as informações do processador

Pode obter informações do processador geral através do WMI **Win32_Processor** classe, embora irá provavelmente pretender filtrar as informações:

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Descrição genérico de uma cadeia a família de processadores, apenas pode devolver o **SystemType** propriedade:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a>Listar o computador fabricante e modelo

Informações de modelo do computador também estão disponíveis no **Win32_ComputerSystem**.
A saída padrão apresentada não terá qualquer filtragem para fornecer dados OEM:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

A saída de comandos como esta, que devolvem informações diretamente a partir de algum hardware, apenas é como boa como os dados que tem.
Algumas informações não está corretamente configuradas por fabricantes de hardware e podem, por conseguinte, não estar disponíveis.

### <a name="listing-installed-hotfixes"></a>Listagem instaladas as correções

Pode listar correções instaladas todas as utilizando **Win32_QuickFixEngineering**:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

Esta classe devolve uma lista de correções que tem este aspeto:

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

Para uma saída mais sucinta, pode pretender excluir algumas propriedades.
Apesar de poder utilizar o `Get-CimInstance`do **propriedade** parâmetro escolher apenas o **HotFixID**, fazê-lo, por isso, irão devolver mais informações, porque todos os metadados é apresentado por predefinição:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixID
```

```output
PSShowComputerName    : True
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4048951
InstalledBy           :
ServicePackInEffect   :
PSComputerName        : .
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

Os dados adicionais são devolvidos porque o parâmetro de propriedade em `Get-CimInstance` restringe as propriedades devolvidas de instâncias de classe WMI, não o objeto devolvido para o Windows PowerShell.
Para reduzir a saída, utilize `Select-Object`:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

### <a name="listing-operating-system-version-information"></a>Listar as informações de versão do sistema operativo

O **Win32_OperatingSystem** propriedades de classe incluem informações de pacote de versão e serviço.
Pode selecionar explicitamente só estas propriedades para obter informações de versão um resumo de **Win32_OperatingSystem**:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

Também pode utilizar carateres universais com o `Select-Object`do **propriedade** parâmetro.
Porque todas as propriedades começando com um **criar** ou **ServicePack** são importantes para utilizar aqui, iremos pode abreviar este para o seguinte formato:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*
```

```output
BuildNumber             : 16299
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a>Listar utilizadores locais e proprietário

Informações gerais de utilizadores local — número de utilizadores licenciados, o número atual de utilizadores e o nome do proprietário — pode ser encontrado com uma seleção de **Win32_OperatingSystem** propriedades dos classe.
Pode selecionar explicitamente as propriedades a apresentar como esta:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Uma versão mais sucinta utilizando carateres universais é:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a>Ao obter espaço livre em disco

Para ver o espaço em disco e o espaço livre para unidades locais, pode utilizar a classe Win32_LogicalDisk WMI.
É necessário ver apenas instâncias com um DriveType de 3 — valor utiliza o WMI para discos rígidos de fixo.

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .

Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum

Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

### <a name="getting-logon-session-information"></a>Obter informações de sessão de início de sessão

Pode obter informações gerais sobre sessões de início de sessão associados a utilizadores através de **Win32_LogonSession** classe WMI:

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a>Obter o utilizador com sessão iniciado num computador

Pode visualizar o utilizador com sessão iniciado num sistema informático específico utilizando Win32_ComputerSystem.
Este comando devolve apenas o utilizador com sessão iniciado no ambiente de trabalho do sistema:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a>Obter a hora Local do computador

Pode obter a hora local atual num computador específico utilizando o **Win32_LocalTime** classe WMI.

```powershell
Get-CimInstance -ClassName Win32_LocalTime -ComputerName .

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2017
PSComputerName : .
```

### <a name="displaying-service-status"></a>Apresentar o estado do serviço

Para ver o estado de todos os serviços num computador específico, localmente pode utilizar o `Get-Service` cmdlet.
Para sistemas remotos, pode utilizar o **Win32_Service** classe WMI.
Se também de utilizar `Select-Object` para filtrar os resultados para **estado**, **nome**, e **DisplayName**, o formato de saída serão praticamente idêntico à `Get-Service`:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Para permitir a apresentação de nomes para os serviços ocasionais com nomes extremamente longos concluída, pode pretender utilizar `Format-Table` com o **AutoSize** e **moldar** parâmetros, para otimizar a largura da coluna e Permita nomes longos moldar em vez de a ser truncado:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
