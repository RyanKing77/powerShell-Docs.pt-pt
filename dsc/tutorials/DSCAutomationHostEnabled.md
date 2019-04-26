---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Chave de registo DSCAutomationHostEnabled
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076498"
---
>Aplica-se a: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>Chave de registo DSCAutomationHostEnabled

DSC utiliza a **DSCAutomationHostEnabled** chave de Registro em **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** para ativar a configuração da máquina em inicial arranque-up.
**DSCAutomationHostEnabled** suporta três modos:

|  Valor de DSCAutomationHostEnabled  |  Descrição   |
|---|---|
0 | Desative a configuração da máquina no arranque. |
1 | Ative a configuração da máquina no arranque. |
2 | Ativar a configurar a máquina apenas se DSC está no estado atual ou pendente. Este é o valor predefinido. |

## <a name="see-also"></a>Veja Também

Para obter um exemplo de como utilizar esta funcionalidade para executar configurações no arranque inicial, consulte [configurar uma máquina virtual no arranque inicial com o DSC](bootstrapDsc.md).
