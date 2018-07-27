---
ms.date: 06/20/2018
keywords: DSC, powershell, configuração, a configuração
title: Recursos do DSC PackageManagement
ms.openlocfilehash: 18cbbfe0715c82dcfdf4a5fb6ee36ee814e43d3b
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268097"
---
# <a name="dsc-packagemanagement-resource"></a>Recursos do DSC PackageManagement

Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0, 5.1 do Windows PowerShell

O **PackageManagement** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para instalar ou desinstalar pacotes de gestão de pacotes num nó de destino. Este recurso requer o **PackageManagement** módulo, disponível no [ http://PowerShellGallery.com ](http://PowerShellGallery.com).

> [!IMPORTANT]
> O **PackageManagement** módulo deve ser, pelo menos, versão 1.1.7.0 as seguintes informações de propriedade esteja correto.

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

| Propriedade | Descrição |
| --- | --- |
| Nome| Especifica o nome do pacote a ser instalada ou desinstalada.|
| AdditionalParameters| Tabela de hash específica do fornecedor de parâmetros transferidos para `Get-Package -AdditionalArguments`. Por exemplo, para o fornecedor de NuGet pode transmitir parâmetros adicionais, como DestinationPath.|
| Certifique-se| Determina se o pacote é para ser instalada ou desinstalada.|
| MaximumVersion|Especifica o máximo permitido de versão do pacote que pretende localizar. Se não adicionar este parâmetro, o recurso localiza a versão mais recente disponível do pacote.|
| MinimumVersion|Especifica o mínimo de versão do pacote que pretende localizar. Se não adicionar este parâmetro, o recurso localiza a versão mais recente disponível do pacote que satisfaça também qualquer versão especificada máximo especificado pelos _MaximumVersion_ parâmetro.|
| ProviderName| Especifica um nome de fornecedor do pacote ao qual pretende definir o âmbito da pesquisa de pacote. Pode obter nomes de fornecedor do pacote ao executar o `Get-PackageProvider` cmdlet.|
| RequiredVersion| Especifica a versão exata do pacote que pretende instalar. Se não especificar este parâmetro, este recurso de DSC instala a versão disponível mais recente do pacote que também coincida com qualquer versão máximo especificado pelos _MaximumVersion_ parâmetro.|
| Origem| Especifica o nome da origem do pacote, onde o pacote pode ser encontrado. Isso pode ser um URI ou uma origem de registada com `Register-PackageSource` ou recurso de DSC PackageManagementSource.|
| SourceCredential | Especifica uma conta de utilizador que tenha direitos para instalar um pacote para um fornecedor do pacote especificado ou a origem.|

## <a name="additional-parameters"></a>Parâmetros adicionais

A tabela seguinte apresenta uma lista de opções para a propriedade AdditionalParameters.

| Parâmetro | Descrição |
| --- | --- |
| DestinationPath| Utilizado por fornecedores, como o fornecedor de Nuget incorporado. Especifica uma localização do ficheiro onde pretende que o pacote a ser instalado.|
| InstallationPolicy| Utilizado por fornecedores, como o fornecedor de Nuget incorporado. Determina se confiam origem do pacote. Um dos: `Untrusted`, `Trusted`.|

## <a name="example"></a>Exemplo

Este exemplo instala o **JQuery** pacote NuGet e **GistProvider** módulo do PowerShell com o **PackageManagement** recursos de DSC. Este exemplo primeiro garante que as origens de pacotes estão disponíveis, em seguida, define o estado esperado dos **JQuery** e **GistProvider** pacotes (NuGet e o PowerShell, respectivamente).

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