---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Como Criar um Separador do PowerShell no ISE do Windows PowerShell
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 080fe89bf1443f51460589b445431913fa20b4b8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057745"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a>Como Criar um Separador do PowerShell no ISE do Windows PowerShell

Separadores no Windows PowerShell Integrated Scripting Environment (ISE) permitem-lhe criar e utilizar vários ambientes de execução dentro do mesmo aplicativo simultaneamente.
Cada separador do PowerShell corresponde a um ambiente de execução separado ou uma sessão.

> [!NOTE]
> Variáveis, funções e aliases que vai criar uma guia não vão ser transferidos para outro. Eles são diferentes sessões do Windows PowerShell.

Utilize os seguintes passos para abrir ou fechar uma guia no Windows PowerShell.
Para mudar o nome de uma guia, defina o [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) propriedade no objeto de scripting de separador do Windows PowerShell.

## <a name="to-create-and-use-a-new-powershell-tab"></a>Criar e utilizar um novo separador do PowerShell

Sobre o **arquivo** menu, clique em **novo separador do PowerShell**. O novo separador do PowerShell abre-se sempre como a janela ativa.
Guias do PowerShell são numerados incrementalmente na ordem que estão abertas.
Cada separador está associado a sua própria janela de consola do Windows PowerShell.
Pode ter até 32 guias do PowerShell com a sua própria sessão aberta por vez (isto é limitado a 8 no Windows PowerShell ISE 2.0.)

Tenha em atenção que ao clicar o **New** ou **aberto** ícones na barra de ferramentas não cria um novo separador com uma sessão separada.
Em vez disso, esses botões abrir um ficheiro de script novo ou existente no separador ativo no momento com uma sessão.
Pode ter vários script ficheiros abrir com cada separador e a sessão.
Os separadores de script para uma sessão de apenas serão apresentados abaixo os separadores de sessão quando a sessão associada está ativa.

Para tornar um separador do PowerShell ativa, clique no separador. Para selecionar a partir de todos os guias do PowerShell que estão abertas, no **vista** menu, clique no separador do PowerShell que pretende utilizar.

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a>Criar e utilizar um novo separador do PowerShell remoto

Sobre o **arquivo** menu, clique em **novo separador do PowerShell remoto** para estabelecer uma sessão num computador remoto.
Uma caixa de diálogo é apresentada e pede-lhe para introduzir os detalhes necessários para estabelecer a ligação remota.
As funções de separador remoto, tal como um separador do PowerShell local, mas os comandos e scripts são executados no computador remoto.

## <a name="to-close-a-powershell-tab"></a>Para fechar um separador do PowerShell

Para fechar uma guia, pode usar qualquer uma das seguintes técnicas:

- Clique no separador que pretende fechar.

- Sobre o **ficheiro** menu, clique em **fechar separador do PowerShell**, ou clique no botão Fechar (**X**) numa guia Active Directory para fechar o separador.

Se tem não foram guardadas ficheiros abrir no separador do PowerShell que está a fechar, que lhe for pedido para guardar ou rejeitá-los.
Para obter mais informações sobre como guardar um script, consulte [como guardar um Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).

## <a name="see-also"></a>Veja Também

- [Introdução ao ISE do Windows PowerShell](Introducing-the-Windows-PowerShell-ISE.md)
- [Como utilizar o painel de consola no ISE do Windows PowerShell](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)