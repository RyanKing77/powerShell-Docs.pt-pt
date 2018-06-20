---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos do DSC WindowsPackageCab
ms.openlocfilehash: 8c4de193c8ea787dd125436f86aa0b5eafdb1509
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190354"
---
# <a name="dsc-windowspackagecab-resource"></a>Recursos do DSC WindowsPackageCab

> Aplica-se a: Windows PowerShell 5.1 e posterior

O **WindowsPackageCab** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para instalar ou desinstalar pacotes CAB (. cab) do Windows num nó de destino.

O nó de destino tem de ter o módulo do DISM PowerShell instalado. Para informações, consulte [DISM de utilização no Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).


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
| Certifique-se| Indica se o pacote está instalado. Defina esta propriedade para "Ausente", certifique-se de que o pacote não está instalado (ou desinstalar o pacote, caso esteja instalada). Defina-o para "Apresentar" (o valor predefinido) para garantir que o pacote está instalado.|
| Caminho| Indica o caminho onde reside o pacote.|
| LogPath| Indica o caminho completo onde pretende que o fornecedor para guardar um ficheiro de registo para instalar ou desinstalar o pacote.|
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é ' DependsOn = "[ ResourceName ResourceType]"'.|

## <a name="example"></a>Exemplo

A seguinte configuração de exemplo utiliza os parâmetros de entrada e assegura que o ficheiro. cab especificado pelo `$Name` parâmetro está instalado.

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