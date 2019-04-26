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
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="534ac-102">Supporting Wildcard Characters in Cmdlet Parameters (Suportar Carateres Universais em Parâmetros de Cmdlets)</span><span class="sxs-lookup"><span data-stu-id="534ac-102">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="534ac-103">Muitas vezes, terá de criar um cmdlet para ser executado em relação a um grupo de recursos, em vez de em relação a um único recurso.</span><span class="sxs-lookup"><span data-stu-id="534ac-103">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="534ac-104">Por exemplo, um cmdlet poderá ter de localizar todos os arquivos num arquivo de dados que têm o mesmo nome ou a extensão.</span><span class="sxs-lookup"><span data-stu-id="534ac-104">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="534ac-105">Tem de fornecer suporte para carateres universais ao conceber um cmdlet que será executado em relação a um grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="534ac-105">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="534ac-106">Com carateres universais é por vezes denominado *globbing*.</span><span class="sxs-lookup"><span data-stu-id="534ac-106">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="534ac-107">Cmdlets do Windows PowerShell que utilizar carateres universais</span><span class="sxs-lookup"><span data-stu-id="534ac-107">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="534ac-108">Muitos cmdlets do Windows PowerShell suporta carateres universais para seus valores de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="534ac-108">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="534ac-109">Por exemplo, quase todos os cmdlet que tem um `Name` ou `Path` parâmetro suporta carateres universais para estes parâmetros.</span><span class="sxs-lookup"><span data-stu-id="534ac-109">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="534ac-110">(Embora a maioria dos cmdlets que tem um `Path` parâmetro também tem um `LiteralPath` parâmetro que não suporta carateres universais.) O comando seguinte mostra como um caractere curinga é usado para retornar todos os cmdlets na sessão atual cujo nome contém o verbo Get.</span><span class="sxs-lookup"><span data-stu-id="534ac-110">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 <span data-ttu-id="534ac-111">**PS > get-command get -\***</span><span class="sxs-lookup"><span data-stu-id="534ac-111">**PS>get-command get-\***</span></span>

## <a name="supported-wildcard-characters"></a><span data-ttu-id="534ac-112">Carateres universais suportados</span><span class="sxs-lookup"><span data-stu-id="534ac-112">Supported Wildcard Characters</span></span>

<span data-ttu-id="534ac-113">Windows PowerShell suporta os seguintes carateres universais.</span><span class="sxs-lookup"><span data-stu-id="534ac-113">Windows PowerShell supports the following wildcard characters.</span></span>

