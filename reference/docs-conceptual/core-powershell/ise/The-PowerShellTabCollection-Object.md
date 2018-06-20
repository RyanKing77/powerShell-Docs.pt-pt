---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: d9088b26de35360b8258d3f15924b3010a986d15
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953077"
---
# <a name="the-powershelltabcollection-object"></a>Objeto PowerShellTabCollection

O **PowerShellTab** objeto da coleção é uma coleção de **PowerShellTab** objetos. Cada **PowerShellTab** objeto funciona como um ambiente de tempo de execução separado. É uma instância da classe de Microsoft.PowerShell.Host.ISE.PowerShellTabs. Um exemplo é o **$psISE.PowerShellTabs** objeto.

## <a name="methods"></a>Métodos

### <a name="add"></a>Adicionar\(\)

Suportado no Windows PowerShell ISE 2.0 e posterior.

Adiciona um novo separador do PowerShell para a coleção. Devolve o separador adicionado recentemente.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Remover\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Suportado no Windows PowerShell ISE 2.0 e posterior.

Remove o separador que é especificado pelo **psTab** parâmetro.

**psTab** separador o PowerShell para remover.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Suportado no Windows PowerShell ISE 2.0 e posterior.

Seleciona o separador do PowerShell que é especificado pelo **psTab** parâmetro para torná-lo no separador de PowerShell atualmente ativo.

**psTab** PowerShell o separador para selecionar.

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

- [O objeto de PowerShellTab](The-PowerShellTab-Object.md)
- [Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)