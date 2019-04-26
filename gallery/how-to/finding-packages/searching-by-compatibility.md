---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Pacotes com o sistema operativo ou edições do PowerShell compatíveis
ms.openlocfilehash: 14038aa9b0453e1d06e6587e97da391b56297c75
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084577"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>Pacotes com sistemas operativos ou edições do PowerShell compatíveis

A partir da versão 5.1, o PowerShell está disponível nas diferentes edições que denotam conjuntos diferentes de recursos e às compatibilidades de plataforma.

## <a name="searching-by-powershell-edition"></a>Pesquisar por edição do PowerShell

As duas edições do PowerShell são:
- **Edição Desktop:** Criado no .NET Framework e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço total do Windows como núcleo de servidor e Desktop do Windows.
- **Edição Core:** Incorporada no .NET Core e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço reduzido do Windows, como o servidor Nano e o Windows IoT.

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>Galeria do PowerShell permite-lhe filtrar pacotes compatíveis para as edições específicas do PowerShell

Se um pacote tem compatível edições do PowerShell especificado, são listados como parte das edições do PowerShell na página de exibição do pacote e também nos resultados de pacotes.
Também pode procurar pacotes compatíveis com o PowerShell.

![Página de exibição de itens com edições do PowerShell](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>Procurar pacotes na galeria da interface do Usuário que funcionam no PowerShell Core

Utilizar etiquetas: "PSEdition_Desktop" e as etiquetas: "PSEdition_Core" aos filtros de pacotes na galeria do PowerShell.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Utilizar etiquetas: "PSEdition_Core" Pesquisar itens compatíveis com o PowerShell Core Edition.

![Resultados da pesquisa para itens compatíveis com o Core PSEdition](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Utilizar etiquetas: "PSEdition_Desktop" Pesquisar itens compatíveis com a edição de ambiente de trabalho do PowerShell.

![Resultados da pesquisa para itens compatíveis com PSEdition da área de trabalho](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>Procurar pacotes encontrar as edições compatíveis com o PowerShell
Pode especificar etiquetas para filtrar para a edição do PowerShell e o sistema operacional.
Utilizar o `Find-Package` cmdlet especificando o `-Tag` parâmetro para especificar a edição (e o sistema operacional) estiver a filtrar.
Como este:

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>Pesquisar por sistema operativo

Uma vez que o PowerShell Core está disponível para Windows, Linux e MacOS, pacotes na galeria podem ser criados para qualquer combinação destes sistemas operativos. Na galeria da interface do Usuário utilize as seguintes etiquetas searchs para encontrar pacotes marcados pelo sistema operativo:

- Tags: "Windows"
- Tags: "Linux"
- Tags: "MacOS"

Pode especificar essas marcas na `Find-Module` (e outros cmdlets no módulo PowerShellGet), assim:

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>A procurar às compatibilidades vários

Pode procurar por um pacote que tenha às compatibilidades vários utilizando a sintaxe:

Tags: "Compatibility1" "Compatibility2"

Por exemplo, se estiver procurando por um pacote com o PowerShell Core compatibilidade, que é executado em meus computadores Windows e Linux, utilize as etiquetas de pesquisa:

Tags: "PSEdition_Core" "Windows" "Linux"

Para procurar com o PowerShell, pode usar o `Find-Module` (e os outros cmdlets no módulo PowerShellGet), assim:

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Obter mais detalhes sobre a criação e encontrar os pacotes com edições do PowerShell compatíveis

- [Módulos com Edições do PowerShell](../../concepts/module-psedition-support.md)
- [Scripts com Edições do PowerShell](../../concepts/script-psedition-support.md)
