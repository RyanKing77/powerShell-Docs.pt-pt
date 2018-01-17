---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos do DSC PackageManagement
ms.openlocfilehash: 4cd7625af7ed0bb3fe971c826ac2075841cdfdc5
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-packagemanagement-resource"></a>Recursos do DSC PackageManagement

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

O **PackageManagement** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para instalar ou desinstalar pacotes de gestão de pacotes num nó de destino. Este recurso necessita do **PackageManagement** módulo, disponível a partir do http://PowerShellGallery.com.

## <a name="syntax"></a>Sintaxe

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

## <a name="properties"></a>Propriedades
|  Propriedade  |  Descrição   | 
|---|---| 
| Nome| Especifica o nome do pacote para ser instalada ou desinstalada.| 
| Origem| Especifica o nome da origem do pacote, onde pode encontrar o pacote. Isto pode ser um URI ou uma origem registado com recurso Register-PackageSource ou PackageManagementSource DSC. O recurso de DSC MSFT_PackageManagementSource também pode registar uma origem de pacote.| 
| Certifique-se| Determina se o pacote é para ser instalada ou desinstalada.| 
| RequiredVersion| Especifica a versão exata do pacote que pretende instalar. Se não especificar este parâmetro, este recurso de DSC instala a versão disponível mais recente do pacote que também coincida com qualquer versão máxima especificada pelo parâmetro MaximumVersion.| 
| MinimumVersion| Especifica o mínimo permitido de versão do pacote que pretende instalar. Se adicionar este parâmetro, neste intalls de recursos do DSC a versão disponível mais recente do pacote que também coincida com qualquer versão especificada máximo especificado pelo parâmetro MaximumVersion.| 
| MaximumVersion| Especifica o máximo permitido de versão do pacote que pretende instalar. Se não especificar este parâmetro, este recurso de DSC instala a versão disponível mais elevado numeradas do pacote.| 
| SourceCredential | Especifica uma conta de utilizador que tenha direitos para instalar um pacote para uma origem ou o fornecedor do pacote especificado.| 
| ProviderName| Especifica um nome de fornecedor do pacote para o qual pretende definir o âmbito da pesquisa de pacote. Pode obter os nomes de fornecedor do pacote, executando o cmdlet Get-PackageProvider.| 
| AdditionalParameters| Fornecedor parâmetros específicos que são transmitidos como uma tabela hash. Por exemplo, para o fornecedor do NuGet pode passar parâmetros adicionais, como DestinationPath.| 

## <a name="additional-parameters"></a>Parâmetros adicionais
A tabela seguinte lista as opções para a propriedade AdditionalParameters.
|  Parâmetro  | Descrição   | 
|---|---|
| DestinationPath| Utilizada pelos fornecedores, tais como o fornecedor do Nuget incorporada. Especifica uma localização de ficheiros onde pretende que o pacote de instalação.|
| InstallationPolicy| Utilizada pelos fornecedores, tais como o fornecedor do Nuget incorporada. Determina se confiar origem do pacote. Um dos: "Não fidedignas", "Fidedigna".|

## <a name="example"></a>Exemplo

Este exemplo instala o **JQuery** pacote NuGet e **GistProvider** utilizando o módulo PowerShell do **PackageManagement** recursos de DSC. Neste exemplo garante primeiro as origens de pacotes estão disponíveis, em seguida, define o estado esperado do **JQuery** e **GistProvider** pacotes (NuGet e o PowerShell, respetivamente).

```powershell
Configuration PackageTest
{    
    PackageManagementSource SourceRepository 
    { 
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }    
    
    PackageManagementSource PSGallery 
    { 
        Ensure      = "Present" 
        Name        = "psgallery" 
        ProviderName= "PowerShellGet" 
        SourceUri   = "https://www.powershellgallery.com/api/v2/"   
        InstallationPolicy ="Trusted" 
    } 
          
    PackageManagement NugetPackage 
    { 
        Ensure               = "Present"  
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1" 
        DependsOn            = "[PackageManagementSource]SourceRepository" 
    }
    
    PackageManagement PSModule 
    { 
        Ensure               = "Present"  
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery" 
    }
}
```

