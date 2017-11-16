---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Chave de registo DSCAutomationHostEnabled
ms.openlocfilehash: e47c929b366f93738343eabc431aab5a4428352d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
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


