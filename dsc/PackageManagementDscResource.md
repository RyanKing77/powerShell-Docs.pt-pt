---
ms.date: 06/20/2018
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos do DSC PackageManagement
ms.openlocfilehash: 3d52934b130d59acee4d7f8a92da2c743c1eb305
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753792"
---
# <a name="dsc-packagemanagement-resource"></a>Recursos do DSC PackageManagement

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0, 5.1 do Windows PowerShell

O **PackageManagement** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para instalar ou desinstalar pacotes de gestão de pacotes num nó de destino. Este recurso necessita do **PackageManagement** módulo, disponível a partir do http://PowerShellGallery.com.

> [!IMPORTANT]
> O **PackageManagement** módulo deve ser, pelo menos, versão 1.1.7.0 as seguintes informações de propriedade corretas.

## <a name="syntax"></a>Sintaxe

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| Nome| Especifica o nome do pacote para ser instalada ou desinstalada.|
| AdditionalParameters| Tabela de hash específica do fornecedor de parâmetros transferidos para `Get-Package -AdditionalArguments`. Por exemplo, para o fornecedor do NuGet pode passar parâmetros adicionais, como DestinationPath.|
| Certifique-se| Determina se o pacote é para ser instalada ou desinstalada.|
| MaximumVersion|Especifica o máximo permitido de versão do pacote que pretende localizar. Se não adicionar este parâmetro, o recurso localiza a versão disponível mais recente do pacote.|
| MinimumVersion|Especifica o mínimo permitido de versão do pacote que pretende localizar. Se não adicionar este parâmetro, o recurso localiza a versão disponível mais recente do pacote que também coincida com qualquer versão especificada máximo especificado pelo _MaximumVersion_ parâmetro.|
| ProviderName| Especifica um nome de fornecedor do pacote para o qual pretende definir o âmbito da pesquisa de pacote. Pode obter os nomes de fornecedor do pacote, executando o `Get-PackageProvider` cmdlet.|
| RequiredVersion| Especifica a versão exata do pacote que pretende instalar. Se não especificar este parâmetro, este recurso de DSC instala a versão disponível mais recente do pacote que também coincida com qualquer versão máxima especificada pelo _MaximumVersion_ parâmetro.|
| Origem| Especifica o nome da origem do pacote, onde pode encontrar o pacote. Isto pode ser um URI ou uma origem registada com `Register-PackageSource` ou recurso PackageManagementSource DSC.|
| SourceCredential | Especifica uma conta de utilizador que tenha direitos para instalar um pacote para uma origem ou o fornecedor do pacote especificado.|

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
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
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