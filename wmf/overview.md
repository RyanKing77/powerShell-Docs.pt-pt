---
ms.date: 06/12/2018
keywords: wmf,powershell,setup
title: Windows Management Framework (WMF)
ms.openlocfilehash: f279f975527dc198dd9b47ca1dc4258f54fafef5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684438"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) fornece uma interface de gestão consistente para Windows. WMF fornece uma forma totalmente integrada para gerir várias versões do cliente do Windows e Windows Server. Pacotes de instalação de WMF contêm atualizações para funcionalidades de gestão e estão disponíveis para versões mais antigas do Windows.

Instalação de WMF adiciona e/ou atualiza as seguintes funcionalidades:

- Windows PowerShell
- Configuração de Estado Pretendido (DSC) do Windows PowerShell
- Ambiente de Script integrado do Windows PowerShell (ISE)
- Gestão Remota do Windows (WinRM)
- Windows Management Instrumentation (WMI)
- Windows PowerShell Web Services (extensão de gestão de IIS de OData)
- Registo de Inventário de Software (SIL)
- Fornecedor do Gestor de servidor CIM

## <a name="wmf-release-notes"></a>Notas de versão do WMF

Para saber mais sobre várias melhorias no PowerShell e outros componentes de um determinado WMF, veja as ligações abaixo para rever as notas de versão:

- [WMF 5.1](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>Disponibilidade WMF em sistemas de operativos do Windows

|Versão do sistema operativo  |[WMF 5.1][] |[WMF 5.0][] |[WMF 4.0][] |[WMF 3.0][]  |[WMF 2.0][] |
|--------------------------|------------|------------|------------|-------------|------------|
|Windows Server 2019       |É fornecido na caixa|            |            |             |            |
|Windows Server 2016       |É fornecido na caixa|            |            |             |            |
|Windows 10                |É fornecido na caixa|É fornecido na caixa|            |             |            |
|Windows Server 2012 R2    |Sim         |Sim         |É fornecido na caixa|             |            |
|Windows 8.1               |Sim         |Sim         |É fornecido na caixa|             |            |
|Windows Server 2012       |Sim         |Sim         |Sim         |É fornecido na caixa |            |
|Windows 8                 |            |            |            |É fornecido na caixa |            |
|Windows Server 2008 R2 SP1|Sim         |Sim         |Sim         |Sim          |É fornecido na caixa|
|Windows 7 SP1             |Sim         |Sim         |Sim         |Sim          |É fornecido na caixa|
|Windows Server 2008 SP2   |            |            |            |Sim          |Sim         |
|Windows Vista             |            |            |            |             |Sim         |
|Windows Server 2003       |            |            |            |             |Sim         |
|Windows XP                |            |            |            |Sim          |            |

**É fornecido na caixa**: As funcionalidades da versão especificada do WMF foram entregues na versão indicada do cliente do Windows ou Windows Server.

[WMF 5.1]: https://aka.ms/wmf51download
[WMF 5.0]: https://aka.ms/wmf5download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
