---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Separação de dados de configuração e de ambiente"
ms.openlocfilehash: 18b18d805ac248b29526862591df5f0ff785937b
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="separating-configuration-and-environment-data"></a>Separação de dados de configuração e de ambiente

>Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

Pode ser útil separar os dados utilizados numa configuração de DSC da configuração do próprio através da utilização de dados de configuração.
Ao fazê-lo, pode utilizar uma configuração única para vários ambientes.

Por exemplo, se estiver a desenvolver uma aplicação, pode utilizar uma configuração para ambientes de desenvolvimento e de produção e utilizar dados de configuração para especificar os dados para cada ambiente.

## <a name="what-is-configuration-data"></a>O que é dados de configuração?

Dados de configuração são os dados que estão definidos numa tabela hash e transmitidos para uma configuração de DSC quando compilar que a configuração.

Para obter uma descrição detalhada do **ConfigurationData** tabela hash, consulte [utilizando dados de configuração](configData.md).

## <a name="a-simple-example"></a>Um exemplo simples

Vamos ver um exemplo muito simples para ver como isto funciona. Vamos criar uma configuração única que assegura que **IIS** está presente no alguns nós e que **Hyper-V** está presente na outros utilizadores: 

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

A última linha este script compila a configuração, transmitir `$MyData` como o valor **ConfigurationData** parâmetro.

O resultado é que são criados dois ficheiros MOF:

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name                                                                                                                    
----                -------------         ------ ----                                                                                                                    
-a----        3/31/2017   5:09 PM           1968 VM-1.mof                                                                                                                
-a----        3/31/2017   5:09 PM           1970 VM-2.mof  
```
 
`$MyData` Especifica a dois nós diferentes, cada uma com a sua própria `NodeName` e `Role`. A configuração cria dinamicamente **nó** blocos, efetuando a coleção de nós que obtém a partir do `$MyData` (especificamente, `$AllNodes`) e filtra nessa coleção contra o `Role` propriedade...

## <a name="using-configuration-data-to-define-development-and-production-environments"></a>Com dados de configuração para definir a ambientes de desenvolvimento e de produção

Vamos ver um exemplo completo que utiliza uma configuração única para configurar ambientes de desenvolvimento e de produção de um Web site. O ambiente de desenvolvimento, IIS e SQL Server são instalados em nós de um único. No ambiente de produção, IIS e o SQL Server estão instalados em nós separados. Iremos utilizar um ficheiro de. psd1 de dados de configuração para especificar os dados para os dois ambientes diferentes.

 ### <a name="configuration-data-file"></a>Ficheiro de dados de configuração

Iremos definir os dados de ambiente de desenvolvimento e de produção no namd ficheiro `DevProdEnvData.psd1` da seguinte forma:

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

### <a name="configuration-script-file"></a>Ficheiro de script de configuração

Agora, na configuração, que está definido num `.ps1` ficheiro, iremos filtrar os nós que definimos no `DevProdEnvData.psd1` pela respetiva função (`MSSQL`, `Dev`, ou ambos) e configurá-los em conformidade. O ambiente de desenvolvimento tem o SQL Server e o IIS num único nó, enquanto que o ambiente de produção tem-los em dois nós diferentes. O conteúdo do site também é diferente, tal como especificado pelo `SiteContents` propriedades.

No final do script de configuração, chamamos a configuração (compilá-la para um documento MOF), passing `DevProdEnvData.psd1` como o `$ConfigurationData` parâmetro.

>**Nota:** esta configuração requer os módulos `xSqlPs` e `xWebAdministration` para ser instalado no nó de destino.

Vamos definir a configuração num ficheiro denominado `MyWebApp.ps1`:

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

Quando executar esta configuração, são criados três ficheiros MOF (um para cada entrada com o nome de **AllNodes** matriz):

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name                                                                                                                    
----                -------------         ------ ----                                                                                                                    
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof                                                                                                            
-a----        3/31/2017   5:47 PM           6994 Dev.mof                                                                                                                 
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a>Utilização de dados do nó não

Pode adicionar chaves adicionais para o **ConfigurationData** tabela hash para dados que não são específicos para um nó.
A seguinte configuração garante a presença dos dois sites.
Os dados para cada Web site são definidos no **AllNodes** matriz.
O ficheiro `Config.xml` é utilizado para os dois Web sites, pelo que definimos numa chave adicional com o nome `NonNodeData`.
Tenha em atenção que pode ter como número de chaves adicional à medida que quiser, pode atribuir o nome-los tudo o que pretende.
`NonNodeData` Não é uma palavra reservada, é apenas o que decidimos nomear a chave adicional.

Aceder às chaves adicionais ao utilizar a variável especial **$ConfigurationData**.
Neste exemplo, `ConfigFileContents` é acedida com a linha:
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 no `File` blocos de recursos.


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


## <a name="see-also"></a>Consulte Também
- [Utilizar dados de configuração](configData.md)
- [Opções de credenciais nos dados de configuração](configDataCredentials.md)
- [Configurações de DSC](configurations.md)

