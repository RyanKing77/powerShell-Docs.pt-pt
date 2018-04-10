---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Separar dados de configuração e de ambiente
ms.openlocfilehash: c89e26105611eae59a926be1432079913c40671f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="separating-configuration-and-environment-data"></a><span data-ttu-id="34fd4-103">Separar dados de configuração e de ambiente</span><span class="sxs-lookup"><span data-stu-id="34fd4-103">Separating configuration and environment data</span></span>

><span data-ttu-id="34fd4-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="34fd4-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="34fd4-105">Pode ser útil separar os dados utilizados numa configuração de DSC da configuração do próprio através da utilização de dados de configuração.</span><span class="sxs-lookup"><span data-stu-id="34fd4-105">It can be useful to separate the data used in a DSC configuration from the configuration itself by using configuration data.</span></span>
<span data-ttu-id="34fd4-106">Ao fazê-lo, pode utilizar uma configuração única para vários ambientes.</span><span class="sxs-lookup"><span data-stu-id="34fd4-106">By doing this, you can use a single configuration for multiple environments.</span></span>

<span data-ttu-id="34fd4-107">Por exemplo, se estiver a desenvolver uma aplicação, pode utilizar uma configuração para ambientes de desenvolvimento e de produção e utilizar dados de configuração para especificar os dados para cada ambiente.</span><span class="sxs-lookup"><span data-stu-id="34fd4-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

## <a name="what-is-configuration-data"></a><span data-ttu-id="34fd4-108">O que é dados de configuração?</span><span class="sxs-lookup"><span data-stu-id="34fd4-108">What is configuration data?</span></span>

<span data-ttu-id="34fd4-109">Dados de configuração são os dados que estão definidos numa tabela hash e transmitidos para uma configuração de DSC quando compilar que a configuração.</span><span class="sxs-lookup"><span data-stu-id="34fd4-109">Configuration data is data that is defined in a hashtable and passed to a DSC configuration when you compile that configuration.</span></span>

<span data-ttu-id="34fd4-110">Para obter uma descrição detalhada do **ConfigurationData** tabela hash, consulte [utilizando dados de configuração](configData.md).</span><span class="sxs-lookup"><span data-stu-id="34fd4-110">For a detailed description of the **ConfigurationData** hashtable, see [Using configuration data](configData.md).</span></span>

## <a name="a-simple-example"></a><span data-ttu-id="34fd4-111">Um exemplo simples</span><span class="sxs-lookup"><span data-stu-id="34fd4-111">A simple example</span></span>

<span data-ttu-id="34fd4-112">Vamos ver um exemplo muito simples para ver como isto funciona.</span><span class="sxs-lookup"><span data-stu-id="34fd4-112">Let's look at a very simple example to see how this works.</span></span>
<span data-ttu-id="34fd4-113">Vamos criar uma configuração única que assegura que **IIS** está presente no alguns nós e que **Hyper-V** está presente na outros utilizadores:</span><span class="sxs-lookup"><span data-stu-id="34fd4-113">We'll create a single configuration that ensures that **IIS** is present on some nodes, and that **Hyper-V** is present on others:</span></span>

```powershell
Configuration MyDscConfiguration {

    Node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        WindowsFeature IISInstall {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }

    }
    Node $AllNodes.Where{$_.Role -eq "VMHost"}.NodeName
    {
        WindowsFeature HyperVInstall {
            Ensure = 'Present'
            Name   = 'Hyper-V'
        }
    }
}

$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            Role = 'WebServer'
        },

        @{
            NodeName    = 'VM-2'
            Role = 'VMHost'
        }
    )
}

MyDscConfiguration -ConfigurationData $MyData
```

<span data-ttu-id="34fd4-114">A última linha este script compila a configuração, transmitir `$MyData` como o valor **ConfigurationData** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="34fd4-114">The last line in this script compiles the configuration, passing `$MyData` as the value **ConfigurationData** parameter.</span></span>

