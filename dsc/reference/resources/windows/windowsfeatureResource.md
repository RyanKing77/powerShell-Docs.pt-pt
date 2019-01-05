---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso WindowsFeature de DSC
ms.openlocfilehash: 7a57f4b2797ab3bb202aea8b2543d1e3f14074e9
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048467"
---
# <a name="dsc-windowsfeature-resource"></a>Recurso WindowsFeature de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O **WindowsFeature** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para se certificar de que funções e funcionalidades são adicionadas ou removidas num nó de destino.

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
| Nome| Indica o nome da função ou funcionalidade que deseja garantir que é adicionado ou removido. Este é o mesmo que o __nome__ propriedade a partir do [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet e não o nome a apresentar da função ou funcionalidade.|
| Credencial| Indica as credenciais a utilizar para adicionar ou remover a função ou funcionalidade.|
| Certifique-se| Indica se a função ou funcionalidade é adicionada. Para garantir que a função ou funcionalidade é adicionado, defina esta propriedade para "Presente" para se certificar de que a função ou funcionalidade for removida, defina a propriedade como "Ausente".|
| IncludeAllSubFeature| Defina esta propriedade como __$true__ para garantir o estado de todas as necessárias subfuncionalidades com o estado do recurso que especificar com o __nome__ propriedade.|
| LogPath| Indique o caminho para um ficheiro de registo onde pretende que o fornecedor de recursos para iniciar a operação.|
| DependsOn| Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|
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