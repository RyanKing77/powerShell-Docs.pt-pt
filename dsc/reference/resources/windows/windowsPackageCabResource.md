---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso WindowsPackageCab de DSC
ms.openlocfilehash: 035944e7ca5c7469250c48a19b79f2f2d5d38e9a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687217"
---
# <a name="dsc-windowspackagecab-resource"></a>Recurso WindowsPackageCab de DSC

> Aplica-se a: Windows PowerShell 5.1 e versões posterior

O **WindowsPackageCab** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para instalar ou desinstalar pacotes de Gabinete (. cab) do Windows num nó de destino.

O nó de destino tem de ter o módulo DISM PowerShell instalado. Para obter informações, consulte [utilize DISM no Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).


## <a name="syntax"></a>Sintaxe

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| Nome| Indica o nome do pacote para quando pretende garantir um estado específico.|
| Certifique-se| Indica se o pacote está instalado. Defina esta propriedade como "Ausente", certifique-se de que o pacote não está instalado (ou desinstalar o pacote se estiver instalado). Defina-o para "Apresentar" (o valor predefinido) para garantir que o pacote está instalado.|
| Caminho| Indica o caminho onde reside o pacote.|
| LogPath| Indica o caminho completo onde pretende que o fornecedor para guardar um ficheiro de registo para instalar ou desinstalar o pacote.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será **ResourceName** e seu tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é "DependsOn ="[ ResourceName ResourceType]"'.|

## <a name="example"></a>Exemplo

A seguinte configuração de exemplo usa parâmetros de entrada e garante que o arquivo. cab especificado pelo `$Name` parâmetro está instalado.

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```