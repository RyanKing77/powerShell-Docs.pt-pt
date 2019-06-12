---
ms.date: 06/03/2019
keywords: PowerShell, o cmdlet
title: Trabalhar com Instalações de Software
ms.openlocfilehash: 6d2111a332f0e8c1b545186d3d950e936aed1834
ms.sourcegitcommit: 4ec9e10647b752cc62b1eabb897ada3dc03c93eb
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830293"
---
# <a name="working-with-software-installations"></a>Trabalhar com Instalações de Software

Aplicativos que são projetados para usar o Windows Installer podem ser acedidos através do WMI **Win32_Product** classe, mas nem todos os aplicativos em uso atualmente utilizam o instalador do Windows.
Aplicativos que usam as rotinas de instalação alternativa não são geridos, normalmente, o Windows Installer.
Técnicas específicas para trabalhar com esses aplicativos depende do software de instalador e as decisões tomadas pelo desenvolvedor do aplicativo. Por exemplo, os aplicativos instalados por copiar os ficheiros para uma pasta no computador, normalmente, não podem ser geridos utilizando técnicas discutidas aqui. Pode gerir estas aplicações, como arquivos e pastas utilizando as técnicas discutidas [trabalhar com ficheiros e pastas](Working-with-Files-and-Folders.md).

