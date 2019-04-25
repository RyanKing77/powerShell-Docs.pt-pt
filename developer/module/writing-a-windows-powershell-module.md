---
title: Escrever um módulo do Windows PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 3c6d8e410427d6cfaa1c15db421b3fe935f7d322
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082061"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="4a09e-102">Writing a Windows PowerShell Module (Escrever um Módulo do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="4a09e-102">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="4a09e-103">Este documento foi escrito para os administradores, desenvolvedores de script e desenvolvedores de cmdlet que precisam para empacotar e distribuir seus cmdlets do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a09e-103">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="4a09e-104">Ao utilizar módulos do Windows PowerShell, pode empacotar e distribuir as suas soluções do Windows PowerShell sem utilizar uma linguagem compilada.</span><span class="sxs-lookup"><span data-stu-id="4a09e-104">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="4a09e-105">Módulos do Windows PowerShell permitem que a partição, organizar e abstraem o código do Windows PowerShell em unidades independentes e reutilizáveis.</span><span class="sxs-lookup"><span data-stu-id="4a09e-105">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="4a09e-106">Com estas unidades reutilizáveis, pode partilhar facilmente os seus módulos diretamente com outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="4a09e-106">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="4a09e-107">Se for um desenvolvedor de script, também pode reempacotar os módulos de terceiros para criar aplicativos personalizados baseados em script.</span><span class="sxs-lookup"><span data-stu-id="4a09e-107">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="4a09e-108">Módulos, semelhantes aos módulos em outras linguagens de script como Perl e Python, ativar soluções de script prontos para produção que utilizam componentes reutilizáveis e redistribuíveis, com o benefício adicional de que lhe permite reempacotar e abstrair vários componentes a Crie soluções personalizadas.</span><span class="sxs-lookup"><span data-stu-id="4a09e-108">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="4a09e-109">Em sua forma mais básica, Windows PowerShell irá tratar qualquer código de script do Windows PowerShell válido guardado num ficheiro. psm1 como um módulo.</span><span class="sxs-lookup"><span data-stu-id="4a09e-109">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="4a09e-110">PowerShell também automaticamente irão tratar qualquer assembly do cmdlet binários como um módulo.</span><span class="sxs-lookup"><span data-stu-id="4a09e-110">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="4a09e-111">No entanto, também pode utilizar um módulo (ou mais especificamente, um manifesto de módulo) para agrupar uma solução inteira.</span><span class="sxs-lookup"><span data-stu-id="4a09e-111">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="4a09e-112">Os seguintes cenários descrevem as utilizações típicas para módulos do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a09e-112">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="4a09e-113">Bibliotecas</span><span class="sxs-lookup"><span data-stu-id="4a09e-113">Libraries</span></span>

<span data-ttu-id="4a09e-114">Módulos podem ser utilizados para empacotar e distribuir bibliotecas coesos de funções que realizam tarefas comuns.</span><span class="sxs-lookup"><span data-stu-id="4a09e-114">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="4a09e-115">Normalmente, os nomes dessas funções partilham um ou mais substantivos que refletem a tarefa comum que são utilizadas.</span><span class="sxs-lookup"><span data-stu-id="4a09e-115">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="4a09e-116">Essas funções também podem ser semelhantes a classes do .NET Framework que podem ter público e membros privados.</span><span class="sxs-lookup"><span data-stu-id="4a09e-116">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="4a09e-117">Por exemplo, uma biblioteca pode conter um conjunto de funções para as transferências de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="4a09e-117">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="4a09e-118">Neste caso, o substantivo que reflete a tarefa comum pode ser "arquivo".</span><span class="sxs-lookup"><span data-stu-id="4a09e-118">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="4a09e-119">Configuração</span><span class="sxs-lookup"><span data-stu-id="4a09e-119">Configuration</span></span>

<span data-ttu-id="4a09e-120">Módulos podem ser utilizados para personalizar o seu ambiente através da adição de cmdlets específicos, provedores, funções e variáveis.</span><span class="sxs-lookup"><span data-stu-id="4a09e-120">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="4a09e-121">Desenvolvimento de código compilado e distribuição</span><span class="sxs-lookup"><span data-stu-id="4a09e-121">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="4a09e-122">Os desenvolvedores do cmdlet e o fornecedor podem utilizar os módulos para testar e distribuir seus códigos compilados sem a necessidade de criar o snap-ins. Importar o assembly que contém o código compilado como um módulo (um módulo de binário) sem a necessidade de criar e registar o snap-ins.</span><span class="sxs-lookup"><span data-stu-id="4a09e-122">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a09e-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="4a09e-123">See Also</span></span>

[<span data-ttu-id="4a09e-124">Noções básicas sobre um módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a09e-124">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="4a09e-125">Como escrever um módulo de Script do PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a09e-125">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="4a09e-126">Como escrever um módulo de PowerShell binário</span><span class="sxs-lookup"><span data-stu-id="4a09e-126">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="4a09e-127">Como escrever um manifesto de módulo do PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a09e-127">How to Write a PowerShell Module Manifest</span></span>](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)

[<span data-ttu-id="4a09e-128">Modificar o caminho de instalação PSModulePath</span><span class="sxs-lookup"><span data-stu-id="4a09e-128">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="4a09e-129">Importar um módulo do PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a09e-129">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="4a09e-130">Instalar um módulo do PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a09e-130">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
