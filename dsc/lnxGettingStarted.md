---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Começar com configuração de estado pretendido (DSC) para Linux"
ms.openlocfilehash: 4fd8460bc5d2564cab291904b60a1a0c26c3e5a7
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="0fa4f-103">Começar com configuração de estado pretendido (DSC) para Linux</span><span class="sxs-lookup"><span data-stu-id="0fa4f-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="0fa4f-104">Este tópico explica como começar a utilizar o PowerShell pretendido Estado Configuration (DSC) para o Linux.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="0fa4f-105">Para obter informações gerais sobre o DSC, consulte [começar com a configuração de estado pretendido do Windows PowerShell](overview.md).</span><span class="sxs-lookup"><span data-stu-id="0fa4f-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="0fa4f-106">Versões suportadas do sistema de operação do Linux</span><span class="sxs-lookup"><span data-stu-id="0fa4f-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="0fa4f-107">As seguintes versões de sistema operativo Linux são suportadas para DSC para Linux.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>
- <span data-ttu-id="0fa4f-108">CentOS 5, 6 e 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="0fa4f-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="0fa4f-109">Debian GNU/Linux 6, 7 e 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="0fa4f-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="0fa4f-110">Oracle Linux 5, 6 e 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="0fa4f-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="0fa4f-111">Red Hat Enterprise Linux Server 5, 6 e 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="0fa4f-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="0fa4f-112">SUSE Linux Enterprise Server 10, 11 e 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="0fa4f-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="0fa4f-113">Ubuntu Server 12.04 LTS, 14.04 LTS e 16.04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="0fa4f-113">Ubuntu Server 12.04 LTS, 14.04 LTS and 16.04 LTS (x86/x64)</span></span>

<span data-ttu-id="0fa4f-114">A tabela seguinte descreve as dependências de pacote necessário para DSC para Linux.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="0fa4f-115">Pacote necessário</span><span class="sxs-lookup"><span data-stu-id="0fa4f-115">Required package</span></span> |  <span data-ttu-id="0fa4f-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="0fa4f-116">Description</span></span> |  <span data-ttu-id="0fa4f-117">Versão mínima</span><span class="sxs-lookup"><span data-stu-id="0fa4f-117">Minimum version</span></span> | 
|---|---|---|
| <span data-ttu-id="0fa4f-118">glibc</span><span class="sxs-lookup"><span data-stu-id="0fa4f-118">glibc</span></span>| <span data-ttu-id="0fa4f-119">Biblioteca de GNU</span><span class="sxs-lookup"><span data-stu-id="0fa4f-119">GNU Library</span></span>| <span data-ttu-id="0fa4f-120">2…4 – 31.30</span><span class="sxs-lookup"><span data-stu-id="0fa4f-120">2…4 – 31.30</span></span>| 
| <span data-ttu-id="0fa4f-121">python</span><span class="sxs-lookup"><span data-stu-id="0fa4f-121">python</span></span>| <span data-ttu-id="0fa4f-122">Python</span><span class="sxs-lookup"><span data-stu-id="0fa4f-122">Python</span></span>| <span data-ttu-id="0fa4f-123">2.4 – 3.4</span><span class="sxs-lookup"><span data-stu-id="0fa4f-123">2.4 – 3.4</span></span>| 
| <span data-ttu-id="0fa4f-124">omiserver</span><span class="sxs-lookup"><span data-stu-id="0fa4f-124">omiserver</span></span>| <span data-ttu-id="0fa4f-125">Abrir Infraestrutura de Gestão</span><span class="sxs-lookup"><span data-stu-id="0fa4f-125">Open Management Infrastructure</span></span>| <span data-ttu-id="0fa4f-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="0fa4f-126">1.0.8.1</span></span>| 
| <span data-ttu-id="0fa4f-127">OpenSSL</span><span class="sxs-lookup"><span data-stu-id="0fa4f-127">openssl</span></span>| <span data-ttu-id="0fa4f-128">Bibliotecas de OpenSSL</span><span class="sxs-lookup"><span data-stu-id="0fa4f-128">OpenSSL Libraries</span></span>| <span data-ttu-id="0fa4f-129">0.9.8 ou 1.0</span><span class="sxs-lookup"><span data-stu-id="0fa4f-129">0.9.8 or 1.0</span></span>| 
| <span data-ttu-id="0fa4f-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="0fa4f-130">ctypes</span></span>| <span data-ttu-id="0fa4f-131">Biblioteca Python CTypes</span><span class="sxs-lookup"><span data-stu-id="0fa4f-131">Python CTypes library</span></span>| <span data-ttu-id="0fa4f-132">Tem de corresponder à versão do Python</span><span class="sxs-lookup"><span data-stu-id="0fa4f-132">Must match Python version</span></span>| 
| <span data-ttu-id="0fa4f-133">libcurl</span><span class="sxs-lookup"><span data-stu-id="0fa4f-133">libcurl</span></span>| <span data-ttu-id="0fa4f-134">biblioteca de clientes http cURL</span><span class="sxs-lookup"><span data-stu-id="0fa4f-134">cURL http client library</span></span>| <span data-ttu-id="0fa4f-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="0fa4f-135">7.15.1</span></span>| 

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="0fa4f-136">Instalar o DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="0fa4f-136">Installing DSC for Linux</span></span>

