---
title: Suporte a caracteres curinga nos parâmetros de Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 6c762d3889bc4b649252390625525db4735f4c1d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067404"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Supporting Wildcard Characters in Cmdlet Parameters (Suportar Carateres Universais em Parâmetros de Cmdlets)

Muitas vezes, terá de criar um cmdlet para ser executado em relação a um grupo de recursos, em vez de em relação a um único recurso. Por exemplo, um cmdlet poderá ter de localizar todos os arquivos num arquivo de dados que têm o mesmo nome ou a extensão. Tem de fornecer suporte para carateres universais ao conceber um cmdlet que será executado em relação a um grupo de recursos.

> [!NOTE]
> Com carateres universais é por vezes denominado *globbing*.

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>Cmdlets do Windows PowerShell que utilizar carateres universais

 Muitos cmdlets do Windows PowerShell suporta carateres universais para seus valores de parâmetro. Por exemplo, quase todos os cmdlet que tem um `Name` ou `Path` parâmetro suporta carateres universais para estes parâmetros. (Embora a maioria dos cmdlets que tem um `Path` parâmetro também tem um `LiteralPath` parâmetro que não suporta carateres universais.) O comando seguinte mostra como um caractere curinga é usado para retornar todos os cmdlets na sessão atual cujo nome contém o verbo Get.

 **PS > get-command get -\***

## <a name="supported-wildcard-characters"></a>Carateres universais suportados

Windows PowerShell suporta os seguintes carateres universais.

|Caráter universal|Descrição|Exemplo|Correspondências|Não corresponde|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|Corresponde a zero ou mais carateres, a partir da posição especificada|a*|Um, ag, Apple||
|?|Correspondências anycharacter na posição especificada|?n|Um, em, no|ran|
|[ ]|Corresponde a um intervalo de carateres|[a-l]ook|livro, cook, vista de olhos|demorou|
|[ ]|Corresponde a caracteres especificados|[bc]ook|livro, cook|Vista de olhos|

Ao conceber cmdlets que suportam carateres universais, permitir combinações de carateres universais. Por exemplo, o seguinte comando utiliza o `Get-ChildItem` cmdlet para obter todos os ficheiros. txt que estão na pasta c:\Techdocs e que começam com as letras "a" através de "l."

**get-childitem c:\techdocs\\[a-l]\*.txt**

O comando anterior utiliza o curinga de intervalo **[a-l]** para especificar que o nome de ficheiro deve começar com os carateres "a" através de "l." O comando, em seguida, utiliza o * caráter universal como um marcador de posição para quaisquer carateres entre a primeira letra do nome do ficheiro e a extensão. txt.

O exemplo seguinte utiliza um padrão de caráter universal do intervalo que exclui a letra "d", mas inclui todas as outras letras de "a" através de "f."

**get-childitem c:\techdocs\\[a-cef]\*.txt**

## <a name="handling-literal-characters-in-wildcard-patterns"></a>Manipulação de carateres Literal de padrões de carateres universais

Se o padrão de caráter universal especificado contém carateres literais, utilize o caráter de acento grave (') como um caráter de escape. Quando especificar bastarão caracteres literais programaticamente, use um único backtick. Quando especificar caracteres literais no prompt de comando, utilize dois backticks. Por exemplo, o padrão seguinte contém duas chaves, que tem de ser executadas literalmente.

"John Smith \`[*']" (especificado por meio de programação)

"João Silva \` \`[*\`']" (especificado no prompt de comando)

Este padrão corresponde a "John Smith [Marketing]" ou "John Smith [desenvolvimento]".

## <a name="cmdlet-output-and-wildcard-characters"></a>Resultado do cmdlet e os carateres universais

Quando os parâmetros de cmdlet suportam carateres universais, uma operação de cmdlet gera normalmente uma saída de matriz. Ocasionalmente, ele não faz sentido suportar uma matriz de saída uma vez que o usuário poderia utilizar apenas um único item por vez. Por exemplo, o `Set-Location` cmdlet oferece suporte a uma matriz de saída uma vez que o utilizador define apenas um único local. Neste caso, o cmdlet ainda suporta carateres universais, mas ela força a resolução para um único local.

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Classe de WildcardPattern](/dotnet/api/system.management.automation.wildcardpattern)
