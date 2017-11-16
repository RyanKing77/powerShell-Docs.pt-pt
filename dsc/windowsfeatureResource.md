---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos do DSC WindowsFeature
ms.openlocfilehash: a3433577a122f6c7e31360e094a089f6ceef77c2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowsfeature-resource"></a>Recursos do DSC WindowsFeature

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

O **WindowsFeature** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para se certificar de que as funções e funcionalidades são adicionadas ou removidas num nó de destino.

## <a name="syntax"></a>Sintaxe

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   | 
|---|---| 
| Nome| Indica o nome da função ou funcionalidade que pretende para se certificar de que é adicionado ou removido. Este é o mesmo que o __nome__ propriedade do [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet e não o nome a apresentar da função ou funcionalidade.| 
| credencial| Indica as credenciais a utilizar para adicionar ou remover a função ou funcionalidade.| 
| Certifique-se| Indica se a função ou funcionalidade é adicionada. Para garantir que a função ou funcionalidade adicionado, defina esta propriedade como "Apresente" para se certificar de que a função ou funcionalidade for removida, defina a propriedade para "Ausente".| 
| IncludeAllSubFeature| Defina esta propriedade como __$true__ para garantir o estado de todos requeridos subfuncionalidades com o estado da funcionalidade especificar com o __nome__ propriedade.| 
| LogPath| Indica o caminho para um ficheiro de registo onde pretende que o fornecedor de recursos para iniciar a operação.| 
| dependsOn| Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.| 
| Origem| Indica a localização do ficheiro de origem a utilizar para instalação, se necessário.| 

## <a name="example"></a>Exemplo
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present" 
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature  
}
```

