---
ms.date: 12/12/2018
keywords: DSC, powershell, recurso, galeria, a configuração
title: Instalar os recursos de DSC adicionais
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080087"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="1ff21-103">Instalar os recursos de DSC adicionais</span><span class="sxs-lookup"><span data-stu-id="1ff21-103">Install Additional DSC Resources</span></span>

<span data-ttu-id="1ff21-104">PowerShell inclui vários recursos de Out-of-the-box para Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="1ff21-104">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="1ff21-105">O **PSDesiredStateConfiguration** módulo contém todos os recursos de DSC de OOB disponíveis na sua instância específica do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ff21-105">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="1ff21-106">Esta é uma lista dos recursos OOB incluídos no PowerShell 4.0 e uma descrição das capacidades do recurso.</span><span class="sxs-lookup"><span data-stu-id="1ff21-106">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="1ff21-107">Esta é uma lista incompleta, como o número de recursos OOB cresceu com cada versão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ff21-107">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|<span data-ttu-id="1ff21-108">Recurso</span><span class="sxs-lookup"><span data-stu-id="1ff21-108">Resource</span></span>  |<span data-ttu-id="1ff21-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ff21-109">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="1ff21-110">**Ficheiro**</span><span class="sxs-lookup"><span data-stu-id="1ff21-110">**File**</span></span>|<span data-ttu-id="1ff21-111">Controla o estado de arquivos e diretórios.</span><span class="sxs-lookup"><span data-stu-id="1ff21-111">Controls the state of files and directories.</span></span> <span data-ttu-id="1ff21-112">Copia os ficheiros a partir de um **origem** para um **destino** e atualiza-las quando o **origem** alterações comparando as datas, as somas de verificação e hashes.</span><span class="sxs-lookup"><span data-stu-id="1ff21-112">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span>|
|<span data-ttu-id="1ff21-113">**Arquivo**</span><span class="sxs-lookup"><span data-stu-id="1ff21-113">**Archive**</span></span>|<span data-ttu-id="1ff21-114">Descompacta arquivos mortos e uma localização especificada.</span><span class="sxs-lookup"><span data-stu-id="1ff21-114">Unpacks archives and a specified location.</span></span> <span data-ttu-id="1ff21-115">Valida os arquivos com uma determinada **soma de verificação**.</span><span class="sxs-lookup"><span data-stu-id="1ff21-115">Validates the archives with a specified **Checksum**.</span></span>|
|<span data-ttu-id="1ff21-116">**Environment**</span><span class="sxs-lookup"><span data-stu-id="1ff21-116">**Environment**</span></span>|<span data-ttu-id="1ff21-117">Gere as variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="1ff21-117">Manages environment variables.</span></span>|
|<span data-ttu-id="1ff21-118">**Grupo**</span><span class="sxs-lookup"><span data-stu-id="1ff21-118">**Group**</span></span>|<span data-ttu-id="1ff21-119">Gere os grupos locais e controla a associação de grupo.</span><span class="sxs-lookup"><span data-stu-id="1ff21-119">Manages local groups and controls group membership.</span></span>|
|<span data-ttu-id="1ff21-120">**registo**</span><span class="sxs-lookup"><span data-stu-id="1ff21-120">**Log**</span></span>|<span data-ttu-id="1ff21-121">Escreve mensagens para o `Microsoft-Windows-Desired State Configuration/Analytic` registo de eventos.</span><span class="sxs-lookup"><span data-stu-id="1ff21-121">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>|
|<span data-ttu-id="1ff21-122">**Pacote**</span><span class="sxs-lookup"><span data-stu-id="1ff21-122">**Package**</span></span>|<span data-ttu-id="1ff21-123">Instala ou desinstala os pacotes usando **argumentos**, **LogPath**, **ReturnCode**, outras definições.</span><span class="sxs-lookup"><span data-stu-id="1ff21-123">Installs or uninstalls packages using **Arguments**, **LogPath**, **ReturnCode**, other settings.</span></span>|
|<span data-ttu-id="1ff21-124">**Registo**</span><span class="sxs-lookup"><span data-stu-id="1ff21-124">**Registry**</span></span>|<span data-ttu-id="1ff21-125">Gere chaves de registo e valores.</span><span class="sxs-lookup"><span data-stu-id="1ff21-125">Manages registry keys and values.</span></span>|
|<span data-ttu-id="1ff21-126">**Script**</span><span class="sxs-lookup"><span data-stu-id="1ff21-126">**Script**</span></span>|<span data-ttu-id="1ff21-127">Permite-lhe criar sua própria [get-teste-set](../resources/get-test-set.md) blocos de script.</span><span class="sxs-lookup"><span data-stu-id="1ff21-127">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>|
|<span data-ttu-id="1ff21-128">**Serviço**</span><span class="sxs-lookup"><span data-stu-id="1ff21-128">**Service**</span></span>|<span data-ttu-id="1ff21-129">Configura os serviços do Windows.</span><span class="sxs-lookup"><span data-stu-id="1ff21-129">Configures Windows services.</span></span>|
|<span data-ttu-id="1ff21-130">**Utilizador**</span><span class="sxs-lookup"><span data-stu-id="1ff21-130">**User**</span></span> |<span data-ttu-id="1ff21-131">Gere utilizadores locais e atributos.</span><span class="sxs-lookup"><span data-stu-id="1ff21-131">Manages local users and attributes.</span></span>|
|<span data-ttu-id="1ff21-132">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="1ff21-132">**WindowsFeature**</span></span>|<span data-ttu-id="1ff21-133">Gere funções e funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="1ff21-133">Manages roles and features.</span></span>|
|<span data-ttu-id="1ff21-134">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="1ff21-134">**WindowsProcess**</span></span>|<span data-ttu-id="1ff21-135">Configura os processos do Windows.</span><span class="sxs-lookup"><span data-stu-id="1ff21-135">Configures Windows processes.</span></span>|