|<span data-ttu-id="534ac-114">Caráter universal</span><span class="sxs-lookup"><span data-stu-id="534ac-114">Wildcard character</span></span>|<span data-ttu-id="534ac-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="534ac-115">Description</span></span>|<span data-ttu-id="534ac-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="534ac-116">Example</span></span>|<span data-ttu-id="534ac-117">Correspondências</span><span class="sxs-lookup"><span data-stu-id="534ac-117">Matches</span></span>|<span data-ttu-id="534ac-118">Não corresponde</span><span class="sxs-lookup"><span data-stu-id="534ac-118">Does not match</span></span>|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|<span data-ttu-id="534ac-119">Corresponde a zero ou mais carateres, a partir da posição especificada</span><span class="sxs-lookup"><span data-stu-id="534ac-119">Matches zero or more characters, starting at the specified position</span></span>|<span data-ttu-id="534ac-120">a\*</span><span class="sxs-lookup"><span data-stu-id="534ac-120">a\*</span></span>|<span data-ttu-id="534ac-121">Um, ag, Apple</span><span class="sxs-lookup"><span data-stu-id="534ac-121">A, ag, Apple</span></span>||
|<span data-ttu-id="534ac-122">?</span><span class="sxs-lookup"><span data-stu-id="534ac-122">?</span></span>|<span data-ttu-id="534ac-123">Correspondências anycharacter na posição especificada</span><span class="sxs-lookup"><span data-stu-id="534ac-123">Matches anycharacter at the specified position</span></span>|<span data-ttu-id="534ac-124">?n</span><span class="sxs-lookup"><span data-stu-id="534ac-124">?n</span></span>|<span data-ttu-id="534ac-125">Um, em, no</span><span class="sxs-lookup"><span data-stu-id="534ac-125">An, in, on</span></span>|<span data-ttu-id="534ac-126">ran</span><span class="sxs-lookup"><span data-stu-id="534ac-126">ran</span></span>|
|<span data-ttu-id="534ac-127">[ ]</span><span class="sxs-lookup"><span data-stu-id="534ac-127">[ ]</span></span>|<span data-ttu-id="534ac-128">Corresponde a um intervalo de carateres</span><span class="sxs-lookup"><span data-stu-id="534ac-128">Matches a range of characters</span></span>|<span data-ttu-id="534ac-129">[a-l]ook</span><span class="sxs-lookup"><span data-stu-id="534ac-129">[a-l]ook</span></span>|<span data-ttu-id="534ac-130">livro, cook, vista de olhos</span><span class="sxs-lookup"><span data-stu-id="534ac-130">book, cook, look</span></span>|<span data-ttu-id="534ac-131">demorou</span><span class="sxs-lookup"><span data-stu-id="534ac-131">took</span></span>|
|<span data-ttu-id="534ac-132">[ ]</span><span class="sxs-lookup"><span data-stu-id="534ac-132">[ ]</span></span>|<span data-ttu-id="534ac-133">Corresponde a caracteres especificados</span><span class="sxs-lookup"><span data-stu-id="534ac-133">Matches the specified characters</span></span>|<span data-ttu-id="534ac-134">[bc]ook</span><span class="sxs-lookup"><span data-stu-id="534ac-134">[bc]ook</span></span>|<span data-ttu-id="534ac-135">livro, cook</span><span class="sxs-lookup"><span data-stu-id="534ac-135">book, cook</span></span>|<span data-ttu-id="534ac-136">Vista de olhos</span><span class="sxs-lookup"><span data-stu-id="534ac-136">look</span></span>|

<span data-ttu-id="534ac-137">Ao conceber cmdlets que suportam carateres universais, permitir combinações de carateres universais.</span><span class="sxs-lookup"><span data-stu-id="534ac-137">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="534ac-138">Por exemplo, o seguinte comando utiliza o `Get-ChildItem` cmdlet para obter todos os ficheiros. txt que estão na pasta c:\Techdocs e que começam com as letras "a" através de "l."</span><span class="sxs-lookup"><span data-stu-id="534ac-138">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

<span data-ttu-id="534ac-139">**get-childitem c:\techdocs\\[a-l]\*.txt**</span><span class="sxs-lookup"><span data-stu-id="534ac-139">**get-childitem c:\techdocs\\[a-l]\*.txt**</span></span>

<span data-ttu-id="534ac-140">O comando anterior utiliza o curinga de intervalo **[a-l]** para especificar que o nome de ficheiro deve começar com os carateres "a" através de "l."</span><span class="sxs-lookup"><span data-stu-id="534ac-140">The previous command uses the range wildcard **[a-l]** to specify that the file name should begin with the characters "a" through "l."</span></span> <span data-ttu-id="534ac-141">O comando, em seguida, utiliza o \* caráter universal como um marcador de posição para quaisquer carateres entre a primeira letra do nome do ficheiro e a extensão. txt.</span><span class="sxs-lookup"><span data-stu-id="534ac-141">The command then uses the \* wildcard character as a placeholder for any characters between the first letter of the file name and the .txt extension.</span></span>

<span data-ttu-id="534ac-142">O exemplo seguinte utiliza um padrão de caráter universal do intervalo que exclui a letra "d", mas inclui todas as outras letras de "a" através de "f."</span><span class="sxs-lookup"><span data-stu-id="534ac-142">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

