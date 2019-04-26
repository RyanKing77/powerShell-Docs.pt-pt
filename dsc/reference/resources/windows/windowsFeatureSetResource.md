---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso WindowsFeatureSet de DSC
ms.openlocfilehash: 8b7c7e72dd58459bd19cb723e5790a82841515c0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076791"
---
# <a name="dsc-windowsfeatureset-resource"></a>Recurso WindowsFeatureSet de DSC

> Aplica-se a: Windows PowerShell 5.0

O **WindowsFeatureSet** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para se certificar de que funções e funcionalidades são adicionadas ou removidas num nó de destino.
Este recurso é um [recursos compostos](../../../resources/authoringResourceComposite.md) que chama o [recurso WindowsFeature](windowsfeatureResource.md) para cada funcionalidade especificada no `Name` propriedade.

Utilize este recurso quando pretender configurar um número de recursos do Windows para o mesmo Estado.

## <a name="syntax"></a>Sintaxe

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| Nome| Os nomes das funções ou funcionalidades que pretende garantir que são adicionados ou removidos. Este é o mesmo que o **Name** propriedade da [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet e não o nome a apresentar das funções ou funcionalidades.|
| Credencial| As credenciais a utilizar para adicionar ou remover as funções ou funcionalidades.|
| Certifique-se| Indica se as funções ou funcionalidades são adicionadas. Para se certificar de que as funções ou funcionalidades foram adicionados, defina esta propriedade para "Presente" para se certificar de que as funções ou funcionalidades são removidas, defina a propriedade como "Ausente".|
| IncludeAllSubFeature| Defina esta propriedade como **$true** para incluir todas as necessárias subfuncionalidades com os recursos que especificar com o **nome** propriedade.|
| LogPath| O caminho para um ficheiro de registo onde pretende que o fornecedor de recursos para iniciar a operação.|
| DependsOn| Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|
| Origem| Indica a localização do ficheiro de origem a utilizar para instalação, se necessário.|

## <a name="example"></a>Exemplo

A seguinte configuração garante que o **servidor Web** (IIS) e **servidor SMTP** funcionalidades e todas as subfuncionalidades de cada um, são instaladas.

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```
