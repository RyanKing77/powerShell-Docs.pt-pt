---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISEAddOnToolCollection
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ff4f19d1a85a592f2f4f09c62caa0971751bdff7
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405385"
---
# <a name="the-iseaddontoolcollection-object"></a>Objeto ISEAddOnToolCollection

O **ISEAddOnToolCollection** objeto é uma coleção de **ISEAddOnTool** objetos. Um exemplo é o **$psISE.CurrentPowerShellTab.VerticalAddOnTools** objeto.

## <a name="methods"></a>Métodos

### <a name="add-name-controltype-isvisible-"></a>Adicione\( nome, ControlType, \[IsVisible\] \)

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.

Adiciona uma nova ferramenta do suplemento à coleção. Devolve a ferramenta do suplemento recém-adicionada. Antes de executar este comando, tem de instalar a ferramenta do suplemento no computador local e carregar a assemblagem.

**Nome** -cadeia de caracteres Especifica o nome a apresentar da ferramenta de suplemento que é adicionado ao ISE do Windows PowerShell.

**ControlType** -tipo Especifica o controle que é adicionado.

**\[IsVisible\]**  -opcional booleano se definido como **$true**, a ferramenta do suplemento está imediatamente visível no painel de ferramenta associados.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a>Remover\( Item \)

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.

Remove a ferramenta do suplemento especificado da coleção.

**Item** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool Especifica o objeto seja removido do ISE do Windows PowerShell.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a>SetSelectedPowerShellTab\( psTab \)

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.

Seleciona o PowerShell separador que o **psTab** parâmetro especifica.

**psTab** -separador de PowerShell Microsoft.PowerShell.Host.ISE.PowerShellTab do selecionar.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a>Remover\( psTab \)

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.

Remove o PowerShell separador que o **psTab** parâmetro especifica.

**psTab** -separador de PowerShell Microsoft.PowerShell.Host.ISE.PowerShellTab do remover.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a>Consulte Também

- [Objeto PowerShellTab](The-PowerShellTab-Object.md)
- [Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)