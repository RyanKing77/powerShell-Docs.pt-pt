---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos do DSC PackageManagementSource
ms.openlocfilehash: 3e67cec9058ecb0e43f882f98f5ec8b92e261a09
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-packagemanagementsource-resource"></a>Recursos do DSC PackageManagementSource

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

O **PackageManagementSource** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para registar ou anular o registo de origens de pacote de gestão num nó de destino. **Origens de gestão do pacote registadas desta forma estão registadas no contexto de sistema utilizável pela conta de sistema ou pelo motor de DSC.** Este recurso necessita do **PackageManagement** módulo, disponível a partir do http://PowerShellGallery.com.

## <a name="syntax"></a>Sintaxe

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propriedades
|  Propriedade  |  Descrição   |
|---|---|
| Nome| Especifica o nome da origem do pacote para ser registado ou não registados no seu sistema.|
| Certifique-se| Determina se a origem do pacote está a ser registado ou não registados.|
| InstallationPolicy| Determina se confiar na origem do pacote. Um dos: "Não fidedignas", "Fidedigna".|
| ProviderName| Especifica o nome do fornecedor OneGet através do qual pode interoperabilidade com a origem do pacote.|
| SourceUri| Especifica o URI da origem do pacote.|
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
        SourceUri   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```