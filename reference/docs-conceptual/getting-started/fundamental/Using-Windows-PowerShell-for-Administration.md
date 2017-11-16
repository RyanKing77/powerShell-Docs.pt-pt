---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "Com o Windows PowerShell para administração"
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
ms.openlocfilehash: fa87745b9be04d14de37a308d870b73c5a98cf83
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="using-windows-powershell-for-administration"></a>Com o Windows PowerShell para administração
O objetivo fundamental do Windows PowerShell está a fornecer melhor, mais fácil controlo administrativo através de sistemas, interativo ou do script. Este capítulo explica soluções para problemas específicos muitos no administrar sistemas Windows com o Windows PowerShell. Apesar de ter não abordámos scripts ou funções no Guia do utilizador do Windows PowerShell, as soluções podem ser utilizadas de scripts ou como funções mais tarde. Vamos mostrar exemplos que incluem funções como parte da solução para resolver problemas.

Ao longo de descrições de solução, verá uma combinação de soluções com cmdlets específicos, o cmdlet de Get-WmiObject geral e ferramentas externas, mesmo que façam parte de infraestruturas do Windows e o .NET Framework. Utilização de ferramentas externas faz parte o objetivo de design de longa duração do Windows PowerShell. Mesmo à medida que cresce o sistema, os utilizadores receberão continuamente situações em que a disponíveis toolsets não tudo o que precisam. Em vez de dependência foster de implementações de cmdlet individualmente, do Windows PowerShell tenta suportar a integrar soluções de cada cenário alternativo possíveis.

