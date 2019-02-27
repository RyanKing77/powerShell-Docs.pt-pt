---
title: Como criar um Snap-in do PowerShell do Windows | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 73834cea1d90943cf954728d6295d8eb33e14f57
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849442"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a>How to Create a Windows PowerShell Snap-in (Como Criar um Snap-in do Windows PowerShell)

Um snap-in do Windows PowerShell fornece um mecanismo para registrar os conjuntos de cmdlets e outro fornecedor de Windows PowerShell com o shell, assim, expandindo a funcionalidade de shell. Um snap-in do Windows PowerShell pode registar todos os cmdlets e provedores num único assembly, ou pode registar-se uma lista de cmdlets e provedores específicos.

Assemblies do snap-in devem ser instalados num diretório protegido, tal como seriam com outros sistemas operacionais. Caso contrário, os utilizadores mal intencionados podem substituir um assembly com código não seguro.

## <a name="windows-powershell-snap-in-classes"></a>Classes de Snap-in do PowerShell de Windows

Windows PowerShell todos os snap-in de classes derivar a [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) ou [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.

## <a name="examples"></a>Exemplos

[Escrever um Snap-in do PowerShell Windows](./writing-a-windows-powershell-snap-in.md): Este exemplo mostra como criar um snap-in que é utilizado para registar todos os cmdlets e provedores num assembly.

[Escrever um Snap-in do PowerShell do Windows personalizados](./writing-a-custom-windows-powershell-snap-in.md): Este exemplo mostra como criar um personalizada snap-in que é utilizado para registar um conjunto específico de cmdlets e provedores que poderão ou poderão não existir num único assembly.

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn)

[System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[Cmdlets de registo](./registering-cmdlets.md)

[Shell do Windows PowerShell SDK](../windows-powershell-reference.md)
