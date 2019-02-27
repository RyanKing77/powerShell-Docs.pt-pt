---
title: PowerShell do Windows formatação ficheiros | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4c8f84-ebd2-4405-bb10-cfc5400d4ad6
caps.latest.revision: 6
ms.openlocfilehash: 35efd36fd70c209e3cbeb9eff0ddf978615fffd6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845599"
---
# <a name="windows-powershell-formatting-files"></a>Windows PowerShell Formatting Files (Ficheiros de Formatação do Windows PowerShell)

Windows PowerShell fornece vários arquivos de formatação (. format.ps1xml) que estão localizados no diretório de instalação (`$pshome`). Cada um desses arquivos define a apresentação predefinida para um conjunto específico de objetos .NET. Estes ficheiros nunca devem ser alterados. No entanto, pode utilizá-los como uma referência para a criação de seus próprios arquivos de formatação personalizados.

Certificate.Format.ps1xml define a exibição dos objetos no arquivo de certificados, tais como certificados x.509 e arquivos de certificados.

DotNetTypes.Format.ps1xml define a exibição dos diversos objetos .NET, como objetos CultureInfo, FileVersionInfo e EventLogEntry.

FileSystem.Format.ps1xml define a exibição de objetos de sistema de ficheiros como objetos de diretório e arquivo.

Define o Help.Format.ps1xml diferentes modos de exibição utilizados pela [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet, como as vistas detalhadas, de completo, parâmetros e exemplo.
Define as exibições diferentes utilizadas pelos [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet, tais como as vistas completas, parâmetros e exemplo detalhadas,.

PowerShellCore.Format.ps1xml define a apresentação dos objetos gerados por cmdlets de núcleo do Windows PowerShell, como aos objectos devolvidos pelos [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) e [Get-histórico](/powershell/module/Microsoft.PowerShell.Core/Get-History) cmdlets.
Define a apresentação dos objetos gerados por cmdlets de núcleo do Windows PowerShell, como aos objectos devolvidos pelos [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) e [Get-histórico](/powershell/module/Microsoft.PowerShell.Core/Get-History) cmdlets.

PowerShellTrace.Format.ps1xml define a exibição dos objetos de rastreio, como aquelas geradas pela [rastreio-Command](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) cmdlet.
Define a exibição dos objetos de rastreio, como aquelas geradas pela [rastreio-Command](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) cmdlet.

Registry.Format.ps1xml define a exibição de objetos de registo como objetos de chave e a entrada.

## <a name="see-also"></a>Consulte Também

[Escrever um Cmdlet do Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md)