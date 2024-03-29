---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Desinstalar o WMF 5.0
ms.openlocfilehash: f562a4a4506bfdede6b23bd186b80f40cc9e45ca
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856190"
---
# <a name="uninstallation-instructions"></a>Instruções de desinstalação

## <a name="using-command-prompt"></a>Usando a linha de comandos

1. Abra **Prompt de comando.**
2. Executar o [Windows Update autónomo iniciador](https://support.microsoft.com/en-us/kb/934307) conforme mostrado abaixo:

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

## <a name="using-control-panel"></a>Usando o painel de controlo

1. Abra **painel de controlo.**
2. Abra **programas**, em seguida, abra **desinstalar um programa.**
3. Clique em **ver atualizações instaladas.**
4. Selecione **Windows Management Framework 5.0** na lista de atualizações instaladas. Isso corresponde à *KB3134758*, *KB3134759*, ou *KB3134760*. Clique em **desinstalar.**
