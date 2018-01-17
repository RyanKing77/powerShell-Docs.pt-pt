---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Chave de registo DSCAutomationHostEnabled
ms.openlocfilehash: c58b7a8f2485ff02f09763749a3de8a75f882d19
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
>Aplica-se a: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>Chave de registo DSCAutomationHostEnabled

DSC utiliza o **DSCAutomationHostEnabled** chave de registo em **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** para ativar a configuração da máquina em cima de arranque inicial.
DSCAutomationHostEnabled suporta três modos de:

|  Valor de DSCAutomationHostEnabled  |  Descrição   | 
|---|---| 
0 | Desative a configurar a máquina em cima de arranque. |
1 | Ative a configurar a máquina em cima de arranque. |
2 | Ativar a configurar a máquina apenas se DSC está no estado pendente ou atual. Este é o valor predefinido. |

## <a name="see-also"></a>Consulte Também

Para obter um exemplo de como utilizar esta funcionalidade para executar as configurações inicial de segurança de arranque, consulte [configurar uma máquinas virtuais em cima de arranque inicial através da utilização de DSC](bootstrapDsc.md).


