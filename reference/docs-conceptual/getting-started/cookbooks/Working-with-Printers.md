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
# <a name="working-with-printers"></a><span data-ttu-id="a2783-103">Trabalhar com impressoras</span><span class="sxs-lookup"><span data-stu-id="a2783-103">Working with Printers</span></span>
<span data-ttu-id="a2783-104">Pode utilizar o Windows PowerShell para gerir impressoras utilizando o WMI e o objeto WScript.Network COM para WSH.</span><span class="sxs-lookup"><span data-stu-id="a2783-104">You can use Windows PowerShell to manage printers by using WMI and the WScript.Network COM object from WSH.</span></span> <span data-ttu-id="a2783-105">Utilizaremos uma combinação de ambas as ferramentas para demonstrar a tarefas específicas.</span><span class="sxs-lookup"><span data-stu-id="a2783-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

### <a name="listing-printer-connections"></a><span data-ttu-id="a2783-106">Ligações de impressora de listagem</span><span class="sxs-lookup"><span data-stu-id="a2783-106">Listing Printer Connections</span></span>
<span data-ttu-id="a2783-107">A forma mais simples para listar as impressoras instaladas num computador consiste em utilizar o WMI **Win32_Printer** classe:</span><span class="sxs-lookup"><span data-stu-id="a2783-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```
Get-WmiObject -Class Win32_Printer -ComputerName
```

<span data-ttu-id="a2783-108">Também pode listar as impressoras utilizando o **WScript.Network** objecto COM que é normalmente utilizado em scripts para WSH:</span><span class="sxs-lookup"><span data-stu-id="a2783-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="a2783-109">Porque este comando devolve uma coleção de cadeia simples de nomes de porta e nomes de dispositivos de impressora sem qualquer distintivo etiquetas, não é fácil interpretar.</span><span class="sxs-lookup"><span data-stu-id="a2783-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

### <a name="adding-a-network-printer"></a><span data-ttu-id="a2783-110">Adicionar uma impressora de rede</span><span class="sxs-lookup"><span data-stu-id="a2783-110">Adding a Network Printer</span></span>
<span data-ttu-id="a2783-111">Para adicionar uma nova impressora de rede, utilize **WScript.Network**:</span><span class="sxs-lookup"><span data-stu-id="a2783-111">To add a new network printer, use **WScript.Network**:</span></span>

```
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a><span data-ttu-id="a2783-112">Definir uma impressora predefinida</span><span class="sxs-lookup"><span data-stu-id="a2783-112">Setting a Default Printer</span></span>
<span data-ttu-id="a2783-113">Para utilizar o WMI para definir a impressora predefinida, localizar a impressora no **Win32_Printer** coleção e, em seguida, invoque o **SetDefaultPrinter** método:</span><span class="sxs-lookup"><span data-stu-id="a2783-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="a2783-114">**WScript.Network** é ligeiramente mais simples utilizar, porque tem um **SetDefaultPrinter** método que utiliza apenas o nome da impressora como um argumento:</span><span class="sxs-lookup"><span data-stu-id="a2783-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a><span data-ttu-id="a2783-115">Remover uma ligação de impressora</span><span class="sxs-lookup"><span data-stu-id="a2783-115">Removing a Printer Connection</span></span>
<span data-ttu-id="a2783-116">Para remover uma ligação de impressora, utilize o **WScript.Network RemovePrinterConnection** método:</span><span class="sxs-lookup"><span data-stu-id="a2783-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```

