---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: O objeto de PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: dcdc16ae126453b6ade64917ac4950cc05e5f8ad
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="the-powershelltabcollection-object"></a>O objeto de PowerShellTabCollection
  O **PowerShellTab** objeto da coleção é uma coleção de **PowerShellTab** objetos. Cada **PowerShellTab** objeto funciona como um ambiente de tempo de execução separado. É uma instância da classe de Microsoft.PowerShell.Host.ISE.PowerShellTabs. Um exemplo é o **$psISE.PowerShellTabs** objeto.

## <a name="methods"></a>Métodos

### <a name="add"></a>Adicionar\(\)
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 Adiciona um novo separador do PowerShell para a coleção. Devolve o separador adicionado recentemente.

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Remover\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 Remove o separador que é especificado pelo **psTab** parâmetro.

 **psTab** separador o PowerShell para remover.

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 Seleciona o separador do PowerShell que é especificado pelo **psTab** parâmetro para torná-lo no separador de PowerShell atualmente ativo.

 **psTab** PowerShell o separador para selecionar.

```
# Save the current tab in a variable and rename it
$OldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName="Old Tab"
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab" 
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab=$oldtab
```

## <a name="see-also"></a>Consulte Também
- [O objeto de PowerShellTab](The-PowerShellTab-Object.md) 
- [O ISE do Windows PowerShell modelo de objeto de Scripting](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referência de modelo de objeto do Windows PowerShell ISE](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [A hierarquia de modelo de objeto ISE](../ise/The-ISE-Object-Model-Hierarchy.md)

  
