---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos do DSC WindowsOptionalFeatureSet
ms.openlocfilehash: 6912e5cf92f23058342bc566bd66dc4be3357a30
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>Recursos do DSC WindowsOptionalFeatureSet

> Aplica-se a: O Windows PowerShell 5.0

O **WindowsOptionalFeatureSet** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para se certificar de que as funcionalidades opcionais estão ativadas num nó de destino. Este recurso é um [recursos composto](authoringResourceComposite.md) que chama o [WindowsOptionalFeature recursos](windowsOptionalFeatureResource.md) para cada funcionalidade especificada no `Name` propriedade.

Utilize este recurso quando pretender configurar um número de funcionalidades opcionais do Windows para o estado do mesmo.

## <a name="syntax"></a>Sintaxe

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ] 
    [ RemoveFilesOnDisable = [bool] ]  
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   | 
|---|---| 
| Nome| Indica o nome das funcionalidades que pretende para se certificar de que estão ativadas ou desativadas.| 
| Certifique-se| Especifica se as funcionalidades estão ativadas. Para garantir que as funcionalidades estão ativadas, defina esta propriedade como "Ativar" para se certificar de que as funcionalidades estão desativadas, definir a propriedade para "Desativar".|
| Origem| Não implementado.|
| NoWindowsUpdateCheck| Especifica se o DISM contacta Windows Update (WU) quando a procurar ficheiros de origem para ativar funcionalidades. Se $true, DISM não contactar WU.|
| RemoveFilesOnDisable| Definido como **$true** para remover todos os ficheiros associados as funcionalidades quando estão desativadas (ou seja, quando **Certifique-se** está definido para "Ausente").|
| Nível de Registo| O nível de saída máximo apresentado nos registos. Os valores aceites são: "ErrorsOnly" (apenas erros são registados), "ErrorsAndWarning" (erros e avisos são registados) e "ErrorsAndWarningAndInformation" (erros, avisos e informações de depuração são registados).|
| LogPath| O caminho para um ficheiro de registo onde pretende que o fornecedor de recursos para iniciar a operação.| 
| dependsOn| Especifica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.| 
 



