---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: psgallery_pseditions
ms.openlocfilehash: 6634da5c2dadee9c0c6470b3d3e8883e6d02160f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="items-with-compatible-powershell-editions"></a>Itens com edições de PowerShell compatível
Começando na versão 5.1, o PowerShell está disponível nas diferentes edições que denotam conjuntos de funcionalidade e compatibilidade de plataforma variados.

- **Edição Desktop:** incorporada no .NET Framework e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço total do Windows, tais como Server Core e o Ambiente de trabalho do Windows.
- **Edição Core:** incorporada no .NET Core e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço reduzido do Windows, tais como Servidor Nano e o IoT do Windows.

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a>Galeria do PowerShell extrai metadados de PSEditions suportados e permite-lhe os itens de filtros compatível para edições específicas do PowerShell

Se um item tem compatível PSEditions especificados, estes serão apresentados como parte do 'PowerShell edições' na página de visualização do item e também nos resultados de itens.
![Página de visualização do item com PSEditions](Images/ItemDisplayPageWithPSEditions.PNG)

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a>Pesquisa de itens de Galeria de IU que funciona em PowerShellCore
Utilize etiquetas: etiquetas e "PSEdition_Desktop": "PSEdition_Core" filtros os itens de galeria do PowerShell.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Utilize etiquetas: "PSEdition_Core" para procurar itens compatíveis com o PowerShell Core edição.
![Resultados da pesquisa para itens compatíveis com PSEdition de núcleo](Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Utilize etiquetas: "PSEdition_Desktop" para procurar itens compatíveis com a edição de ambiente de trabalho do PowerShell.
![Resultados da pesquisa de itens compatíveis com o ambiente de trabalho PSEdition](Images/SearchResultsWithPSEdition_Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a>Obter mais detalhes sobre a criação e localizar os itens com edições de PowerShell compatível
### <a name="modules-with-pseditionspsgetmodulemodulewithpseditionsupportmd"></a>[Módulos com PSEditions](../psget/module/modulewithpseditionsupport.md)
### <a name="scripts-with-pseditionspsgetscriptscriptwithpseditionsupportmd"></a>[Scripts com PSEditions](../psget/script/scriptwithpseditionsupport.md)

