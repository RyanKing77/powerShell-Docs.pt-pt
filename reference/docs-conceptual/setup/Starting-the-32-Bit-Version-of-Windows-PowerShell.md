---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "A iniciar a versão de 32 bits do Windows PowerShell"
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: d682ce45ebc92cda3a9008ab608bacf9ef8eba57
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a>A iniciar a versão de 32 bits do Windows PowerShell
Quando instalar o Windows PowerShell no computador de 64 bits, **Windows PowerShell (x86)**, está instalada uma versão de 32 bits do Windows PowerShell para além da versão de 64 bits. Quando executar o Windows PowerShell, executa a versão de 64 bits por predefinição.

No entanto, ocasionalmente, poderá ter de executar **Windows PowerShell (x86)**, tal como quando estiver a utilizar um módulo que requer a versão de 32 bits ou quando estiverem a ligar remotamente a um computador de 32 bits.

Para iniciar uma versão de 32 bits do Windows PowerShell, utilize qualquer um dos seguintes procedimentos.

#### <a name="in-windows-server-2012-r2"></a>No Windows Server® 2012 R2

- No **iniciar** ecrã, escreva **Windows PowerShell (x86)**. Clique em de **Windows PowerShell x86** mosaico.

- No **Gestor de servidor**, do **ferramentas** menu, selecione **Windows PowerShell (x86)**.

- No ambiente de trabalho, mova o cursor para o canto superior direito, clique em **pesquisa**, tipo **PowerShell x86** e, em seguida, clique em **Windows PowerShell (x86)**.

- Linha de comandos, introduza:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>No Windows Server® 2012

- No **iniciar** ecrã, escreva **PowerShell** e, em seguida, clique em **Windows PowerShell (x86)**.

- No **Gestor de servidor**, do **ferramentas** menu, selecione **Windows PowerShell (x86)**.

- No ambiente de trabalho, mova o cursor para o canto superior direito, clique em **pesquisa**, tipo **PowerShell** e, em seguida, clique em **Windows PowerShell (x86)**.

- Linha de comandos, introduza:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>No Windows® 8.1

- No **iniciar** ecrã, escreva **Windows PowerShell (x86)**. Clique em de **Windows PowerShell x86** mosaico.

- Se estiver a executar [ferramentas de administração remota do servidor](http://go.microsoft.com/fwlink/?LinkID=304145) para Windows 8.1, pode também abrir o Windows PowerShell x86 a partir de **ManagerTools servidor** menu. Selecione **Windows PowerShell (x86)**.

- No ambiente de trabalho, mova o cursor para o canto superior direito, clique em **pesquisa**, tipo **PowerShell x86** e, em seguida, clique em **Windows PowerShell (x86)**.
   
- Linha de comandos, introduza:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>No Windows® 8

- No **iniciar** ecrã, mova o cursor para o canto superior direito, clique em **definições**, clique em **mosaicos**e, em seguida, mova o **Mostrar Ferramentas administrativas** controlo de deslize para Sim. Em seguida, escreva **PowerShell** e clique em **Windows PowerShell (x86)**.

- Se estiver a executar [ferramentas de administração remota do servidor](http://www.microsoft.com/download/details.aspx?id=28972) para o Windows 8, pode também abrir o Windows PowerShell x86 do **servidor ManagerTools** menu. Selecione **Windows PowerShell (x86)**.

- No **iniciar** ecrã ou ambiente de trabalho, escreva **PowerShell (x86)** e, em seguida, clique em **Windows PowerShell (x86)**.

- Linha de comandos, introduza:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

