---
ms.date: 06/12/2017
contributor: manikb
keywords: cmdlet do powershell do galeria, psget
title: Cmdlets de resolução de problemas
ms.openlocfilehash: e8890cb6bbe661b8524d83cabf91483acbde8095
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="troubleshooting-cmdlets"></a>Cmdlets de resolução de problemas

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