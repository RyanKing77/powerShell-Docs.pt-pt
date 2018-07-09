---
ms.date: 06/12/2017
contributor: manikb
keywords: cmdlet do powershell do galeria, psget
title: Cmdlets de resolução de problemas
ms.openlocfilehash: c0a1fbcafd8c4443dc9d628c54c4c525d9701861
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892479"
---
# <a name="troubleshooting-cmdlets"></a>Cmdlets de resolução de problemas

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Como resolver "Aviso: não foi possível transferir o pacote 'nome do seu pacote'" problema

É reportado que `Install-Module` ou `Update-Module` falhar, às vezes, em algumas máquinas.
Com base na nossa investigação, é algo a ver com a ligação de rede.
Recentemente atualizámos fornecedor NuGet, de modo a que pode transferir pacotes de forma fiável.
Pode seguir as instruções abaixo para instalar a compilação mais recente do fornecedor NuGet e, em seguida, instalar ou atualizar o seu módulo.
Vamos utilizar o módulo "Azure" como exemplo abaixo.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```