---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos do DSC WindowsOptionalFeature
ms.openlocfilehash: 388fbe1bc430098d6680902e0b5643243fbf7f4c
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2017
---
# <a name="dsc-windowsoptionalfeature-resource"></a>Recursos do DSC WindowsOptionalFeature

> Aplica-se a: O Windows PowerShell 5.0

O **WindowsOptionalFeature** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para se certificar de que as funcionalidades opcionais estão ativadas num nó de destino.

## <a name="syntax"></a>Sintaxe

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   | 
|---|---| 
| Nome| Indica o nome da funcionalidade que pretende para se certificar de que está ativado ou desativado.| 
| Certifique-se| Especifica se a funcionalidade está ativada. Para garantir que a funcionalidade está ativada, defina esta propriedade como "Ativar" para se certificar de que a funcionalidade está desativada, defina a propriedade para "Desativar".|
| Origem| Não implementado.|
| NoWindowsUpdateCheck| Especifica se o DISM contacta Windows Update (WU) quando procurar os ficheiros de origem ativar uma funcionalidade. Se $true, DISM não contactar WU.|
| RemoveFilesOnDisable| Definido como **$true** para remover todos os ficheiros associados a funcionalidade quando está desativado (ou seja, quando **Certifique-se** está definido para "Ausente").|
| Nível de Registo| O nível de saída máximo apresentado nos registos. Os valores aceites são: "ErrorsOnly" (apenas erros são registados), "ErrorsAndWarning" (erros e avisos são registados) e "ErrorsAndWarningAndInformation" (erros, avisos e informações de depuração são registados).|
| LogPath| O caminho para um ficheiro de registo onde pretende que o fornecedor de recursos para iniciar a operação.| 
| dependsOn| Especifica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.| 
 


