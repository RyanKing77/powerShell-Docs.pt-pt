---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Pacotes com edições do PowerShell compatíveis
ms.openlocfilehash: e16cfb0ee30e344c9399bec2985baafc5a252fd7
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004154"
---
# <a name="packages-with-compatible-powershell-editions"></a>Pacotes com edições do PowerShell compatíveis

Começando na versão 5.1, o PowerShell está disponível nas diferentes edições que denotam conjuntos de funcionalidade e compatibilidade de plataforma variados.

- **Edição Desktop:** incorporada no .NET Framework e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço total do Windows, tais como Server Core e o Ambiente de trabalho do Windows.
- **Edição Core:** incorporada no .NET Core e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço reduzido do Windows, tais como Servidor Nano e o IoT do Windows.

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-packages-compatible-for-specific-powershell-editions"></a>Galeria do PowerShell extrai metadados de edições do PowerShell suportados e permite os pacotes de filtros compatível para edições específicas do PowerShell

Se um pacote tem compatível edições do PowerShell especificados, estes serão apresentados como parte das edições do PowerShell na página de exibição do pacote e também nos resultados de pacotes.

![Página de exibição de itens com edições do PowerShell](../../Images/manual_package_download.png)

## <a name="search-for-packages-in-the-gallery-ui-which-works-on-powershellcore"></a>Procurar pacotes na galeria da interface do Usuário que funciona em PowerShellCore

Utilizar etiquetas: "PSEdition_Desktop" e as etiquetas: "PSEdition_Core" aos filtros de pacotes na galeria do PowerShell.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Utilizar etiquetas: "PSEdition_Core" Pesquisar itens compatíveis com o PowerShell Core Edition.

![Resultados da pesquisa para itens compatíveis com o Core PSEdition](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Utilizar etiquetas: "PSEdition_Desktop" Pesquisar itens compatíveis com a edição de ambiente de trabalho do PowerShell.

![Resultados da pesquisa para itens compatíveis com PSEdition da área de trabalho](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Obter mais detalhes sobre a criação e encontrar os pacotes com edições do PowerShell compatíveis

- [Módulos com Edições do PowerShell](../../concepts/module-psedition-support.md)
- [Scripts com Edições do PowerShell](../../concepts/script-psedition-support.md)
