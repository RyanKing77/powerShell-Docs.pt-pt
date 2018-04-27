---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Recolher Informações sobre os Computadores
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: 7f5a5f6accd57a84e2bcb3d20c14640a8e028791
ms.sourcegitcommit: a9aa5e8d0fab0cbb3e4e6cff0e3ca8c0339ab4e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/27/2018
---
# <a name="collecting-information-about-computers"></a>Recolher Informações sobre os Computadores

**Get-WmiObject** é o cmdlet mais importante para o sistema geral, as tarefas de gestão. Todas as definições de subsistema críticas são expostas através do WMI. Além disso, o WMI trata dados como objetos que estão em coleções de um ou mais itens. Porque o Windows PowerShell também funciona com objetos e tem um pipeline que permite-lhe tratar único ou vários objetos da mesma forma, o acesso WMI genérico permite-lhe efetuar algumas tarefas avançadas com pouco trabalho.

Os exemplos seguintes demonstram como recolher informações específicas, utilizando **Get-WmiObject** contra um computador arbitrário. Especificamos o **ComputerName** parâmetro com o valor de ponto (**.**), que representa o computador local. Pode especificar um nome ou endereço IP associado a qualquer computador que pode aceder através do WMI. Para obter informações sobre o computador local, pode omitir o **- ComputerName.**

### <a name="listing-desktop-settings"></a>Definições de ambiente de trabalho de listagem

Iremos irá começar com um comando que recolhe informações sobre os ambientes de trabalho no computador local.

```powershell
Get-WmiObject -Class Win32_Desktop -ComputerName .
```

Esta ação devolve informações para todos os ambientes de trabalho, quer sejam em utilização ou não.

> [!NOTE]
> As informações devolvidas pelo algumas classes WMI podem ser muito detalhada e, muitas vezes, incluir metadados sobre a classe WMI. Porque a maioria destas propriedades de metadados tem nomes que começam com um caráter de sublinhado duplo, pode filtrar as propriedades utilizando Select-Object. Especifique apenas as propriedades que começam com carateres alfabéticos utilizando **[a-z]*** como o valor da propriedade. Por exemplo:

```powershell
Get-WmiObject -Class Win32_Desktop -ComputerName . | Select-Object -Property [a-z]*
```

Para filtrar os metadados, utilize um operador de pipeline (|) para enviar os resultados do comando Get-WmiObject para `Select-Object -Property [a-z]*`.

### <a name="listing-bios-information"></a>Listar informações do BIOS

A classe WMI Win32_BIOS devolve informações bastante compact e completas sobre o BIOS do sistema no computador local:

```powershell
Get-WmiObject -Class Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a>Listar as informações do processador

Pode obter informações do processador geral através do WMI **Win32_Processor** classe, embora irá provavelmente pretender filtrar as informações:

```powershell
Get-WmiObject -Class Win32_Processor -ComputerName . | Select-Object -Property [a-z]*
```

Descrição genérico de uma cadeia a família de processadores, apenas pode devolver o **SystemType** propriedade:

```
PS> Get-WmiObject -Class Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a>Listar o computador fabricante e modelo

Informações de modelo do computador também estão disponíveis no **Win32_ComputerSystem**. A saída padrão apresentada não terá qualquer filtragem para fornecer dados OEM:

```
PS> Get-WmiObject -Class Win32_ComputerSystem

Domain              : WORKGROUP
Manufacturer        : Compaq Presario 06
Model               : DA243A-ABA 6415cl NA910
Name                : MyPC
PrimaryOwnerName    : Jane Doe
TotalPhysicalMemory : 804765696
```

A saída de comandos como esta, que devolvem informações diretamente a partir de algum hardware, apenas é como boa como os dados que tem. Algumas informações não está corretamente configuradas por fabricantes de hardware e podem, por conseguinte, não estar disponíveis.

### <a name="listing-installed-hotfixes"></a>Listagem instaladas as correções

Pode listar correções instaladas todas as utilizando **Win32_QuickFixEngineering**:

```powershell
Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName .
```

Esta classe devolve uma lista de correções que tem este aspeto:

```output
Description         : Update for Windows XP (KB910437)
FixComments         : Update
HotFixID            : KB910437
Install Date        :
InstalledBy         : Administrator
InstalledOn         : 12/16/2005
Name                :
ServicePackInEffect : SP3
Status              :
```

