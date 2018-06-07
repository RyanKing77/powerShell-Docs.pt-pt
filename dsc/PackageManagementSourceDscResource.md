---
ms.date: 06/20/2018
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos do DSC PackageManagementSource
ms.openlocfilehash: 5d049b05c387cafe27edb202d569852b10852dce
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753775"
---
# <a name="dsc-packagemanagementsource-resource"></a>Recursos do DSC PackageManagementSource

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0, 5.1 do Windows PowerShell

O **PackageManagementSource** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para registar ou anular o registo de origens de pacote de gestão num nó de destino. **Origens de gestão do pacote registadas desta forma estão registadas no contexto de sistema utilizável pela conta de sistema ou pelo motor de DSC.** Este recurso necessita do **PackageManagement** módulo, disponível a partir do http://PowerShellGallery.com.

> [!IMPORTANT]
> O **PackageManagement** módulo deve ser, pelo menos, versão 1.1.7.0 as seguintes informações de propriedade corretas.

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
| Nome| Especifica o nome da origem do pacote para ser registado ou não registados no seu sistema.|
| ProviderName| Especifica o nome do fornecedor OneGet através do qual pode interoperabilidade com a origem do pacote.|
| SourceLocation| Especifica o URI da origem do pacote.|
| Certifique-se| Determina se a origem do pacote está a ser registado ou não registados.|
| InstallationPolicy| Utilizada pelos fornecedores, tais como o fornecedor do Nuget incorporada. Determina se confiar origem do pacote. Um dos: "Não fidedignas", "Fidedigna".|
| SourceCredential| Fornece acesso ao pacote de uma origem remota.|

## <a name="example"></a>Exemplo

Neste exemplo regista o http://nuget.org origem do pacote com o **PackageManagementSource** recursos de DSC.

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