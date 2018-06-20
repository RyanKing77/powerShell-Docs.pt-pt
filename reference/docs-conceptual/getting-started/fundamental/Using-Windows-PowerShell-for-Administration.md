---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Utilizar o Windows PowerShell para Administração
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
ms.openlocfilehash: 69790ddd6bae26dd18e30af860bad4c749cd86a5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954335"
---
# <a name="using-windows-powershell-for-administration"></a>Utilizar o Windows PowerShell para Administração
O objetivo fundamental do Windows PowerShell está a fornecer melhor, mais fácil controlo administrativo através de sistemas, interativo ou do script. Este capítulo explica soluções para problemas específicos muitos no administrar sistemas Windows com o Windows PowerShell. Apesar de ter não abordámos scripts ou funções no Guia do utilizador do Windows PowerShell, as soluções podem ser utilizadas de scripts ou como funções mais tarde. Vamos mostrar exemplos que incluem funções como parte da solução para resolver problemas.

Ao longo de descrições de solução, verá uma combinação de soluções com cmdlets específicos, o cmdlet de Get-WmiObject geral e ferramentas externas, mesmo que façam parte de infraestruturas do Windows e o .NET Framework. Utilização de ferramentas externas faz parte o objetivo de design de longa duração do Windows PowerShell. Mesmo à medida que cresce o sistema, os utilizadores receberão continuamente situações em que a disponíveis toolsets não tudo o que precisam. Em vez de dependência foster de implementações de cmdlet individualmente, do Windows PowerShell tenta suportar a integrar soluções de cada cenário alternativo possíveis.