<span data-ttu-id="34fd4-115">O resultado é que são criados dois ficheiros MOF:</span><span class="sxs-lookup"><span data-stu-id="34fd4-115">The result is that two MOF files are created:</span></span>

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

<span data-ttu-id="34fd4-116">`$MyData` Especifica a dois nós diferentes, cada uma com a sua própria `NodeName` e `Role`.</span><span class="sxs-lookup"><span data-stu-id="34fd4-116">`$MyData` specifies two different nodes, each with its own `NodeName` and `Role`.</span></span> <span data-ttu-id="34fd4-117">A configuração cria dinamicamente **nó** blocos, efetuando a coleção de nós que obtém a partir do `$MyData` (especificamente, `$AllNodes`) e filtra nessa coleção contra o `Role` propriedade...</span><span class="sxs-lookup"><span data-stu-id="34fd4-117">The configuration dynamically creates **Node** blocks by taking the collection of nodes it gets from `$MyData` (specifically, `$AllNodes`) and filters that collection against the `Role` property..</span></span>

## <a name="using-configuration-data-to-define-development-and-production-environments"></a><span data-ttu-id="34fd4-118">Com dados de configuração para definir a ambientes de desenvolvimento e de produção</span><span class="sxs-lookup"><span data-stu-id="34fd4-118">Using configuration data to define development and production environments</span></span>

<span data-ttu-id="34fd4-119">Vamos ver um exemplo completo que utiliza uma configuração única para configurar ambientes de desenvolvimento e de produção de um Web site.</span><span class="sxs-lookup"><span data-stu-id="34fd4-119">Let's look at a complete example that uses a single configuration to set up both development and production environments of a website.</span></span> <span data-ttu-id="34fd4-120">O ambiente de desenvolvimento, IIS e SQL Server são instalados em nós de um único.</span><span class="sxs-lookup"><span data-stu-id="34fd4-120">In the development environment, both IIS and SQL Server are installed on a single nodes.</span></span> <span data-ttu-id="34fd4-121">No ambiente de produção, IIS e o SQL Server estão instalados em nós separados.</span><span class="sxs-lookup"><span data-stu-id="34fd4-121">In the production environment, IIS and SQL Server are installed on separate nodes.</span></span> <span data-ttu-id="34fd4-122">Iremos utilizar um ficheiro de. psd1 de dados de configuração para especificar os dados para os dois ambientes diferentes.</span><span class="sxs-lookup"><span data-stu-id="34fd4-122">We'll use a configuration data .psd1 file to specify the data for the two different environments.</span></span>

 ### <a name="configuration-data-file"></a><span data-ttu-id="34fd4-123">Ficheiro de dados de configuração</span><span class="sxs-lookup"><span data-stu-id="34fd4-123">Configuration data file</span></span>

<span data-ttu-id="34fd4-124">Iremos definir os dados de ambiente de desenvolvimento e de produção no namd ficheiro `DevProdEnvData.psd1` da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="34fd4-124">We'll define the development and production environment data in a file namd `DevProdEnvData.psd1` as follows:</span></span>

```powershell
@{

    AllNodes = @(

        @{
            NodeName        = "*"
            SQLServerName   = "MySQLServer"
            SqlSource       = "C:\Software\Sql"
            DotNetSrc       = "C:\Software\sxs"
        WebSiteName     = "New website"
        },

        @{
            NodeName        = "Prod-SQL"
            Role            = "MSSQL"
        },

        @{
            NodeName        = "Prod-IIS"
            Role            = "Web"
            SiteContents    = "C:\Website\Prod\SiteContents\"
            SitePath        = "\\Prod-IIS\Website\"
        },

        @{
            NodeName         = "Dev"
            Role             = "MSSQL", "Web"
            SiteContents     = "C:\Website\Dev\SiteContents\"
            SitePath         = "\\Dev\Website\"
        }
    )
}
```

