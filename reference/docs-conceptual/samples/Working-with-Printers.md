---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Trabalhar com Impressoras
ms.openlocfilehash: 816388325cc3155f1dbd1bc15fc1736155216092
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030671"
---
# <a name="working-with-printers"></a>Trabalhar com Impressoras

Pode utilizar o Windows PowerShell para gerir impressoras utilizando o WMI e o objeto WScript COM do WSH. Utilizamos uma combinação de ambas as ferramentas para demonstrar as tarefas específicas.

## <a name="listing-printer-connections"></a>Listagem conexões de impressora

A forma mais simples para listar as impressoras instaladas num computador é usar o WMI **Win32_Printer** classe:

```powershell
Get-WmiObject -Class Win32_Printer
```

Também pode listar as impressoras utilizando o **WScript** objeto COM que é normalmente utilizado em scripts do WSH:

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Uma vez que este comando devolve uma coleção de cadeia de caracteres simples de nomes de porta e os nomes de dispositivo de impressora sem qualquer distinção rótulos, não é fácil de interpretar.

## <a name="adding-a-network-printer"></a>Adicionar uma impressora de rede

Para adicionar uma nova impressora de rede, utilize **WScript**:

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a>Definir uma impressora padrão

Para usar o WMI para definir a impressora predefinida, localize a impressora no **Win32_Printer** coleção e, em seguida, invoque o **SetDefaultPrinter** método:

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript** é um pouco mais fácil de utilizar, porque tem uma **SetDefaultPrinter** método que usa apenas o nome da impressora como um argumento:

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a>Remover uma conexão de impressora

Para remover uma conexão de impressora, utilize o **WScript RemovePrinterConnection** método:

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```