<span data-ttu-id="0fa4f-137">Tem de instalar o [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) antes de instalar o DSC de Linux.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="0fa4f-138">Instalar o OMI</span><span class="sxs-lookup"><span data-stu-id="0fa4f-138">Installing OMI</span></span>

<span data-ttu-id="0fa4f-139">Configuração do estado pretendido de para Linux requer o servidor CIM Open Management Infrastructure (OMI), versão 1.0.8.1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="0fa4f-140">Pode ser transferido OMI da Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="0fa4f-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="0fa4f-141">Para instalar o OMI, instale o pacote que é adequado para o seu sistema Linux (.rpm ou .deb) e a versão de OpenSSL (ssl_098 ou ssl_100) e a arquitetura (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="0fa4f-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="0fa4f-142">Pacotes RPM são adequados para CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server e Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="0fa4f-143">Pacotes de DEB são adequados para Debian GNU/Linux e Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="0fa4f-144">Os pacotes de ssl_098 são adequados para computadores com OpenSSL 0.9.8 instalado enquanto os pacotes de ssl_100 são adequados para computadores com OpenSSL 1.0 instalado.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> <span data-ttu-id="0fa4f-145">**Tenha em atenção**: para determinar a versão de OpenSSL instalada, execute o comando `openssl version`.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-145">**Note**: To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="0fa4f-146">Execute o seguinte comando para instalar o OMI num sistema CentOS 7 x64.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="0fa4f-147">Instalar o DSC</span><span class="sxs-lookup"><span data-stu-id="0fa4f-147">Installing DSC</span></span>

