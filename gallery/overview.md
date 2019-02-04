---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, powershell, cmdlet, psgallery, psget
title: A galeria do PowerShell
ms.openlocfilehash: d3e3b9d8bb3d6cefd3a3bfe79b012bb1dc1d8a2d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685460"
---
# <a name="the-powershell-gallery"></a>A galeria do PowerShell

A galeria do PowerShell é o repositório central para o conteúdo do PowerShell. Nela, pode encontrar útil módulos do PowerShell que contém comandos do PowerShell e de recursos do Desired State Configuration (DSC).
Também pode encontrar scripts do PowerShell, algumas das quais podem conter fluxos de trabalho do PowerShell e que descrevem um conjunto de tarefas e fornecer o sequenciamento para essas tarefas. Alguns desses pacotes são criados pela Microsoft e outros são criados pela Comunidade do PowerShell.

## <a name="powershellget-overview"></a>Descrição geral do PowerShellGet

O módulo PowerShellGet contém cmdlets para descobrir, instalar, atualizar e publicação de pacotes do PowerShell que contêm os artefactos, tais como módulos, recursos de DSC, funcionalidades de função e Scripts a partir do [galeria do PowerShell](https://www.PowerShellGallery.com)e outros repositórios privados.

## <a name="getting-started-with-the-gallery"></a>Guia de introdução da Galeria

Instalar pacotes a partir da Galeria requer a versão mais recente do módulo PowerShellGet.
Ver [instalar o PowerShellGet](installing-psget.md) para obter instruções completas.

Veja a [introdução ao](getting-started.md) página para obter mais informações sobre como utilizar comandos do PowerShellGet com a galeria. Também pode executar *Update-Help-Module PowerShellGet* para instalar ajuda local para estes comandos.

## <a name="supported-operating-systems"></a>Sistemas operativos suportados

O **PowerShellGet** requer o módulo **Windows PowerShell 3.0 ou mais recente**, ou **PowerShell Core 6.0 ou mais recente**.

Uma versão adequada do **Windows PowerShell** está disponível para estes sistemas operativos:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**O PowerShellGet** requer o .NET Framework 4.5 ou superior. Pode instalar o .NET Framework 4.5 ou superior partir [aqui](https://msdn.microsoft.com/library/5a4x27ek.aspx).

Uma vez que **PowerShell Core** é Multiplataforma e o que significa que ele funciona no Windows, Linux e MacOS, que também faz **PowerShellGet** disponíveis nesses sistemas. Para obter uma lista completa de sistemas suportados pelo **PowerShell Core** veja [instalar o PowerShell](/powershell/scripting/setup/installing-powershell).

Muitos módulos hospedados na Galeria irão oferecer suporte a sistemas operacionais diferentes e têm requisitos adicionais. Consulte a documentação para os módulos para obter mais informações.

## <a name="got-a-question-have-feedback"></a>Tem uma pergunta? Tem comentários?

Obter mais informações sobre a galeria do PowerShell e o PowerShellGet podem ser encontradas no [introdução ao](getting-started.md) página. Introduza os comentários e relatório de problemas usando [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).
