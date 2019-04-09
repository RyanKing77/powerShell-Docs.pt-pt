---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Trabalhar com Impressoras
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: 77ebb26369b6a40e9c8c7bbbc52347d614cbf083
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292998"
---
# <a name="working-with-printers"></a><span data-ttu-id="cc193-103">Trabalhar com Impressoras</span><span class="sxs-lookup"><span data-stu-id="cc193-103">Working with Printers</span></span>

<span data-ttu-id="cc193-104">Pode utilizar o Windows PowerShell para gerir impressoras utilizando o WMI e o objeto WScript COM do WSH.</span><span class="sxs-lookup"><span data-stu-id="cc193-104">You can use Windows PowerShell to manage printers by using WMI and the WScript.Network COM object from WSH.</span></span> <span data-ttu-id="cc193-105">Utilizamos uma combinação de ambas as ferramentas para demonstrar as tarefas específicas.</span><span class="sxs-lookup"><span data-stu-id="cc193-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

## <a name="listing-printer-connections"></a><span data-ttu-id="cc193-106">Listagem conexões de impressora</span><span class="sxs-lookup"><span data-stu-id="cc193-106">Listing Printer Connections</span></span>

<span data-ttu-id="cc193-107">A forma mais simples para listar as impressoras instaladas num computador é usar o WMI **Win32_Printer** classe:</span><span class="sxs-lookup"><span data-stu-id="cc193-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```powershell
Get-WmiObject -Class Win32_Printer -ComputerName
```

<span data-ttu-id="cc193-108">Também pode listar as impressoras utilizando o **WScript** objeto COM que é normalmente utilizado em scripts do WSH:</span><span class="sxs-lookup"><span data-stu-id="cc193-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="cc193-109">Uma vez que este comando devolve uma coleção de cadeia de caracteres simples de nomes de porta e os nomes de dispositivo de impressora sem qualquer distinção rótulos, não é fácil de interpretar.</span><span class="sxs-lookup"><span data-stu-id="cc193-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

## <a name="adding-a-network-printer"></a><span data-ttu-id="cc193-110">Adicionar uma impressora de rede</span><span class="sxs-lookup"><span data-stu-id="cc193-110">Adding a Network Printer</span></span>

<span data-ttu-id="cc193-111">Para adicionar uma nova impressora de rede, utilize **WScript**:</span><span class="sxs-lookup"><span data-stu-id="cc193-111">To add a new network printer, use **WScript.Network**:</span></span>

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a><span data-ttu-id="cc193-112">Definir uma impressora padrão</span><span class="sxs-lookup"><span data-stu-id="cc193-112">Setting a Default Printer</span></span>

<span data-ttu-id="cc193-113">Para usar o WMI para definir a impressora predefinida, localize a impressora no **Win32_Printer** coleção e, em seguida, invoque o **SetDefaultPrinter** método:</span><span class="sxs-lookup"><span data-stu-id="cc193-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="cc193-114">**WScript** é um pouco mais fácil de utilizar, porque tem uma **SetDefaultPrinter** método que usa apenas o nome da impressora como um argumento:</span><span class="sxs-lookup"><span data-stu-id="cc193-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a><span data-ttu-id="cc193-115">Remover uma conexão de impressora</span><span class="sxs-lookup"><span data-stu-id="cc193-115">Removing a Printer Connection</span></span>

<span data-ttu-id="cc193-116">Para remover uma conexão de impressora, utilize o **WScript RemovePrinterConnection** método:</span><span class="sxs-lookup"><span data-stu-id="cc193-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```