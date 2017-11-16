---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Trabalhar com impressoras
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: c8b4d728c9fddd39e1aeb56d6f9b8ffffe4c7292
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="working-with-printers"></a>Trabalhar com impressoras
Pode utilizar o Windows PowerShell para gerir impressoras utilizando o WMI e o objeto WScript.Network COM para WSH. Utilizaremos uma combinação de ambas as ferramentas para demonstrar a tarefas específicas.

### <a name="listing-printer-connections"></a>Ligações de impressora de listagem
A forma mais simples para listar as impressoras instaladas num computador consiste em utilizar o WMI **Win32_Printer** classe:

```
Get-WmiObject -Class Win32_Printer -ComputerName
```

Também pode listar as impressoras utilizando o **WScript.Network** objecto COM que é normalmente utilizado em scripts para WSH:

```
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Porque este comando devolve uma coleção de cadeia simples de nomes de porta e nomes de dispositivos de impressora sem qualquer distintivo etiquetas, não é fácil interpretar.

### <a name="adding-a-network-printer"></a>Adicionar uma impressora de rede
Para adicionar uma nova impressora de rede, utilize **WScript.Network**:

```
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a>Definir uma impressora predefinida
Para utilizar o WMI para definir a impressora predefinida, localizar a impressora no **Win32_Printer** coleção e, em seguida, invoque o **SetDefaultPrinter** método:

```
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript.Network** é ligeiramente mais simples utilizar, porque tem um **SetDefaultPrinter** método que utiliza apenas o nome da impressora como um argumento:

```
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a>Remover uma ligação de impressora
Para remover uma ligação de impressora, utilize o **WScript.Network RemovePrinterConnection** método:

```
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```