> [!CAUTION]
> O **Win32_Product** classe não é otimizada de consulta. Consultas que utilizam filtros de caráter universal com que o WMI para utilizar o fornecedor do MSI para enumerar todos os produtos instalados, em seguida, analisar a lista completa em seqüência para processar o filtro. Esta ação também inicia uma verificação de consistência de pacotes instalados, verificar e reparar a instalação. A validação é um processo lento e pode resultar em erros nos logs de eventos. Para obter mais informações de procura [KB artigo 974524](https://support.microsoft.com/help/974524).

## <a name="listing-windows-installer-applications"></a>A listagem de aplicações do Windows Installer

Para listar os aplicativos instalados com o instalador do Windows num sistema local ou remoto, utilize a seguinte consulta WMI simple:

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)"
```

```Output
Name               Caption                     Vendor                 Version      IdentifyingNumber
----               -------                     ------                 -------      -----------------
Microsoft .NET ... Microsoft .NET Core Runt... Microsoft Corporation  16.72.26629  {ACC73072-9AD5-416C-94B...
```

Para exibir todas as propriedades do **Win32_Product** objeto para a exibição, utilize o **propriedades** parâmetro dos cmdlets de formatação, como o `Format-List` cmdlet, com um valor de `*` (todos).

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.2 (x64)
Version               : 16.72.26629
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.2 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.2 (x64)
IdentifyingNumber     : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20180816
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\414c96e.msi
PackageCache          : C:\WINDOWS\Installer\414c96e.msi
PackageCode           : {D20AC783-1EC5-4A58-9277-F452F5EB9AD9}
PackageName           : dotnet-runtime-2.1.2-win-x64.msi
ProductID             :
RegCompany            :
RegOwner              :
Transforms            :
URLInfoAbout          :
URLUpdateInfo         :
WordCount             : 0
PSComputerName        :
CimClass              : root/cimv2:Win32_Product
CimInstanceProperties : {Caption, Description, IdentifyingNumber, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

Em alternativa, pode utilizar o `Get-CimInstance` **filtro** parâmetro para selecionar apenas o Microsoft .NET Framework 2.0. O valor do **filtro** parâmetro utiliza a sintaxe de linguagem WQL (WMI Query), não a sintaxe de Windows PowerShell. Por exemplo:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property *
```

Para listar apenas as propriedades que lhe interessam, utilize o **propriedade** parâmetro dos cmdlets de formatação para listar as propriedades pretendidas.

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.2 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\414c96e.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a>A listagem de todos os aplicativos desinstalados

Uma vez que aplicativos mais padrão registar um desinstalador no Windows, podemos trabalhar com esses localmente localizando-los no registo do Windows. Não é possível garantida para localizar todos os aplicativos num sistema. No entanto, é possível localizar todos os programas com listagens apresentadas na **adicionar ou remover programas**. **Adicionar ou remover programas** encontra esses aplicativos na seguinte chave do Registro:

`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.

Podemos examinar esta chave para encontrar aplicações. Para facilitar ver a chave de desinstalação, podemos mapear uma unidade do PowerShell para esta localização de registo:

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```
Agora, temos uma unidade com o nome "desinstalar:" que pode ser utilizado para rápida e conveniente, procure as instalações de aplicativos. Que podemos encontrar o número de aplicativos instalados por contar o número de chaves de registro na desinstalação: Unidade do PowerShell:

```
(Get-ChildItem -Path Uninstall:).Count
459
```

Poderemos pesquisar esta lista de aplicativos ainda mais usando uma variedade de técnicas, a partir **Get-ChildItem**. Para obter uma lista de aplicativos e guardá-los no **$UninstallableApplications** variável, utilize o seguinte comando:

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

Para apresentar os valores das entradas de registro nas chaves de registo em desinstalar, utilize o método GetValue das chaves de registo. O valor do método é o nome da entrada do Registro.

Por exemplo, para localizar os nomes a apresentar dos aplicativos na chave Uninstall, utilize o seguinte comando:

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

Não é garantido que estes valores são exclusivos. No exemplo seguinte, dois itens instalados são apresentadas como "Windows Media Encoder 9 série":

```powershell
$UninstallableApplications | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}
```

```Output
Name                           Property
----                           --------
{ACC73072-9AD5-416C-94BF-D82DD AuthorizedCDFPrefix :
CEA0F1B}                       Comments            :
                               Contact             :
                               DisplayVersion      : 16.72.26629
                               HelpLink            :
                               HelpTelephone       :
                               InstallDate         : 20180816
                               InstallLocation     :
                               InstallSource       : C:\ProgramData\Package
                               Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
                               ModifyPath          : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               NoModify            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 67156
                               SystemComponent     : 1
                               UninstallString     : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 16
                               VersionMinor        : 72
                               WindowsInstaller    : 1
                               Version             : 273180677
                               Language            : 1033
                               DisplayName         : Microsoft .NET Core Runtime - 2.1.2 (x64)
```

## <a name="installing-applications"></a>Instalação de aplicativos

Pode utilizar o **Win32_Product** classe para instalar pacotes de instalador do Windows, localmente ou remotamente.

> [!NOTE]
> Para instalar uma aplicação, tem de iniciar o PowerShell com a opção "Executar como administrador".

Ao instalar remotamente, utilize um caminho de rede de convenção de Nomenclatura Universal (UNC) para especificar o caminho para o pacote. msi, uma vez que o subsistema WMI não compreende os caminhos de PowerShell. Por exemplo instalar o pacote de NewPackage.msi localizados na partilha de rede `\\AppServ\dsp` no computador remoto PC01, escreva o seguinte comando na linha de comandos do PowerShell:

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

Aplicativos que não utilizam a tecnologia Windows Installer podem ter métodos específicos de aplicativo para implantação automatizada. Consulte a documentação para o aplicativo ou consulte o sistema de suporte do fornecedor do aplicativo.

## <a name="removing-applications"></a>Remoção de aplicativos

Remover um pacote de instalador do Windows com o PowerShell funciona em aproximadamente da mesma forma que a instalação de um pacote. Eis um exemplo que seleciona o pacote para desinstalar com base no respetivo nome; em alguns casos poderá ser mais fácil de filtrar com o **IdentifyingNumber**:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

Remoção de outras aplicações não é tão simples, mesmo quando feito localmente. Que podemos encontrar as cadeias de caracteres de desinstalação de linha de comandos para estas aplicações ao extrair os **UninstallString** propriedade.
Este método funciona para aplicações do Windows Installer e para programas mais antigos que aparece sob a chave de desinstalação:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Pode filtrar a saída com o nome a apresentar, se assim o desejar:

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

No entanto, essas cadeias de caracteres não podem ser diretamente utilizáveis no prompt do PowerShell sem algumas modificações.

## <a name="upgrading-windows-installer-applications"></a>Atualizando aplicativos do Windows Installer

Para atualizar uma aplicação, terá de saber o nome da aplicação e o caminho para o pacote de atualização de aplicação. Com essas informações, pode atualizar uma aplicação com um único comando do PowerShell:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
