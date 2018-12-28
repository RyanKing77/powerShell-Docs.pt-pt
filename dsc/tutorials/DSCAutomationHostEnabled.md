---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Chave de registo DSCAutomationHostEnabled
ms.openlocfilehash: 38e3189323c39a522b2ccad89f5cfcadf5e45616
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404710"
---
>Aplica-se a: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>Chave de registo DSCAutomationHostEnabled

DSC utiliza a **DSCAutomationHostEnabled** chave de Registro em **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** para ativar a configuração da máquina no arranque inicial.
DSCAutomationHostEnabled suporta três modos:

|  Valor de DSCAutomationHostEnabled  |  Descrição   |
|---|---|
0 | Desative a configuração da máquina no arranque. |
1 | Ative a configuração da máquina no arranque. |
2 | Ativar a configurar a máquina apenas se DSC está no estado atual ou pendente. Este é o valor predefinido. |

## <a name="see-also"></a>Consulte Também

Para obter um exemplo de como utilizar esta funcionalidade para executar configurações no arranque inicial, consulte [configurar uma máquina virtual no arranque inicial com o DSC](bootstrapDsc.md).