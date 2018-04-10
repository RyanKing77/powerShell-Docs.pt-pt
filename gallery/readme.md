---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, powershell, cmdlet, psgallery, psget
title: A galeria do PowerShell
ms.openlocfilehash: 9519b8bcca9f43419a33db380c3b852e9bb354ac
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="the-powershell-gallery"></a>A galeria do PowerShell

A galeria do PowerShell consiste no repositório central para o conteúdo do PowerShell. Pode encontrar os novos comandos do PowerShell ou de recursos de configuração de estado pretendido (DSC) na galeria.

## <a name="powershellget-overview"></a>Descrição geral de PowerShellGet

O módulo de PowerShellGet contém cmdlets para detetar, instalar, atualizar e publicar PowerShell artefactos, tais como módulos, recursos de DSC, capacidades de função e Scripts a partir de [galeria do PowerShell](https://www.PowerShellGallery.com) e outra privada repositórios.

## <a name="getting-started-with-the-gallery"></a>Introdução à Galeria

Instalar itens da galeria do requer a versão mais recente do módulo PowerShellGet, que está disponível no Windows 10, no Windows Management Framework (WMF) 5.0 ou no instalador do MSI com base em (para PowerShell 3 e 4).

- [**Obter o Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),
- [**Obter o WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), ou
- [**Obter o Instalador MSI**](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

Com a versão mais recente [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) módulo, pode:

-   Pesquisa através de itens na galeria com [encontrar o módulo](https://go.microsoft.com/fwlink/?LinkId=821658) e [localizar Script](https://go.microsoft.com/fwlink/?LinkId=822322)
-   Guardar itens para o sistema da galeria com [guardar-Module](https://go.microsoft.com/fwlink/?LinkId=821669) e [Script guardar](https://go.microsoft.com/fwlink/?LinkId=822334)
-   Instale os itens da galeria com [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) e [Script de instalação](https://go.microsoft.com/fwlink/?LinkId=822327)
-   Carregar itens para a galeria com [publicar-Module](https://go.microsoft.com/fwlink/?LinkId=821666) e [publicar Script](https://go.microsoft.com/fwlink/?LinkId=822331)
-   Adicione o seus próprios repositório personalizado com [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)

Veja o [introdução](psgallery/psgallery_gettingstarted.md) página para obter mais informações sobre como utilizar comandos PowerShellGet com a galeria. Também pode executar *Update-Help-PowerShellGet módulo* instalar ajuda local para estes comandos.

## <a name="supported-operating-systems"></a>Sistemas operativos suportados

O **PowerShellGet** módulo requer **PowerShell 3.0 ou mais recente**.

Por conseguinte, **PowerShellGet** necessita de um dos seguintes sistemas operativos:

- 10 do Windows
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** também requer o .NET Framework 4.5 ou superior. Pode instalar o .NET Framework 4.5 ou superior do [aqui](https://msdn.microsoft.com/library/5a4x27ek.aspx).


## <a name="got-a-question-have-feedback"></a>Recebeu uma pergunta? Tem comentários?

Podem encontrar mais informações sobre a galeria do PowerShell e PowerShellGet no [introdução](psgallery/psgallery_gettingstarted.md) página. Forneça comentários e comunicar problemas com [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).