### <a name="configuration-script-file"></a><span data-ttu-id="34fd4-125">Ficheiro de script de configuração</span><span class="sxs-lookup"><span data-stu-id="34fd4-125">Configuration script file</span></span>

<span data-ttu-id="34fd4-126">Agora, na configuração, que está definido num `.ps1` ficheiro, iremos filtrar os nós que definimos no `DevProdEnvData.psd1` pela respetiva função (`MSSQL`, `Dev`, ou ambos) e configurá-los em conformidade.</span><span class="sxs-lookup"><span data-stu-id="34fd4-126">Now, in the configuration, which is defined in a `.ps1` file, we filter the nodes we defined in `DevProdEnvData.psd1` by their role (`MSSQL`, `Dev`, or both), and configure them accordingly.</span></span>
<span data-ttu-id="34fd4-127">O ambiente de desenvolvimento tem o SQL Server e o IIS num único nó, enquanto que o ambiente de produção tem-los em dois nós diferentes.</span><span class="sxs-lookup"><span data-stu-id="34fd4-127">The development environment has both the SQL Server and IIS on one node, while the production environment has them on two different nodes.</span></span>
<span data-ttu-id="34fd4-128">O conteúdo do site também é diferente, tal como especificado pelo `SiteContents` propriedades.</span><span class="sxs-lookup"><span data-stu-id="34fd4-128">The site contents is also different, as specified by the `SiteContents` properties.</span></span>

<span data-ttu-id="34fd4-129">No final do script de configuração, chamamos a configuração (compilá-la para um documento MOF), passing `DevProdEnvData.psd1` como o `$ConfigurationData` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="34fd4-129">At the end of the configuration script, we call the configuration (compile it into a MOF document), passing `DevProdEnvData.psd1` as the `$ConfigurationData` parameter.</span></span>

><span data-ttu-id="34fd4-130">**Nota:** esta configuração requer os módulos `xSqlPs` e `xWebAdministration` para ser instalado no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="34fd4-130">**Note:** This configuration requires the modules `xSqlPs` and `xWebAdministration` to be installed on the target node.</span></span>