Para uma saída mais sucinta, pode pretender excluir algumas propriedades. Apesar de poder utilizar o **propriedade Get-WmiObject** parâmetro escolher apenas o **HotFixID**, fazê-lo, por isso, irão devolver mais informações, porque todos os metadados é apresentado por predefinição:

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixID

HotFixID         : KB910437
__GENUS          : 2
__CLASS          : Win32_QuickFixEngineering
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
```

Os dados adicionais são devolvidos porque o parâmetro de propriedade em **Get-WmiObject** restringe as propriedades devolvidas de instâncias de classe WMI, não o objeto devolvido para o Windows PowerShell. Para reduzir a saída, utilize **Select-Object**:

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId

HotFixId
--------
KB910437
```

### <a name="listing-operating-system-version-information"></a>Listar as informações de versão do sistema operativo

O **Win32_OperatingSystem** propriedades de classe incluem informações de pacote de versão e serviço. Pode selecionar explicitamente só estas propriedades para obter informações de versão um resumo de **Win32_OperatingSystem**:

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

Também pode utilizar carateres universais com o **propriedade Select-Object** parâmetro. Porque todas as propriedades começando com um **criar** ou **ServicePack** são importantes para utilizar aqui, iremos pode abreviar este para o seguinte formato:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*

BuildNumber             : 2600
BuildType               : Uniprocessor Free
OSType                  : 18
ServicePackMajorVersion : 2
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a>Listar utilizadores locais e proprietário

Informações gerais de utilizadores local — número de utilizadores licenciados, o número atual de utilizadores e o nome do proprietário — pode ser encontrado com uma seleção de **Win32_OperatingSystem** propriedades. Pode selecionar explicitamente as propriedades a apresentar como esta:

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Uma versão mais sucinta utilizando carateres universais é:

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a>Ao obter espaço livre em disco

Para ver o espaço em disco e o espaço livre para unidades locais, pode utilizar a classe WMI Win32_LogicalDisk. É necessário ver apenas instâncias com um DriveType de 3 — valor utiliza o WMI para discos rígidos de fixo.

```
PS> Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 65541357568
Size         : 203912880128
VolumeName   : Local Disk

DeviceID     : Q:
DriveType    : 3
ProviderName :
FreeSpace    : 44298250240
Size         : 122934034432
VolumeName   : New Volume

PS> Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum

Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

### <a name="getting-logon-session-information"></a>Obter informações de sessão de início de sessão

Pode obter informações gerais sobre sessões de início de sessão associados a utilizadores através de classe WMI Win32_LogonSession:

```powershell
Get-WmiObject -Class Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a>Obter o utilizador com sessão iniciado num computador

Pode visualizar o utilizador com sessão iniciado num sistema informático específico utilizando Win32_ComputerSystem. Este comando devolve apenas o utilizador com sessão iniciado no ambiente de trabalho do sistema:

```powershell
Get-WmiObject -Class Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a>Obter a hora Local do computador

Pode obter a hora local atual num computador específico, utilizando a classe WMI Win32_LocalTime. Porque esta classe por predefinição apresenta todos os metadados, poderá pretender filtrá-la utilizando **Select-Object**:

```
PS> Get-WmiObject -Class Win32_LocalTime -ComputerName . | Select-Object -Property [a-z]*

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2006
```

### <a name="displaying-service-status"></a>Apresentar o estado do serviço

Para ver o estado de todos os serviços num computador específico, localmente pode utilizar o **Get-Service** cmdlet conforme mencionado anteriormente. Para sistemas remotos, pode utilizar a classe Win32_Service de WMI. Se também de utilizar **Select-Object** para filtrar os resultados para **estado**, **nome**, e **DisplayName**, o formato de saída serão quase idêntica do **Get-Service**:

```powershell
Get-WmiObject -Class Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Para permitir a apresentação de nomes para os serviços ocasionais com nomes extremamente longos concluída, pode pretender utilizar **Format-Table** com o **AutoSize** e **moldar** parâmetros , para otimizar a largura da coluna e permitir que os nomes longos moldar em vez de a ser truncado:

```powershell
Get-WmiObject -Class Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
