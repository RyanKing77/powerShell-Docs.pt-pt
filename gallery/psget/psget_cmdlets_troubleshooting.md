---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: psget_cmdlets_troubleshooting
ms.openlocfilehash: ccb39f44e8d11f1e2a912da0c4f18b700e836c91
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Como resolver "Aviso: Falha ao transferir o pacote 'nome do seu pacote'" problema?




Foi reportado que instalar módulo módulo de atualização, por vezes, falha ou em algumas máquinas.
Com base na nossa investigação, é algo com a ligação de rede.
Foi actualizado recentemente fornecedor NuGet para que pode transferir pacotes de forma fiável.
Pode seguir as instruções abaixo para instalar a compilação mais recente do fornecedor do NuGet e, em seguida, instalar ou atualizar o seu módulo.
Vamos utilizar o módulo de 'Azure' como um exemplo abaixo.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

