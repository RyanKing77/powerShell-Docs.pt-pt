---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 64a29aa87507e65a182837df538c5e695c420cb3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222059"
---
# <a name="uninstallation-instructions"></a>Instruções de desinstalação

## <a name="using-command-prompt"></a>Utilizando a linha de comandos
1.  Abra **linha de comandos.**
2.  Execute o [iniciador de autónomo do Windows Update](https://support.microsoft.com/en-us/kb/934307) conforme mostrado abaixo:

No Windows Server 2012 R2 e Windows 8.1:
```powershell
wusa /uninstall /kb:3134758
```
No Windows Server 2012:
```powershell
wusa /uninstall /kb:3134759
```
No Windows Server 2008 R2 SP1 e Windows 7 SP1:
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a>Utilizando o painel de controlo
1.  Abra **painel de controlo.**
2.  Abrir **programas**, em seguida, abra **desinstalar um programa.**
3.  Clique em **ver atualizações instaladas.**
4.  Selecione **Windows Management Framework 5.0** da lista de atualizações instaladas. Isto corresponde à *KB3134758*, *KB3134759*, ou *KB3134760*. Clique em **desinstalar.**
