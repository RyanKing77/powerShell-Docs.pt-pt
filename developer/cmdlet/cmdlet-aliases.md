---
title: Aliases de cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849967"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="fa0fe-102">Cmdlet Aliases (Aliases de Cmdlets)</span><span class="sxs-lookup"><span data-stu-id="fa0fe-102">Cmdlet Aliases</span></span>

<span data-ttu-id="fa0fe-103">Pode utilizar o cmdlet aliases para melhorar a experiência de utilizador do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fa0fe-103">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="fa0fe-104">Pode adicionar aliases para cmdlets usados com freqüência para reduzir a digitação e para facilitar a concluir as tarefas rapidamente.</span><span class="sxs-lookup"><span data-stu-id="fa0fe-104">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="fa0fe-105">Pode incluir aliases incorporados nos seus cmdlets ou os utilizadores possam definir seus próprios aliases personalizados.</span><span class="sxs-lookup"><span data-stu-id="fa0fe-105">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="fa0fe-106">Por exemplo, o [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet tem um incorporado `gcm` alias.</span><span class="sxs-lookup"><span data-stu-id="fa0fe-106">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="fa0fe-107">Também pode usar aliases para adicionar nomes de comandos a partir de outras linguagens, para que os usuários não precisam aprender novos comandos.</span><span class="sxs-lookup"><span data-stu-id="fa0fe-107">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="fa0fe-108">Diretrizes de alias</span><span class="sxs-lookup"><span data-stu-id="fa0fe-108">Alias Guidelines</span></span>

<span data-ttu-id="fa0fe-109">Ao criar aliases incorporadas para os cmdlets, siga estas diretrizes:</span><span class="sxs-lookup"><span data-stu-id="fa0fe-109">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="fa0fe-110">Antes de atribuir aliases, inicie o Windows PowerShell e, em seguida, execute o [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet para ver os aliases que já estão a ser utilizados.</span><span class="sxs-lookup"><span data-stu-id="fa0fe-110">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="fa0fe-111">Inclua um prefixo de alias que referencia o verbo do nome do cmdlet e um sufixo de alias que referencia o substantivo do nome do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fa0fe-111">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="fa0fe-112">Por exemplo, o alias para o `Import-Module` cmdlet é "ipmo".</span><span class="sxs-lookup"><span data-stu-id="fa0fe-112">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="fa0fe-113">Para obter uma lista de todos os verbos e seus aliases, consulte [verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="fa0fe-113">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="fa0fe-114">Para cmdlets que têm o mesmo verbo, incluem o mesmo prefixo de alias.</span><span class="sxs-lookup"><span data-stu-id="fa0fe-114">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="fa0fe-115">Por exemplo, os aliases para todos os cmdlets do Windows PowerShell que têm o verbo "Get" no respetivo nome utilizam o prefixo "g".</span><span class="sxs-lookup"><span data-stu-id="fa0fe-115">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="fa0fe-116">Para cmdlets que têm o mesmo substantivo, incluem o mesmo sufixo de alias.</span><span class="sxs-lookup"><span data-stu-id="fa0fe-116">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="fa0fe-117">Por exemplo, os aliases para todos os cmdlets do Windows PowerShell que tenham o substantivo "Session" no respetivo nome utilizam o sufixo "sn".</span><span class="sxs-lookup"><span data-stu-id="fa0fe-117">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="fa0fe-118">Para cmdlets que são equivalentes aos comandos em outros idiomas, utilize o nome do comando.</span><span class="sxs-lookup"><span data-stu-id="fa0fe-118">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="fa0fe-119">Em geral, verifique aliases o mais curtos possível.</span><span class="sxs-lookup"><span data-stu-id="fa0fe-119">In general, make aliases as short as possible.</span></span> <span data-ttu-id="fa0fe-120">Certifique-se de que o alias tem pelo menos um caráter distinto para o verbo e um caráter de distinto para o substantivo.</span><span class="sxs-lookup"><span data-stu-id="fa0fe-120">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="fa0fe-121">Adicione mais carateres, conforme necessário para que o alias exclusivo.</span><span class="sxs-lookup"><span data-stu-id="fa0fe-121">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa0fe-122">Veja Também</span><span class="sxs-lookup"><span data-stu-id="fa0fe-122">See Also</span></span>

[<span data-ttu-id="fa0fe-123">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fa0fe-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
