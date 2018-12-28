---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Começar com o Desired State Configuration (DSC) para Linux
ms.openlocfilehash: 69f087434455aae8e97ea07c79c52e493412d134
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404908"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="53856-103">Começar com o Desired State Configuration (DSC) para Linux</span><span class="sxs-lookup"><span data-stu-id="53856-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="53856-104">Este tópico explica como começar a utilizar o PowerShell Desired State Configuration (DSC) para Linux.</span><span class="sxs-lookup"><span data-stu-id="53856-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="53856-105">Para obter informações gerais sobre o DSC, veja [introdução ao Windows PowerShell Desired State Configuration](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="53856-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="53856-106">Versões suportadas do sistema de operação do Linux</span><span class="sxs-lookup"><span data-stu-id="53856-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="53856-107">As seguintes versões do sistema operativo Linux são suportadas para DSC para Linux.</span><span class="sxs-lookup"><span data-stu-id="53856-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>

- <span data-ttu-id="53856-108">CentOS 5, 6 e 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="53856-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="53856-109">Debian GNU/Linux 6, 7 e 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="53856-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="53856-110">Oracle Linux 5, 6 e 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="53856-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="53856-111">Red Hat Enterprise Linux Server 5, 6 e 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="53856-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="53856-112">SUSE Linux Enterprise Server 10, 11 e 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="53856-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="53856-113">Servidor de Ubuntu 12.04 LTS, 14.04 LTS e 16.04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="53856-113">Ubuntu Server 12.04 LTS, 14.04 LTS and 16.04 LTS (x86/x64)</span></span>

<span data-ttu-id="53856-114">A tabela seguinte descreve as dependências de pacote necessária para DSC para Linux.</span><span class="sxs-lookup"><span data-stu-id="53856-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="53856-115">Pacote necessário</span><span class="sxs-lookup"><span data-stu-id="53856-115">Required package</span></span> |  <span data-ttu-id="53856-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="53856-116">Description</span></span> |  <span data-ttu-id="53856-117">Versão mínima</span><span class="sxs-lookup"><span data-stu-id="53856-117">Minimum version</span></span> |
|---|---|---|
| <span data-ttu-id="53856-118">glibc</span><span class="sxs-lookup"><span data-stu-id="53856-118">glibc</span></span>| <span data-ttu-id="53856-119">Biblioteca do GNU</span><span class="sxs-lookup"><span data-stu-id="53856-119">GNU Library</span></span>| <span data-ttu-id="53856-120">2... 4 – 31.30</span><span class="sxs-lookup"><span data-stu-id="53856-120">2…4 – 31.30</span></span>|
| <span data-ttu-id="53856-121">Python</span><span class="sxs-lookup"><span data-stu-id="53856-121">python</span></span>| <span data-ttu-id="53856-122">Python</span><span class="sxs-lookup"><span data-stu-id="53856-122">Python</span></span>| <span data-ttu-id="53856-123">2.4 – 3.4</span><span class="sxs-lookup"><span data-stu-id="53856-123">2.4 – 3.4</span></span>|
| <span data-ttu-id="53856-124">omiserver</span><span class="sxs-lookup"><span data-stu-id="53856-124">omiserver</span></span>| <span data-ttu-id="53856-125">Abrir Infraestrutura de Gestão</span><span class="sxs-lookup"><span data-stu-id="53856-125">Open Management Infrastructure</span></span>| <span data-ttu-id="53856-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="53856-126">1.0.8.1</span></span>|
| <span data-ttu-id="53856-127">OpenSSL</span><span class="sxs-lookup"><span data-stu-id="53856-127">openssl</span></span>| <span data-ttu-id="53856-128">Bibliotecas de OpenSSL</span><span class="sxs-lookup"><span data-stu-id="53856-128">OpenSSL Libraries</span></span>| <span data-ttu-id="53856-129">0.9.8 ou 1.0</span><span class="sxs-lookup"><span data-stu-id="53856-129">0.9.8 or 1.0</span></span>|
| <span data-ttu-id="53856-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="53856-130">ctypes</span></span>| <span data-ttu-id="53856-131">Biblioteca de Python CTypes</span><span class="sxs-lookup"><span data-stu-id="53856-131">Python CTypes library</span></span>| <span data-ttu-id="53856-132">Tem de corresponder à versão do Python</span><span class="sxs-lookup"><span data-stu-id="53856-132">Must match Python version</span></span>|
| <span data-ttu-id="53856-133">libcurl</span><span class="sxs-lookup"><span data-stu-id="53856-133">libcurl</span></span>| <span data-ttu-id="53856-134">biblioteca de clientes de http de cURL</span><span class="sxs-lookup"><span data-stu-id="53856-134">cURL http client library</span></span>| <span data-ttu-id="53856-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="53856-135">7.15.1</span></span>|

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="53856-136">Instalar o DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="53856-136">Installing DSC for Linux</span></span>

