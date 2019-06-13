---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto PowerShellTabCollection
ms.openlocfilehash: 5a1318534ddce19c2f5faa0d2013e2b38d8b79e5
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030480"
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

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

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

## <a name="see-also"></a>Veja Também

- [Objeto PowerShellTab](The-PowerShellTab-Object.md)
- [Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)
