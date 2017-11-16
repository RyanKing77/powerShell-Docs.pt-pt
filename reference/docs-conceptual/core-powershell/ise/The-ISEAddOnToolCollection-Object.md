---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: O objeto de ISEAddOnToolCollection
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ba8b4e0e3952226407f00dea8b32785633256089
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="the-iseaddontoolcollection-object"></a>O objeto de ISEAddOnToolCollection
  O **ISEAddOnToolCollection** objeto é uma coleção de **ISEAddOnTool** objetos. Um exemplo é o **$psISE.CurrentPowerShellTab.VerticalAddOnTools** objeto.

## <a name="methods"></a>Métodos

### <a name="add-name-controltype-isvisible-"></a>Adicionar\( nome, ControlType, \[IsVisible\]\)
  Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores. 

 Adiciona uma nova ferramenta de suplemento à coleção. Devolve a ferramenta de suplemento adicionados recentemente. Antes de executar este comando, tem de instalar a ferramenta de suplemento no computador local e carregar a assemblagem.

 **Nome** -cadeia Especifica o nome a apresentar da ferramenta de suplemento que é adicionado ao ISE do Windows PowerShell.

 **ControlType** -tipo Especifica o controlo é adicionado.

 **\[IsVisible\]**  -opcional booleano se definido como **$true**, a ferramenta de suplemento é imediatamente visível no painel de ferramenta associado.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a>Remover\( Item\)
  Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores. 

 Remove a ferramenta de suplemento especificado da coleção.

 **Item** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool Especifica o objeto a ser removido do ISE do Windows PowerShell.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a>SetSelectedPowerShellTab\( psTab\)
  Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores. 

 Seleciona o PowerShell separador que o **psTab** parâmetro especifica.

 **psTab** -separador de PowerShell o Microsoft.PowerShell.Host.ISE.PowerShellTab para selecionar.

```powershell
      $newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

### <a name="remove-pstab-"></a>Remover\( psTab\)
  Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores. 

 Remove o PowerShell separador que o **psTab** parâmetro especifica.

 **psTab** -separador de PowerShell Microsoft.PowerShell.Host.ISE.PowerShellTab do remover.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a>Consulte Também
- [O objeto de PowerShellTab](The-PowerShellTab-Object.md) 
- [O ISE do Windows PowerShell modelo de objeto de Scripting](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referência de modelo de objeto do Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [A hierarquia de modelo de objeto ISE](The-ISE-Object-Model-Hierarchy.md)

  
