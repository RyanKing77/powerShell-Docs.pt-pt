---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Como Criar um Separador do PowerShell no ISE do Windows PowerShell
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 4d4388d889f2178b2cd24cb0f3350aee37327625
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a>Como Criar um Separador do PowerShell no ISE do Windows PowerShell

Separadores no Windows PowerShell Integrated Scripting Environment (ISE) permitem-lhe criar e utilizar vários ambientes de execução na mesma aplicação de em simultâneo.
Cada separador PowerShell corresponde a um ambiente de execução separados ou a sessão.

> **TENHA EM ATENÇÃO**:
>
> As variáveis, funções e aliases que criar no um separador não passa para outro. Os valores são diferentes sessões do Windows PowerShell.

Utilize os seguintes passos para abrir ou fechar um separador no Windows PowerShell.
Para mudar o nome de um separador, defina o [DisplayName](The-PowerShellTab-Object.md#displayname) propriedade do objeto de scripting do Windows PowerShell separador.

## <a name="to-create-and-use-a-new-powershell-tab"></a>Criar e utilizar um novo separador do PowerShell

No **ficheiro** menu, clique em **novo separador do PowerShell**. O novo separador do PowerShell abre-se sempre como a janela ativa.
Separadores de PowerShell incrementalmente estão numeradas pela ordem que estão abertas.
Cada separador está associado a respetiva janela de consola do Windows PowerShell.
Pode ter até 32 PowerShell separadores com as suas próprias sessão aberta numa altura (trata limitada a 8 no Windows PowerShell ISE 2.0.)

Tenha em atenção que ao clicar no **novo** ou **abra** ícones na barra de ferramentas não criar um novo separador com uma sessão separada.
Em vez disso, os botões de abrir um ficheiro de script novo ou existente no separador atualmente ativo com uma sessão.
Pode ter vários script ficheiros são abertos com cada separador e a sessão.
Os separadores de script para uma sessão só serão apresentados abaixo os separadores de sessão quando a sessão associada está ativa.

Para tornar um separador de PowerShell ativa, clique no separador. Para selecionar todos os separadores de PowerShell que são abertos, no **vista** menu, clique no separador de PowerShell que pretende utilizar.

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a>Criar e utilizar um novo separador do PowerShell remoto

No **ficheiro** menu, clique em **novo separador do PowerShell remoto** para estabelecer uma sessão num computador remoto.
Uma caixa de diálogo é apresentada e pede-lhe que introduza os detalhes necessários para estabelecer a ligação remota.
As funções do separador remoto tal como um separador de PowerShell local, mas os comandos e scripts são executados no computador remoto.

## <a name="to-close-a-powershell-tab"></a>Para fechar um separador de PowerShell

Para fechar um separador, pode utilizar as seguintes técnicas:

- Clique no separador que pretende fechar.

- No **ficheiro** menu, clique em **separador de PowerShell fechar**, ou clique no botão Fechar (**X**) um separador de Active Directory para fechar o separador.

Se tem não foram guardadas ficheiros são abertos no separador de PowerShell que está a fechar, que lhe for pedido para guardar ou eliminá-las.
Para obter mais informações sobre como guardar um script, consulte [como guardar um Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).

## <a name="see-also"></a>Consulte Também

- [Introdução ao ISE do Windows PowerShell](Introducing-the-Windows-PowerShell-ISE.md)
- [Como utilizar o painel de consola no ISE do Windows PowerShell](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)