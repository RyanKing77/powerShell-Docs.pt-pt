---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Recolher Informações sobre os Computadores
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: d837684108656e17ebf26189bd4841c5de01051c
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293168"
---
# <a name="collecting-information-about-computers"></a>Recolher Informações sobre os Computadores

Cmdlets da **CimCmdlets** módulo são os cmdlets mais importantes para tarefas de gestão do sistema geral.
Todas as definições de subsistema críticos são expostas por meio de WMI.
Além disso, o WMI trata dados como objetos que estão em coleções de um ou mais itens.
Como o Windows PowerShell também funciona com objetos e tem um pipeline que permite tratar únicos ou vários objetos da mesma forma, o acesso WMI genérico permite-lhe executar algumas tarefas avançadas com muito pouco de trabalho.

Os exemplos seguintes demonstram como recolher informações específicas, utilizando `Get-CimInstance` num computador arbitrário.
Especificamos o **nomedocomputador** parâmetro com o valor de ponto (**.**), que representa o computador local.
Pode especificar um nome ou endereço IP associado a qualquer computador que pode aceder através do WMI.
Para obter informações sobre o computador local, poderia omitir a **ComputerName** parâmetro.

## <a name="listing-desktop-settings"></a>Listagem das configurações de Desktops

Vamos começar com um comando que coleta informações sobre as áreas de trabalho no computador local.

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

Esta ação devolve informações para todas as áreas de trabalho, quer estejam em utilização ou não.

> [!NOTE]
> Informações devolvidas por algumas classes WMI podem ser muito detalhada e, muitas vezes, incluir metadados sobre a classe WMI.
Uma vez que a maioria dessas propriedades de metadados têm nomes que começam com **Cim**, pode filtrar as propriedades utilizando `Select-Object`.
Especifique a **- ExcludeProperty** parâmetro com "Cim *" como o valor.
Por exemplo:

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Para filtrar os metadados, utilize um operador de pipeline (|) para enviar os resultados do `Get-CimInstance` comando para `Select-Object -ExcludeProperty "CIM*"`.

## <a name="listing-bios-information"></a>A listagem de informações do BIOS

O WMI **Win32_BIOS** classe devolve informações bastante compactas e completas sobre o BIOS do sistema no computador local:

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

## <a name="listing-processor-information"></a>A listagem de informações do processador

Pode recuperar as informações do processador geral através do WMI **Win32_Processor** de classe, embora provavelmente desejará filtrar as informações:

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Para uma cadeia de descrição genérica da família de processadores, pode simplesmente retornar o **SystemType** propriedade:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a>A listagem de fabricante de computador e o modelo

Informações do modelo de computador também estão disponíveis a partir **Win32_ComputerSystem**.
A saída exibida padrão não terá de filtragem para fornecer dados de OEM:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

A saída dos comandos como esta, que devolvem informações diretamente a partir de algum hardware, apenas é tão bom quanto os de dados que tiver.
Algumas informações não estão configuradas corretamente por fabricantes de hardware e podem, por conseguinte, ficar indisponíveis.

## <a name="listing-installed-hotfixes"></a>Listagem instalados Hotfixes

Pode listar as correções instaladas tudo usando **Win32_QuickFixEngineering**:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

Essa classe retorna uma lista de correções que tem esta aparência:

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

Para mais sucinta saída, pode querer excluir algumas propriedades.
Apesar de poder utilizar o `Get-CimInstance`da **propriedade** parâmetro escolher apenas a **HotFixID**, ao fazê-lo por isso, na verdade, retornará obter mais informações, uma vez que todos os metadados é apresentado por predefinição:

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

Os dados adicionais são retornados, porque o parâmetro de propriedade no `Get-CimInstance` restringe as propriedades retornadas de instâncias de classes do WMI, não o objeto retornado para o Windows PowerShell.
Para reduzir a saída, utilize `Select-Object`:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a>A listagem de informações de versão do sistema operativo

O **Win32_OperatingSystem** propriedades de classe incluem informações de pacote de versão e o serviço.
Pode selecionar apenas essas propriedades para obter informações sobre a versão um resumo de explicitamente **Win32_OperatingSystem**:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

Também pode utilizar carateres universais com o `Select-Object`da **propriedade** parâmetro.
Uma vez que todas as propriedades de um a partir **crie** ou **Service Pack** são importantes para utilizar aqui, podem reduzir isso para o seguinte formato:

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

## <a name="listing-local-users-and-owner"></a>A listagem de utilizadores locais e proprietário

Informações gerais de utilizadores local — o número de utilizadores com licenças, número de utilizadores e o nome do proprietário atual — podem ser encontrados com uma seleção de **Win32_OperatingSystem** propriedades de classe.
Pode selecionar explicitamente as propriedades para apresentar como este:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Uma versão mais sucinta usando caracteres curinga é:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a>Obter o espaço em disco disponível

Para ver o espaço em disco e o espaço livre para unidades locais, pode usar a classe WMI de Win32_LogicalDisk.
É necessário ver apenas instâncias com drivetype igual de 3 – o valor que utiliza o WMI para fixo discos rígidos.

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

## <a name="getting-logon-session-information"></a>Obter informações de sessão de início de sessão

Pode obter informações gerais sobre sessões de início de sessão associados a utilizadores através da **Win32_LogonSession** classe WMI:

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

## <a name="getting-the-user-logged-on-to-a-computer"></a>Obter o utilizador com sessão iniciado num computador

Pode exibir o usuário conectado a um sistema de computador específico usando Win32_ComputerSystem.
Este comando devolve apenas o utilizador com sessão iniciado na área de trabalho do sistema:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

## <a name="getting-local-time-from-a-computer"></a>Obter a hora Local de um computador

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

## <a name="displaying-service-status"></a>Exibir o Status do serviço

Para ver o estado de todos os serviços num computador específico, pode usar localmente o `Get-Service` cmdlet.
Para sistemas remotos, pode utilizar o **Win32_Service** classe WMI.
Caso também utilize `Select-Object` para filtrar os resultados para **Status**, **nome**, e **DisplayName**, o formato de saída será quase idêntico do `Get-Service`:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Para permitir a apresentação completa de nomes para os serviços ocasionais com nomes muito longos, talvez queira usar `Format-Table` com o **AutoSize** e **encapsular** parâmetros, para otimizar a largura da coluna e Permitir nomes longos encapsular em vez de que está a ser truncado:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
