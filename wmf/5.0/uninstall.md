---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 3392db954c22030bb64ae5093619d23952e1fcdb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
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

