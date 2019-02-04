---
ms.date: 08/09/2017
keywords: PowerShell, cmdlet, download, instalação, configuração, o windows 10, windows 8.1, windows 8.0, windows 7
title: Instalar o Windows PowerShell
ms.openlocfilehash: 1630ba445c88953b2729232ae7d80afa326f25e6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687329"
---
# <a name="installing-windows-powershell"></a>Instalar o Windows PowerShell

Windows PowerShell é instalado por predefinição em todos os Windows, começando com o Windows 7 SP1 e Windows Server 2008 R2 SP1.

Se estiver interessado no PowerShell 6 e posterior, tem de instalar o PowerShell Core em vez do Windows PowerShell. Para isso, consulte [instalar o PowerShell Core no Windows](Installing-PowerShell-Core-on-Windows.md).

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a>Localizar o PowerShell no Windows 10, 8.1, 8.0 e 7

Às vezes, localizando PowerShell consola ou ISE (ambiente de script integrado) no Windows pode ser difícil, à medida que sua localização passa de uma versão do Windows para a próxima.

As tabelas seguintes devem ajudá-lo a encontrar PowerShell na sua versão do Windows.
Todas as versões listadas aqui são a versão original, conforme lançado, não existem atualizações.

### <a name="for-console"></a>Para a consola

Versão | Localização
-- | --
Windows 10 | Ícone de Windows canto inferior esquerdo de clique, comece a escrever o PowerShell
Windows 8.1, 8.0 | Na tela iniciar, comece a escrever o PowerShell.<br/>Se, na área de trabalho, clique o ícone de Windows canto inferior esquerdo, comece a escrever o PowerShell
Windows 7 SP1 | Clique em esquerdo inferior Windows ícone de canto, sobre o início de caixa de pesquisa digitando o PowerShell

### <a name="for-ise"></a>Para ISE

Versão | Localização
-- | --
Windows 10 | Ícone de Windows canto inferior esquerdo de clique, começa a digitar ISE
Windows 8.1, 8.0 | Na tela iniciar, digite **ISE do PowerShell**.<br/>Se, na área de trabalho, clique em deixado o ícone de Windows de canto inferior, escreva **ISE do PowerShell**
Windows 7 SP1 | Clique em esquerdo inferior Windows ícone de canto, sobre o início de caixa de pesquisa digitando o PowerShell

## <a name="finding-powershell-in-windows-server-versions"></a>Localizar PowerShell nas versões do Windows Server

A partir do Windows Server 2008 R2, sistema de operativo do Windows podem ser instalado sem a interface de usuário gráfica (GUI).
Edições do Windows Server sem GUI são nomeadas **Core** edições e edições com a GUI são nomeados **ambiente de trabalho**.

### <a name="windows-server-core-editions"></a>Edições do Windows Server Core

Todas as edições Core, iniciar a sessão para o servidor obtém uma janela de linha de comandos do Windows.

Tipo `powershell` e prima **ENTER** para iniciar o PowerShell dentro da sessão de linha de comandos.
Tipo de `exit` para terminar a sessão do PowerShell e voltar ao prompt de comando.

### <a name="windows-server-desktop-editions"></a>Edições de área de trabalho do Windows Server

Em todas as edições de área de trabalho, clique no ícone de Windows do canto inferior esquerdo, comece a escrever o PowerShell.
Obtenha o console e opções do ISE.

A única exceção à regra acima é o ISE do Windows Server 2008 R2 SP1; Neste caso, clique no ícone de Windows do canto inferior esquerdo, escreva o ISE do PowerShell.

## <a name="how-to-check-the-version-of-powershell"></a>Como verificar a versão do PowerShell

Para encontrar a versão do PowerShell tiver instalado, inicie uma consola do PowerShell (ou ISE) e o tipo `$PSVersionTable` e prima **ENTER**. Procure o `PSVersion` valor.

## <a name="upgrading-existing-windows-powershell"></a>Atualizar existente do Windows PowerShell

O pacote de instalação para o PowerShell vem de dentro de um instalador do WMF.
A versão do programa de instalação WMF corresponde à versão do PowerShell; Não é sem instalador autônomo para o Windows PowerShell.

Se precisar de atualizar a versão existente do PowerShell, no Windows, utilize a tabela seguinte para localizar o instalador para a versão do PowerShell que pretende atualizar para.

Windows | PS 3.0 | PS 4.0 | PS 5.0 | PS 5.1 |
--|--|--|--|--|
Windows 10 (consulte Note1)<br/>Windows Server 2016 | - | - | - | instalado
Windows 8.1<br/>Windows Server 2012 R2 | - | instalado | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 8<br/>Windows Server 2012 | instalado | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 7 SP1<br/>Windows Server 2008 R2 SP1 | [WMF 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> [!NOTE]
>
> Na versão inicial do Windows 10, com as atualizações automáticas ativadas, o PowerShell é atualizado da versão 5.0 para 5.1.
>
> Se a versão original do Windows 10 não forem atualizada por meio de atualizações do Windows, a versão do PowerShell é 5.0.

## <a name="need-azure-powershell"></a>Precisa do PowerShell do Azure

Se estiver procurando **do Azure PowerShell**, pode começar com [descrição geral do Azure PowerShell](/powershell/azure/overview).

Caso contrário, o que poderá ser necessário é [instalar e configurar o Azure PowerShell](/powershell/azure/install-azurerm-ps)

## <a name="see-also"></a>Consulte Também

[Requisitos de sistema do PowerShell do Windows](Windows-PowerShell-System-Requirements.md)

[Iniciar o Windows PowerShell](../getting-started/Starting-Windows-PowerShell.md)