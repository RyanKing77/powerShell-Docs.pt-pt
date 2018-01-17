---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos do DSC WindowsFeatureSet
ms.openlocfilehash: a2bb008852ccfdc04998a57d3e64e08bf05e6433
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowsfeatureset-resource"></a>Recursos do DSC WindowsFeatureSet

> Aplica-se a: O Windows PowerShell 5.0

O **WindowsFeatureSet** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para se certificar de que as funções e funcionalidades são adicionadas ou removidas num nó de destino.
Este recurso é um [recursos composto](authoringResourceComposite.md) que chama o [WindowsFeature recursos](windowsfeatureResource.md) para cada funcionalidade especificada no `Name` propriedade.

Utilize este recurso quando pretender configurar um número de funcionalidades do Windows para o estado do mesmo.

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
| Nome| Os nomes das funções ou funcionalidades que pretende para se certificar de que são adicionados ou removidos. Este é o mesmo que o **nome** propriedade o [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet e não o nome a apresentar das funções ou funcionalidades.| 
| credencial| As credenciais a utilizar para adicionar ou remover as funções ou funcionalidades.| 
| Certifique-se| Indica se as funções ou funcionalidades são adicionadas. Para garantir que as funções ou funcionalidades são adicionados, defina esta propriedade como "Apresente" para garantir que as funções ou funcionalidades, definir a propriedade para "Ausente".| 
| IncludeAllSubFeature| Defina esta propriedade como **$true** para incluir todos requeridas subfuncionalidades com as funcionalidades que especificar com o **nome** propriedade.| 
| LogPath| O caminho para um ficheiro de registo onde pretende que o fornecedor de recursos para iniciar a operação.| 
| dependsOn| Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.| 
| Origem| Indica a localização do ficheiro de origem a utilizar para instalação, se necessário.| 

## <a name="example"></a>Exemplo

A seguinte configuração assegura que o **servidor Web** (IIS) e **servidor SMTP** funcionalidades e todas as subfuncionalidades de cada um, são instaladas.

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