<span data-ttu-id="1ff21-136">Os recursos OOB permitem que um ponto de partida para operações comuns.</span><span class="sxs-lookup"><span data-stu-id="1ff21-136">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="1ff21-137">Se os recursos OOB não atenderem às suas necessidades, pode escrever a sua própria [recurso personalizado](../resources/authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="1ff21-137">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="1ff21-138">Antes de escrever um recurso personalizado para resolver seu problema, deve procurar por meio do grande número de recursos de DSC que já foram criados pela Microsoft e a Comunidade do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ff21-138">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="1ff21-139">Pode encontrar recursos de DSC em ambos os [galeria do PowerShell](https://www.powershellgallery.com/) e [GitHub](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="1ff21-139">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="1ff21-140">Também pode instalar os recursos de DSC diretamente a partir da consola do PowerShell através de [PowerShellGet](/powershell/module/powershellget/).</span><span class="sxs-lookup"><span data-stu-id="1ff21-140">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="1ff21-141">Installing PowerShellGet (Instalar o PowerShellGet)</span><span class="sxs-lookup"><span data-stu-id="1ff21-141">Installing PowerShellGet</span></span>

<span data-ttu-id="1ff21-142">Para determinar se já tiver **PowerShell** obter ou para obter ajuda instalá-lo, consulte o guia seguinte: [Instalar o PowerShellGet](/powershell/gallery/installing-psget).</span><span class="sxs-lookup"><span data-stu-id="1ff21-142">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="1ff21-143">Localizar recursos de DSC a utilização do PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="1ff21-143">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="1ff21-144">Uma vez **PowerShellGet** está instalado no seu sistema, pode encontrar e instalar os recursos de DSC alojados no [galeria do PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="1ff21-144">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="1ff21-145">Em primeiro lugar, utilize o [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet para localizar os recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="1ff21-145">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="1ff21-146">Quando executa `Find-DSCResource` pela primeira vez, verá o seguinte pedido para instalar o fornecedor"NuGet".</span><span class="sxs-lookup"><span data-stu-id="1ff21-146">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

<span data-ttu-id="1ff21-147">Depois prima 'y', está instalado o fornecedor de "NuGet", é apresentada uma lista de recursos de DSC que pode instalar a partir da galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ff21-147">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="1ff21-148">Não é apresentada a lista porque é muito grande.</span><span class="sxs-lookup"><span data-stu-id="1ff21-148">List is not shown because it is very large.</span></span>

<span data-ttu-id="1ff21-149">Também pode especificar a `-Name` parâmetro utilizando carateres universais, ou `-Filter` parâmetro sem carateres universais para limitar a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="1ff21-149">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="1ff21-150">Neste exemplo tenta encontrar um recurso de "Fuso horário" DSC com os carateres universais.</span><span class="sxs-lookup"><span data-stu-id="1ff21-150">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1ff21-151">Atualmente, existe um bug no `Find-DSCResource` cmdlet que impede a utilização de carateres universais em ambos os `-Name` e `-Filter` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1ff21-151">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="1ff21-152">O segundo exemplo abaixo mostra uma solução usando `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="1ff21-152">The second example below shows a workaround using `Where-Object`.</span></span>

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

<span data-ttu-id="1ff21-153">Também pode utilizar `Where-Object` para localizar os recursos de DSC com a filtragem mais granular.</span><span class="sxs-lookup"><span data-stu-id="1ff21-153">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="1ff21-154">Essa abordagem será mais lenta do que usando incorporado em parâmetros de filtragem.</span><span class="sxs-lookup"><span data-stu-id="1ff21-154">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="1ff21-155">Para obter mais informações sobre a filtragem, consulte [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="1ff21-155">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="1ff21-156">Instalar os recursos de DSC com o PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="1ff21-156">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="1ff21-157">Para instalar um recurso de DSC, utilize o [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, especificando o nome do módulo mostrado na **módulo** nome nos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="1ff21-157">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="1ff21-158">O recurso de "Fuso horário" existe no módulo "ComputerManagementDSC", é assim que este exemplo instala o módulo.</span><span class="sxs-lookup"><span data-stu-id="1ff21-158">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="1ff21-159">Se não tiver considerado fidedigno da galeria do PowerShell, verá o aviso abaixo solicitar a confirmação e, com instruções como evitar pedidos subsequentes no instala.</span><span class="sxs-lookup"><span data-stu-id="1ff21-159">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="1ff21-160">Prima 'y' para continuar a instalar o módulo.</span><span class="sxs-lookup"><span data-stu-id="1ff21-160">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="1ff21-161">Após a instalação, pode verificar se o seu novo recurso está instalado usando [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span><span class="sxs-lookup"><span data-stu-id="1ff21-161">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

<span data-ttu-id="1ff21-162">Também pode exibir outros recursos no seu módulo recentemente instalado, especificando o `-ModuleName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1ff21-162">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a><span data-ttu-id="1ff21-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ff21-163">See also</span></span>

- [<span data-ttu-id="1ff21-164">Quais são os recursos?</span><span class="sxs-lookup"><span data-stu-id="1ff21-164">What are Resources?</span></span>](../resources/resources.md)