<span data-ttu-id="34fd4-131">Vamos definir a configuração num ficheiro denominado `MyWebApp.ps1`:</span><span class="sxs-lookup"><span data-stu-id="34fd4-131">Let's define the configuration in a file named `MyWebApp.ps1`:</span></span>

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs
    Import-DscResource -Module xWebAdministration

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.NodeName
   {
        # Install prerequisites
        WindowsFeature installdotNet35
        {
            Ensure      = "Present"
            Name        = "Net-Framework-Core"
            Source      = "c:\software\sxs"
        }

        # Install SQL Server
        xSqlServerInstall InstallSqlServer
        {
            InstanceName = $Node.SQLServerName
            SourcePath   = $Node.SqlSource
            Features     = "SQLEngine,SSMS"
            DependsOn    = "[WindowsFeature]installdotNet35"

        }
   }

   Node $AllNodes.Where{$_.Role -contains "Web"}.NodeName
   {
        # Install the IIS role
        WindowsFeature IIS
        {
            Ensure       = 'Present'
            Name         = 'Web-Server'
        }

        # Install the ASP .NET 4.5 role
        WindowsFeature AspNet45
        {
            Ensure       = 'Present'
            Name         = 'Web-Asp-Net45'

        }

        # Stop the default website
        xWebsite DefaultSite
        {
            Ensure       = 'Present'
            Name         = 'Default Web Site'
            State        = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn    = '[WindowsFeature]IIS'

        }

        # Copy the website content
        File WebContent

        {
            Ensure          = 'Present'
            SourcePath      = $Node.SiteContents
            DestinationPath = $Node.SitePath
            Recurse         = $true
            Type            = 'Directory'
            DependsOn       = '[WindowsFeature]AspNet45'

        }


        # Create the new Website

        xWebsite NewWebsite

        {

            Ensure          = 'Present'
            Name            = $Node.WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

<span data-ttu-id="34fd4-132">Quando executar esta configuração, são criados três ficheiros MOF (um para cada entrada com o nome de **AllNodes** matriz):</span><span class="sxs-lookup"><span data-stu-id="34fd4-132">When you run this configuration, three MOF files are created (one for each named entry in the **AllNodes** array):</span></span>

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a><span data-ttu-id="34fd4-133">Utilização de dados do nó não</span><span class="sxs-lookup"><span data-stu-id="34fd4-133">Using non-node data</span></span>

<span data-ttu-id="34fd4-134">Pode adicionar chaves adicionais para o **ConfigurationData** tabela hash para dados que não são específicos para um nó.</span><span class="sxs-lookup"><span data-stu-id="34fd4-134">You can add additional keys to the **ConfigurationData** hashtable for data that is not specific to a node.</span></span>
<span data-ttu-id="34fd4-135">A seguinte configuração garante a presença dos dois sites.</span><span class="sxs-lookup"><span data-stu-id="34fd4-135">The following configuration ensures the presence of two websites.</span></span>
<span data-ttu-id="34fd4-136">Os dados para cada Web site são definidos no **AllNodes** matriz.</span><span class="sxs-lookup"><span data-stu-id="34fd4-136">Data for each website are defined in the **AllNodes** array.</span></span>
<span data-ttu-id="34fd4-137">O ficheiro `Config.xml` é utilizado para os dois Web sites, pelo que definimos numa chave adicional com o nome `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="34fd4-137">The file `Config.xml` is used for both websites, so we define it in an additional key with the name `NonNodeData`.</span></span>
<span data-ttu-id="34fd4-138">Tenha em atenção que pode ter como número de chaves adicional à medida que quiser, pode atribuir o nome-los tudo o que pretende.</span><span class="sxs-lookup"><span data-stu-id="34fd4-138">Note that you can have as many additional keys as you want, and you can name them anything you want.</span></span>
<span data-ttu-id="34fd4-139">`NonNodeData` Não é uma palavra reservada, é apenas o que decidimos nomear a chave adicional.</span><span class="sxs-lookup"><span data-stu-id="34fd4-139">`NonNodeData` is not a reserved word, it is just what we decided to name the additional key.</span></span>

<span data-ttu-id="34fd4-140">Aceder às chaves adicionais ao utilizar a variável especial **$ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="34fd4-140">You access additional keys by using the special variable **$ConfigurationData**.</span></span>
<span data-ttu-id="34fd4-141">Neste exemplo, `ConfigFileContents` é acedida com a linha:</span><span class="sxs-lookup"><span data-stu-id="34fd4-141">In this example, `ConfigFileContents` is accessed with the line:</span></span>
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 <span data-ttu-id="34fd4-142">no `File` blocos de recursos.</span><span class="sxs-lookup"><span data-stu-id="34fd4-142">in the `File` resource block.</span></span>


```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName           = “*”
            LogPath            = “C:\Logs”
        },

        @{
            NodeName = “VM-1”
            SiteContents = “C:\Site1”
            SiteName = “Website1”
        },


        @{
            NodeName = “VM-2”;
            SiteContents = “C:\Site2”
            SiteName = “Website2”
        }
    );

    NonNodeData =
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }
}

configuration WebsiteConfig
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite

    node $AllNodes.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = “Present”
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + “\\config.xml”
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```


## <a name="see-also"></a><span data-ttu-id="34fd4-143">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="34fd4-143">See Also</span></span>
- [<span data-ttu-id="34fd4-144">Utilizar dados de configuração</span><span class="sxs-lookup"><span data-stu-id="34fd4-144">Using configuration data</span></span>](configData.md)
- [<span data-ttu-id="34fd4-145">Opções de credenciais nos dados de configuração</span><span class="sxs-lookup"><span data-stu-id="34fd4-145">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="34fd4-146">Configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="34fd4-146">DSC Configurations</span></span>](configurations.md)