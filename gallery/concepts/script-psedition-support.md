---
ms.date: 06/12/2017
contributor: manikb
keywords: cmdlet do powershell do galeria, psget
title: Scripts com edições do PowerShell compatíveis
ms.openlocfilehash: e364879f611429a8583e550fb7704431e456fbb1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686636"
---
# <a name="script-with-compatible-powershell-editions"></a>Scripts com edições do PowerShell compatíveis

Começando na versão 5.1, o PowerShell está disponível nas diferentes edições que denotam conjuntos de funcionalidade e compatibilidade de plataforma variados.

- **Edição Desktop:** Criado no .NET Framework e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço total do Windows como núcleo de servidor e Desktop do Windows.

- **Edição Core:** Incorporada no .NET Core e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço reduzido do Windows, como o servidor Nano e o Windows IoT.

A edição em execução do PowerShell é apresentada na propriedade PSEdition da $PSVersionTable.

```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

Os autores de script podem impedir que um script em execução, a menos que ele é executado numa edição compatível do PowerShell com o parâmetro PSEdition num `#requires` instrução.

```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell editions 'Core'. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

Os utilizadores da galeria do PowerShell podem encontrar a lista de scripts suportado numa edição específica do PowerShell.
Scripts sem etiquetas PSEdition_Desktop e PSEdition_Core são considerados para funcionar bem, na edição de ambiente de trabalho do PowerShell.

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEdition_Desktop

# Find scripts supported on PowerShell Core edition
Find-Script -Tag PSEdition_Core
```

## <a name="more-details"></a>Obter mais detalhes

- [Módulos com Edições do PowerShell](module-psedition-support.md)
- [Suporte de edições do PowerShell no PowerShellGallery](../how-to/finding-packages/searching-by-compatibility.md)
