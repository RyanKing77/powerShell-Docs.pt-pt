---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Trabalhar com Instalações de Software
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: 9369e3c5ac670895cd4fbd3ebc895c50efd02051
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984345"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="fa79c-103">Trabalhar com Instalações de Software</span><span class="sxs-lookup"><span data-stu-id="fa79c-103">Working with Software Installations</span></span>

<span data-ttu-id="fa79c-104">Aplicativos que são projetados para usar o Windows Installer podem ser acedidos através do WMI **Win32_Product** classe, mas nem todos os aplicativos em uso atualmente utilizam o instalador do Windows.</span><span class="sxs-lookup"><span data-stu-id="fa79c-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span> <span data-ttu-id="fa79c-105">Uma vez que o instalador do Windows oferece uma gama mais ampla de técnicas padrão para trabalhar com aplicativos instaláveis, nos concentraremos principalmente nesses aplicativos.</span><span class="sxs-lookup"><span data-stu-id="fa79c-105">Because the Windows Installer provides the widest range of standard techniques for working with installable applications, we will focus primarily on those applications.</span></span> <span data-ttu-id="fa79c-106">Aplicativos que usam as rotinas de instalação alternativa em geral, não serão geridos pelo instalador do Windows.</span><span class="sxs-lookup"><span data-stu-id="fa79c-106">Applications that use alternate setup routines will generally not be managed by the Windows Installer.</span></span> <span data-ttu-id="fa79c-107">Técnicas específicas para trabalhar com esses aplicativos dependerá do software de instalador e as decisões tomadas pelo desenvolvedor do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fa79c-107">Specific techniques for working with those applications will depend on the installer software and decisions made by the application developer.</span></span>

> [!NOTE]
> <span data-ttu-id="fa79c-108">Aplicativos que são instalados por copiar os ficheiros de aplicação para o computador normalmente não podem ser geridos utilizando técnicas discutidas aqui.</span><span class="sxs-lookup"><span data-stu-id="fa79c-108">Applications that are installed by copying the application files to the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="fa79c-109">Pode gerir estas aplicações, como ficheiros e pastas utilizando as técnicas discutidas na seção "A trabalhar com ficheiros e pastas".</span><span class="sxs-lookup"><span data-stu-id="fa79c-109">You can manage these applications as files and folders by using the techniques discussed in the "Working With Files and Folders" section.</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="fa79c-110">A listagem de aplicações do Windows Installer</span><span class="sxs-lookup"><span data-stu-id="fa79c-110">Listing Windows Installer Applications</span></span>

<span data-ttu-id="fa79c-111">Para listar os aplicativos instalados com o instalador do Windows num sistema local ou remoto, utilize a seguinte consulta WMI simple:</span><span class="sxs-lookup"><span data-stu-id="fa79c-111">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

<span data-ttu-id="fa79c-112">Para exibir todas as propriedades do objeto Win32_Product para a exibição, utilize o parâmetro de propriedades dos cmdlets de formatação, como o cmdlet Format-List, com um valor de \* (todos).</span><span class="sxs-lookup"><span data-stu-id="fa79c-112">To display all of the properties of the Win32_Product object to the display, use the Properties parameter of the formatting cmdlets, such as the Format-List cmdlet, with a value of \* (all).</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Microsoft .NET Framework 2.0"} | Format-List -Property *

