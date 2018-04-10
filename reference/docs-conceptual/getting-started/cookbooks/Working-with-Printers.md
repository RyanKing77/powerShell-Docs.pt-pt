---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Trabalhar com Impressoras
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: 5638629fdf79371c8eff9ee9194b642034250fff
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-printers"></a>Trabalhar com Impressoras

Pode utilizar o Windows PowerShell para gerir impressoras utilizando o WMI e o objeto WScript.Network COM para WSH. Utilizaremos uma combinação de ambas as ferramentas para demonstrar a tarefas específicas.

### <a name="listing-printer-connections"></a>Ligações de impressora de listagem

A forma mais simples para listar as impressoras instaladas num computador consiste em utilizar o WMI **Win32_Printer** classe:

```powershell
Get-WmiObject -Class Win32_Printer -ComputerName
```

Também pode listar as impressoras utilizando o **WScript.Network** objecto COM que é normalmente utilizado em scripts para WSH:

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Porque este comando devolve uma coleção de cadeia simples de nomes de porta e nomes de dispositivos de impressora sem qualquer distintivo etiquetas, não é fácil interpretar.

### <a name="adding-a-network-printer"></a>Adicionar uma impressora de rede

Para adicionar uma nova impressora de rede, utilize **WScript.Network**:

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a>Definir uma impressora predefinida

Para utilizar o WMI para definir a impressora predefinida, localizar a impressora no **Win32_Printer** coleção e, em seguida, invoque o **SetDefaultPrinter** método:

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript.Network** é ligeiramente mais simples utilizar, porque tem um **SetDefaultPrinter** método que utiliza apenas o nome da impressora como um argumento:

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a>Remover uma ligação de impressora

Para remover uma ligação de impressora, utilize o **WScript.Network RemovePrinterConnection** método:

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```