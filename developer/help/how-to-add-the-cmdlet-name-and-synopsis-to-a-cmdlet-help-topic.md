---
title: Como adicionar o nome do Cmdlet e o resumo para um tópico de ajuda do Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850891"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="eb729-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic (Como Adicionar o Nome e Sinopse do Cmdlet a um Tópico de Ajuda de Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="eb729-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="eb729-103">Esta secção descreve como adicionar o conteúdo que é apresentado nas secções nome e o resumo da ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb729-103">This section describes how to add content that is displayed in the NAME and SYNOPSIS sections of the cmdlet help.</span></span> <span data-ttu-id="eb729-104">No ficheiro de ajuda, este conteúdo é adicionado ao nó de comando para cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb729-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="eb729-105">Para obter uma visão completa de um arquivo de ajuda, abra de um dos ficheiros dll Help.xml localizado no diretório de instalação do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb729-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="eb729-106">Por exemplo, o ficheiro de Microsoft.PowerShell.Commands.Management.dll Help.xml contém conteúdo para vários dos cmdlets do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb729-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="eb729-107">Para adicionar o nome do Cmdlet e uma sinopse</span><span class="sxs-lookup"><span data-stu-id="eb729-107">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="eb729-108">O ajuda do cmdlet pode exibir duas descrições para o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb729-108">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="eb729-109">A descrição primeiro é uma breve descrição que é conhecida como o resumo.</span><span class="sxs-lookup"><span data-stu-id="eb729-109">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="eb729-110">A segunda descrição é uma descrição mais detalhada que será discutida [adicionando a descrição detalhada para um tópico de ajuda do Cmdlet](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="eb729-110">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span> <span data-ttu-id="eb729-111">Ambas as descrições dessas devem ser gravadas como um único parágrafo.</span><span class="sxs-lookup"><span data-stu-id="eb729-111">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="eb729-112">Na sinopse não repita o nome do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb729-112">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="eb729-113">Informar o utilizador que o cmdlet Get-Server obtém um servidor é breve, mas não informativos.</span><span class="sxs-lookup"><span data-stu-id="eb729-113">Informing the user that the Get-Server cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="eb729-114">Em vez disso, utilize sinónimos e adicione detalhes para a descrição.</span><span class="sxs-lookup"><span data-stu-id="eb729-114">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="eb729-115">Exemplo: "Obtém um objeto que representa um computador local ou remoto."</span><span class="sxs-lookup"><span data-stu-id="eb729-115">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="eb729-116">Utilize verbos simples, como "get", "Criar" e "alterar" no resumo.</span><span class="sxs-lookup"><span data-stu-id="eb729-116">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="eb729-117">Evite utilizar "set", porque são vaga e palavras bonitas como "modificar."</span><span class="sxs-lookup"><span data-stu-id="eb729-117">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="eb729-118">Exemplo: "Obtém informações sobre a assinatura Authenticode num ficheiro."</span><span class="sxs-lookup"><span data-stu-id="eb729-118">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="eb729-119">Escreva na voz ativa.</span><span class="sxs-lookup"><span data-stu-id="eb729-119">Write in active voice.</span></span> <span data-ttu-id="eb729-120">Por exemplo, "usar o objeto TimeSpan..." é bem mais claro que o "ao objeto TimeSpan pode ser utilizado para..."</span><span class="sxs-lookup"><span data-stu-id="eb729-120">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="eb729-121">Evite o verbo "apresentação" ao descrever a cmdlets que obter objetos.</span><span class="sxs-lookup"><span data-stu-id="eb729-121">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="eb729-122">Embora o Windows PowerShell apresenta os dados de cmdlet, é importante apresentar os utilizadores ao conceito de que o cmdlet devolve objetos do .NET Framework cujos dados podem não ser apresentados.</span><span class="sxs-lookup"><span data-stu-id="eb729-122">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="eb729-123">Se enfatizar a exibição, o utilizador pode não perceber que o cmdlet poderá ter devolvido muitas outras propriedades úteis e métodos que não seja exibidos.</span><span class="sxs-lookup"><span data-stu-id="eb729-123">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb729-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="eb729-124">See Also</span></span>

 [<span data-ttu-id="eb729-125">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eb729-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)