---
ms.date: 04/19/2019
keywords: wmf,powershell,setup
title: Windows Management Framework (WMF)
ms.openlocfilehash: 6d25b4025bbc86f6be0e5c74db9f1fbe6705d816
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984321"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) fornece uma interface de gestão consistente para Windows. WMF fornece uma forma totalmente integrada para gerir várias versões do cliente do Windows e Windows Server. Pacotes de instalação de WMF contêm atualizações para funcionalidades de gestão e estão disponíveis para versões mais antigas do Windows.

Instalação de WMF adiciona e/ou atualiza as seguintes funcionalidades:

- Windows PowerShell
- Windows PowerShell Desired State Configuration (DSC)
- Ambiente de Script integrado do Windows PowerShell (ISE)
- Gestão remota do Windows (WinRM)
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

|        Versão do Sistema Operativo         | [WMF 5.1][]  | WMF 5.0<br>*Sem suporte* | [WMF 4.0][]  | [WMF 3.0][]  | [WMF 2.0][]  |
| --------------------------------------- | ------------ | --------------------------- | ------------ | ------------ | ------------ |
| Windows Server de 2019                     | É fornecido na caixa |                             |              |              |              |
| Windows Server 2016                     | É fornecido na caixa |                             |              |              |              |
| Windows 10                              | É fornecido na caixa | É fornecido na caixa                |              |              |              |
| Windows Server 2012 R2                  | Sim          | Sim                         | É fornecido na caixa |              |              |
| Windows 8.1                             | Sim          | Sim                         | É fornecido na caixa |              |              |
| Windows Server 2012                     | Sim          | Sim                         | Sim          | É fornecido na caixa |              |
| Windows 8<br>*Sem suporte*           |              |                             |              | É fornecido na caixa |              |
| Windows Server 2008 R2 SP1              | Sim          | Sim                         | Sim          | Sim          | É fornecido na caixa |
| Windows 7 SP1                           | Sim          | Sim                         | Sim          | Sim          | É fornecido na caixa |
| Windows Server 2008 SP2                 |              |                             |              | Sim          | Sim          |
| Windows Vista<br>*Sem suporte*       |              |                             |              |              | Sim          |
| Windows Server 2003<br>*Sem suporte* |              |                             |              |              | Sim          |
| Windows XP<br>*Sem suporte*          |              |                             |              | Sim          | Sim          |

- **É fornecido na caixa**: As funcionalidades da versão especificada do WMF foram entregues na versão indicada do cliente do Windows ou Windows Server.
- **Sem suporte**: Esses produtos já não são suportados pela Microsoft. Tem de atualizar para uma nova versão é suportada. Para obter mais informações, consulte a [Política de ciclo de vida da Microsoft][] página.

> [!NOTE]
> O instalador do WMF 5.0 já não está disponível ou suportado. Foi substituída pelo WMF 5.1.

[Política de ciclo de vida da Microsoft]: https://support.microsoft.com/lifecycle
[WMF 5.1]: https://aka.ms/wmf51download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
