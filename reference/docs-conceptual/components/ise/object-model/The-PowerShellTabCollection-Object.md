---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: d9088b26de35360b8258d3f15924b3010a986d15
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405397"
---
# <a name="the-powershelltabcollection-object"></a>Objeto PowerShellTabCollection

O **PowerShellTab** objeto da coleção é uma coleção de **PowerShellTab** objetos. Cada **PowerShellTab** objeto funciona como um ambiente de tempo de execução separado. É uma instância da classe Microsoft.PowerShell.Host.ISE.PowerShellTabs. Um exemplo é o **$psISE.PowerShellTabs** objeto.

## <a name="methods"></a>Métodos

### <a name="add"></a>Adicionar\(\)

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

Adiciona um novo separador do PowerShell para a coleção. Ele retorna a guia recém-adicionada.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Remover\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

Remove a guia especificada pelos **psTab** parâmetro.

**psTab** separador do PowerShell a remover.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

Seleciona o separador do PowerShell que é especificado pela **psTab** parâmetro para tornar o separador do PowerShell atualmente ativo.

**psTab** separador do PowerShell a selecionar.

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a>Consulte Também

- [Objeto PowerShellTab](The-PowerShellTab-Object.md)
- [Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)