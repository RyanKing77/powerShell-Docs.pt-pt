---
ms.date: 08/09/2017
keywords: PowerShell, cmdlet, transferir, instalar, a configuração, o windows 10, windows 8.1, windows 8.0, windows 7
title: Instalar o Windows PowerShell
ms.openlocfilehash: 89f0f689ebfcd34dd4c8ec3824ec8ab4bddc34d9
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/25/2018
---
# <a name="installing-windows-powershell"></a>Instalar o Windows PowerShell
Windows PowerShell é instalado por predefinição em todos os Windows, começando com o Windows 7 SP1 e Windows Server 2008 R2 SP1.

Se estiver interessado no PowerShell 6 e posterior, terá de instalar o PowerShell Core em vez do Windows PowerShell. Para tal, consulte [instalação principal do PowerShell no Windows](Installing-PowerShell-Core-on-Windows.md).

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a>Localizar o PowerShell no Windows 10, 8.1, 8.0 e 7

Por vezes, localizar PowerShell consola ou ISE (ambiente de Scripting integrado) no Windows pode ser difícil, como localização de move de uma versão do Windows para o seguinte.

As tabelas seguintes deverão ajudar a encontrar PowerShell na sua versão do Windows.
Todas as versões listadas aqui tem a versão original, à lançadas com não existem atualizações.

### <a name="for-console"></a>Para a consola

Versão | Localização
-- | --
10 do Windows | Clique em ícone do Windows canto inferior esquerdo, comece a escrever o PowerShell
Windows 8.1, 8.0 | No ecrã Iniciar, comece a escrever o PowerShell.<br/>Se, no ambiente de trabalho, clique em ícone do Windows canto inferior esquerdo, comece a escrever o PowerShell
Windows 7 SP1 | Clique em esquerdo inferior canto ícone do Windows, no início de caixa de pesquisa escrevendo o PowerShell

### <a name="for-ise"></a>Para ISE

Versão | Localização
-- | --
10 do Windows | Clique em ícone do Windows canto inferior esquerdo, comece a escrever ISE
Windows 8.1, 8.0 | No ecrã Iniciar, escreva **ISE do PowerShell**.<br/>Se no ambiente de trabalho, clique em deixado ícone do Windows canto inferior, escreva **ISE do PowerShell**
Windows 7 SP1 | Clique em esquerdo inferior canto ícone do Windows, no início de caixa de pesquisa escrevendo o PowerShell

## <a name="finding-powershell-in-windows-server-versions"></a>Localizar PowerShell em versões do Windows Server

A partir do Windows Server 2008 R2, sistema operativo Windows pode ser instalado sem a interface de utilizador gráfica (GUI).
Edições do Windows Server sem GUI são denominadas **Core** edições e edições com a GUI são denominados **ambiente de trabalho**.

### <a name="windows-server-core-editions"></a>Edições do Windows Server Core

Em todas as edições Core, quando iniciar sessão para o servidor de obter uma janela de linha de comandos do Windows.

Tipo `powershell` e prima **ENTER** para iniciar o PowerShell dentro da sessão de linha de comandos.
Tipo `exit` para terminar a sessão do PowerShell e regressar à linha de comandos.

### <a name="windows-server-desktop-editions"></a>Edições de ambiente de trabalho do Windows Server

Todas as edições de ambiente de trabalho, clique no ícone de Windows canto inferior esquerdo, comece a escrever o PowerShell.
Obter a consola e opções de ISE.

A única exceção à regra acima é o ISE do Windows Server 2008 R2 SP1; Neste caso, clique no ícone de Windows canto inferior esquerdo, escreva o ISE do PowerShell.

## <a name="how-to-check-the-version-of-powershell"></a>Como verificar a versão do PowerShell

Para localizar a versão do PowerShell que instalou o, inicie uma consola do PowerShell (ou o ISE) e o tipo `$PSVersionTable` e prima **ENTER**. Procure o `PSVersion` valor.

## <a name="upgrading-existing-windows-powershell"></a>Atualizar existentes do Windows PowerShell

O pacote de instalação para o PowerShell ficar no interior de um programa de instalação do WMF.
A versão do programa de instalação do WMF corresponde à versão do PowerShell; Não há nenhum instalador autónomo do Windows PowerShell.

Se precisar de atualizar a versão existente do PowerShell, no Windows, utilize a seguinte tabela para localizar o instalador para a versão do PowerShell que pretende atualizar para.

Windows | PS 3.0 | PS 4.0 | PS 5.0 | PS 5.1 |
--|--|--|--|--|
Windows 10 (consulte Note1)<br/>Windows Server 2016 | - | - | - | instalado
Windows 8.1<br/>Windows Server 2012 R2 | - | instalado | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 8<br/>Windows Server 2012 | instalado | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 7 SP1<br/>Windows Server 2008 R2 SP1 | [WMF 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> **Tenha em atenção 1**:
  >>
  >> A edição inicial do Windows 10, com as atualizações automáticas ativada, PowerShell obtém atualizado da versão 5.0 para 5.1.
  >>
  >> Se a versão original do Windows 10 não for atualizada através de atualizações do Windows, a versão do PowerShell é 5.0.

## <a name="need-azure-powershell"></a>Precisa do Azure PowerShell

Se estiver à procura de **Azure PowerShell**, poderá começar pela [descrição geral do Azure PowerShell](https://docs.microsoft.com/powershell/azure).

Caso contrário, o que poderá ser necessário é [instalar e configurar o Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-azurerm-ps)

## <a name="see-also"></a>Consulte Também

- [Requisitos de sistema do PowerShell do Windows](Windows-PowerShell-System-Requirements.md)
- [A partir do Windows PowerShell](Starting-Windows-PowerShell.md)