Name              : Microsoft .NET Framework 2.0
Version           : 2.0.50727
InstallState      : 5
Caption           : Microsoft .NET Framework 2.0
Description       : Microsoft .NET Framework 2.0
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
InstallDate       : 20060506
InstallDate2      : 20060506000000.000000-000
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\619ab2.msi
SKUNumber         :
Vendor            : Microsoft Corporation
```

<span data-ttu-id="fa79c-113">Em alternativa, pode utilizar o **filtro de Get-WmiObject** parâmetro para selecionar apenas o Microsoft .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="fa79c-113">Or, you could use the **Get-WmiObject Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="fa79c-114">Como o filtro utilizado neste comando é um filtro WMI, ele usa a sintaxe de linguagem WQL (WMI Query), não o Windows PowerShell sintaxe.</span><span class="sxs-lookup"><span data-stu-id="fa79c-114">Because the filter used in this command is a WMI filter, it uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="fa79c-115">Em vez disso:</span><span class="sxs-lookup"><span data-stu-id="fa79c-115">Instead,:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

<span data-ttu-id="fa79c-116">Observe que consultas WQL com frequência, caracteres de uso, como espaços ou sinais de igual, que têm um significado especial no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fa79c-116">Note that WQL queries frequently use characters, such as spaces or equal signs, that have a special meaning in Windows PowerShell.</span></span> <span data-ttu-id="fa79c-117">Por esse motivo, é prudente sempre coloque o valor do parâmetro de filtro de aspas.</span><span class="sxs-lookup"><span data-stu-id="fa79c-117">For this reason, it is prudent to always enclose the value of the Filter parameter in quotation marks.</span></span> <span data-ttu-id="fa79c-118">Também pode utilizar o caráter de escape do Windows PowerShell, um acento grave (\`), apesar de não poder melhorar a legibilidade.</span><span class="sxs-lookup"><span data-stu-id="fa79c-118">You can also use the Windows PowerShell escape character, a backtick (\`), although it may not improve readability.</span></span> <span data-ttu-id="fa79c-119">O seguinte comando equivale ao comando anterior e retorna os mesmos resultados, mas utiliza o acento grave usar caracteres especiais, em vez de analisar a cadeia de filtro de todo.</span><span class="sxs-lookup"><span data-stu-id="fa79c-119">The following command is equivalent to the previous command and returns the same results, but uses the backtick to escape special characters, instead of quoting the entire filter string.</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

<span data-ttu-id="fa79c-120">Para listar apenas as propriedades que lhe interessam, utilize o parâmetro de propriedade dos cmdlets de formatação para listar as propriedades pretendidas.</span><span class="sxs-lookup"><span data-stu-id="fa79c-120">To list only the properties that interest you, use the Property parameter of the formatting cmdlets to list the desired properties.</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName . | Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
...
Name              : HighMAT Extension to Microsoft Windows XP CD Writing Wizard
InstallDate       : 20051022
InstallLocation   : C:\Program Files\HighMAT CD Writing Wizard\
PackageCache      : C:\WINDOWS\Installer\113b54.msi
Vendor            : Microsoft Corporation
Version           : 1.1.1905.1
IdentifyingNumber : {FCE65C4E-B0E8-4FBD-AD16-EDCBE6CD591F}
...
```

<span data-ttu-id="fa79c-121">Por fim localizar apenas os nomes dos aplicativos instalados, um simples **Format-Wide** instrução simplifica a saída:</span><span class="sxs-lookup"><span data-stu-id="fa79c-121">Finally, to find only the names of installed applications, a simple **Format-Wide** statement simplifies the output:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

<span data-ttu-id="fa79c-122">Apesar de agora, temos várias formas de considerar aplicações a utilizar o instalador do Windows para instalação, não levamos em outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="fa79c-122">Although we now have several ways to look at applications that used the Windows Installer for installation, we have not considered other applications.</span></span> <span data-ttu-id="fa79c-123">Uma vez que aplicativos mais padrão registrar seus desinstalador com Windows, podemos trabalhar com esses localmente localizando-los no registo do Windows.</span><span class="sxs-lookup"><span data-stu-id="fa79c-123">Because most standard applications register their uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span>

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="fa79c-124">A listagem de todos os aplicativos desinstalados</span><span class="sxs-lookup"><span data-stu-id="fa79c-124">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="fa79c-125">Embora não existe nenhuma forma garantida para localizar todos os aplicativos num sistema, é possível localizar todos os programas com listagens apresentadas na caixa de diálogo Adicionar ou remover programas.</span><span class="sxs-lookup"><span data-stu-id="fa79c-125">Although there is no guaranteed way to find every application on a system, it is possible to find all programs with listings displayed in the Add or Remove Programs dialog box.</span></span> <span data-ttu-id="fa79c-126">Adicionar ou remover programas encontra esses aplicativos na seguinte chave do Registro:</span><span class="sxs-lookup"><span data-stu-id="fa79c-126">Add or Remove Programs finds these applications in the following registry key:</span></span>

<span data-ttu-id="fa79c-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span><span class="sxs-lookup"><span data-stu-id="fa79c-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span></span>