<span data-ttu-id="53856-137">Tem de instalar o [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) antes de instalar o DSC para Linux.</span><span class="sxs-lookup"><span data-stu-id="53856-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="53856-138">Instalar o OMI</span><span class="sxs-lookup"><span data-stu-id="53856-138">Installing OMI</span></span>

<span data-ttu-id="53856-139">Desired State Configuration for Linux requer que o servidor CIM Open Management Infrastructure (OMI), versão 1.0.8.1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="53856-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="53856-140">O OMI pode ser transferido da Open Group: [Abra o Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="53856-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="53856-141">Para instalar o OMI, instale o pacote que é adequado para o seu sistema Linux (.rpm ou .deb) e a versão de OpenSSL (ssl_098 ou ssl_100) e a arquitetura (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="53856-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="53856-142">Pacotes de RPM são adequadas para CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server e Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="53856-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="53856-143">Pacotes de DEB são adequadas para Debian GNU/Linux e Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="53856-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="53856-144">Os pacotes de ssl_098 são adequados para computadores com OpenSSL 0.9.8 instalado enquanto os pacotes de ssl_100 são adequados para computadores com o 1.0 OpenSSL instalado.</span><span class="sxs-lookup"><span data-stu-id="53856-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="53856-145">Para determinar a versão de OpenSSL instalada, execute o comando `openssl version`.</span><span class="sxs-lookup"><span data-stu-id="53856-145">To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="53856-146">Execute o seguinte comando para instalar o OMI num sistema de CentOS 7 x64.</span><span class="sxs-lookup"><span data-stu-id="53856-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="53856-147">Instalar o DSC</span><span class="sxs-lookup"><span data-stu-id="53856-147">Installing DSC</span></span>

<span data-ttu-id="53856-148">DSC para Linux está disponível para download [aqui](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span><span class="sxs-lookup"><span data-stu-id="53856-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span></span>

<span data-ttu-id="53856-149">Para instalar o DSC, instale o pacote que é adequado para o seu sistema Linux (.rpm ou .deb) e a versão de OpenSSL (ssl_098 ou ssl_100) e a arquitetura (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="53856-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="53856-150">Pacotes de RPM são adequadas para CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server e Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="53856-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="53856-151">Pacotes de DEB são adequadas para Debian GNU/Linux e Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="53856-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="53856-152">Os pacotes de ssl_098 são adequados para computadores com OpenSSL 0.9.8 instalado enquanto os pacotes de ssl_100 são adequados para computadores com o 1.0 OpenSSL instalado.</span><span class="sxs-lookup"><span data-stu-id="53856-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="53856-153">Para determinar a versão de OpenSSL instalada, execute a versão de openssl de comando.</span><span class="sxs-lookup"><span data-stu-id="53856-153">To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="53856-154">Execute o seguinte comando para instalar o DSC num sistema de CentOS 7 x64.</span><span class="sxs-lookup"><span data-stu-id="53856-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a><span data-ttu-id="53856-155">Utilizar o DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="53856-155">Using DSC for Linux</span></span>

<span data-ttu-id="53856-156">As secções seguintes explicam como criar e executar configurações de DSC em computadores com Linux.</span><span class="sxs-lookup"><span data-stu-id="53856-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="53856-157">Criar um documento de MOF de configuração</span><span class="sxs-lookup"><span data-stu-id="53856-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="53856-158">A palavra-chave de configuração do Windows PowerShell é utilizada para criar uma configuração para computadores Linux, assim como para computadores Windows.</span><span class="sxs-lookup"><span data-stu-id="53856-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="53856-159">Os passos seguintes descrevem a criação de um documento de configuração para um computador Linux com o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="53856-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="53856-160">Importe o módulo de nx.</span><span class="sxs-lookup"><span data-stu-id="53856-160">Import the nx module.</span></span> <span data-ttu-id="53856-161">O módulo do Windows PowerShell nx contém o esquema para recursos incorporados para DSC para Linux e tem de ser instalado no computador local e importado para a configuração.</span><span class="sxs-lookup"><span data-stu-id="53856-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

   - <span data-ttu-id="53856-162">Para instalar o módulo de nx, copie o diretório de módulo nx para qualquer um `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` ou `$PSHOME\Modules`.</span><span class="sxs-lookup"><span data-stu-id="53856-162">To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="53856-163">O módulo de nx está incluído no DSC para o pacote de instalação de Linux.</span><span class="sxs-lookup"><span data-stu-id="53856-163">The nx module is included in the DSC for Linux installation package.</span></span> <span data-ttu-id="53856-164">Para importar o módulo de nx na sua configuração, utilize o `Import-DSCResource` comando:</span><span class="sxs-lookup"><span data-stu-id="53856-164">To import the nx module in your configuration, use the `Import-DSCResource` command:</span></span>

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. <span data-ttu-id="53856-165">Definir uma configuração e gerar o documento de configuração:</span><span class="sxs-lookup"><span data-stu-id="53856-165">Define a configuration and generate the configuration document:</span></span>

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile 
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="53856-166">Enviar a configuração para o computador com Linux</span><span class="sxs-lookup"><span data-stu-id="53856-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="53856-167">Documentos de configuração (ficheiros MOF) podem ser enviados para o computador Linux, com o [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="53856-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="53856-168">Para utilizar este cmdlet, juntamente com o [Get-dscconfiguration para](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), ou [Test-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlets, remotamente para um computador Linux, tem de utilizar um CIMSession.</span><span class="sxs-lookup"><span data-stu-id="53856-168">In order to use this cmdlet, along with the [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), or [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="53856-169">O [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet é utilizado para criar um CIMSession para o computador Linux.</span><span class="sxs-lookup"><span data-stu-id="53856-169">The [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="53856-170">O código seguinte mostra como criar um CIMSession para DSC para Linux.</span><span class="sxs-lookup"><span data-stu-id="53856-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90
```

> [!NOTE]
> <span data-ttu-id="53856-171">Para o modo "Push", a credencial do usuário tem de ser o utilizador raiz no computador Linux.</span><span class="sxs-lookup"><span data-stu-id="53856-171">For “Push” mode, the user credential must be the root user on the Linux computer.</span></span>
> <span data-ttu-id="53856-172">Ligações de SSL/TLS apenas são suportadas para DSC para Linux, o `New-CimSession` deve ser utilizado com o parâmetro – UseSSL definido como $true.</span><span class="sxs-lookup"><span data-stu-id="53856-172">Only SSL/TLS connections are supported for DSC for Linux, the `New-CimSession` must be used with the –UseSSL parameter set to $true.</span></span>
> <span data-ttu-id="53856-173">O certificado SSL utilizado pelo OMI (para DSC) é especificado no ficheiro: `/opt/omi/etc/omiserver.conf` com as propriedades: pemfile e ficheiro de chave.</span><span class="sxs-lookup"><span data-stu-id="53856-173">The SSL certificate used by OMI (for DSC) is specified in the file: `/opt/omi/etc/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
> <span data-ttu-id="53856-174">Se este certificado não é considerado fidedigno pelo computador do Windows que está a executar o [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet no, pode optar por ignorar a validação do certificado com as opções de CIMSession: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span><span class="sxs-lookup"><span data-stu-id="53856-174">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span></span>

<span data-ttu-id="53856-175">Execute o seguinte comando para enviar a configuração de DSC para o nó de Linux.</span><span class="sxs-lookup"><span data-stu-id="53856-175">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="53856-176">Distribuir a configuração com um servidor de solicitação</span><span class="sxs-lookup"><span data-stu-id="53856-176">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="53856-177">Configurações podem ser distribuídas para um computador com Linux com um servidor de solicitação, assim como para computadores Windows.</span><span class="sxs-lookup"><span data-stu-id="53856-177">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="53856-178">Para obter orientações sobre como utilizar um servidor de solicitação, veja [Windows PowerShell Desired State Configuration Pull servidores](../pull-server/pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="53856-178">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](../pull-server/pullServer.md).</span></span> <span data-ttu-id="53856-179">Para obter informações adicionais e limitações relacionadas ao uso de computadores com Linux com um servidor de solicitação, consulte as notas de versão para de Desired State Configuration para Linux.</span><span class="sxs-lookup"><span data-stu-id="53856-179">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="53856-180">Trabalhar com configurações localmente</span><span class="sxs-lookup"><span data-stu-id="53856-180">Working with configurations locally</span></span>

<span data-ttu-id="53856-181">DSC para Linux inclui scripts para trabalhar com a configuração do computador local do Linux.</span><span class="sxs-lookup"><span data-stu-id="53856-181">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="53856-182">Estes scripts estão localizar no `/opt/microsoft/dsc/Scripts` e inclua o seguinte:</span><span class="sxs-lookup"><span data-stu-id="53856-182">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>

- <span data-ttu-id="53856-183">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="53856-183">GetDscConfiguration.py</span></span>

<span data-ttu-id="53856-184">Devolve a configuração atual aplicada ao computador.</span><span class="sxs-lookup"><span data-stu-id="53856-184">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="53856-185">Semelhante para o cmdlet do Windows PowerShell `Get-DscConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="53856-185">Similar to the Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

- <span data-ttu-id="53856-186">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="53856-186">GetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="53856-187">Devolve o meta-configuração atual aplicada ao computador.</span><span class="sxs-lookup"><span data-stu-id="53856-187">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="53856-188">Semelhante ao cmdlet [Get-dsclocalconfigurationmanager para](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="53856-188">Similar to the cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

- <span data-ttu-id="53856-189">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="53856-189">InstallModule.py</span></span>

<span data-ttu-id="53856-190">Instala um módulo de recurso personalizado do DSC.</span><span class="sxs-lookup"><span data-stu-id="53856-190">Installs a custom DSC resource module.</span></span> <span data-ttu-id="53856-191">Requer o caminho para um ficheiro. zip que contém a biblioteca de objetos partilhados do módulo e ficheiros MOF de esquema.</span><span class="sxs-lookup"><span data-stu-id="53856-191">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- <span data-ttu-id="53856-192">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="53856-192">RemoveModule.py</span></span>

<span data-ttu-id="53856-193">Remove um módulo de recurso personalizado do DSC.</span><span class="sxs-lookup"><span data-stu-id="53856-193">Removes a custom DSC resource module.</span></span> <span data-ttu-id="53856-194">Requer o nome do módulo para remover.</span><span class="sxs-lookup"><span data-stu-id="53856-194">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

- <span data-ttu-id="53856-195">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="53856-195">StartDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="53856-196">Aplica-se um ficheiro MOF de configuração para o computador.</span><span class="sxs-lookup"><span data-stu-id="53856-196">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="53856-197">Semelhante a [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="53856-197">Similar to the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="53856-198">Requer o caminho para a configuração do MOF para aplicar.</span><span class="sxs-lookup"><span data-stu-id="53856-198">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- <span data-ttu-id="53856-199">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="53856-199">SetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="53856-200">Aplica-se um ficheiro MOF de configuração de Meta no computador.</span><span class="sxs-lookup"><span data-stu-id="53856-200">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="53856-201">Semelhante a [Set-dsclocalconfigurationmanager para](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="53856-201">Similar to the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span> <span data-ttu-id="53856-202">Requer o caminho para o MOF de configuração de Meta para aplicar.</span><span class="sxs-lookup"><span data-stu-id="53856-202">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="53856-203">PowerShell Desired State Configuration para ficheiros de registo do Linux</span><span class="sxs-lookup"><span data-stu-id="53856-203">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="53856-204">Os seguintes ficheiros de registo são gerados para DSC para Linux de mensagens.</span><span class="sxs-lookup"><span data-stu-id="53856-204">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="53856-205">Ficheiro de registo</span><span class="sxs-lookup"><span data-stu-id="53856-205">Log file</span></span>|<span data-ttu-id="53856-206">Diretório</span><span class="sxs-lookup"><span data-stu-id="53856-206">Directory</span></span>|<span data-ttu-id="53856-207">Descrição</span><span class="sxs-lookup"><span data-stu-id="53856-207">Description</span></span>|
|---|---|---|
|<span data-ttu-id="53856-208">**omiserver. log**</span><span class="sxs-lookup"><span data-stu-id="53856-208">**omiserver.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="53856-209">Mensagens relacionadas com a operação do servidor OMI CIM.</span><span class="sxs-lookup"><span data-stu-id="53856-209">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="53856-210">**DSC.log**</span><span class="sxs-lookup"><span data-stu-id="53856-210">**dsc.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="53856-211">Mensagens relacionadas com a operação das operações de recursos do Gestor de configuração Local (LCM) e de DSC.</span><span class="sxs-lookup"><span data-stu-id="53856-211">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|
