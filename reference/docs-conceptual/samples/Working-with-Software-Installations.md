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
# <a name="working-with-software-installations"></a><span data-ttu-id="acd74-103">Trabalhar com Instalações de Software</span><span class="sxs-lookup"><span data-stu-id="acd74-103">Working with Software Installations</span></span>

<span data-ttu-id="acd74-104">Aplicativos que são projetados para usar o Windows Installer podem ser acedidos através do WMI **Win32_Product** classe, mas nem todos os aplicativos em uso atualmente utilizam o instalador do Windows.</span><span class="sxs-lookup"><span data-stu-id="acd74-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span>
<span data-ttu-id="acd74-105">Aplicativos que usam as rotinas de instalação alternativa não são geridos, normalmente, o Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="acd74-105">Applications that use alternate setup routines are not usually managed by the Windows Installer.</span></span>
<span data-ttu-id="acd74-106">Técnicas específicas para trabalhar com esses aplicativos depende do software de instalador e as decisões tomadas pelo desenvolvedor do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="acd74-106">Specific techniques for working with those applications depends on the installer software and decisions made by the application developer.</span></span> <span data-ttu-id="acd74-107">Por exemplo, os aplicativos instalados por copiar os ficheiros para uma pasta no computador, normalmente, não podem ser geridos utilizando técnicas discutidas aqui.</span><span class="sxs-lookup"><span data-stu-id="acd74-107">For example, applications installed by copying the files to a folder on the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="acd74-108">Pode gerir estas aplicações, como arquivos e pastas utilizando as técnicas discutidas [trabalhar com ficheiros e pastas](Working-with-Files-and-Folders.md).</span><span class="sxs-lookup"><span data-stu-id="acd74-108">You can manage these applications as files and folders by using the techniques discussed in [Working With Files and Folders](Working-with-Files-and-Folders.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="acd74-109">O **Win32_Product** classe não é otimizada de consulta.</span><span class="sxs-lookup"><span data-stu-id="acd74-109">The **Win32_Product** class is not query optimized.</span></span> <span data-ttu-id="acd74-110">Consultas que utilizam filtros de caráter universal com que o WMI para utilizar o fornecedor do MSI para enumerar todos os produtos instalados, em seguida, analisar a lista completa em seqüência para processar o filtro.</span><span class="sxs-lookup"><span data-stu-id="acd74-110">Queries that use wildcard filters cause WMI to use the MSI provider to enumerate all installed products then parse the full list sequentially to handle the filter.</span></span> <span data-ttu-id="acd74-111">Esta ação também inicia uma verificação de consistência de pacotes instalados, verificar e reparar a instalação.</span><span class="sxs-lookup"><span data-stu-id="acd74-111">This also initiates a consistency check of packages installed, verifying and repairing the install.</span></span> <span data-ttu-id="acd74-112">A validação é um processo lento e pode resultar em erros nos logs de eventos.</span><span class="sxs-lookup"><span data-stu-id="acd74-112">The validation is a slow process and may result in errors in the event logs.</span></span> <span data-ttu-id="acd74-113">Para obter mais informações de procura [KB artigo 974524](https://support.microsoft.com/help/974524).</span><span class="sxs-lookup"><span data-stu-id="acd74-113">For more information seek [KB article 974524](https://support.microsoft.com/help/974524).</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="acd74-114">A listagem de aplicações do Windows Installer</span><span class="sxs-lookup"><span data-stu-id="acd74-114">Listing Windows Installer Applications</span></span>

<span data-ttu-id="acd74-115">Para listar os aplicativos instalados com o instalador do Windows num sistema local ou remoto, utilize a seguinte consulta WMI simple:</span><span class="sxs-lookup"><span data-stu-id="acd74-115">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)"
```

```Output
Name               Caption                     Vendor                 Version      IdentifyingNumber
----               -------                     ------                 -------      -----------------
Microsoft .NET ... Microsoft .NET Core Runt... Microsoft Corporation  16.72.26629  {ACC73072-9AD5-416C-94B...
```

<span data-ttu-id="acd74-116">Para exibir todas as propriedades do **Win32_Product** objeto para a exibição, utilize o **propriedades** parâmetro dos cmdlets de formatação, como o `Format-List` cmdlet, com um valor de `*` (todos).</span><span class="sxs-lookup"><span data-stu-id="acd74-116">To display all the properties of the **Win32_Product** object to the display, use the **Properties** parameter of the formatting cmdlets, such as the `Format-List` cmdlet, with a value of `*` (all).</span></span>

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

<span data-ttu-id="acd74-117">Em alternativa, pode utilizar o `Get-CimInstance` **filtro** parâmetro para selecionar apenas o Microsoft .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="acd74-117">Or, you could use the `Get-CimInstance` **Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="acd74-118">O valor do **filtro** parâmetro utiliza a sintaxe de linguagem WQL (WMI Query), não a sintaxe de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="acd74-118">The value of the **Filter** parameter uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="acd74-119">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="acd74-119">For example:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property *
```

<span data-ttu-id="acd74-120">Para listar apenas as propriedades que lhe interessam, utilize o **propriedade** parâmetro dos cmdlets de formatação para listar as propriedades pretendidas.</span><span class="sxs-lookup"><span data-stu-id="acd74-120">To list only the properties that interest you, use the **Property** parameter of the formatting cmdlets to list the desired properties.</span></span>

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

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="acd74-121">A listagem de todos os aplicativos desinstalados</span><span class="sxs-lookup"><span data-stu-id="acd74-121">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="acd74-122">Uma vez que aplicativos mais padrão registar um desinstalador no Windows, podemos trabalhar com esses localmente localizando-los no registo do Windows.</span><span class="sxs-lookup"><span data-stu-id="acd74-122">Because most standard applications register an uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span> <span data-ttu-id="acd74-123">Não é possível garantida para localizar todos os aplicativos num sistema.</span><span class="sxs-lookup"><span data-stu-id="acd74-123">There is no guaranteed way to find every application on a system.</span></span> <span data-ttu-id="acd74-124">No entanto, é possível localizar todos os programas com listagens apresentadas na **adicionar ou remover programas**.</span><span class="sxs-lookup"><span data-stu-id="acd74-124">However, it is possible to find all programs with listings displayed in **Add or Remove Programs**.</span></span> <span data-ttu-id="acd74-125">**Adicionar ou remover programas** encontra esses aplicativos na seguinte chave do Registro:</span><span class="sxs-lookup"><span data-stu-id="acd74-125">**Add or Remove Programs** finds these applications in the following registry key:</span></span>

<span data-ttu-id="acd74-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span><span class="sxs-lookup"><span data-stu-id="acd74-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span></span>

<span data-ttu-id="acd74-127">Podemos examinar esta chave para encontrar aplicações.</span><span class="sxs-lookup"><span data-stu-id="acd74-127">We can examine this key to find applications.</span></span> <span data-ttu-id="acd74-128">Para facilitar ver a chave de desinstalação, podemos mapear uma unidade do PowerShell para esta localização de registo:</span><span class="sxs-lookup"><span data-stu-id="acd74-128">To make it easier to view the Uninstall key, we can map a PowerShell drive to this registry location:</span></span>

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```
<span data-ttu-id="acd74-129">Agora, temos uma unidade com o nome "desinstalar:" que pode ser utilizado para rápida e conveniente, procure as instalações de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="acd74-129">We now have a drive named "Uninstall:" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="acd74-130">Que podemos encontrar o número de aplicativos instalados por contar o número de chaves de registro na desinstalação: Unidade do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="acd74-130">We can find the number of installed applications by counting the number of registry keys in the Uninstall: PowerShell drive:</span></span>

```
(Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="acd74-131">Poderemos pesquisar esta lista de aplicativos ainda mais usando uma variedade de técnicas, a partir **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="acd74-131">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="acd74-132">Para obter uma lista de aplicativos e guardá-los no **$UninstallableApplications** variável, utilize o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="acd74-132">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

<span data-ttu-id="acd74-133">Para apresentar os valores das entradas de registro nas chaves de registo em desinstalar, utilize o método GetValue das chaves de registo.</span><span class="sxs-lookup"><span data-stu-id="acd74-133">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="acd74-134">O valor do método é o nome da entrada do Registro.</span><span class="sxs-lookup"><span data-stu-id="acd74-134">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="acd74-135">Por exemplo, para localizar os nomes a apresentar dos aplicativos na chave Uninstall, utilize o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="acd74-135">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="acd74-136">Não é garantido que estes valores são exclusivos.</span><span class="sxs-lookup"><span data-stu-id="acd74-136">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="acd74-137">No exemplo seguinte, dois itens instalados são apresentadas como "Windows Media Encoder 9 série":</span><span class="sxs-lookup"><span data-stu-id="acd74-137">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

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

## <a name="installing-applications"></a><span data-ttu-id="acd74-138">Instalação de aplicativos</span><span class="sxs-lookup"><span data-stu-id="acd74-138">Installing Applications</span></span>

<span data-ttu-id="acd74-139">Pode utilizar o **Win32_Product** classe para instalar pacotes de instalador do Windows, localmente ou remotamente.</span><span class="sxs-lookup"><span data-stu-id="acd74-139">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="acd74-140">Para instalar uma aplicação, tem de iniciar o PowerShell com a opção "Executar como administrador".</span><span class="sxs-lookup"><span data-stu-id="acd74-140">To install an application, you must start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="acd74-141">Ao instalar remotamente, utilize um caminho de rede de convenção de Nomenclatura Universal (UNC) para especificar o caminho para o pacote. msi, uma vez que o subsistema WMI não compreende os caminhos de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="acd74-141">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand PowerShell paths.</span></span> <span data-ttu-id="acd74-142">Por exemplo instalar o pacote de NewPackage.msi localizados na partilha de rede `\\AppServ\dsp` no computador remoto PC01, escreva o seguinte comando na linha de comandos do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="acd74-142">For example, to install the NewPackage.msi package located in the network share `\\AppServ\dsp` on the remote computer PC01, type the following command at the PowerShell prompt:</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

<span data-ttu-id="acd74-143">Aplicativos que não utilizam a tecnologia Windows Installer podem ter métodos específicos de aplicativo para implantação automatizada.</span><span class="sxs-lookup"><span data-stu-id="acd74-143">Applications that do not use Windows Installer technology may have application-specific methods for automated deployment.</span></span> <span data-ttu-id="acd74-144">Consulte a documentação para o aplicativo ou consulte o sistema de suporte do fornecedor do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="acd74-144">Check the documentation for the application or consult the application vendor's support system.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="acd74-145">Remoção de aplicativos</span><span class="sxs-lookup"><span data-stu-id="acd74-145">Removing Applications</span></span>

<span data-ttu-id="acd74-146">Remover um pacote de instalador do Windows com o PowerShell funciona em aproximadamente da mesma forma que a instalação de um pacote.</span><span class="sxs-lookup"><span data-stu-id="acd74-146">Removing a Windows Installer package using PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="acd74-147">Eis um exemplo que seleciona o pacote para desinstalar com base no respetivo nome; em alguns casos poderá ser mais fácil de filtrar com o **IdentifyingNumber**:</span><span class="sxs-lookup"><span data-stu-id="acd74-147">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

<span data-ttu-id="acd74-148">Remoção de outras aplicações não é tão simples, mesmo quando feito localmente.</span><span class="sxs-lookup"><span data-stu-id="acd74-148">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="acd74-149">Que podemos encontrar as cadeias de caracteres de desinstalação de linha de comandos para estas aplicações ao extrair os **UninstallString** propriedade.</span><span class="sxs-lookup"><span data-stu-id="acd74-149">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span>
<span data-ttu-id="acd74-150">Este método funciona para aplicações do Windows Installer e para programas mais antigos que aparece sob a chave de desinstalação:</span><span class="sxs-lookup"><span data-stu-id="acd74-150">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="acd74-151">Pode filtrar a saída com o nome a apresentar, se assim o desejar:</span><span class="sxs-lookup"><span data-stu-id="acd74-151">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="acd74-152">No entanto, essas cadeias de caracteres não podem ser diretamente utilizáveis no prompt do PowerShell sem algumas modificações.</span><span class="sxs-lookup"><span data-stu-id="acd74-152">However, these strings may not be directly usable from the PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="acd74-153">Atualizando aplicativos do Windows Installer</span><span class="sxs-lookup"><span data-stu-id="acd74-153">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="acd74-154">Para atualizar uma aplicação, terá de saber o nome da aplicação e o caminho para o pacote de atualização de aplicação.</span><span class="sxs-lookup"><span data-stu-id="acd74-154">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="acd74-155">Com essas informações, pode atualizar uma aplicação com um único comando do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="acd74-155">With that information, you can upgrade an application with a single PowerShell command:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