<span data-ttu-id="fa79c-128">Também podemos examinar esta chave para encontrar aplicações.</span><span class="sxs-lookup"><span data-stu-id="fa79c-128">We can also examine this key to find applications.</span></span> <span data-ttu-id="fa79c-129">Para facilitar ver a chave de desinstalação, podemos mapear uma unidade do Windows PowerShell para esta localização de registo:</span><span class="sxs-lookup"><span data-stu-id="fa79c-129">To make it easier to view the Uninstall key, we can map a Windows PowerShell drive to this registry location:</span></span>

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> <span data-ttu-id="fa79c-130">O **HKLM:** unidade está mapeada para a raiz do **HKEY_LOCAL_MACHINE**, por isso, usamos essa unidade no caminho para a chave de desinstalação.</span><span class="sxs-lookup"><span data-stu-id="fa79c-130">The **HKLM:** drive is mapped to the root of **HKEY_LOCAL_MACHINE**, so we used that drive in the path to the Uninstall key.</span></span> <span data-ttu-id="fa79c-131">Em vez de **HKLM:** poderia especificamos o caminho do registo através de um **HKLM** ou **HKEY_LOCAL_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="fa79c-131">Instead of **HKLM:** we could have specified the registry path by using either **HKLM** or **HKEY_LOCAL_MACHINE**.</span></span> <span data-ttu-id="fa79c-132">A vantagem de utilizar uma unidade de registo existente é que podemos utilizar conclusão de tabulação para preencher os nomes de chaves, pelo que não é necessário para escrevê-los.</span><span class="sxs-lookup"><span data-stu-id="fa79c-132">The advantage of using an existing registry drive is that we can use tab-completion to fill in the keys names, so we do not need to type them.</span></span>

<span data-ttu-id="fa79c-133">Agora, temos uma unidade com o nome "Desinstalar", que pode ser usado de maneira rápida e conveniente, procurar as instalações de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="fa79c-133">We now have a drive named "Uninstall" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="fa79c-134">Que podemos encontrar o número de aplicativos instalados por contar o número de chaves de registro na desinstalação: Unidade do Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fa79c-134">We can find the number of installed applications by counting the number of registry keys in the Uninstall: Windows PowerShell drive:</span></span>

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="fa79c-135">Poderemos pesquisar esta lista de aplicativos ainda mais usando uma variedade de técnicas, a partir **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="fa79c-135">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="fa79c-136">Para obter uma lista de aplicativos e guardá-los no **$UninstallableApplications** variável, utilize o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="fa79c-136">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> <span data-ttu-id="fa79c-137">Estamos a utilizar um demorado nome de variável aqui por motivos de clareza.</span><span class="sxs-lookup"><span data-stu-id="fa79c-137">We are using a lengthy variable name here for clarity.</span></span> <span data-ttu-id="fa79c-138">Na utilização real, não há motivo para usar nomes longos.</span><span class="sxs-lookup"><span data-stu-id="fa79c-138">In actual use, there is no reason to use long names.</span></span> <span data-ttu-id="fa79c-139">Embora seja possível usar a conclusão de tabulação para nomes de variáveis, também pode utilizar nomes de caracteres de 1 a 2 para a velocidade.</span><span class="sxs-lookup"><span data-stu-id="fa79c-139">Although you can use tab-completion for variable names, you can also use 1-2 character names for speed.</span></span> <span data-ttu-id="fa79c-140">Nomes de mais tempo e descritivos são mais úteis quando estiver a desenvolver o código para reutilização.</span><span class="sxs-lookup"><span data-stu-id="fa79c-140">Longer, descriptive names are most useful when you are developing code for reuse.</span></span>

<span data-ttu-id="fa79c-141">Para apresentar os valores das entradas de registro nas chaves de registo em desinstalar, utilize o método GetValue das chaves de registo.</span><span class="sxs-lookup"><span data-stu-id="fa79c-141">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="fa79c-142">O valor do método é o nome da entrada do Registro.</span><span class="sxs-lookup"><span data-stu-id="fa79c-142">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="fa79c-143">Por exemplo, para localizar os nomes a apresentar dos aplicativos na chave Uninstall, utilize o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="fa79c-143">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="fa79c-144">Não é garantido que estes valores são exclusivos.</span><span class="sxs-lookup"><span data-stu-id="fa79c-144">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="fa79c-145">No exemplo seguinte, dois itens instalados são apresentadas como "Windows Media Encoder 9 série":</span><span class="sxs-lookup"><span data-stu-id="fa79c-145">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

## <a name="installing-applications"></a><span data-ttu-id="fa79c-146">Instalação de aplicativos</span><span class="sxs-lookup"><span data-stu-id="fa79c-146">Installing Applications</span></span>

