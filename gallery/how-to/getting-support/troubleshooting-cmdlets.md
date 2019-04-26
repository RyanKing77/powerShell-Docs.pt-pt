---
ms.date: 06/12/2017
contributor: manikb
keywords: cmdlet do powershell do galeria, psget
title: Cmdlets de resolução de problemas
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084186"
---
# <a name="troubleshooting-cmdlets"></a>Cmdlets de resolução de problemas

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Como resolver "Aviso: Não foi possível transferir o pacote 'nome do seu pacote' "problema

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
