---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Separar dados de configuração e de ambiente
ms.openlocfilehash: 24a92e5e4f15959498b57a1488a688d5548f3585
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404812"
---
# <a name="separating-configuration-and-environment-data"></a>Separar dados de configuração e de ambiente

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Pode ser útil separar os dados usados numa configuração de DSC da configuração em si, utilizando dados de configuração.
Ao fazer isso, pode utilizar uma configuração única para vários ambientes.

Por exemplo, se estiver a desenvolver uma aplicação, pode utilizar uma configuração para ambientes de desenvolvimento e produção e utilizar dados de configuração para especificar os dados para cada ambiente.

## <a name="what-is-configuration-data"></a>O que é, dados de configuração?

Dados de configuração são os dados que são definidos numa tabela de hash e passados para uma configuração de DSC, quando compilar essa configuração.

Para obter uma descrição detalhada do **ConfigurationData** hashtable, consulte [usando dados de configuração](configData.md).

## <a name="a-simple-example"></a>Um exemplo simples

Vamos examinar um exemplo muito simples para ver como isso funciona.
Vamos criar uma configuração única que garante que **IIS** está presente em alguns nós e que **Hyper-V** está presente no outras pessoas:

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

A última linha neste script compila a configuração, passando `$MyData` como o valor **ConfigurationData** parâmetro.

O resultado é que são criados dois ficheiros de MOF:

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

`$MyData` Especifica os dois nós diferentes, cada um com seu próprio `NodeName` e `Role`. A configuração cria dinamicamente **nó** blocos, efetuando a coleção de nós que obtém a partir do `$MyData` (especificamente, `$AllNodes`) e filtra essa coleção em relação a `Role` propriedade....

## <a name="using-configuration-data-to-define-development-and-production-environments"></a>Usando dados de configuração para definir a ambientes de desenvolvimento e produção

Vamos examinar um exemplo completo que utiliza uma configuração única para configurar ambientes de desenvolvimento e produção de um Web site. O ambiente de desenvolvimento, o IIS e SQL Server são instalados num único nós. No ambiente de produção, o IIS e o SQL Server estão instalados em nós separados. Vamos utilizar um ficheiro de. psd1 de dados de configuração para especificar os dados para os dois ambientes diferentes.

 ### <a name="configuration-data-file"></a>Ficheiro de dados de configuração

Vamos definir os dados de ambiente de desenvolvimento e produção num arquivo chamado `DevProdEnvData.psd1` da seguinte forma:

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

Agora, na configuração, que é definida numa `.ps1` arquivo, podemos filtrar os nós que definimos nos `DevProdEnvData.psd1` pela respetiva função (`MSSQL`, `Dev`, ou ambos) e configurá-los em conformidade.
O ambiente de desenvolvimento tem o SQL Server e o IIS num único nó, enquanto o ambiente de produção tem-los em dois nós diferentes.
O conteúdo do site também é diferente, tal como especificado pelo `SiteContents` propriedades.

No final do script de configuração, chamamos a configuração (compilá-lo num documento MOF), passando `DevProdEnvData.psd1` como o `$ConfigurationData` parâmetro.

>**Nota:** Esta configuração requer os módulos `xSqlPs` e `xWebAdministration` seja instalado no nó de destino.

Vamos definir a configuração num arquivo chamado `MyWebApp.ps1`:

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

Quando executar esta configuração, são criados três ficheiros de MOF (um para cada chamada de entrada na **AllNodes** matriz):

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a>Utilizar os dados de nós não

Pode adicionar chaves adicionais para o **ConfigurationData** hashtable para dados que não são específicos para um nó.
A seguinte configuração garante a presença de dois Web sites.
Os dados para cada Web site são definidos na **AllNodes** matriz.
O ficheiro `Config.xml` é utilizado para ambos os Web sites, pelo que podemos defini-lo de uma chave adicional com o nome `NonNodeData`.
Tenha em atenção de que pode ter tantos chaves adicionais conforme desejar e pode nomeá-los que quiser.
`NonNodeData` Não é uma palavra reservada, é apenas o que decidimos nomeie a chave adicional.

Aceder a chaves adicionais ao utilizar a variável especial **$ConfigurationData**.
Neste exemplo, `ConfigFileContents` são acedidos com a linha:
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 na `File` bloco de recursos.


```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName           = “*”
            LogPath            = “C:\Logs”
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
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = “Present”
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
