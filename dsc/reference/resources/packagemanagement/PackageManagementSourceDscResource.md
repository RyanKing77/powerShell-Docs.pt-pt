---
ms.date: 06/20/2018
keywords: DSC, powershell, configuração, a configuração
title: Recursos do DSC PackageManagementSource
ms.openlocfilehash: e51b5318288bef458567dd4b58d17caaea3ed69b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077590"
---
# <a name="dsc-packagemanagementsource-resource"></a>Recursos do DSC PackageManagementSource

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1

O **PackageManagementSource** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para registar ou anular o registo de origens do pacote de gestão num nó de destino. **Origens de gestão do pacote registadas dessa forma são registadas no contexto de sistema, utilizável pela conta do sistema ou pelo motor de DSC.** Este recurso requer o **PackageManagement** módulo, disponível no http://PowerShellGallery.com.

> [!IMPORTANT]
> O **PackageManagement** módulo deve ser, pelo menos, versão 1.1.7.0 as seguintes informações de propriedade esteja correto.

## <a name="syntax"></a>Sintaxe

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| Nome| Especifica o nome da origem do pacote a ser efetuado ou cancelado no seu sistema.|
| ProviderName| Especifica o nome do fornecedor OneGet por meio do qual pode fornecer interoperabilidade com a origem do pacote.|
| SourceLocation| Especifica o URI de origem do pacote.|
| Certifique-se| Determina se a origem do pacote deve ser efetuado ou cancelado.|
| InstallationPolicy| Utilizado por fornecedores, como o fornecedor de Nuget incorporado. Determina se confiam origem do pacote. Um dos: "Não confiáveis", "fidedigno".|
| SourceCredential| Fornece acesso ao pacote de sobre uma origem remota.|

## <a name="example"></a>Exemplo

Neste exemplo registra o http://nuget.org pacote de origem com o **PackageManagementSource** recursos de DSC.

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```