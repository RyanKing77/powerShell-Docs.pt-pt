---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso WindowsOptionalFeature de DSC
ms.openlocfilehash: 390caefd2ad190afc651b22ed1beb5cf1d604527
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048449"
---
# <a name="dsc-windowsoptionalfeature-resource"></a>Recurso WindowsOptionalFeature de DSC

> Aplica-se a: Windows PowerShell 5.0

O **WindowsOptionalFeature** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para garantir que as funcionalidades opcionais estão ativadas num nó de destino.

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
| Nome| Indica o nome do recurso que deseja garantir que está ativado ou desativado.|
| Certifique-se| Especifica se a funcionalidade está ativada. Para garantir que o recurso é ativado, defina esta propriedade para "Ativar" para se certificar de que a funcionalidade está desativada, defina a propriedade "Desativar".|
| Origem| Não implementado.|
| NoWindowsUpdateCheck| Especifica se o DISM contacta Windows Update (WU) ao pesquisar os ficheiros de origem ativar uma funcionalidade. Se $true, DISM não entre em contato com WU.|
| RemoveFilesOnDisable| Definido como **$true** para remover todos os ficheiros associados a funcionalidade quando está desativado (ou seja, quando **Certifique-se** está definido para "Ausente").|
| Nível de Registo| O nível de saída máximo apresentado nos registos. Os valores aceites são: "ErrorsOnly" (apenas erros são registados), "ErrorsAndWarning" (erros e avisos são registados) e "ErrorsAndWarningAndInformation" (erros, avisos e informações de depuração são registados).|
| LogPath| O caminho para um ficheiro de registo onde pretende que o fornecedor de recursos para iniciar a operação.|
| DependsOn| Especifica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|