<span data-ttu-id="534ac-143">**get-childitem c:\techdocs\\[a-cef]\*.txt**</span><span class="sxs-lookup"><span data-stu-id="534ac-143">**get-childitem c:\techdocs\\[a-cef]\*.txt**</span></span>

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="534ac-144">Manipulação de carateres Literal de padrões de carateres universais</span><span class="sxs-lookup"><span data-stu-id="534ac-144">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="534ac-145">Se o padrão de caráter universal especificado contém carateres literais, utilize o caráter de acento grave (') como um caráter de escape.</span><span class="sxs-lookup"><span data-stu-id="534ac-145">If the wildcard pattern you specify contains literal characters, use the backtick character (\`) as an escape character.</span></span> <span data-ttu-id="534ac-146">Quando especificar bastarão caracteres literais programaticamente, use um único backtick.</span><span class="sxs-lookup"><span data-stu-id="534ac-146">When you specify literal characters programmatically, use a single backtick.</span></span> <span data-ttu-id="534ac-147">Quando especificar caracteres literais no prompt de comando, utilize dois backticks.</span><span class="sxs-lookup"><span data-stu-id="534ac-147">When you specify literal characters at the command prompt, use two backticks.</span></span> <span data-ttu-id="534ac-148">Por exemplo, o padrão seguinte contém duas chaves, que tem de ser executadas literalmente.</span><span class="sxs-lookup"><span data-stu-id="534ac-148">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="534ac-149">"John Smith \`[\*']" (especificado por meio de programação)</span><span class="sxs-lookup"><span data-stu-id="534ac-149">"John Smith \`[\*\`]" (specified programmatically)</span></span>

<span data-ttu-id="534ac-150">"João Silva \` \`[\*\`']" (especificado no prompt de comando)</span><span class="sxs-lookup"><span data-stu-id="534ac-150">"John Smith \`\`[\*\`\`]"  (specified at the command prompt)</span></span>

<span data-ttu-id="534ac-151">Este padrão corresponde a "John Smith [Marketing]" ou "John Smith [desenvolvimento]".</span><span class="sxs-lookup"><span data-stu-id="534ac-151">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span>

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="534ac-152">Resultado do cmdlet e os carateres universais</span><span class="sxs-lookup"><span data-stu-id="534ac-152">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="534ac-153">Quando os parâmetros de cmdlet suportam carateres universais, uma operação de cmdlet gera normalmente uma saída de matriz.</span><span class="sxs-lookup"><span data-stu-id="534ac-153">When cmdlet parameters support wildcard characters, a cmdlet operation usually generates an array output.</span></span> <span data-ttu-id="534ac-154">Ocasionalmente, ele não faz sentido suportar uma matriz de saída uma vez que o usuário poderia utilizar apenas um único item por vez.</span><span class="sxs-lookup"><span data-stu-id="534ac-154">Occasionally, it makes no sense to support an array output because the user might use only a single item at a time.</span></span> <span data-ttu-id="534ac-155">Por exemplo, o `Set-Location` cmdlet oferece suporte a uma matriz de saída uma vez que o utilizador define apenas um único local.</span><span class="sxs-lookup"><span data-stu-id="534ac-155">For example, the `Set-Location` cmdlet does support an array output because the user sets only a single location.</span></span> <span data-ttu-id="534ac-156">Neste caso, o cmdlet ainda suporta carateres universais, mas ela força a resolução para um único local.</span><span class="sxs-lookup"><span data-stu-id="534ac-156">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="534ac-157">Veja Também</span><span class="sxs-lookup"><span data-stu-id="534ac-157">See Also</span></span>

[<span data-ttu-id="534ac-158">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="534ac-158">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="534ac-159">Classe de WildcardPattern</span><span class="sxs-lookup"><span data-stu-id="534ac-159">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