<span data-ttu-id="fa79c-147">Pode utilizar o **Win32_Product** classe para instalar pacotes de instalador do Windows, localmente ou remotamente.</span><span class="sxs-lookup"><span data-stu-id="fa79c-147">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="fa79c-148">No Windows Vista, Windows Server 2008 e versões posteriores do Windows, para instalar uma aplicação, tem de iniciar Windows PowerShell com a opção "Executar como administrador".</span><span class="sxs-lookup"><span data-stu-id="fa79c-148">On Windows Vista, Windows Server 2008, and later versions of Windows, to install an application, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="fa79c-149">Ao instalar remotamente, utilize um caminho de rede de convenção de Nomenclatura Universal (UNC) para especificar o caminho para o pacote. msi, uma vez que o subsistema WMI não compreende caminhos do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fa79c-149">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand Windows PowerShell paths.</span></span> <span data-ttu-id="fa79c-150">Por exemplo instalar o pacote de NewPackage.msi localizados na partilha de rede \\ \\AppServ\\dsp no computador remoto PC01, escreva o seguinte comando na linha de comandos do Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fa79c-150">For example, to install the NewPackage.msi package located in the network share \\\\AppServ\\dsp on the remote computer PC01, type the following command at the Windows PowerShell prompt:</span></span>

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

<span data-ttu-id="fa79c-151">Aplicativos que não utilizam a tecnologia Windows Installer podem ter métodos específicos de aplicações disponíveis para implementação automatizada.</span><span class="sxs-lookup"><span data-stu-id="fa79c-151">Applications that do not use Windows Installer technology may have application-specific methods available for automated deployment.</span></span> <span data-ttu-id="fa79c-152">Para determinar se existe um método para a automatização de implementação, consulte a documentação para o aplicativo ou consulte o sistema de suporte do fornecedor do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fa79c-152">To determine whether there is a method for deployment automation, check the documentation for the application or consult the application vendor's support system.</span></span> <span data-ttu-id="fa79c-153">Em alguns casos, mesmo que o fornecedor do aplicativo não ter um design do aplicativo para a automatização da instalação, o fabricante de software do instalador pode ter algumas técnicas de automação.</span><span class="sxs-lookup"><span data-stu-id="fa79c-153">In some cases, even if the application vendor did not specifically design the application for installation automation, the installer software manufacturer may have some techniques for automation.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="fa79c-154">Remoção de aplicativos</span><span class="sxs-lookup"><span data-stu-id="fa79c-154">Removing Applications</span></span>

<span data-ttu-id="fa79c-155">Remover um pacote do Windows Installer com o Windows PowerShell funciona em aproximadamente da mesma forma que a instalação de um pacote.</span><span class="sxs-lookup"><span data-stu-id="fa79c-155">Removing a Windows Installer package by using Windows PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="fa79c-156">Eis um exemplo que seleciona o pacote para desinstalar com base no respetivo nome; em alguns casos poderá ser mais fácil de filtrar com o **IdentifyingNumber**:</span><span class="sxs-lookup"><span data-stu-id="fa79c-156">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

<span data-ttu-id="fa79c-157">Remoção de outras aplicações não é tão simples, mesmo quando feito localmente.</span><span class="sxs-lookup"><span data-stu-id="fa79c-157">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="fa79c-158">Que podemos encontrar as cadeias de caracteres de desinstalação de linha de comandos para estas aplicações ao extrair os **UninstallString** propriedade.</span><span class="sxs-lookup"><span data-stu-id="fa79c-158">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span> <span data-ttu-id="fa79c-159">Este método funciona para aplicações do Windows Installer e para programas mais antigos que aparece sob a chave de desinstalação:</span><span class="sxs-lookup"><span data-stu-id="fa79c-159">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="fa79c-160">Pode filtrar a saída com o nome a apresentar, se assim o desejar:</span><span class="sxs-lookup"><span data-stu-id="fa79c-160">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="fa79c-161">No entanto, essas cadeias de caracteres não podem ser diretamente utilizáveis no prompt do Windows PowerShell sem algumas modificações.</span><span class="sxs-lookup"><span data-stu-id="fa79c-161">However, these strings may not be directly usable from the Windows PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="fa79c-162">Atualizando aplicativos do Windows Installer</span><span class="sxs-lookup"><span data-stu-id="fa79c-162">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="fa79c-163">Para atualizar uma aplicação, terá de saber o nome da aplicação e o caminho para o pacote de atualização de aplicação.</span><span class="sxs-lookup"><span data-stu-id="fa79c-163">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="fa79c-164">Com essas informações, pode atualizar uma aplicação com um único comando do Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fa79c-164">With that information, you can upgrade an application with a single Windows PowerShell command:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```