---
title: Escrever um ficheiro de formatação de PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39acce45-5144-43ba-894d-a4ce782fa67d
caps.latest.revision: 13
ms.openlocfilehash: f89f0009972d5237d71cb8f0d1c53cd0ae614b67
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083580"
---
# <a name="writing-a-powershell-formatting-file"></a><span data-ttu-id="3edab-102">Writing a PowerShell Formatting File (Escrever um Ficheiro de Formatação do PowerShell)</span><span class="sxs-lookup"><span data-stu-id="3edab-102">Writing a PowerShell Formatting File</span></span>

<span data-ttu-id="3edab-103">"Escrever um ficheiro de formatação de PowerShell" é para desenvolvedores de comando que estão escrevendo cmdlets ou as funções que objetos para a linha de comando de saída.</span><span class="sxs-lookup"><span data-stu-id="3edab-103">"Writing a PowerShell Formatting File" is for command developers who are writing cmdlets or functions that output objects to the command line.</span></span> <span data-ttu-id="3edab-104">Arquivos de formatação definem como o PowerShell exibe esses objetos na linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="3edab-104">Formatting files define how PowerShell displays those objects at the command line.</span></span> <span data-ttu-id="3edab-105">Esta documentação fornece uma descrição geral de formatação de ficheiros, obter uma explicação sobre os conceitos que deve compreender ao escrever esses arquivos, exemplos de XML utilizado nesses arquivos e uma seção de referência para os elementos XML.</span><span class="sxs-lookup"><span data-stu-id="3edab-105">This documentation provides an overview of formatting files, an explanation of the concepts that you should understand when writing these files, examples of XML used in these files, and a reference section for the XML elements.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="3edab-106">Nesta Secção</span><span class="sxs-lookup"><span data-stu-id="3edab-106">In This Section</span></span>

<span data-ttu-id="3edab-107">[Descrição geral de ficheiros de formatação](./formatting-file-overview.md) descreve é que um ficheiro de formato e os componentes gerais de um ficheiro de formatação, incluindo funcionalidades comuns que podem ser definidas no ficheiro, os diferentes tipos de vistas de formato que podem ser definidas para objetos .NET e uma um exemplo simplificado do XML usado para definir uma vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="3edab-107">[Formatting File Overview](./formatting-file-overview.md) Describes what a format file is and the general components of a formatting file, including common features that can be defined in the file, the different types of format views that can be defined for .NET objects, and a simplified example of the XML used to define a table view.</span></span>

<span data-ttu-id="3edab-108">[Conceitos de ficheiro de formatação](./formatting-file-concepts.md) inclui informações que poderá precisar de saber que, ao criar a sua própria formatação ficheiros, como os diferentes tipos de vistas que pode definir e componentes especiais dessas vistas.</span><span class="sxs-lookup"><span data-stu-id="3edab-108">[Formatting File Concepts](./formatting-file-concepts.md) Includes information that you might need to know when creating your own formatting files, such as the different types of views that you can define and special components of those views.</span></span>

<span data-ttu-id="3edab-109">[Exemplos de arquivos de formatação](./examples-of-formatting-files.md) exemplos de XML fornece de vários arquivos de formatação, incluindo exemplos de uma vista de tabela, uma vista de lista e uma vista alargada, bem como exemplos que mostram como definir funcionalidades, como os conjuntos de seleção, condições de seleção, e controles comuns.</span><span class="sxs-lookup"><span data-stu-id="3edab-109">[Examples of Formatting Files](./examples-of-formatting-files.md) Provides XML examples of several formatting files, including examples of a table view, a list view, and a wide view, as well as examples that show how to define features such as selection sets, selection conditions, and common controls.</span></span>

<span data-ttu-id="3edab-110">[Formatar referência XML](./format-schema-xml-reference.md) inclui tópicos de referência para os elementos XML usados num arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="3edab-110">[Format XML Reference](./format-schema-xml-reference.md) Includes reference topics for the XML elements used in a formatting file.</span></span>
