---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: psget_cmdlets_troubleshooting
ms.openlocfilehash: bc49dc78b8205d1194ddfe4bdca98b3e681860bd
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
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