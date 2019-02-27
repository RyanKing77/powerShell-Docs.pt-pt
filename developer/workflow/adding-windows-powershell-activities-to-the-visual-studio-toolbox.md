---
title: Adição de atividades do Windows PowerShell para a caixa de ferramentas do Visual Studio | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56852109"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a>Adding Windows PowerShell Activities to the Visual Studio Toolbox (Adicionar Atividades do Windows PowerShell à Caixa de Ferramentas do Visual Studio)

Antes de criar um fluxo de trabalho do PowerShell usando o Designer de fluxo de trabalho, primeiro tem de adicionar as atividades do PowerShell para a caixa de ferramentas num projeto de aplicativo de console do fluxo de trabalho do Studio visuais. O procedimento seguinte mostra como adicionar as atividades do Microsoft.PowerShell.Core.Activities assembly para a caixa de ferramentas do Visual Studio.

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a>Adição de atividades do Windows PowerShell para a caixa de ferramentas

1. Crie um novo projeto de aplicação de consola do fluxo de trabalho no Visual Studio.

2. Sobre o **View** menu, clique em **caixa de ferramentas**.

3. Adicionar uma nova guia na caixa de ferramentas, clicar com o botão direito dentro da caixa de ferramentas e clique em **separador adicionar**e dê um nome, tais como "Atividades de PowerShell" ao novo separador.

   Adicionar um separador permite-lhe agrupar as atividades do PowerShell separadas de outras ferramentas na caixa de ferramentas.

4. No separador da nova caixa de ferramentas, clique em **escolher itens...** . O **escolher itens da caixa de ferramentas** é apresentada a caixa de diálogo.

5. Na **escolher itens da caixa de ferramentas** caixa de diálogo, clique nas **System.Activities** separador.

6. Clique em **procurar**.

7. Navegue para a pasta de %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e e faça duplo clique Microsoft.PowerShell.Core.Activities.dll.

8. Clique em **OK**. As atividades definidas pelo Microsoft.PowerShell.Core.Activities assembly estão agora disponíveis na caixa de ferramentas.

## <a name="see-also"></a>Consulte Também

[Escrever um fluxo de trabalho do Windows PowerShell](./writing-a-windows-powershell-workflow.md)

[Criar um fluxo de trabalho com atividades do Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md)