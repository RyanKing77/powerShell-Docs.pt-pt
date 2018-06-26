---
ms.date: 06/12/2018
keywords: wmf,powershell,setup
title: Windows Management Framework (WMF)
ms.openlocfilehash: 17011f88c364cb56a0c87f092873ccd99db450bc
ms.sourcegitcommit: 68093cc12a7a22c53d11ce7d33c18622921a0dd1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2018
ms.locfileid: "36940395"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) fornece uma interface de gestão consistente para o Windows. WMF fornece uma forma totalmente integrada para gerir várias versões de cliente Windows e Windows Server. Pacotes de instalador do WMF contêm atualizações para funcionalidades de gestão e estão disponíveis para as versões mais antigas do Windows.

Instalação do WMF adiciona e/ou atualiza as seguintes funcionalidades:

- Windows PowerShell
- Configuração de Estado Pretendido (DSC) do Windows PowerShell
- Ambiente de Script integrada do Windows PowerShell (ISE)
- Gestão Remota do Windows (WinRM)
- Windows Management Instrumentation (WMI)
- Serviços do Windows PowerShell Web (extensão IIS de OData da gestão)
- Registo de Inventário de Software (SIL)
- Fornecedor do Gestor de servidor CIM

## <a name="wmf-release-notes"></a>Notas de versão do WMF

Para saber mais sobre vários melhoramentos no PowerShell e outros componentes de uma determinada WMF, consulte as ligações abaixo para rever as notas de versão:

- [WMF 5.1](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>Disponibilidade do WMF em sistemas operativos Windows

|Versão do sistema operativo  |[WMF 5.1][] |[WMF 5.0][] |[WMF 4.0][] |[WMF 3.0][]  |[WMF 2.0][] |
|--------------------------|------------|------------|------------|-------------|------------|
|Windows Server 2016       |Na caixa de ships|            |            |             |            |
|10 do Windows                |Na caixa de ships|Na caixa de ships|            |             |            |
|Windows Server 2012 R2    |Sim         |Sim         |Na caixa de ships|             |            |
|Windows 8.1               |Sim         |Sim         |Na caixa de ships|             |            |
|Windows Server 2012       |Sim         |Sim         |Sim         |Na caixa de ships |            |
|Windows 8                 |            |            |            |Na caixa de ships |            |
|Windows Server 2008 R2 SP1|Sim         |Sim         |Sim         |Sim          |Na caixa de ships|
|Windows 7 SP1             |Sim         |Sim         |Sim         |Sim          |Na caixa de ships|
|Windows Server 2008 SP2   |            |            |            |Sim          |Sim         |
|Windows Vista             |            |            |            |             |Sim         |
|Windows Server 2003       |            |            |            |             |Sim         |
|Windows XP                |            |            |            |Sim          |            |

**É fornecido na caixa**: as funcionalidades da versão especificada do WMF foram fornecidas na versão de cliente do Windows ou Windows Server indicada.

[WMF 5.1]: https://aka.ms/wmf51download
[WMF 5.0]: https://aka.ms/wmf5download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