<span data-ttu-id="0fa4f-148">O DSC de Linux está disponível para transferência [aqui](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="0fa4f-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest).</span></span> 

<span data-ttu-id="0fa4f-149">Para instalar o DSC, instale o pacote que é adequado para o seu sistema Linux (.rpm ou .deb) e a versão de OpenSSL (ssl_098 ou ssl_100) e a arquitetura (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="0fa4f-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="0fa4f-150">Pacotes RPM são adequados para CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server e Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="0fa4f-151">Pacotes de DEB são adequados para Debian GNU/Linux e Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="0fa4f-152">Os pacotes de ssl_098 são adequados para computadores com OpenSSL 0.9.8 instalado enquanto os pacotes de ssl_100 são adequados para computadores com OpenSSL 1.0 instalado.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> <span data-ttu-id="0fa4f-153">**Tenha em atenção**: para determinar a versão de OpenSSL instalada, execute a versão de openssl de comando.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-153">**Note**: To determine the installed OpenSSL version, run the command openssl version.</span></span>
 
<span data-ttu-id="0fa4f-154">Execute o seguinte comando para instalar o DSC num sistema CentOS 7 x64.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`


## <a name="using-dsc-for-linux"></a><span data-ttu-id="0fa4f-155">Utilizar o DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="0fa4f-155">Using DSC for Linux</span></span>

<span data-ttu-id="0fa4f-156">As secções seguintes explicam como criar e executar as configurações de DSC nos computadores com Linux.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="0fa4f-157">Criar um documento MOF de configuração</span><span class="sxs-lookup"><span data-stu-id="0fa4f-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="0fa4f-158">A palavra-chave de configuração do Windows PowerShell é utilizada para criar uma configuração para computadores Linux, tal como em computadores Windows.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="0fa4f-159">Os passos seguintes descrevem a criação de um documento de configuração para um computador com Linux através do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="0fa4f-160">Importe o módulo de nx.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-160">Import the nx module.</span></span> <span data-ttu-id="0fa4f-161">O módulo do Windows PowerShell nx contém o esquema de recursos incorporados para DSC para Linux e tem de ser instalado no computador local e importado para a configuração.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

    <span data-ttu-id="0fa4f-162">-Para instalar o módulo de nx, copie o diretório de módulo nx quer `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` ou `$PSHOME\Modules`.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-162">-To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="0fa4f-163">O módulo de nx está incluído no DSC Linux pacote de instalação (MSI).</span><span class="sxs-lookup"><span data-stu-id="0fa4f-163">The nx module is included in the DSC for Linux installation package (MSI).</span></span> <span data-ttu-id="0fa4f-164">Para importar o módulo de nx na configuração, utilize o __importação DSCResource__ comando:</span><span class="sxs-lookup"><span data-stu-id="0fa4f-164">To import the nx module in your configuration, use the __Import-DSCResource__ command:</span></span>
    
```powershell
Configuration ExampleConfiguration{
   
    Import-DSCResource -Module nx

}
```
2. <span data-ttu-id="0fa4f-165">Definir uma configuração e gerar o documento de configuração:</span><span class="sxs-lookup"><span data-stu-id="0fa4f-165">Define a configuration and generate the configuration document:</span></span>

```powershell
Configuration ExampleConfiguration{
   
    Import-DscResource -Module nx
 
    Node  "linuxhost.contoso.com"{
    nxFile ExampleFile {

        DestinationPath = "/tmp/example"
        Contents = "hello world `n"
        Ensure = "Present"
        Type = "File"
    }

    }
}
ExampleConfiguration -OutputPath:"C:\temp" 
```

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="0fa4f-166">Enviar a configuração para o computador com Linux</span><span class="sxs-lookup"><span data-stu-id="0fa4f-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="0fa4f-167">Documentos de configuração (ficheiros MOF) podem ser enviados para o computador Linux com o [início DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span> <span data-ttu-id="0fa4f-168">Para poder utilizar este cmdlet, juntamente com o [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx), ou [teste DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlets, remotamente para um computador com Linux, tem de utilizar um CIMSession.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-168">In order to use this cmdlet, along with the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx), or [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="0fa4f-169">O [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet é utilizado para criar um CIMSession pelo computador Linux.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-169">The [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="0fa4f-170">O código seguinte mostra como criar um CIMSession para DSC para Linux.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true 
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90 
```

> <span data-ttu-id="0fa4f-171">**Tenha em atenção**:</span><span class="sxs-lookup"><span data-stu-id="0fa4f-171">**Note**:</span></span>
* <span data-ttu-id="0fa4f-172">Para o modo "Push", as credenciais de utilizador tem de ser o utilizador raiz no computador Linux.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-172">For “Push” mode, the user credential must be the root user on the Linux computer.</span></span>
* <span data-ttu-id="0fa4f-173">Ligações de SSL/TLS só são suportadas DSC para Linux, New-CimSession tem de ser utilizado com o parâmetro – UseSSL definido como $true.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-173">Only SSL/TLS connections are supported for DSC for Linux, the New-CimSession must be used with the –UseSSL parameter set to $true.</span></span>
* <span data-ttu-id="0fa4f-174">O certificado SSL utilizado pelo OMI (para DSC) está especificado no ficheiro: `/opt/omi/etc/omiserver.conf` com as propriedades: pemfile e ficheiro de chave.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-174">The SSL certificate used by OMI (for DSC) is specified in the file: `/opt/omi/etc/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
<span data-ttu-id="0fa4f-175">Se este certificado não é considerado fidedigno pelo computador Windows que está a executar o [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet no, pode optar por ignorar a validação de certificado com as opções de CIMSession:`-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span><span class="sxs-lookup"><span data-stu-id="0fa4f-175">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span></span>

<span data-ttu-id="0fa4f-176">Execute o seguinte comando para enviar a configuração de DSC ao nó de Linux.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-176">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="0fa4f-177">Distribuir a configuração com um servidor de solicitação</span><span class="sxs-lookup"><span data-stu-id="0fa4f-177">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="0fa4f-178">Configurações podem ser distribuídas para um computador com Linux com um servidor de solicitação, tal como em computadores Windows.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-178">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="0fa4f-179">Para obter orientações sobre a utilização de um servidor de solicitação, consulte [Windows PowerShell pretendido Estado solicitação servidores de configuração](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="0fa4f-179">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="0fa4f-180">Para obter informações adicionais e limitações relacionadas com a utilização de computadores com Linux com um servidor de solicitação, consulte as notas de versão para configuração de estado pretendido para Linux.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-180">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="0fa4f-181">Trabalhar com configurações localmente</span><span class="sxs-lookup"><span data-stu-id="0fa4f-181">Working with configurations locally</span></span>

<span data-ttu-id="0fa4f-182">DSC para Linux inclui scripts para trabalhar com a configuração do computador local do Linux.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-182">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="0fa4f-183">Estes scripts estão localizar no `/opt/microsoft/dsc/Scripts` e incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0fa4f-183">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>
* <span data-ttu-id="0fa4f-184">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="0fa4f-184">GetDscConfiguration.py</span></span>

 <span data-ttu-id="0fa4f-185">Devolve a configuração atual, aplicada ao computador.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-185">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="0fa4f-186">Semelhante para o cmdlet Get-DscConfiguration do cmdlet do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-186">Similar to the Windows PowerShell cmdlet Get-DscConfiguration cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

* <span data-ttu-id="0fa4f-187">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="0fa4f-187">GetDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="0fa4f-188">Devolve a configuração atual do meta-aplicada ao computador.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-188">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="0fa4f-189">Semelhante ao cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-189">Similar to the cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

* <span data-ttu-id="0fa4f-190">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="0fa4f-190">InstallModule.py</span></span>

 <span data-ttu-id="0fa4f-191">Instala um módulo de recursos de DSC personalizado.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-191">Installs a custom DSC resource module.</span></span> <span data-ttu-id="0fa4f-192">Requer que o caminho para um ficheiro. zip que contém a biblioteca de partilhado do objeto de módulo e ficheiros MOF de esquema.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-192">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

* <span data-ttu-id="0fa4f-193">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="0fa4f-193">RemoveModule.py</span></span>

 <span data-ttu-id="0fa4f-194">Remove um módulo de recursos de DSC personalizado.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-194">Removes a custom DSC resource module.</span></span> <span data-ttu-id="0fa4f-195">Requer o nome do módulo a remover.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-195">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

* <span data-ttu-id="0fa4f-196">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="0fa4f-196">StartDscLocalConfigurationManager.py</span></span> 

 <span data-ttu-id="0fa4f-197">Aplica-se um ficheiro MOF de configuração para o computador.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-197">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="0fa4f-198">Semelhante para o [início DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-198">Similar to the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span> <span data-ttu-id="0fa4f-199">Requer que o caminho para a configuração MOF a aplicar.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-199">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

* <span data-ttu-id="0fa4f-200">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="0fa4f-200">SetDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="0fa4f-201">Aplica-se um ficheiro MOF da configuração de metadados para o computador.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-201">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="0fa4f-202">Semelhante para o [conjunto DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-202">Similar to the [Set-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) cmdlet.</span></span> <span data-ttu-id="0fa4f-203">Requer que o caminho para o MOF de configuração Meta para aplicar.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-203">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="0fa4f-204">Configuração de estado para ficheiros de registo do Linux de pretendido do PowerShell</span><span class="sxs-lookup"><span data-stu-id="0fa4f-204">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="0fa4f-205">Os seguintes ficheiros de registo são gerados para DSC para mensagens de Linux.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-205">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="0fa4f-206">Ficheiro de registo</span><span class="sxs-lookup"><span data-stu-id="0fa4f-206">Log file</span></span>|<span data-ttu-id="0fa4f-207">Diretório</span><span class="sxs-lookup"><span data-stu-id="0fa4f-207">Directory</span></span>|<span data-ttu-id="0fa4f-208">Descrição</span><span class="sxs-lookup"><span data-stu-id="0fa4f-208">Description</span></span>|
|---|---|---|
|<span data-ttu-id="0fa4f-209">omiserver.log</span><span class="sxs-lookup"><span data-stu-id="0fa4f-209">omiserver.log</span></span>|<span data-ttu-id="0fa4f-210">/var/opt/omi/log</span><span class="sxs-lookup"><span data-stu-id="0fa4f-210">/var/opt/omi/log</span></span>|<span data-ttu-id="0fa4f-211">Mensagens relacionadas com a operação do servidor OMI CIM.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-211">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="0fa4f-212">dsc.log</span><span class="sxs-lookup"><span data-stu-id="0fa4f-212">dsc.log</span></span>|<span data-ttu-id="0fa4f-213">/var/opt/omi/log</span><span class="sxs-lookup"><span data-stu-id="0fa4f-213">/var/opt/omi/log</span></span>|<span data-ttu-id="0fa4f-214">Mensagens relacionadas com a operação das operações de recursos do Gestor de configuração Local (MMC) e DSC.</span><span class="sxs-lookup"><span data-stu-id="0fa4f-214">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|

